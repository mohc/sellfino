<p align="center"><a href="https://www.sellfino.com" target="_blank" rel="noopener noreferrer"><img width="200" src="https://www.sellfino.com/images/logo.png" alt="Sellfino logo"></a></p>

---

## Introduction

Sellfino **Open Source Shopify App Store** is the PHP & Vue.js based platform with free apps for Shopify and framework for developing custom ones. You can now use and modify apps that do the same work as your paid ones from offical Shopify Store - for free :punch:

#### Support and Contribution

Join our awesome community! Here is how you can connect with us:
- [Website](https://www.sellfino.com) - all info here + live chat
- [Discord](https://discordapp.com/invite/wrFnzZ3) - channels to discuss new ideas and ask for help
- [Messanger](https://m.me/104484064333760) - if you want to chat on Facebook
- [Email](mailto:contact@sellfino.com) - whenever we are out of touch, drop us a message


<img src="https://www.sellfino.com/images/screen.jpg">

## Apps

| | App | Status | Description |
|---------|---------|--------|-------------|
| <img width="30" src="https://www.sellfino.com/images/out-of-stock-icon.png"> | [Out of Stock Manager] | ![ready] | Let your customers know when out of stock products are available again
| <img width="30" src="https://www.sellfino.com/images/metafields.png"> | [Metafields Editor] | ![ready] | Edit metafields for products, collections, store and more
| <img width="30" src="https://www.sellfino.com/images/zero-stock-icon.png"> | [Zero Stock to Hide] | ![ready] | Hides products from your store automatically when out of stock
| <img width="30" src="https://www.sellfino.com/images/preorder-icon.png"> | [Pre-Order Creator] | ![ready] | Manage pre-order & coming-soon products
| <img width="30" src="https://www.sellfino.com/images/low-stock-icon.png"> | Low Stock Watcher | ![doing] | Automate email alerts for low stock products
| <img width="30" src="https://www.sellfino.com/images/3d-icon.png"> | 3D Rotate | ![soon] | Display full perspective of the product in your theme
| <img width="30" src="https://www.sellfino.com/images/faq-icon.png"> | FAQ for Products | ![soon] | Let your customers ask questions and manage the answers
| <img width="30" src="https://www.sellfino.com/images/loyalty-icon.png"> | Loyalty Program | ![soon] | Reward your customers with discounts and other bonuses
| | *More to come* | ![soon] | Join [Discord](https://discordapp.com/invite/wrFnzZ3) and send your ideas for new apps

[Out of Stock Manager]: https://github.com/sellfino/app-out-of-stock-manager
[Metafields Editor]: https://github.com/sellfino/app-metafields-editor
[Zero Stock to Hide]: https://github.com/sellfino/app-zero-stock-to-hide
[Pre-Order Creator]: https://github.com/sellfino/app-preorder-creator

[ready]: https://img.shields.io/badge/ready-success.svg
[doing]: https://img.shields.io/badge/in%20progress-yellow.svg
[soon]: https://img.shields.io/badge/soon-4655FD.svg

## Requirements
- **PHP 7.*** - whole platform is flat-file based so simple hosting should do the work
- **SSL Certificate** - embedded apps are obliged to use https when using API. Either buy one of the SSL Certificates or find hosting with free Let's Encrypt feature (i.e. Bluehost.com)
- **Shopify Partner Account** - you need API keys to authenticate the app
- **Cron** - this is optional, but useful when you need to manage heavy processes (like importing 1k products, sending emails, etc.)
- **Composer** - If you don't have access to *composer*, go [here](https://github.com/sellfino/vendors) and copy everything into the root folder of the platform.

## Installation
#### 1. Shopify Partner Account
- **1.1.** Go to the Shopify Partner website [https://partners.shopify.com](https://partners.shopify.com) and setup your account.
- **1.2.** When it is ready, login to your new account and click *Apps*.
- **1.3.** Now click *Create App*.
- **1.4.** Name your app first (i.e. Sellfino App Store), then provide URL to your hosting, where you will put our platform (in our example: https://your-app-domain.com/).
- **1.5.** In *Whitelisted redirection URL(s)* provide these links (keep both with slash and without at the end):
`
https://your-app-domain.com/auth/shopify/callback
https://your-app-domain.com/auth/shopify/callback/
`
- **1.6.** Click *Create App* button on top bar.
- **1.7.** Copy and save *API key* and *API secret key* - we will use them later in our environment variables.
- **1.8.** Go to the *Extensions* and make sure that *Embedded app* is active (green tick box should be right to this title).

#### 2. Platform setup
- **2.1.** Copy whole code from the Sellfino repository and upload it to your server.
- **2.2.** Run `composer install` in the root folder. If you don't have access to *composer*, go [here](https://github.com/sellfino/vendors) and copy everything into the root. These are all vendors that are needed to run the platform.
- **2.3.** Rename `.env.sample` to `.env` and edit this file.
- **2.4.** Replace API keys with those that you got earlier. Under *HOST* provide URL to your hosting where you put the platform. Under *SCOPE* there are requirements needed to make future apps work - you can remove or add new ones based on what you need. Full list is [here](https://help.shopify.com/en/api/getting-started/authentication/oauth/scopes).
- **2.5.** Point your domain to `public_html` folder in your hosting control panel.

#### 3. Adding stores
- **3.1.** Go to your app's domain (i.e. https://your-app-domain.com) - you should see form to provide URL of store.
- **3.2.** Add store's URL of yours or your client. Remember to use domain with `*.myshopify.com` suffix.
- **3.3.** You should be redirected to your store - accept everything and it's done - you can go to the new master app (Sellfino App Store) and add apps you have. Congratulations! :tada:
- **3.4.** If your or yours client store uses custom domain, you need to add it to the whitelist. After successful installation of the new store, in the root folder of the platform you should see `.domain` file. Add your all domains here and point them to `*.myshopify.com` primary domain of the store. It will filter all of the calls to your server and reject ones not from your stores. Example:
```
"yourdomain.com":"your-store-domain.myshopify.com"
```
- **3.5.** You can add as many stores as you want. Every store has its own folder under `stores` directory and JSON database.

#### 4. Apps
- **4.1.** To install new app, you need to copy folder of this app and put it under `apps` directory.
- **4.2.** When you go to the master app, you should see it in the *Disabled* list. Now you only need to click green button to activate it.
- **4.3.** Go to the *Settings* and provide SMTP details if you want to send emails to your customers.

## Custom apps
Based on the apps that we implemented, you can write your custom ones. Please make sure that you use unique handle - it should be also the same as the app folder's name.

:exclamation: **You can also have apps that are listed for selected stores only.**

To do that, open `info.json` file of the app and add:
```
"private":"client-store.myshopify.com"
```

If you need to show it on multiple stores, separate domains with coma:
```
"private":"client-store.myshopify.com,second-client-store.myshopify.com"
```

Use domains with `*.myshopify.com` suffix.

## Queue
There are some tasks that are quite heavy for server to process - importing large number of products, sending thousends of emails, etc. Without proper solution, you could end with blocked pipeline of action, waiting minutes or more for task to finish, until you could do next thing. We can solve this problem with queues. 

In simple words - instead of running the task immidiately, we postpone it to run it by **Cron**. Here is an example:
- App wants to send email. Instead of sending right the way, platforms saves details of the email and other important things in JSON file, under `queue` folder. You can now do other things in your apps.
- You setup Cron to run **Worker** that checks if there is any task to do - it's being done in the background. If Worker sees there is file in the `queue` folder, it reads it, start the program attached to it and deletes the file after that, so it will not be run in the next round.

Here is the example how the code for Cron should look like (it will run every minute, 24/7):
```
* * * * * php /home/your-app-domain.com/public_html/worker.php
```

## Credits
Here is the list of awesome stuff we used to build our platform:
- [Argon Dashboard](https://www.creative-tim.com/product/argon-dashboard) - one of the most beautiful (and free) dashboard themes
- [Icons8 Animal Icons](https://icons8.com/icon/pack/animals/color) - the whole library of fantastic icons (we use animals because they look cute :heart_eyes_cat:)

## Copyright
Copyright (c) 2019-present, Lucas Szarzynski

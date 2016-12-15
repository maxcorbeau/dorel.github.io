---
layout: manual
title: Wordpress and Polymer setup
category: Use technology
draft: false
---

Wordpress is the main application used for all our branded marketing websites. In this document we zoom in to the Wordpress containers that are defined in [the Container Architecture](./container-architecture.html).

## Overview

![Container Setup](/assets/img/wp-polymer-theme-template-setup.png "Wordpress and Polymer Setup")

## Wordpress Setup

All Wordpress containers are setup with the <code>wp-cli</code>. The use of the <code>wp-cli</code> has several benefits for us, which are:

- *Scripting* - You can put several commands in a text file and have it executed automatically. This way we can standardize certain processes that are used regularly. This also ties in with other services we use to automate the installation process.
- *The keyboard is faster than the mouse* - For power users, typing a command can be orders of magnitude faster than pressing a button in a web browser.

With the <code>wp-cli</code> we install the necesarry assets for our Wordpress setup to exist. The minimum requirements for our Wordpress container are:

- Dorel.io custom theme (not visible for the end user)
- Custom Dorel Pagetemplates
- [ACF Pro Plugin](https://www.advancedcustomfields.com/pro/)
- [ACF WPCLI Plugin](https://github.com/dorel/advanced-custom-fields-wpcli)
- Dorel Custom Fields (ACF import file)
- [WP REST API Plugin](http://v2.wp-api.org/)
- [WP REST API Menus Plugin](https://nl.wordpress.org/plugins/wp-api-menus/)
- [WP ACF TO REST API Plugin](https://nl.wordpress.org/plugins/acf-to-rest-api/)

The Wordpress container will primarily be used as a CMS setup. The [REST API Plugin](http://v2.wp-api.org/) channels all data to our [Polymer SPA](http://www.dorel.io/service-manual/global-design-framework/frontend-SPA.html) where we will handle how a page looks and where components are build up.

### Dorel.io Theme - one to rule them all

Dorel Juvenile WP uses a custom theme. The end user will not be able to switch themes or to disable/enable this theme. The CMS will supply the needs of all our brands out of the box. It will also serve a predefined set of page templates. Each page template has its own standard set of fields. Besides the standard fields the end user can add [predefined components](http://www.dorel.io/service-manual/make-software/creating-Polymer-collect-elements.html). These [predefined components](http://www.dorel.io/service-manual/make-software/creating-Polymer-collect-elements.html) are maintained and created by the ACF plugin.

### ACF Pro Plugin

Dorel Juvenile chose to use the [ACF Pro Plugin](https://www.advancedcustomfields.com/pro/), because it has a wide range of custom fields available and it is highly customizable. With this plugin installed, Dorel Juvenile can create custom field groups and assign them to specific page templates, posts or options pages. The creation of option pages gives Dorel an oppertunity to separate site wide options from other parts of the CMS. It also gives Dorel an easy way to control the custom page builder Dorel needs for different page templates.

The [ACF Pro Plugin](https://www.advancedcustomfields.com/pro/) holds all predefined fields and [custom components](http://www.dorel.io/service-manual/make-software/creating-Polymer-collect-elements.html) a brand needs to build their pages. In the [ACF Pro Plugin](https://www.advancedcustomfields.com/pro/) Dorel specifies which predefined fields and [components](http://www.dorel.io/service-manual/make-software/creating-Polymer-collect-elements.html) can be added to which page templates. There is an options page where main settings can be enabled or disabled.

### ACF WPCLI Plugin

Because the Wordpress platform can only be installed through the <code>wp-cli</code>, we need a way to import/export the custom fields that are created by the [ACF Pro Plugin](https://www.advancedcustomfields.com/pro/). The [ACF WPCLI Plugin](https://github.com/dorel/advanced-custom-fields-wpcli) extends the <code>wp-cli</code> with <code>acf</code> specific commands. Please refer to the [documentation](https://github.com/dorel/advanced-custom-fields-wpcli) of the [ACF WPCLI Plugin](https://github.com/dorel/advanced-custom-fields-wpcli) to find out the exact usage.

### ACF Import file

TBD;

### WP REST API Plugin

At the start of the Dorel Juvenile project Wordpress didn't have REST endpoints build in to its core yet. To enable REST endpoints for Wordpress' content Dorel Juvenile installed the [WP REST API Plugin](http://v2.wp-api.org/). The feature to merge the [WP REST API Plugin](http://v2.wp-api.org/)' code into the Wordpress core is planned later in 2016.

<b>UPDATE:</b> As of 6 December 2016 Automattic released Wordpress 4.7. This update includes merging the code of the [WP REST API Plugin](http://v2.wp-api.org/) into the Wordpress Core. Please check the [release notes](https://wordpress.org/news/2016/12/vaughan/) for more information on this update.

### WP REST API Menus Plugin

The [WP REST API Plugin](http://v2.wp-api.org/) has a lot of endpoints to retrieve Wordpress' content. One of the endpoints that is unfortunately missing is a way to retrieve menus and menu locations. The [WP REST API Menus Plugin](https://nl.wordpress.org/plugins/wp-api-menus/) creates endpoints to do just this.

### WP ACF TO REST API Plugin

The Dorel Juvenile Wordpress Theme relies heavily on the [ACF Pro Plugin](https://www.advancedcustomfields.com/pro/) and the [WP REST API Plugin](http://v2.wp-api.org/) to retrieve its custom content. However out of the box the [WP REST API Plugin](http://v2.wp-api.org/) doesn't have an endpoint to retrieve ACF content, because ACF is a third party plugin. The [WP ACF TO REST API Plugin](https://nl.wordpress.org/plugins/acf-to-rest-api/) adds ACF content to pages and creates endpoints to retrieve option pages fields.

### Polymer Components

[Polymer components](http://www.dorel.io/service-manual/make-software/creating-Polymer-collect-elements.html), like they exist in the kitchensink, can be added by the end user to every page/post template. The CMS has a mandatory area of fields and an area where [components](http://www.dorel.io/service-manual/make-software/creating-Polymer-collect-elements.html) can be added and arranged. The end user needs to fill in the required fields per component and update the page accordingly.

### REST API

[Wordpress' REST API](http://www.dorel.io/service-manual/making-services/how-to-design-RESTful-APIs.html) is called upon in the [Polymer SPA](http://www.dorel.io/service-manual/global-design-framework/frontend-SPA.html). The API call for a page, for example, will return data that builds up the page demanded by the visitor. The [Polymer SPA](http://www.dorel.io/service-manual/global-design-framework/frontend-SPA.html) routing will lead to the right page template and loads the [components](http://www.dorel.io/service-manual/make-software/creating-Polymer-collect-elements.html) defined by the end user in the Wordpress CMS. More info on the complete [REST API](http://www.dorel.io/service-manual/making-services/how-to-design-RESTful-APIs.html) can be found [here](http://v2.wp-api.org/).



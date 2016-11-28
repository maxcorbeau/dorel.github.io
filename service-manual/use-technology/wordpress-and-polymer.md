---
layout: manual
title: Wordpress and Polymer setup
category: Use technology
draft: true
---

Wordpress is the main application used for all our branded marketing websites. In this document we zoom in to the Wordpress containers that are defined in [the Container Architecture](./container-architecture.html).

## Overview

![Container Setup](/assets/img/wp-polymer-theme-template-setup.png "Wordpress and Polymer Setup")

## Wordpress Setup

All Wordpress containers are setup with the <code>wp-cli</code>. The use of the <code>wp-cli</code> has several benefits for us, which are:

- *Scripting* - You can put several commands in a text file and have it executed automatically. This way we can standardize certain processes that are used regularly. This also ties in with other services we use to automate the installation process.
- *The keyboard is faster than the mouse* - For power users, typing a command can be orders of magnitude faster than pressing a button in a web browser.

With the <code>wp-cli</code> we install the necesarry assets for our Wordpress setup to exist. The minimum requirements for our Wordpress container are:

- Dorel.io Theme
- Custom Dorel Pagetemplates
- [ACF Pro Plugin](https://www.advancedcustomfields.com/pro/)
- Dorel Custom Fields (ACF import file)
- [WP REST API Plugin](http://v2.wp-api.org/)
- [SAML SSO Plugin](https://wordpress.org/plugins/saml-20-single-sign-on/installation/)

### Dorel.io Theme - one theme to rule them all

We've created one custom theme to supply the needs of all our brands. The custom theme serves all standard page templates. Each page template has its own standard set of fields. Besides the standard fields the end user can add predefined components. These predefined components are maintained and created by the ACF plugin.

### ACF Pro Plugin

Dorel Juvenile chose to use the ACF Plugin, because it has a wide range of custom fields available and it is highly customizable. With the plugin in Dorel Juvenile can create custom field groups and assign them to specific page templates, posts or options pages. The creation of option pages gives Dorel an oppertunity to separate site wide options from other parts of the CMS. It also lets Dorel Juvenile disable or enable Wordpress' CMS features. 

For the Dorel theme the ACF Pro Plugin holds all predefined fields and custom components a brand needs to build their pages. In the ACF plugin Dorel specifies which predefined fields and components can be added to which page templates. There is an options page where main settings can be enabled or disabled. More info can be found [here](https://www.advancedcustomfields.com/pro/).

### Polymer Components

Polymer components, like they exist in the kitchensink, can be added by the end user to every page/post template. The Dorel.io theme has a mandatory area of fields and an area where components can be added and arranged. The end user needs to fill in the required fields per component and update the page accordingly.

### REST API

Wordpress' REST API is called upon in the Polymer SPA. The API call for a page, for example, will return data that builds up the page demanded by the visitor. The Polymer SPA routing will lead to the right page template and loads the components defined by the end user in the Wordpress CMS. More info on the complete REST API can be found [here](http://v2.wp-api.org/).



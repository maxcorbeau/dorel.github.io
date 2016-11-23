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
- ACF Pro Plugin
- Dorel Custom Fields (ACF import file)

### Dorel.io Theme - one theme to rule them all

We've created one custom theme to supply the needs of all our brands. The custom theme serves all standard page templates. Each page template has its own standard set of fields. Besides the standard fields the end user can add predefined components. These predefined components are maintained and created by the ACF plugin.

### ACF Pro Plugin

The ACF Pro Plugin holds all predefined fields and custom components a brand needs to build their pages. In the ACF plugin Dorel specifies which predefined fields and components can be added to which page templates. 

### Polymer Components

Polymer components, like they exist in the kitchensink, can be added by the end user to every page template. The Dorel.io theme has a mandatory area of fields and an area where components can be added and arranged. The end user needs to fill in the required fields per component and update the page accordingly.

### REST API

Wordpress' REST API is called upon in the Polymer SPA. The API call for a page, for example, will return data that builds up the page demanded by the visitor. The Polymer SPA routing will lead to the right page template and loads the components defined by the end user in the Wordpress CMS.



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

1. We can manage our Wordpress installation in a bash script
2. Less steps need to be taken to make our WP installation work

With the <code>wp-cli</code> we install the necesarry assets for our Wordpress setup to exist. The minimum requirements for our Wordpress container are:

- Dorel.io Theme
- Custom Dorel Pagetemplates
- ACF Pro Plugin
- Dorel Custom Fields (ACF import file)

### Dorel.io Theme - one theme to rule them all

We've created one custom theme to supply the needs of all our brands. The custom theme serves all standard page templates. Each page template has its own standard set of custom fields. Besides the standard fields the end user can add predefined components. These predefined components are handled and created by the ACF plugin. Inside the ACF plugin new components and the fields that are mandatory can be created.

### ACF Pro Plugin

The ACF Pro Plugin holds all predefined fields and custom components a brand needs to build their pages. 

### Polymer Components

Polymer components, like they exist in the kitchensink, can be added by the end user to every page template. The Dorel.io theme has an area and a button where components can be added and arranged. The end user needs to fill in the fields required per component and update the page accordingly.


TBD;

All Wordpress containers are setup with the <code>wp-cli</code>. There are two main reasons:

- *Scripting* - You can put several commands in a text file and have it executed automatically. This way we can standardize certain processes that are used regularly. This also ties in with other services we use to automate the installation process.
- *The keyboard is faster than the mouse* - For power users, typing a command can be orders of magnitude faster than pressing a button in a web browser.

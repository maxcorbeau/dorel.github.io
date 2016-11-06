---
layout: manual
title: Wordpress and Polymer
category: Use technology
draft: true
---

Wordpress is the main application used for all our branded marketing websites. The following diagram will explain in detail how Wordpress is setup in combination with the Polymer building blocks. In this document we zoom in to the Wordpress containers that are defined in [the Container Architecture](./container-architecture.html).

## Overview

![Container Setup](/assets/img/wp-polymer-setup.png "Wordpress and Polymer Setup")

## Wordpress Setup

All Wordpress containers are setup with the <code>wp-cli</code>. The use of the <code>wp-cli</code> has several benefits for us, which are:
1. We can manage our Wordpress installation in a bash script
2. Less steps need to be taken to make our WP installation work

The minimum requirements for our Wordpress container are:
- Dorel.io Theme
- ACF Pro Plugin
- Polymer Components

### Dorel.io Theme - one theme to rule them all

We've created one custom theme to supply the needs of all our brands. The custom theme serves all predefined page templates. Page templates defines it's layout. Clients can choose between a one column page, two column page or a page with content and a sidebar.

### ACF Pro Plugin

A page template alone is not of any use yet. The page now only has a layout. We can enrich these pages with building blocks.

### Polymer Components

TBD;

All Wordpress containers are setup with the <code>wp-cli</code>. There are two main reasons:

- *Scripting* - You can put several commands in a text file and have it executed automatically. This way we can standardize certain processes that are used regularly. This also ties in with other services we use to automate the installation process.
- *The keyboard is faster than the mouse* - For power users, typing a command can be orders of magnitude faster than pressing a button in a web browser.

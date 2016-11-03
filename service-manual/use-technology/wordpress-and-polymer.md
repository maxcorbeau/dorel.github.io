---
layout: manual
title: Wordpress and Polymer
category: Use technology
draft: false
---

Wordpress is the main application used for all our branded marketing websites. The following diagram will explain in detail how Wordpress is setup in combination with the Polymer building blocks. In this document we zoom in to the Wordpress containers we've defined in [the Container Architecture](./container-architecture.html).

_Note: click [here](./cms-cloud-architecture.html) for the cloud architecture_

## Overview

![Container Setup](/assets/img/wp-polymer-setup.png "Wordpress and Polymer Setup")

## Wordpress Setup

All Wordpress containers are setup with the <code>wp-cli</code>. There are two main reasons:

- *Scripting* - You can put several commands in a text file and have it executed automatically. This way we can standardize certain processes that are used regularly. This also ties in with other services we use to automate the installation process.
- *The keyboard is faster than the mouse* - For power users, typing a command can be orders of magnitude faster than pressing a button in a web browser.

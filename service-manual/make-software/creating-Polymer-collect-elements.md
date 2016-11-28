---
layout: manual
title: Creating Polymer collect elements
category: Make software
draft: false
---

As described in [Dorel Juvenile's platform strategy](/service-manual/vision/platforms-and-ecosystems.html) all platforms should have [RESTful APIs](/service-manual/making-services/how-to-design-RESTful-APIs.html) which should be addressable from other platforms. In the case of web applications, the API based information will be distributed through [Polymer](http://polymer-project.org).

The usage of frontend-SPA's is described here: [Single Page Application](/service-manual/global-design-framework/frontend-SPA.html)

## Collect element

Every platform should have its own element. For example, Magento has a Magento Element, Wordpress a Wordpress Element and so on. Elements to collect information are called Collect Elements.

Examples are:

- [Magento Collect](https://github.com/bobvanluijt/magento-collect)
- [Wordpress Collect](https://github.com/dorel/wordpress-collect)
- PIM Collect

## Designing an element

All elements start with the name of the platform followed by the verb collect. For example: `magento-collect`. Next, the element describes the information it is collecting.

For example:

- `magento-collect-products`
- `magento-collect-carts`

_Note how this is often the first plural nouns of the endpoint_

For more information about designing RESTful APIs within Dorel Juvenile: [How to design RESTful APIs](/service-manual/making-services/how-to-design-RESTful-APIs.html)

## In-depth architecture per element

All elements should have detailed architectural styles inside its repository readme files.

Example:  [Magento Collect](https://github.com/bobvanluijt/magento-collect/blob/develop/README.md)

## Extending the front-end object

The frontend object should cache results retrieved from the APIs during a session. Detailed information can be found [here](http://www.dorel.io/service-manual/global-design-framework/frontend-SPA.html#example).
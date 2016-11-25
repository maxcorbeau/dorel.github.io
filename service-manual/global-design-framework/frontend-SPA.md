---
layout: manual
title: Single Page Application
category: Global Design Framework
draft: false
---

Dorel Juvenile's front-end architecture is based on two core principles. Firstly, Dorel Juvenile's [platform and ecosystems strategy](/service-manual/vision/platforms-and-ecosystems.html), and secondly the [single-page application (SPA)](https://en.wikipedia.org/wiki/Single-page_application) to give users the experience of using a native mobile / desktop application. Practically this means that all Javascript, HTML, and Cascading style sheet (CSS) files are hosted as a static platform-application itself.

General rules for the hosting of the application files:

- All files are set as non-dynamic content as described on the [cloud architecture page](/service-manual/use-technology/cms-cloud-architecture.html).
- The [SPA and framework](/service-manual/global-design-framework/atomic-design.html) is the source of the domain of a website. When the framework is updated, the [Point of Presence (PoP) locations](https://peering.google.com/#/infrastructure) will be invalidated. For more information see [&para; Scoping of platforms bullet point 2](/service-manual/use-technology/cms-cloud-architecture.html).
- The platform is the content delivery platform. Meaning that there is no middleware to deliver the content from the server to the PoP locations.
- For more information on the URL structures of all platforms, read [&para; Scoping of platforms](/service-manual/use-technology/cms-cloud-architecture.html).

## Polymer

Dorel Juvenile uses [W3C](https://w3.org) standard based [web components](https://en.wikipedia.org/wiki/Web_Components) in the form of the [Polymer library](https://www.polymer-project.org/). This means that all the applications build inside the Dorel IO ecosystem are defined as single-page applications (SPA).

## PRPL pattern

Dorel Juvenile uses the [PRPL pattern](https://www.polymer-project.org/1.0/toolbox/server#prpl-pattern) and HTTP2 to deliver content to the SPA. A diagram of the architecture including the SPAs are available on the [container architecture](/service-manual/use-technology/container-architecture.html) page.

## Polymer elements for integrating with Dorel Juvenile's platforms. 

Dorel Juvenile's [platform and ecosystems strategy](/service-manual/use-technology/container-architecture.html) defines platforms as having RESTful API's and being single purpose. That means that every data source is on a specific platform serving a specific service. Examples of platform services are; e-commerce, CMS content, analytics, etcetera.

Every platform should have their own element. A page can have multiple elements to request content from different API's.

## Scoping REST API data

Every data request should extend the `window._collect` object, followed by a four letter abbreviation and a key if needed. Everything after this should follow the path of the RESTful API definition.

Two important architectural directions to bear in mind when creating new custom elements:

- In case an API supports filtering, the filter should be set to only request the information needed. In the example below only the `name`, `weight` and `bundle_product_options` information is requested.
- Requesting information through an element should be possible in two ways; *soft* and *hard*. Soft means that a request will first travel through the `_collect` object and use the information if it already exists. Hard means that it will always collect it from the API.

_Soft_ request might be product information details and _hard_ requests might be shopping cart information.

The collect object can be addressed through binding or through handlebars within a collect element like: `{{ MAGE.name }}`.

### Collect Elements

Collect elements collect the information from the responsible REST API's.

- [Magento Collect](https://github.com/dorel/magento-collect)
- [Wordpress Collect](https://github.com/dorel/wordpress-collect)

### Example

The example below shows the inclusion of both Magento 2 and Wordpress information.

```
{
  window: { // window object for the global scope
    _collect: { // private collect object
      MAGE: { // object representing a platform, in this case Magento 2
        "/V1/product/test123": { // API endpoint, note how the object represents the Magento 2 JSON schema
          name: "Test Product",
          weight: 123,
          extension_attributes: {
            bundle_product_options: [{
              option_id: 1,
              title: "some title",
            }]
          }
        }
        WRPS: { // object representing a platform, in this case Wordpress
          "/categories/0": { // API endpoint, note how the object represents the Wordpress JSON schema
            id:1,
            link:"Some url"
          },
          "/posts/1": {
            date:"2016-11-18T16:09:51.328Z",
            id:0
          }
        }
      }
    }
  }
}
```

- [Magento 2 JSON schema](http://devdocs.magento.com/swagger/)
- [Wordpress JSON schema](https://app.swaggerhub.com/api/starfishmod/Wordpress/0.1.0)

## Search engine optimization (SEO) and JSON-LD

All pages should contain the correct [JSON-LD](http://json-ld.org/) information.
---
layout: manual
title: Cloud Architecture
category: Use technology
draft: false
---

Dorel Juvenile leverages the power of the Google Cloud to bring webservices as fast as possible to the end-users.

_Note: click [here](./container-architecture.html) for the container architecture_

## Platforms

As defined in the [holistic strategy](../../strategy/holistic), Dorel Juvenile uses a platform strategy to connect all services. Thoese services are delivered through their respective APIs and can be consumed by other platforms.

## Scoping and configuration of platforms

As shown in the [container architecture diagram](/service-manual/use-technology/container-architecture.html), the domain scoping will be as follows:

- All containers that have RESTful API's exposed should have the following domain setup: [API name].api.[subdomain].[domain].[top-level domain]. For example: mage.api.www.maxicosi.com for the Magento 2 RESTful API.
- The only exception is the Single Page Application (SPA). This application should be available through: [subdomain].[domain].[top-level domain].

Also note that the following rule applies to the source code: _"All containers should have source code implemented from one unique Github Repository"_. Meaning that every container should have -in case needed- its own Github Repository.

## Leveraging Point of Presence and Content Delivery Network locations.

Google Cloud consists of a [large network of PoP locations](https://peering.google.com/#/infrastructure) that Dorel Juvenile uses to deliver content to customers as quick as possibe. To learn more about the Google Cloud CDN concept visit [this page](https://cloud.google.com/cdn/docs/caching).

Dorel Juvenile defines content as follows:
- Non-dynamic
- Semi-dynamic
- Super-dynamic

### Non-dynamic content

Non-dynamic content is often in the form of Javascript, Cascading Style Sheets and images.

Headers:

```
Expires: 1y;             # Expires after one year
Cache-Control: "public"; # Enable cache for PoP locations
```

### Semi-dynamic content

Semi-dynamic content is often in the form of dynamically generated posts that have an approximate lifetime longer than a day. For example a product page or a blog post. This can also be in the form of an API response.

_Note: this content should be [invalidated](https://cloud.google.com/cdn/docs/invalidating-cached-content) when it is updated._

Headers:

```
Expires: 233s;           # Expires after the average web visit time
Cache-Control: "public"; # Enable cache for PoP locations
```

### Super-dyamic content

Super dynamic content is content that needs a server interaction to render. An example might be dynamic pricing, a shopping cart or a checkout process.

Headers:

```
Expires: 0;                # Expires after the average web visit time
Cache-Control: "no-cache"; # Enable cache for PoP locations
```

### Expire headers

There are three types of expires headers:

- on = always 1 year: `1y`
- semi-on = always the average visiting time. Currently 233 seconds, `233s`
- off = `0`

### Setup

![Content Delivery Setup](/assets/img/gcloud-loadbalance-architecture.png "Content Delivery Setup")
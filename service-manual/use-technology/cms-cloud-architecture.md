---
layout: manual
title: CMS Cloud Architecture
category: Use technology
draft: false
---

{% include breadcrumbs.html %}

Dorel leverages the power of the Google Cloud to bring webservices as fast as possible to the end-users.

_Note: click [here](./container-architecture) for the container architecture_

## Platforms

As defined in the [holistic strategy](../../strategy/holistic), Dorel uses a platform strategy to connect all services. Thoese services are delivered through their respective APIs and can be consumed by other platforms.

## Leveraging Point of Presence and Content Delivery Network locations.

Google Cloud consists of a [large network of PoP locations](https://peering.google.com/#/infrastructure) that Dorel uses to deliver content to customers as quick as possibe. To learn more about the Google Cloud CDN concept visit [this page](https://cloud.google.com/cdn/docs/caching).

Dorel defines content as follows:
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
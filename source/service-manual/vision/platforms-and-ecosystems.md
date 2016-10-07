---
layout: manual
title: Platforms and Ecosystems
category: Vision
draft: false
---

{% include breadcrumbs.html %}

For platforms and ecosystems, Dorel uses custom definitions based on generally accepted terms. Things that are not fetchable in one of these two categories are often applications (see below).

All new services Dorel uses should meet the platform and ecosystem requirenements.

## Definition of a platform

A platform is a service that can run with _any_ provider on _any_ location and should meet the following requirements.

1. *A platform has an API*. Preferably using generally accepted architectural styles such as RESTful. Platforms have integrations that are generally accepted as bad practices, like batch jobs, are avoided.
2. *Technology Agnostic*. If the above requirenment is met, we do not care about what technology runs the service.
3. *Scalable*. We expect the service to scale regardless of our usage.

Dorel uses these measurements regardless of these services run inhouse or at a Platform as a Service provider. Different platforms can be hosted at different providers or inhouse.

## Definition of an ecosystem

A combination of platforms define the ecosystem.

An ecosystem is identified based on the following requirements;

1. *Adaptive*. The ecosystem changes over time and should be adaptive to all platforms that meet the platform requirenments.
2. *Self-organising*. The ecosystem changes over time, different sets of platforms create different ecosystems.
3. *Open*. The platform can always be extended with other platforms or sub-ecosystems.

_Important: Dorel avoids third party walled gardens. Meaning that access to ecosystems are restricted. This would be concidered an anti-pattern!_

## Definition of an application

On top of a platform, an application can be build. An application often has the form of a website, app or physical device. An application is identified based on the following requirements.

1. The application is itself a platform (see platform requirements).
2. The application is build on top of a platform.

_Important: Note, that an application can exsist without a platform. But that this would be concidered an anti-pattern! Every application should have / use proper platforms_

## Example

An example of a platform and an application.

### Magento, an e-commerce platform

Following Dorel's platform definitions, Magento 1.x is _not_ a platform but only an application. Because of the RESTful API interface in Magento 2. Magento became a hybrid, an application _and_ a platform. Read more about how Dorel uses Magento 2 [here](./technology/ecommerce-container-architecture).

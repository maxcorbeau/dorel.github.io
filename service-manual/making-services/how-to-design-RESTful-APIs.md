---
layout: manual
title: How to design RESTful APIs
category: Making Services
draft: false
---

One of the most important definitions of the [Dorel Juvenile platform strategy](/service-manual/vision/platforms-and-ecosystems.html) entails the usages of Application Programming Interfaces, better known as APIs.

This means that all platforms should have API's that follow the [RESTful architecture](https://en.wikipedia.org/wiki/Representational_state_transfer), regardless if they are created internally or externally.

When you need to create RESTful APIs for your own platform, you should follow these guidelines.

## Use Swagger (Open API Initiative) documentation

[Dorel Juvenile's Swagger Github Repo.](https://github.com/dorel/API-swaggers)

All API's should be defined using the Swagger 2.0 documentation style.

More information:

- [Swagger.io](http://swagger.io)

## Take immutability into account

- Safe methods are HTTP methods that do not modify resources.
- An idempotent HTTP method is aN HTTP method that can be called many times without different outcomes

| **HTTP Method** | **Idempotent** | **Safe** |
| OPTIONS	      | yes            | yes      |
| GET             | yes            | yes      |
| HEAD            | yes            | yes      |
| PUT             | yes            | no       |
| POST            | no             | no       |
| DELETE          | yes            | no       |
| PATCH           | no             | no       |

More information:

- [Idempotency](http://www.restapitutorial.com/lessons/idempotency.html)
- [PUT VS POST](http://restcookbook.com/HTTP%20Methods/put-vs-post/)

## Use (plural) nuons

Example:

| **Resource**   | **GET**                  | **POST**        | **PUT**                 | **DELETE**              |
| products       | Returns list of products | Creates product | Not used or update bulk | Not used or delete all  |
| /products/{id} | Gets specific product    |  Not used       | Updates product         | Deletes product         |

## Apply filtering, sorting, field selection and paging for collections

Example:
`GET /products/{id}?fields=color,name`

Example:
`GET /products/{id}?offset=10&limit=5`

## API versioning

Always version APIs using Semver prefixed with 'v' in the URL.

Example:
`GET https://api.dorel.io/someApi/v1.0.0/products`

## Use proper HTTP status codes

```
200 – OK – Eyerything is working
201 – OK – New resource has been created
204 – OK – The resource was successfully deleted
304 – Not Modified – The client can use cached data
400 – Bad Request – The request was invalid or cannot be served. The exact error should be explained in the error payload. E.g. „The JSON is not valid“
401 – Unauthorized – The request requires an user authentication
403 – Forbidden – The server understood the request, but is refusing it or the access is not allowed.
404 – Not found – There is no resource behind the URI.
422 – Unprocessable Entity – Should be used if the server cannot process the enitity, e.g. if an image cannot be formatted or mandatory fields are missing in the payload.
500 – Internal Server Error – API developers should avoid this error. If an error occurs in the global catch blog, the stracktrace should be logged and not returned as response.
```
---
layout: manual
title: JavaScript Track Method
category: Analytics
draft: false
---

This article describes the `dorel.track` method, which is part of the [SPA Javascript library](/service-manual/global-design-framework/frontend-SPA.html).

## What it is ##

The method is nothing less than a wrapper for GTM `dataLayer.push` method. The reason for using a wrapper instead of the `dataLayer.push` directly is that:
 
  - Our `track` calls remain vendor-neutral
  - Should we need to add analytics functionality to the method or switch from GTM to another data collection tool (e.g. segment.com), it can be done with 1 single change by modifying the `track` wrapper method.
 
```
track: function(data) {
	var dataLayer = dataLayer || [];
	dataLayer.push(data);
} 
```

## General rules ##

A few rules when using the `dorel.track` method:
 
 - the function MUST take 1 parameter and 1 parameter only (`data`)
 - the `data` parameter MUST be an object (dataLayer model constraint)
 - the `data` parameter MUST have the `event` property defined (to be used as trigger in `GTM`)
 
## Use Cases ##

### API calls ###

Sample code showing how to track data when making API calls

```
// after response is received from the API
var data = {
  event: 'api_called',
  request: request, // request = parameters used to query the API
  response: response, // response = data received from API
}
track(data)
```

### JSON-LD information ###

Sample code showing how to track data inserted into the JSON-LD tag

```
// after JSON-LD data is available
var data = {
  event: 'json_loaded',
  parameters: obj // obj = JSON-LD data in an object format
}
```
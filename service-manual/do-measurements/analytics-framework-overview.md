---
layout: manual
title: Analytics Framework Overview
category: Do Measurements
draft: false
---

## Background ##
The objective is to deliver Analytics as a Service (AaaS) so that business units can gather insights about applications and their users without the need to implement analytics themselves. This process will be done in phases:

 1. **MVP ('17Q1)**:  based on Google Analytics/Tag Manager and the new Dorel.io framework 
 2. **Extension (TBD)**: to offer analytics capabilities (e.g. predictive) Google Analytics doesn't offer.

## Steps involved ##

Several steps are needed to go from the data we collect to the insights we deliver. Those steps are discussed in more details further below in this document. Here is an overview:

![Analytics Levels](/assets/img/analytics-levels.png "Analytics Levels")

## Application level ##

### 1- Data Collection ###

For this step we need 2 ingredients:

 - **data**: (obviously) this can be data of different nature (user data, product data...) and different sources (Wordpress API, Magento API, HTML code...)
 - **triggers**: to know when this data is available (a user submitted a form, the page is being loaded.... note: we're building applications that are more and more dynamic, so most data isn't available when the page is being loaded)

Regarding the data ingredient, we must take into consideration the following principles:

 - **Business needs constantly evolve**:  Therefore our data collection process has to have as little business rules as possible, otherwise, we will constantly be changing our data collection process
 - **You cannot go back in time to collect volatile data** (like a lot of the analytics data is) you didn't collect: therefore, it's better to grab extra data, even if it looks like you don't need it at the time, as it might become handy in the future
 - **We have data model constraints** imposed by certain analytics tools (e.g. Google Analytics e-commerce data has to be formatted a specific way): therefore, we need to format the data at some point so it can be used by the Analytics tools
 - **Data should be open** in order to make switching or integrating other data collection processes harder in the future: therefore, we need to separate the data collection process into 2 phases, a data presentation phase where data remains in open format, vendor-agnostic format, and a data-formatting phase where we comply with vendor's data model requirements

![Data Collection Split](/assets/img/analytics-levels-01-data-collection-split.png "Data Collection Split")

**Tooling Decision: Google Tag Manager**
The data collection layer will be handled by Google Tag Manager because:

 - it's already in used within Dorel
 - it's free
 - it's robust (Google)
 - it's widely used ([1.7M websites to date](https://trends.builtwith.com/widgets/tag-management), can leverage community support)
 - it has built-in version control
 - it has a UI with built-in helpers (reduces the amount of custom work required)
 - it's lightweight (the default JavaScript file size is very minimal, our job it is to keep that as low as possible)

GTM works in 2 modes:

 - **pull**: you define triggers and collect data from within GTM (with JavaScript)
 - **push**: data is being pushed to GTM via JavaScript using the `dataLayer` , which in our case will be handled via the `dorel.track` method.

Putting all the pieces together, the data collection layer looks as follows:

![Data Collection Details](/assets/img/analytics-levels-01-data-collection-details.png "Data Collection Details")


## Analytics solution side ##

**Tooling Decision**
The Analytics side will be handled by Google Analytics because:

 - it's already in used within Dorel
 - it's free
 - it's robust (Google)
 - it satisfies most reporting needs at the moment

Note: other analytics solutions can easily be added in the future by simply adding routines to Google Tag Manager to send the collected data to those new solutions (e.g. our own databases on Amazon or Google Cloud to have complete freedom to analyze and report on the data the way we want without any of the constraints of the current analytics tools).

*documentation reminder: as we add solutions to our analytics stack in the future, using tables to clearly highlight the benefits/limitations of each solution at each step of the analytics process is advised.*

### 2 - Data Storage ###

Done by Google Analytics. [We must bear in mind the 10 million hits per month property limit](https://developers.google.com/analytics/devguides/collection/ios/v3/limits-quotas) and monitor our traffic to upgrade to Google Analytics 360 if needed.

### 3 - Data cleanup ###

Google Analytics offers (very limited) data cleanup possibilities through the use of filters. The problem with using Google Analytics filters is that it's irreversible (e.g. previously collected data cannot be fixed if the wrong filters were used, only newly collected data can), therefore the recommendation is to limit the use of filters to a minimum (ideally none) and handle filtering at reporting layer whenever possible.

### 4 - Data Enrichment ###

We plan on enriching the Google Analytics data with offline and marketing data from other sources using the [Google Analytics Data Import feature](https://support.google.com/analytics/answer/3191589?hl=en) and potentially other tools such as [Funnel.io](https://funnel.io).

### 5 - Data Analysis ###

Analysis capabilities will be those provided by Google Analytics or other reporting tools we might choose (e.g. Funnel.io). We can also leverage the [Google Analytics Reporting API](https://developers.google.com/analytics/devguides/reporting/core/v4/) to download and analyze the data with our own internal resources. However the API has limitations on the number of dimensions and metrics that can be retrieved, making it difficult if not impossible to reconstruct the user/session data. If the business need is to analyze the data freely, then the solution doesn't sit with Google Analytics but with sending a copy of our analytics data to our own data wharehouse.

### 6 - Reporting ###

Different reporting solutions are currently being evaluated (e.g. [Funnel.io](https://funnel.io), [Supermetrics](https://supermetrics.com), [Klipflio](https://www.klipfolio.com), [Tableau](http://www.tableau.com), [Oogst Online](http://www.oogstonline.nl)) to determine what is the best fit for Dorel.

Some level of manual work will be needed to setup the basic reporting dashboards, with the goal that the reporting should be flexible and simple enough to allow for self-service reporting covering most needs of business units.
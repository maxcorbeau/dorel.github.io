---
layout: manual
title: Dimensions
category: Analytics
draft: false
---

## What are dimensions? ##

Dimensions are qualitative information that describe the data (e.g. country, language, brand, product type), as opposed to metrics (e.g. # visits, revenue...) which quantify it.

## Why are they important? ##

### For Analytics ###

Dimensions allow you to segment your data to identify patterns or differences from which you can further investigate.

For instance if you look at a metric by itself, it's pretty useless:

| METRIC (e.g. conversion rate) |
|:-----------------------------:|
|              15%              |

Now if you start to segment by the `Marketing Channel` dimension, things get more interesting:

| DIMENSION (e.g. Marketing Channel) | METRIC (e.g. conversion rate) |
|:----------------------------------:|:-----------------------------:|
| Google                             |              15%              |
| Bing                               |              15%              |
| Linkedin                           |              30%              |
| Facebook                           |              10%              |
| Twitter                            |              10%              |

Now suddenly you can see that certain channels perform better, and others worse, and you can keep segmenting to find out why (does it have to do with the `landing page` people land on, the `content` of our campaigns on these channels?...

### Dimensions impact business as a whole ###

You never design just for Analytics. If you measure it, it's because it matters to the business. In the end, your dimensions represent data that matters to the business and is used and disseminated at various levels:

 - **SEO**:  some of your dimensions will be used in various ways (`JSON-LD`, `Schema`) to help Search Engines crawl and understand your content.
 - **Content teams**:  dimensions can help content teams tag the content to help with inventory and maintenance.
 - **CMS**:  if content editors need to input values for those dimensions, specific fields must be made available via the CMS.
 - **Design**: if the technical solution to provide values for dimensions is to have them pre-filled at design template level, then suddenly dimensions are impacting your template creation process.
 - **etc...**

## How to create those dimensions? ##

Creating dimensions is performed in 2 steps:

 1. **Inventory**: make a list of dimensions that are releveant to the business (see list further below) so you can plan their implementation.
 2. **Implementation**: create a process so that the right values are consistently fed to those dimensions at each level (analytics, SEO, content creation...).

## Inventory ##

The current list of dimensions is appended below. The reason for having 20 dimensions is because it is a hard limitation we have from Google Analytics which remains our main reporting tool. `FREE SLOT` are dimensions we haven't assigned yet but wan't to keep open for future use. Some dimensions are there solely for technical reasons (e.g. Optimizely integration).

| Id |       Category      | Dimension           | Value                                                                                                                                                                                                                                                         | Example                                            | Why use it?                                                                                                                                      | SCOPE     |
|:--:|:-------------------:|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| 1  |         User        | ID                  | Unique ID coming from user database when user is authenticated                                                                                                                                                                                                | 123456778                                          | Track authenticate users across websites/devices                                                                                                 | USER      |
| 2  |         User        | Type                | User Type as per CRM segmentation                                                                                                                                                                                                                             | Reseller, Consumer, Prospect...                    | Analyze behaviour based on user type                                                                                                             | USER      |
| 3  |         User        | Login state         | Whether user is logged in or not                                                                                                                                                                                                                              | Logged in / Logged out                             | Understand to what extent we are able to keep users authenticated with Dorel services (important condition to providing a customized experience) | USER      |
| 4  |         User        | FREE SLOT           | TBD                                                                                                                                                                                                                                                           | TBD                                                | TBD                                                                                                                                              | USER      |
| 5  |        Brand        | Name                | Brand name as defined by business                                                                                                                                                                                                                             | Quinny, Maxi Cosi...                               | Measure brand performance                                                                                                                        | USER      |
| 6  | Location            | Country             | ISO_3166-1_alpha-2 country code. Use "ALL" if not targeted at a specific country                                                                                                                                                                              | FR,UK....                                          | Measure country performance                                                                                                                      | PAGE      |
| 7  | Content             | Primary             | Although pages might be composed of various components of different types (e.g. Product, FAQ...) we want to                                                                                                                                                   | Product, Article, FAQ,.....                        | Measure influence of primary content items on performance                                                                                        | PAGE      |
| 8  | Content             | Page Name           | As web still relies heavily on URLs as navigation/reference point. We cannot rely on the URsL because they are language-specific and change over time. We need a new dimension that identifies a page in a unique, persistent, cross-language fashion         | Homepage, Support Contact Page, Product A page     | Measure page performance at global level                                                                                                         | PAGE      |
| 9  | Content             | Language            | Language+region code as defined in the HTML hreflang tag. Reason for taking into account this localized version of a language is because of very international position of Dorel and significant differences within the same language "family" (e.g. English) | be-NL,nl-NL,en-GB                                  | Measure language performance                                                                                                                     | PAGE      |
| 10 | Content             | Topic               | First categorization level of content                                                                                                                                                                                                                         | Product, Service, Warranty, Safety, Marketing, R&D | Measure content performance based on the topic                                                                                                   | COMPONENT |
| 11 | Content             | FREE SLOT           | TBD                                                                                                                                                                                                                                                           | TBD                                                | TBD                                                                                                                                              | COMPONENT |
| 12 | Design              | Template            | Template name                                                                                                                                                                                                                                                 | 2-column template                                  | Measure design performance                                                                                                                       | TEMPLATE  |
| 13 | Design              | Position            | Indication of position within template                                                                                                                                                                                                                        | 1-1 (first column, first block)                    | Measure component performance based on its position within a template                                                                            | TEMPLATE  |
| 14 | Product / Accessory | Name                | Product name                                                                                                                                                                                                                                                  | Pebble Plus                                        | Measure performance on a product level                                                                                                           | COMPONENT |
| 15 | Product / Accessory | Variant             | Product variant                                                                                                                                                                                                                                               | Pebble Plus RED                                    | Understand how variants perform across products                                                                                                  | COMPONENT |
| 16 | Product / Accessory | Category - Level 1  | First categorization level for products                                                                                                                                                                                                                       | Car Seat, Stroller                                 | Measure product performance at category level                                                                                                    | COMPONENT |
| 17 | Product / Accessory | Category - Level 2  | Second categorization level for products                                                                                                                                                                                                                      | Baby, Toddler, Child                               | For each category, measure performance of sub-categories                                                                                         | COMPONENT |
| 18 | Tools Integration   | Optimizely - Slot 1 | Optimizely integration slot 1                                                                                                                                                                                                                                 | experiment ID                                      | Measure data based on A/B testing experiments                                                                                                    | PAGE      |
| 19 | Tools Integration   | Optimizely - Slot 2 | Optimizely integration slot 2                                                                                                                                                                                                                                 | experiment ID                                      | Measure data based on A/B testing experiments                                                                                                    | PAGE      |
| 20 | Tools Integration   | Hotjar User Id      | Hotjar integration slot                                                                                                                                                                                                                                       | Hotjar integration ID                              | Being able to tie analytics and session recording data together                                                                                  | PAGE      |


## Implementation ##

### Criteria ###

Implementation details have yet to be finalized, nonetheless a few examples are appended below to show what is possible and get discussions started. The criteria we must take into account:

 - **INPUT HOW**: how are values fed (technically) to the dimensions?
 - **INPUT WHO**: who is in charge for setting those values?
 - **INPUT WHEN**: when are the values inserted?
 - **CHANGE FREQUENCY**: how often is a dimension likely to change?
 - **OUTPUT HOW**: how is Analytics going to read the dimension values?
 - **OUTPUT WHEN**: when is Analytics going to read those values?

### Limit Manual Input ###

Regardless of how each dimension is implemented, we must follow the below rule:

**!!! Manual input has to be reduced to a minimum !!!**

If we do not follow this rule, it is only a matter of time before values assigned to dimensions become inconsistent (e.g. "Homepage" vs. "Home", vs "home page"....) and start impacting several aspects of digital (Analytics, SEO, content creation/maintenance....).

### Why we must think this through ###

To illustrate why it is important to carefully choose how those dimensions are implemented, let's take the example of the `Content - Type` dimension which describes what a piece of content is about:

 - We can simply add an input field to the page/component template in Wordpress and let content editors enter a few words about them
 - But we all know manual input will create mess sooner or later
 - So we can decide to instead define drop-down lists from which content editors can choose from
 - Comes the question: who maintains those lists and how much effort would it be if we want to do it at a global scale to maintain consistency?
 - We might also realize that content editors just aren't trained or focused enough to choose the appropriate values
 - So instead we decide to pre-fill those values per template, so that whenever someone chooses a template (e.g. Car seat page template), then we automatically know what it's about
 - But suddenly our templates are content-specific and the number of templates will increase dramatically as our content does....

| Dimension           | INPUT HOW                                   | INPUT WHEN                                    | INPUT WHO                            | OUTPUT HOW             |
|---------------------|---------------------------------------------|-----------------------------------------------|--------------------------------------|------------------------|
| ID                  | Request to user database                    | Loading page                                  | Cookie                               |                        |
| Type                | Google Analytics API                        | Periodic basis                                | No need, fed directly into analytics |                        |
| Login state         | Request to user database                    |                                               |                                      |                        |
| FREE SLOT           |                                             |                                               |                                      |                        |
| Name                | Inserted into site-wide configuration       | Creating website                              | Website Owner                        | Read from meta tag     |
| Country             | Inserted into page based on Wordpress setup | Creating page                                 | Content editor                       | Read from hreflang tag |
| Primary             | ???                                         | Creating page                                 | Content editor                       | ??                     |
| Page Name           | ???                                         | Creating page                                 | Content editor                       | ??                     |
| Language            | ???                                         | Creating page                                 | Content editor                       | Read from hreflang tag |
| Topic               | ???                                         | Adding component to page                      | ??                                   |                        |
| FREE SLOT           |                                             |                                               |                                      |                        |
| Template            | Creating template                           | Content admins in coordination with designers |                                      |                        |
| Position            |                                             |                                               |                                      |                        |
| Name                |                                             |                                               |                                      |                        |
| Variant             |                                             |                                               |                                      |                        |
| Category - Level 1  |                                             |                                               |                                      |                        |
| Category - Level 2  |                                             |                                               |                                      |                        |
| Optimizely - Slot 1 | Inserted by Optimizely automatically        | Automatic                                     | Automatic                            | Automatic              |
| Optimizely - Slot 2 | Inserted by Optimizely automatically        | Automatic                                     | Automatic                            | Automatic              |
| Hotjar User Id      | Inserted by Hotjar automatically            | Automatic                                     | Automatic                            | Automatic              |



---
layout: manual
title: 2.2.0 Dimensions
category: Analytics
draft: false
---

## What are they? ##

Dimensions are qualitative information that describe the data (e.g. country, language, brand, product type), as opposed to metrics (e.g. # visits, revenue...) which quantify it.

## Why are they important? ##

### For Analytics ###

Dimensions allow you to segment your data to identify patterns or differences from which you can further investigate.

Indeed, looking at a metric by itself can be pretty useless:

| METRIC (e.g. conversion rate) |
|:-----------------------------:|
|              15%              |

By segmenting with the `Marketing Channel` dimension, we learn more from our data:

| DIMENSION (e.g. Marketing Channel) | METRIC (e.g. conversion rate) |
|:----------------------------------:|:-----------------------------:|
| Google                             |              15%              |
| Bing                               |              15%              |
| Linkedin                           |              30%              |
| Facebook                           |              10%              |
| Twitter                            |              10%              |

Suddenly we see that certain channels perform better, and others worse, and we can further segment to find out why (does it have to do with the `landing page` people land on, the `content` of our campaigns on these channels?...)

### Dimensions impact business as a whole ###

You never design just for Analytics. If you measure it, it's because it matters to the business. In the end, your dimensions represent data that matters to the business and is used and disseminated at various levels:

 - **SEO**:  some of your dimensions will be used in various ways (`JSON-LD`, `Schema`) to help Search Engines crawl and understand your content.
 - **Content teams**:  dimensions can help content teams tag the content to help with inventory and maintenance.
 - **CMS**:  if content editors need to input values for those dimensions, specific fields must be made available via the CMS.
 - **Design**: if the technical solution to provide values for dimensions is to have them pre-filled at design template level, then suddenly dimensions are impacting your template creation process.
 - **etc...**

## How to create those dimensions? ##

Creating dimensions is performed in 2 steps:

 1. **Inventory**: make a list of dimensions that are releveant to the business (see list further below) and define what values should be fed to those dimensions.
 2. **Implementation**: create a process so that the proper values are consistently fed to the dimensions.
 
## Scopes ##

Dimensions inventoried so far can have 1 of the below scopes:

 - **USER**: persists for each user (e.g. User Id)
 - **SESSION**: persists for each user session (i.e. visit)
 - **SITE**: persists for each website (e.g. Site Brand)
 - **TEMPLATE**: persists for each template (e.g. Template Name)
 - **PAGE**: persists for each page (e.g. Page Name)
 - **COMPONENT**: persists for each page component (e.g. Content Type for a particular page component)
 
The mechanism by which the dimensions are set for each scope has yet to be defined.

## Inventory ##

The current list of dimensions is appended below. The reason for having 20 dimensions is because it is a hard limitation imposed by Google Analytics which remains our main reporting tool. `FREE SLOT` are dimensions we haven't assigned yet but wan't to keep open for future use. Some dimensions are there solely for technical reasons (e.g. Optimizely integration).

| ID | SCOPE     | DIMENSION                      | DESCRIPTION                                                                                                                                                                                                                                                   | EXAMPLE                                            |
|----|-----------|--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------|
| 1  | USER      | User - Id                      | Unique ID coming from user database when user is authenticated                                                                                                                                                                                                | 123456778                                          |
| 2  | USER      | User - Type                    | User Type as per CRM segmentation                                                                                                                                                                                                                             | Reseller, Consumer, Prospect...                    |
| 3  | SESSION   | User - Login state             | Whether user is logged in or not                                                                                                                                                                                                                              | Logged in / Logged out                             |
| 4  | USER      | FREE SLOT                      | TBD                                                                                                                                                                                                                                                           | TBD                                                |
| 5  | SITE      | Brand - Name                   | Brand name as defined by business                                                                                                                                                                                                                             | Quinny, Maxi Cosi...                               |
| 6  | PAGE      | Location - Country             | ISO_3166-1_alpha-2 country code. Use "ALL" if not targeted at a specific country                                                                                                                                                                              | FR,UK....                                          |
| 7  | PAGE      | Content - Page Primary Content | Although pages might be composed of various components of different types (e.g. Product, FAQ...) we want to                                                                                                                                                   | Product, Article, FAQ,.....                        |
| 8  | PAGE      | Page - Name                    | As web still relies heavily on URLs as navigation/reference point. We cannot rely on the URsL because they are language-specific and change over time. We need a new dimension that identifies a page in a unique, persistent, cross-language fashion         | Homepage, Support Contact Page, Product A page     |
| 9  | PAGE      | Page - Language                | Language+region code as defined in the HTML hreflang tag. Reason for taking into account this localized version of a language is because of very international position of Dorel and significant differences within the same language "family" (e.g. English) | be-NL,nl-NL,en-GB                                  |
| 10 | COMPONENT | Content - Topic                | First categorization level of content                                                                                                                                                                                                                         | Product, Service, Warranty, Safety, Marketing, R&D |
| 11 | COMPONENT | Content - FREE SLOT            | TBD                                                                                                                                                                                                                                                           | TBD                                                |
| 12 | TEMPLATE  | Design - Template              | Template name                                                                                                                                                                                                                                                 | 2-column template                                  |
| 13 | TEMPLATE  | Design - Position              | Indication of position within template                                                                                                                                                                                                                        | 1-1 (first column, first block)                    |
| 14 | COMPONENT | Product - Name                 | Product name                                                                                                                                                                                                                                                  | Pebble Plus                                        |
| 15 | COMPONENT | Product - Variant              | Product variant                                                                                                                                                                                                                                               | Pebble Plus RED                                    |
| 16 | COMPONENT | Product - Category - Level 1   | First categorization level for products                                                                                                                                                                                                                       | Car Seat, Stroller                                 |
| 17 | COMPONENT | Product - Category - Level 2   | Second categorization level for products                                                                                                                                                                                                                      | Baby, Toddler, Child                               |
| 18 | PAGE      | Tools - Optimizely 1           | Optimizely integration slot 1                                                                                                                                                                                                                                 | experiment ID                                      |
| 19 | PAGE      | Tools - Optimizely 2           | Optimizely integration slot 2                                                                                                                                                                                                                                 | experiment ID                                      |
| 20 | PAGE      | Tools - Hotjar                 | Hotjar integration slot                                                                                                                                                                                                                                       | Hotjar integration ID                              |

## Implementation ##

### Criteria ###

Implementation details have yet to be finalized, nonetheless a few examples are appended below to show what is possible and get discussions started. The criteria we must take into account:

 - **INPUT - WHO**: who is in charge for deciding on the dimension values?
 - **INPUT - WHEN**: when are the values inserted?
 - **INPUT - HOW**: how?
 - **INPUT - CHANGE**: how often are values for a given dimension changing?
 - **OUTPUT - HOW**: how is Analytics reading the dimension values?
 - **OUTPUT - WHEN**: when is Analytics reading those values?

### Limit Manual Input ###

Regardless of how each dimension is implemented, we must follow the below rule:

**!!! Manual input has to be reduced to a minimum !!!**

If we do not follow this rule, it is only a matter of time before values assigned to dimensions become inconsistent (e.g. "Homepage" vs. "Home", vs "home page"....) and start impacting several aspects of Digital (Analytics, SEO, content creation/maintenance....).

### Implementation is critical ###

To illustrate why it is important to carefully choose how those dimensions are implemented, let's take the example of the `Content - Type` dimension which describes what a piece of content is about:

 - We could simply add an input field to the page/component template in Wordpress and let content editors enter a few words to describe the content
 - But we all know manual input will be inconsistent, unstructured, and subject to translation variations and typos...
 - So we could instead decide to define drop-down lists from which content editors could choose values from
 - Comes the question: who maintains those lists and how much effort would it be if we want to do it at a local vs. global level?
 - If content editors aren't trained or motivated enough to choose the appropriate values, dimensions will either remain empty or with incorrect values.
 - So instead we could decide to pre-fill those values per template, so that whenever someone chooses a template (e.g. Contact page template), the dimension values are pre-filled.
 - But suddenly our templates would be content-specific and we would have to create new templates solely for the purpose of maintaining different dimensions values...


### Implementation ###

TBD
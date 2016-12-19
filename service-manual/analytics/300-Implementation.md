---
layout: manual
title: 3.0.0 Implementation
category: Analytics
draft: false
---

The implementation section comprises the following articles:
 - **3.0.0 Implementation Overview**: the current page, where we introduce the implementation process and its key principles
 - **3.1.0 Designing a scalable solution**: illustrates what needs to be done if we want Analytics to scale
 - **3.2.0 Data Collection**: details on the data collection part of the process
 - **3.2.1 JavaScript Track Method**: JavaScript method used as part of the data collection process

In essence we can represent the analytics implementation process as the steps needed to go from data to insights:

![process](/assets/img/analytics/process_essence.png)

It is up to us to determine how advanced the process needs to be to deliver the insights defined by our Measurement Model. The objective should be to make the process as simple as possible. A more detailed diagram of the implemenation process is available at the end of this page.

## Key Principles ##

To understand why some of the implementation decisions are made, it is paramount to bear in mind the following principles:

 - **Business needs constantly evolve**:  Therefore our data collection process has to have as little dependency on business lobic as possible, otherwise we will constantly be changing our implementation process as the business evolves.
 - **You cannot go back in time to collect volatile data you didn't collect** (like a lot of the analytics data is): therefore, it is better to grab extra data, even if it looks not needed at the time, as it might become useful in the future.
 - **We have data model constraints** imposed by certain analytics tools (e.g. Google Analytics e-commerce data has to be formatted a specific way): therefore, we need to format the data at some point so it can be used by the Analytics tools
 - **Data should be open** in order to make switching or integrating other analytics tools easier in the future.


## Implementation Process ##
 
Below is a our implementation process as it currently stands. Clic on each link to get more details

![data](/assets/img/analytics/process_data.png)
 1. [**Data Collection**](320-data-collection.html)
 2. [**Data Storage**](330-data-storage.html)
 3. [**Data Analysis**](340-data-analysis.html)
 4. [**Reporting**](350-reporting.html)
![insights](/assets/img/analytics/process_insights.png)
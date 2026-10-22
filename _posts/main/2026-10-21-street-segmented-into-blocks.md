---
layout: post
title: Streets are now segmented into blocks
---

![image street-segment-archer-ave.png](assets/images/street-segment-archer-ave.png)



Crash Stop Chicago now organizes data at the street segment (i.e. block) level, e.g. if you live on 125 N Dearborn Street you can now view traffic crash data for [100-199 S Dearborn St](https://crashstop.org/chicago/street-segments/s-dearborn-st--100-199), instead of needing to sort through the data for the entire stretch of [South Dearborn St](https://crashstop.org/chicago/streets/s-dearborn-st).

This took a lot of backend re-wrangling — mostly redoing how I transform the [city's Street Center Lines database](https://data.cityofchicago.org/Transportation/Street-Center-Lines/6imu-meau), but I think it's worth it because it opens the door to more pointed and relevant analyses, such as examining the impact of traffic safety features within their immediate blocks.

It's also nice that you can now type in a partial address into the location search and find data within a block of you without me having to send your input into Google's geocoder:

![image street-segment-autocomplete.png](assets/images/street-segment-autocomplete.png)



I've been making a lot of incremental interface changes over the past few weeks too, and plan to continue to do so until the data finally looks nice and understandable. My latest tweaks have been to the top infobox for location pages, de-emphasizing the historical total in favor of showing recent crash activity and comparing it to recent historical averages:

![image location-topline-kpi-redesign.png](assets/images/location-topline-kpi-redesign.png)

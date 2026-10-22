---
layout: post
title: Ungeocoded crash records no longer omitted
---

About 1,000 crash records (including 9 fatalities) in the city database lack geocoordinates, and I had early on for some reason omitted those records from my site queries default — which left them out not only from the maps but also the statistical aggregates.

I've now removed that filter, so the stat aggregates will slightly change:


| Year  | Crashes w/o coords | Fatalities w/o coords | Total Crashes |
| ----- | -----------------: | --------------------: | ------------: |
| **Total** | **971**        | **9**                 | **141,714**   |
| 2026  | 81                 | 1                     | 9,184         |
| 2025  | 136                | 1                     | 17,897        |
| 2024  | 141                | 1                     | 18,441        |
| 2023  | 129                | 1                     | 16,766        |
| 2022  | 100                | 1                     | 16,033        |
| 2021  | 121                | 1                     | 16,331        |
| 2020  | 79                 | 1                     | 14,167        |
| 2019  | 96                 | 2                     | 16,314        |
| 2018  | 88                 | 0                     | 16,581        |



An example: the data record for this [July 14, 2022 fatal 4-car crash](https://crashstop.org/chicago/crashes/31881cfc3d0a9b4a172ab170210891adc9b7263c639beaf16b05fde86e207092de9b33006c7e6608b324fad1994fe574ef3b40d666faf3d3e8d6629bf8d03993) that killed a 29-year-old passenger ([related Chicago Sun-Times story](https://chicago.suntimes.com/news/2022/7/15/23219846/man-dead-3-year-old-boy-among-3-others-hurt-in-traffic-crash-near-ohare-airport)), which took place at [4331 N. Mannheim Rd](https://www.google.com/maps/place/4331+N+Mannheim+Rd,+Schiller+Park,+IL+60176/), has empty latitude and longitude fields. This crash, like most of the non-geocoded records, appear to take place near freeways and/or the airports. I'll have to figure out a way to manually add coordinates for these situations.



<!--
-- Query for reference sake

WITH
Src AS (
  SELECT
    SUBSTR(crash_date, 1, 4) AS Year
    , fatal_tally
    , latitude is null AS missing_coords
FROM crashes_serving
)

SELECT
Year
, SUM(missing_coords) AS [Crashes w/o coords]
, SUM(IIF(missing_coords, fatal_tally, 0)) AS [Fatalities w/o coords]
, COUNT(1) AS `Total Crashes`

FROM (
    SELECT * FROM Src
    UNION ALL
    SELECT 'Total' AS Year, fatal_tally, missing_coords FROM Src
)

GROUP BY Year
ORDER BY Year desc
 -->

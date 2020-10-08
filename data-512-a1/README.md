# data-512-a1
Directory for DATA 512-A1: Data Curation Wikipedia Page Views
# Project Goal
The goal of this data curation project is to analyze the pageview traffic on English Wikipedia. Provided two APIs from Wikimedia Foundation REST API, licensed and subject to the terms of use as described in https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions, the notebook produces several output files that can be used to understand the timeseries of English Wikipedia page traffic. The output files include five .json files with the data from the API endpoints for various traffic types, one .csv file with the joined data from all the traffic types and APIs, and one .png file with the timeseries chart of pageviews per month per traffic type.
# Resources
Pagecount API
- Documentation: https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts
- Endpoint: https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end

Pageviews API
- Documentation: https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews
- Endpoint: https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end

Sample code for API calls
- Example notebook: http://paws-public.wmflabs.org/paws-public/User:Jtmorgan/data512_a1_example.ipynb
- CCO License: https://creativecommons.org/share-your-work/public-domain/cc0/
# en-wikipedia_traffic_200712-202008.csv 
| column                  | value     | description                            | data type |
|-------------------------|-----------|----------------------------------------|-----------|
| year                    | YYYY      | year pageviews were collected          | string    |
| month                   | MM        | month pageviews were collected         | string    |
| pagecount_all_views     | num_views | legacy API, query type =  all views    | integer   |
| pagecount_desktop_views | num_views | legacy API, query type = desktop views | integer   |
| pagecount_mobile_views  | num_views | legacy API,  query type = mobile views | integer   |
| pageview_all_views      | num_views | new API, query type = all views        | integer   |
| pageview_desktop_views  | num_views | new API, query type = desktop views    | integer   |
| pageview_mobile_views   | num_views | new API, query type = mobile views     | integer   |
# Data Issues and Considerations
There are some differences in the data collection of the legacy pagecounts API and the new pageviews API. The legacy API does not filter out views attributed to self-reported bots, while the new API does. While the legacy API contains historical data, which has not been updated since the time of upload, the new API updates and backfills data at the end of the queried timestamp. It is important to note that latest data can take more than 24 hours to be updated. 

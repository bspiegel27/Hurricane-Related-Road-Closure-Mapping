# Project 5 - Disaster Evacuation Route Planning

# Context and Background

Our 5th project as data science immersives was aimed at helping New Light Technologies with their open source disaster analytics platform as several other immersive cohorts at General Assembly have done. We were split into groups of 3 and were given freedom to select a project from a list of options. We chose a project involving use of social media and other news sources to get real-time road closures and restrictions in support of disaster evacuation route planning. This project is extremely relevant as popular GPS products like Waze as well as transportation departments often struggle to get road closures and incidents fast enough to ensure directions provided to consumers are accurate in real-time, especially during crucial times such as disasters. From a technical perspective, this was an interesting project for a variety of reasons. First, we had the freedom to explore different news sources and decide which would be best for real-time information. Second, there were various analytical steps at each point along the way that made for a nuanced final product. Third, our final product is a map for which we did not have any "true" observed values. As such, we had to be creative in the way we evaluated how well we identified the right locations of an incident.

# Process and Results Summary

We evaluated Hurricanes Michael, Florence, and Harvey as these were recent and damaging storms for which social media data collection would be reasonable and representative of future events. We gathered several thousand historical tweets linked to either key local 511 and traffic twitter accounts, or hurricane-specific hashtags. First, we used keywords to tag tweets with confirmed road closure or restriction. Next, we tagged tweets via keyword search across a variety of gathered geographical tags (highways, cities, counties, exits and mile markers), and constructed addresses for each tweet. Addresses were then geocoded to longitude and latitude coordinates using arcGIS geocoding, and plotted on a map for evaluation via Bokeh. Overall, we were able to plot a significant portion of tweets, though plotting was more accurate if tweets contained identified highway exits, mile markers, or intersecting highways. Additional work would improve the ability to identify highways via intersecting roads and other features. Further, advanced NLP techniques could be used to go beyond keyword searching of tweets for improved performance.

Below is a summary of each key step in the process described above, including a repository directory at the bottom

# News Source Selection

# Twitter Searching Criteria

# Tweet Text Cleaning

# Road Status Determination

# Geographic Feature Tagging

The goal of this analysis is to construct detailed addresses that enable accurate plotting on a map.
We read through a variety of tweets to understand how road incidents were communicated and noticed a few useful trends. First, tweets describing a road incident are almost always about a major highway, with that highway typically mentioned early on in the tweet. Second, supporting areas (cities, towns, and counties) and/or intersecting or nearby roads are used to describe where along a highway the incident occurred. Third, typos and abbreviations are extremely common and needed to be accounted for. With this in mind, we first gathered lists of geographic features in these categories.
Highways were gathered largely from wikipedia and state dept of transportation accounts, and included main and auxiliary interstates, US routes, and state highways. County highways and local roads were not included as lists of these roads are typically stored on individual state county websites or not at all. However, to identify presence of roads, we did create a list of road suffixes (eg avenue, street, lane) such that we could identify presence of a road without knowing its name. Improvement to our list generation could be made by determining how to extract layers from exising map APIs to create a database of street and road names. Cities and counties were siimlarly gathered from wikipedia. Individual exits and mile markers were not gathered, though by searching for "exit" and "mile markes" specifically, we were able to identify tweets containing these fatures.
To tag features and incorporate abbreviations, feature dictionaries were created with keys as a specific feature (eg US-1) and values as a list of abbreviations: (US1, US 1, US-1). When searching through tweet text, presence of any abbreviation for a specific feature resulted in that tweet being tagged. This process hihgly prioritized being sensititive to geographic information, and will catch abbreviations that may not be relevant given context. Future work could involve more advanced NLP techniques to ensure that abbreviations are classified appropriately. Address generation and geocoding takes this high sensitivity into account.
For each tweet, we create multiple potential addresses based on features that were tagged. For instanc, if both a highway exit and mile marker are found, one option would be the highway + exit, and other would be highway + mile marker. Format of resuling addresses are: Highway + intersecting feature + city/county + state. 

# Geocoding
Once a list of addresses are created for each tweet, we then had to convert this to a longitude and latitude for accurate mapping. To do so, we evaluated a couple of different packages available within Python's GeoPy library and determined that arcGIS was a great option. First, the website has strong python documentation and enables easy creation of account to utilize its API. Further, its geocoding function has "category filtering" that enables searching over only specific types of geographic points (eg highway exits, street intersections and many many more).

[arcGis Python Tutorial](https://developers.arcgis.com/labs/browse/?product=python&topic=any)
[arcGis Category Filtering](https://developers.arcgis.com/rest/geocode/api-reference/geocoding-category-filtering.htm#GUID-20D9858C-C27C-4C9C-BE4C-1EDB36E04D62)

For each address generated in the prior step, we use arcGIS to generate lat/long coordinates. Thenm using arcGIS's match score (out of 100) for each address within a tweet, we then assign each tweet the best possible match when one is found. In many cases, there are multiple incidents described within one tweet, or the incident lies in between two exits. The former isn't something we accounted for and could be added in further iterations of this project. For cases of the the latter, our method will result in plotting of one of the ends of an incident as opposed to plotting a point in between two sections of a highway. More advanced NLP to understand how different addresses identified within a tweet relate to each other could be used to improve our mapping of tweets when more than one accurate address/set of coordinates are identified.

# Mapping

File Structure and Other Details

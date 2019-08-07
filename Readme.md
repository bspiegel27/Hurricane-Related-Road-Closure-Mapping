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

The goal of this piece of the analysis is to construct detailed addresses that will enable accurate plotting on a map.
We read through a variety of tweets to understand how road incidents were communicated. We noticed a variety of trends that drove geographic feature tagging. First, tweets describing a road incident are almost always about a major highway, with that highway typically mentioned early on in the tweet. Second, supporting areas (cities, towns, and counties) and/or intersecting or nearby roads are used to describe where along a highway the incident occurred. Third, typos and abbreviations are extremely common and needed to be accounted for. The first step in the analysis involved gathering lists of geographic features.
Highways were gathered largely from wikipedia and state dept of transportation accounts, and included main and auxiliary interstates, US routes, and state highways. County highways and local roads were not included as lists of these roads are typically stored on individual state county websites or not at all. However, to identify presence of roads, we did create a list of road suffixes (eg avenue, street, lane) such that we could identify presence of a road without knowing its name. Improvement to our list generation could be made by determining how to extract layers from exising map APIs to create a database of street and road names. Cities and counties were siimlarly gathered from wikipedia. Individual exits and mile markers were not gathered, though



Geocoding

Mapping

File Structure and Other Details

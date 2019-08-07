# Project 5 - Disaster Evacuation Route Planning

Context and Background

Our 5th project as data science immersives was aimed at helping New Light Technologies with their open source disaster analytics platform as several other immersive cohorts at General Assembly have done. We were split into groups of 3 and were given freedom to select a project from a list of options. We chose a project involving use of social media and other news sources to get real-time road closures and restrictions in support of disaster evacuation route planning. This project is extremely relevant as popular GPS products like Waze as well as transportation departments often struggle to get road closures and incidents fast enough to ensure directions provided to consumers are accurate in real-time, especially during crucial times such as disasters. From a technical perspective, this was an interesting project for a variety of reasons. First, we had the freedom to explore different news sources and decide which would be best for real-time information. Second, there were various analytical steps at each point along the way that made for a nuanced final product. Third, our final product is a map for which we did not have any "true" observed values. As such, we had to be creative in the way we evaluated how well we identified the right locations of an incident.

Process and Results Summary

We evaluated Hurricanes Michael, Florence, and Harvey as these were recent and damaging storms for which social media data collection would be reasonable and representative of future events. We gathered several thousand historical tweets linked to either key local 511 and traffic twitter accounts, or hurricane-specific hashtags. First, we used keywords to tag tweets with confirmed road closure or restriction. Next, we tagged tweets via keyword search across a variety of gathered geographical tags (highways, cities, counties, exits and mile markers), and constructed addresses for each tweet. Addresses were then geocoded to longitude and latitude coordinates using arcGIS geocoding, and plotted on a map for evaluation via Bokeh. Overall, we were able to plot a significant portion of tweets, though plotting was more accurate if tweets contained identified highway exits, mile markers, or intersecting highways. Additional work would improve the ability to identify highways via intersecting roads and other features. Further, advanced NLP techniques could be used to go beyond keyword searching of tweets for improved performance.

Below is a summary of each key step in the process described above, including a repository directory at the bottom

News Source Selection

Twitter Searching Criteria

Tweet Text Cleaning

Geographic Feature Tagging

Once tweets were gathered, we read through a variety of tweets to understand how road incidents were communicated. We noticed a variety of trends that drove geographic feature tagging. First, tweets describing a road incident are almost always about a major highway, with that highway typically mentioned early on in the tweet. Second, a combination of supporting areas (cities, towns, and counties) and intersecting or nearby roads (exits are often mentioned. 

Geocoding

Mapping

File Structure and Other Details

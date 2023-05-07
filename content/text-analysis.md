---
title: Text analysis
prev: network-analysis
---

We decided to do text analysis on the reptile database subset as described in earlier section. We chose to do it only on the reptiles due to the nature of scraping that many pages takes quite a while, but also more importantly due to the size of the resulting dataset being quite quite large. The text analysis consisted of scraping all the wikipedia pages mentioned and doign TF-IDF on all the body text of the page. The body text is pretty much everything except for the info-boxes, headers and such.

Our goal with TF-IDF text analysis was to investigate if it can show connections between different animals the same way we do through our network analysis. Furthermore we want to shine some light on the downsides and upsides of this approach.


As seen in the network analysis there are some clear clustering going on in the dataset. Our hope is that we will be able to see a clear correlation between a short path between two nodes in the network, and a high TF-IDF score of their respective analysis of their wikipedia page. To investigate this we have chosen to pick out some nodes which can clearly be seen on the network graph to belong to a certain community, and look at the tf-idf score of said node.

For this the following points were chosen:

1. laudakia_dayana (Lizard cluster)
2. geophis_fulvoguttatus (Snake cluster)
3. northern_yellow-faced_turtle (Turtle cluster)

<p align="center">
<img src="/images/laudakia_dayana_wordcloud.png" width="45%" />
&nbsp; &nbsp; &nbsp; &nbsp;
<img src="/images/geophis_fulvoguttatus_wordcloud.png" width="45%" />
</p>

<!-- <img src="/images/northern_yellow-faced_turtle_wordcloud.png" width="400"/> -->
---
title: Text analysis
prev: network-analysis
---

We decided to do text analysis on the reptile database subset as described in earlier section. We chose to do it only on the reptiles due to the nature of scraping that many pages takes quite a while, but also more importantly due to the size of the resulting dataset being quite quite large. The text analysis consisted of scraping all the wikipedia pages mentioned and doign TF-IDF on all the body text of the page. The body text is pretty much everything except for the info-boxes, headers and such.

Our goal with TF-IDF text analysis was to investigate if it can show connections between different animals the same way we do through our network analysis. Furthermore we want to shine some light on the downsides and upsides of this approach.


As seen in the network analysis there are some clear clustering going on in the dataset. Our hope is that we will be able to see a clear correlation between a short path between two nodes in the network, and a high TF-IDF score of their respective analysis of their wikipedia page. To investigate this we have chosen to pick out some nodes which can clearly be seen on the network graph to belong to a certain community, and look at the tf-idf score of said nodes.

For this the following points were chosen:
1. laudakia_dayana (Lizard cluster)
2. geophis_fulvoguttatus (Snake cluster)
3. northern_yellow-faced_turtle (Turtle cluster)

The wordclouds for these three points can be seen below

<div style="display:flex;margin-bottom:5px;">
     <div style="flex:1;padding-right:10px;">
          <img src="/images/laudakia_dayana_wordcloud.png" width="400"/>
     </div>
     <div style="flex:1;padding-left:10px;">
          <img src="/images/geophis_fulvoguttatus_wordcloud.png" width="400"/>
     </div>
</div>
<div style="display:flex">
     <div style="flex:1;padding-left:10px;">
          <img src="/images/northern_yellow-faced_turtle_wordcloud.png" width="400"/>
     </div>
     <!-- <div style="flex:1;padding-left:10px;">
          <img src="/images/geophis_fulvoguttatus_wordcloud.png" width="300"/>
     </div> -->
</div>

Though it might be hard to spot, all the wordclouds contain the word of their cluster. The easiest ones to spot are node 2 and 3, with both snake and turtle being quite big which means they got quite a high TF-IDF score.

You might notice that there is not any references to other specific animals, and there is a clear reason for this. A word in text analysis is assumed a collection of characters (or digits) separated by a space. This is done by a simple regular expression, but what is means is that an animal like northern yellow-faced turtle, is not recognized as one word (or animal) as one might expect, but instead as 3 separate words. [northeren, yellow-faced, turtle]. The fact that these words should be interpreted as one token gets lost in the text analysis. One way to solve this problem is doing something called N-shingling or N-grams. Where we look at all combinations of N bundles of words. instead of separating each word py a space. This also has the added benefit of getting some context to the word we might be interested in, as we also look at the N words before and after the word, so we get a more complete picture. However the clear downside of this approach, and the main reason for why we didnt do this, is that it is space and computationally expensive. This should not come as a shock to you, as we are basically going from just having each word independantally, to having combinations of words. The space and time complexity of doing this goes up exponentially, which means that if we do bi-shingling or tri-shingling we would go from about 30,000 words to easily 100,000 combinations if not more.


For a more in depth text analysis, we refer to the [Explainer Notebook](../explainer-notebook.html), where we will dive more into the specific TF-IDF score numbers, and how we do the text analysis itself.



---
title: Data description
prev: "/"
next: network-analysis
---

The data that will be used in the analysis, has been gathered by using the WikiData API using their query builder. Due to the Wikipedia pages not having a category called "Animals" that allows you to gather all the animal pages, we will use an alternative which is querying on the Wikidata pages that have a "Animal Diversity Website (ADW) taxon id". This query results in 46,959 animal pages, all these pages are then sent to the Wikidata API again, but this time looking if they have a english wikipedia page connected to it. This query further reduces the dataset to 31,754 animal pages. For each of the pages we access their Wikipedia page, and get all the hyperlinks that link to other wikipedia pages, aswell as the information that is contained in the infobox. 
This info is used for assigning attributes, we gather "Class", "Order", "Superfamily" and "Family". This also allows us to remove redirect pages in a fast way, this is due to one only being able to detect if a page is redirect by either calling MediaWiki API or scraping the page. Both of these methods are extremly slow as a page usually has more than 30 links. By looking for a infobox we dont have to do an extra request, and since redirect pages dont have a info page, we can easily filter them out. 
This results in a graph with 31,393 nodes and 703,510 edges. Due to the size of this dataset, we wish to further reduce it, due to computational running time. By looking at the network graph below, where each color is a unique class (Mammal, Reptile, etc.):
<img src="/images/network_all.png" width="800" />
We can see that there is clustering of the different animal classes, we will focus on Reptile (which is the larger purple cluster in the right hand side). This can be done using two different methods, one of them being querying the WikiData API with another condition and the second one being going through the node attributes and looking for the ones being "Class: Reptile". We choose to query the WikiData API with another condition, this was done due to some infoboxes not having a "Class" row, aswell as with the WikiData we will start with the original 46,959 pages and taking the intersection with the new condition. The condition that was chosen is the "Reptile Database ID", if the wikidata page has a link to its corresponding "Reptile Database" we assume that the wikipedia page is about a reptile. Using the same process as before we end up with 4,847 wikipedia pages.
The resulting network can be seen below, where each color is a unique family (Alligatoridae, Gekkonidae, etc.):
<img src="/images/Reptile_network.png" width="800" />
This resultning network has 64 unique families, 1038 nodes and 9977 edges. If we look at weights in the graph (amount of times a page references a different wikipedia page about reptiles)
<img src="/images/reptile_network_references.png" width="800" />

[Network](../network-analysis)
<img src="/images/dtu-logo.png" width="200" />


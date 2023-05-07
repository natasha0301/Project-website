---
title: Data description
prev: "/"
next: network-analysis
---

The data that will be used in the analysis, has been gathered by using the WikiData API using their query builder. Due to the Wikipedia pages not having a category called "Animals" that allows you to gather all the animal pages, we will use an alternative which is querying on the Wikidata pages that have a "Animal Diversity Website (ADW) taxon id". This query results in 46,959 animal pages, all these pages are then sent to the Wikidata API again, but this time looking if they have a english wikipedia page connected to it. This query further reduces the dataset to 31,754 animal pages. For each of the pages we access their Wikipedia page, and get all the hyperlinks that link to other wikipedia pages, aswell as the information that is contained in the infobox. This info is used for assigning attributes, we gather "Class", "Order", "Superfamily" and "Family". This also allows us to remove redirect pages in a fast way, this is due to one only being able to detect if a page is redirect by either calling MediaWiki API or scraping the page. Both of these methods are extremly slow as a page usually has more than 30 links. By looking for a infobox we dont have to do an extra request, and since redirect pages dont have a info page, we can easily filter them out. 

Due to the size of this dataset, we wish to further reduce it, due to computational running time. By looking at the network graph in [Network](./network-analysis.md)

<img src="/images/dtu-logo.png" width="200" />


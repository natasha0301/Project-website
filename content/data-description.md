---
title: Data description
prev: "/"
next: network-analysis
---

The data that will be used in the analysis, has been gathered by using the WikiData API using their query builder. Due to the Wikipedia pages not having a category called "Animals" that allows you to gather all the animal pages, we will use an alternative which is querying on the Wikidata pages that have a "Animal Diversity Website (ADW) taxon id". This query results in 46,959 animal pages, all these pages are then sent to the Wikidata API again, but this time looking if they have a english wikipedia page connected to it. This query further reduces the dataset to 31,754 animal pages. For each of the pages we access their Wikipedia page, and get all the hyperlinks that link to other wikipedia pages, aswell as the information that is contained in the infobox. 
This info is used for assigning attributes, we gather "Class", "Order", "Superfamily" and "Family". For an Elephant these attributes would be:
1. Class: Mammalia
2. Order: Proboscidea
3. Superfamily: Elephantoidea
4. Family: Elephantidae

This also allows us to remove redirect pages in a fast way, this is due to one only being able to detect if a page is redirect by either calling MediaWiki API or scraping the page. Both of these methods are extremly slow as a page usually has more than 30 links. By looking for a infobox we dont have to do an extra request, and since redirect pages dont have a info page, we can easily filter them out. 
This results in a graph with 31,393 nodes and 703,510 edges. Due to the size of this dataset, we wish to get another dataset that is smaller, due to computational running time during the text analysis. By looking at the network graph below, where each color is a unique class (Mammal, Reptile, etc.):
<img src="/images/network_all.png" width="800" />
We can see that there is clustering of the different animal classes, we will focus on Reptile (which is the larger purple cluster in the right hand side). This can be done using two different methods, one of them being querying the WikiData API with another condition and the second one being going through the node attributes and looking for the ones being "Class: Reptile". We choose to query the WikiData API with another condition, this was done due to some infoboxes not having a "Class" row, aswell as with the WikiData we will start with the original 46,959 pages and taking the intersection with the new condition. The condition that was chosen is the "Reptile Database ID", if the wikidata page has a link to its corresponding "Reptile Database" we assume that the wikipedia page is about a reptile. Using the same process as before we end up with 4,847 wikipedia pages.
The resulting network can be seen below, where each color is a unique family (Alligatoridae, Gekkonidae, etc.):
<img src="/images/Reptile_network.png" width="800" />
This resultning network has 64 unique families, 1,038 nodes and 9,977 edges. If we compare this to the network graph for the large network, we see that the clustering is not entirely the same, this is partly caused by the smaller dataset not containing the larger animal pages (Human, Reptile, Bird), we therefore remove a lot of the edges.

For the text analysis we will only look at the smaller Reptile Network, due to computational running time. However for the network analysis we will look at both.

The data can be accesed either at the bottom of the webpage, by using the direct links below or the main link [here](https://github.com/cerichs/CSS_Project_A_and_B/tree/main/data):
### Attributes
1. [animal_attributes.pickle](https://github.com/cerichs/CSS_Project_A_and_B/blob/main/data/animal_attributes.pickle) Node attributes for the large network.
2. [Reptile_attributes.pickle](https://github.com/cerichs/CSS_Project_A_and_B/blob/main/data/Reptile_attributes.pickle) Node attributes for the smaller reptile network.

### Edgeweights and nodes
1. [all_animal_to_all_animal.pickle](https://github.com/cerichs/CSS_Project_A_and_B/blob/main/data/all_animal_to_all_animal.pickle) Edgeweights and nodes for the large network.
2. [data_plain_long_reptile.pickle](https://github.com/cerichs/CSS_Project_A_and_B/blob/main/data/data_plain_long_reptile.pickle) Edgeweights and nodes for the smaller reptile network.


---
title: Network analysis
prev: data-description
next: text-analysis
---

For the network analysis we will begin by looking at the large network, as previously shown in [Data](../data-description), the network seems to have some clustering that is seperated by the different animal classes. 
<img src="/images/network_all.png" width="800" />

As also seen, some animal classes have more subclusters, the primary 4 and their location in respect to the center <font color=#a328cc>Reptilia</font> (South-east),  <font color=#cc7228>Arachnida</font> (East), <font color=#cc4428>Amphibia</font> (North) and <font color=#2882cc>Mammalia</font> (South-west). 
And we see other classes such as <font color=#cc9728>Aves</font> (South), <font color=#cc3228>Actinopterygii</font> (West) and <font color=#289dcc>Insecta</font> (North-East), where its nodes are still in one big clusters and that are no or minor subclusters.

In order to see if these connection can be caused by pure chance, we will start by looking at the fraction of edges that are in the same class, and compare it to one where the edges are randomly shuffled. For our network we see that the average fraction of edges that belong in the same class is 0.685 and for the randomly shuffled network it is 0.158. This strongly indicates that this cannot be explained by pure chance. This also makes sense when we think about what the underlying data actually is, the wikipedia pages for the majority of the animals in this dataset are not that long. Resulting in the page only containing information that is strictly about this animal and only a few references to articles that relate to the species. We do not observe an Arachnida linking to an Actinopterygii, as these two animal classes live in totally different eco systems.

If we then look at the assortativity coefficient, which is a measurement for how likely similar nodes are to connect to other similar nodes over dissimilar nodes. When looking at the attribute Class we observe the coefficient to be 0.777, which indicates a strong connection that nodes in similar classes connect to each other and not from different classes. If we instead compare this for when we look at the attribute Family we see a coefficient of 0.352. Indicating that it is more likely for a node to connect to dissimilar nodes (when comparing to 0.777), the network with color coding by family can be seen below:

<img src="/images/network_all_family.png" width="800" />

When comparing the two networks visually, we also observe this result. For color coding by class we see that nodes of similar classes (colors) are more likely to be connected to each other than to ones of different classes (different colors). Whereas for color coding by family, we see that the nodes of the same family are more likely to connect to other families.

If we look at the modularity, ie. the degree of clustering and how well the nodes can be organized into distinct communities. We observe the same kind of difference as before, if the split is done by Class we obtain a modularity of 0.369 and for a split by Family a modularity of 0.158. This suggests that the partitioning based on "Class" is a better representation of the community structure in the network than the partitioning based on "Family". A score of 0.369 indicates is moderately stuctured into communities, which is also what is observed in the visualisation.

However, there is a problem with the dataset, which is that there are nodes for "Animal", "Reptilia", etc. A "cleaned" network where the nodes for the different classes, orders, superfamily and families are removed, aswell as the following nodes "Animal","Reptile","Arthropod","Chordate","Bird","Rodent" & "Insect" can be seen below:
<img src="/images/network_cleaned.png" width="800" />

However this "cleaned" network will not be used for the analysis, since there is no clear line to draw in regards to what should be removed and what shouldn't. As there is a good argument for also removing "Spider" and "Frog" if we have removed "Bird". For curiosity sake, with a Class split it gets a assortativity coefficient of 0.912 and modularity of 0.215.

Moving away from the "cleaned" network and back to the original network, if we try to apply community detection on the network using the Louvain algorithm, we get the following statistics about the network:
1. Number of communities: 30
2. Communitiy sizes (first 10): 10084, 5832, 3353, 3051, 2868, 1204, 900, 514, 356, 332
3. Modularity: 0.79

The network with Louvain communities can be seen below:
<img src="/images/Louvain-network.png" width="800" />

To see how good Louvain performs, we compute the accuracy. Louvain has predicted 30 unique labels, whereas there are 106 ground truth labels. The accuracy is calculated by taking the amount of correct class assignment and devide it by total assignments. This gives an accuracy of 64.7%. The confusion matrix is too big to show it here in any meaningful way as there are 106 ground truth labels. To see the full confusion matrix refer to the [source code](https://github.com/cerichs/CSS_Project_A_and_B/blob/main/analysis.py#L247) (as the explainer notebook also is unable to output its full size).

However as can be seen in the plots, it is able to correctly identify the larger cluster, as it assumes these clusters are all the same Class.
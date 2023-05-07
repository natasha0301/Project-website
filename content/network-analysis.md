---
title: Network analysis
prev: data-description
next: text-analysis
---

For the network analysis we will begin by looking at the large network, as previously shown in [Data](../data-description.md), the network seems to have some clustering that is seperated by the different animal classes. 
<img src="/images/network_all.png" width="800" />

As also seen, some animal classes have more subclusters, the primary 4 and their location in respect to the center <font color=#a328cc>Reptilia</font> (South-east),  <font color=#cc7228>Arachnida</font> (East), <font color=#cc4428>Amphibia</font> (North) and <font color=#2882cc>Mammalia</font> (South-west). 
And we see other classes such as <font color=#cc9728>Aves</font> (South), <font color=#cc3228>Actinopterygii</font> (West) and <font color=#289dcc>Insecta</font> (North-East), where its nodes are still in one big clusters and that are no or minor subclusters.

In order to see if these connection can be caused by pure chance, we will start by looking at the fraction of edges that are in the same class, and compare it to one where the edges are randomly shuffled. For our network we see that the average fraction of edges that belong in the same class is 0.685 and for the randomly shuffled network it is 0.158. This strongly indicates that this cannot be explained by pure chance. This also makes sense when we think about what the underlying data actually is, the wikipedia pages for the majority of the animals in this dataset are not that long. Resulting in the page only containing information that is strictly about this animal and only a few references to articles that relate to the species. We do not observe an Arachnida linking to an Actinopterygii, as these two animal classes live in totally different eco systems.

If we then look at the assortativity coefficient, which is a measurement for how likely similar nodes are to connect to other similar nodes over dissimilar nodes. When looking at the attribute Class we observe the coefficient to be 0.777, which indicates a strong connection that nodes in similar classes connect to each other and not from different classes. If we instead compare this for when we look at the attribute Family we see a coefficient of 0.352. Indicating that it is more likely for a node to connect to dissimilar nodes (when comparing to 0.777), the network with color coding by family can be seen below:

<img src="/images/network_all_family.png" width="800" />

When comparing the two networks visually, we also observe this result. For color coding by class we see that nodes of similar classes (colors) are more likely to be connected to each other than to ones of different classes (different colors). Whereas for color coding by family, we see that the nodes of the same family are more likely to connect to other families.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. In nulla tellus, tempus sed lobortis quis, venenatis ac ante. Maecenas accumsan augue ultricies metus hendrerit, in ultrices urna fringilla. Suspendisse lobortis egestas magna, sit amet fermentum ligula tincidunt vitae. Suspendisse cursus non dui a vulputate. Cras vestibulum vulputate enim eu placerat. Ut scelerisque semper justo sit amet auctor. Aliquam sit amet iaculis tortor.

> Nulla in justo hendrerit, tincidunt mauris et, porta est. Donec in leo vitae est ultrices dapibus id nec tortor. Maecenas ut ipsum eu nisl cursus facilisis scelerisque eu ex. Aliquam euismod elementum libero, at vehicula ipsum.

Nam commodo lorem quis tortor euismod, ut ultrices orci aliquet. Sed eget dui nec sem ullamcorper convallis id nec ante. Aliquam ultricies a massa quis semper. Donec suscipit augue ut sagittis hendrerit. Aliquam erat volutpat. Proin aliquet maximus nibh, id aliquet justo maximus at. Sed accumsan ante id aliquam pellentesque. Aliquam nec hendrerit quam. Suspendisse maximus eros sollicitudin, accumsan turpis eu, blandit nulla. Nunc lorem elit, molestie at libero gravida, placerat consectetur ante. Sed tincidunt viverra tellus a vehicula.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam blandit lobortis turpis. Praesent porttitor, turpis eu posuere molestie, sem dolor scelerisque sapien, eu aliquet ante felis ac metus. Pellentesque semper ultricies urna. Aenean auctor, turpis ut convallis ultrices, eros tellus bibendum risus, eu varius velit ante et diam. In suscipit lorem orci, eu placerat nibh dignissim ut. Nullam consequat nisl dui, in ornare risus porttitor sed. Integer vitae nibh semper purus ultrices rutrum. Pellentesque non diam ornare, imperdiet elit a, tempus lacus. Suspendisse viverra euismod dapibus.
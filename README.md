hierarchical-clustering-java
============================

Implementation of an agglomerative hierarchical clustering algorithm in Java. Different linkage approaches are supported:
* Average Linkage
* Single Linkage
* Complete Linkage

What you put in
---------------

Pass an distance matrix and a cluster name array along with an linkage strategy to the clustering algorithm:

    String[] names = new String[] { "O1", "O2", "O3", "O4", "O5", "O6" };
    double[][] distances = new double[][] { 
        { 0, 1, 9, 7, 11, 14 },
        { 1, 0, 4, 3, 8, 10 }, 
        { 9, 4, 0, 9, 2, 8 },
        { 7, 3, 9, 0, 6, 13 }, 
        { 11, 8, 2, 6, 0, 10 },
        { 14, 10, 8, 13, 10, 0 }};

    ClusteringAlgorithm alg = new DefaultClusteringAlgorithm();
    Cluster cluster = alg.performClustering(distances, names,
        new AverageLinkageStrategy());

What you get out
----------------

A java object *Cluster* is returned, that represents an hierachy of clusters based on their distances.
You may want to visualize the result using the Swing component *DendrogramPanel*:

    DendrogramPanel dp = new DendrogramPanel();
    dp.setModel(cluster);

Whem embedded into a JFrame the dendrogram panel should display this:

![Screenshot](https://raw.github.com/lbehnke/hierarchical-clustering-java/master/etc/screenshot1.png "Average linkage")

Same data but different linkage strategy (MinimumLinkageStrategy) result in this diagram:

![Screenshot](https://raw.github.com/lbehnke/hierarchical-clustering-java/master/etc/screenshot2.png "Minimum linkage")

References
----------
[Average linkage clustering](http://en.wikipedia.org/wiki/UPGMA "Average linkage clustering")
[Single linkage clustering](http://en.wikipedia.org/wiki/Single-linkage_clustering "Single linkage clustering")
[Complete linkage clustering](http://en.wikipedia.org/wiki/Complete_linkage_clustering "Complete linkage clustering")


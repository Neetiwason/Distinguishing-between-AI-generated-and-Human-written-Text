## Metrics Used

This is the comprehensive list of all metrics used in generating our training dataset:

- [`nx.degree_centrality(G)`](#degree-centrality)
- [`nx.eigenvector_centrality_numpy(G)`](#eigenvector-centrality)
- [`nx.closeness_centrality(G)`](#closeness-centrality)
- [`nx.closeness_vitality(G)`](#closeness-vitality)
- [`nx.betweenness_centrality(G)`](#betweenness-centrality)
- [`nx.edge_load_centrality(G)`](#edge-load-centrality)
- [`nx.all_pairs_node_connectivity(G)`](#all-pairs-node-connectivity)
- [`nx.average_neighbor_degree(G)`](#average-neighbor-degree)
- [`nx.average_degree_connectivity(G)`](#average-degree-connectivity)
- [`nx.clustering(G)`](#clustering)
- [`nx.degree_assortativity_coefficient(G)`](#degree-assortativity-coefficient)
- [`nx.degree_pearson_correlation_coefficient(G)`](#degree-pearson-correlation-coefficient)
- [`nx.average_clustering(G)`](#average-clustering)
- [`nx.check_planarity(G)[0]`](#planarity)

>### Degree Centrality
---

Degree centrality is a measure of the importance of a node in a graph. It is defined as the number of links incident upon a node (i.e., the number of ties that a node has). The degree centrality of a vertex, for a given graph with vertices and edges, is defined as the number of edges that are connected to that vertex.

Degree centrality can be interpreted in terms of the immediate risk of a node for catching whatever is flowing through the network (such as a virus, or some information). In other words, nodes with high degree centrality are more likely to be important in the network than nodes with low degree centrality.

The degree centrality algorithm is widely used in graph data science to measure the importance of nodes in a network analysis. It can be calculated using the following formula:

$C_D(v) = d_v / (n - 1)$

where $C_D(v)$ is the degree centrality of node $v$, $d_v$ is the degree of node $v$, and $n$ is the total number of nodes in the network.

>### Eigenvector Centrality
---

Eigenvector centrality is another measure of the importance of a node in a graph. It is based on the idea that a node is important if it is connected to other important nodes. In other words, nodes with high eigenvector centrality are more likely to be important in the network than nodes with low eigenvector centrality.

The eigenvector centrality algorithm is widely used in graph data science to measure the importance of nodes in a network analysis. It can be calculated using the following formula:

$C_E(v) = \frac{1}{λ} \sum\limits_{(u,v) \in E} C_E(u)$

where $C_E(v)$ is the eigenvector centrality of node $v$, $(u,v)$ are edges in the graph, $E$ is the set of edges in the graph, and $λ$ is a scalar value.

The eigenvector centrality algorithm is used in many applications, including ranking web pages (PageRank), identifying influential agents in social networks, and identifying systemically important firms in a production network.

>### Closeness Centrality
---

Closeness centrality is a measure of centrality in a network, which is calculated as the sum of the length of the shortest paths between a node and all other nodes in the graph. In other words, it measures how close a node is to all other nodes in the network. The more central a node is, the closer it is to all other nodes.

Closeness centrality is often used to identify nodes that are able to spread information very efficiently through a graph. It can be calculated for both directed and undirected graphs. The formula for closeness centrality involves taking the reciprocal of the sum of the shortest path distances between a node and all other nodes in the graph. It can be calculated using the formula:

$C_C(v) = \frac{n - 1}{\sum\limits_{u \in V} d(u, v)}$

where $n$ is the number of nodes in the graph, $d(u,v)$ is the shortest path distance between nodes $u$ and $v$, and $C_C​(v)$ is the normalized closeness centrality of node $v$.

>### Closeness Vitality
---

Closeness vitality is a measure of the importance of a node in a graph. It is defined as the change in the sum of distances between all node pairs when excluding that node. It measures how much the sum of the shortest path lengths in the graph increases when a particular node is removed.

First, compute the Wiener Index for the entire graph, which is the sum of the reciprocals of the closeness centrality for each node given as:

$W = \sum\limits_{v \in V} 1/C_C(v)$

Next, for each node, calculate the Wiener index again for a subgraph including all nodes but node $v$.

$W(v) = \sum\limits_{u \in V, u \neq v} 1/C_C(u)$

The vitality of a node is simply the difference between the total Wiener index and the Wiener index for the subgraph:

$C_V(v) = W - W(v)$

This measure gives an indication of how much longer shortest paths in the network become if a particular node is removed.

>### Betweenness Centrality
---

Betweenness centrality is a measure of centrality in a network, which is calculated based on shortest paths between nodes. It measures the extent to which a node lies on the shortest path between other nodes in the network.
The formula for betweenness centrality is given by:

$C_B​(v) = \sum\limits_{s\neq v \neq t} \frac{​\sigma_{st}(v)}{\sigma_{st}} ​$

where $s$ and $t$ are nodes in the graph, $σ_{st}$​ is the total number of shortest paths from node $s$ to node $t$, and $σ_{st}​(v)$ is the number of those shortest paths that pass through node $v$.

Betweenness centrality finds wide application in network theory: it represents the degree of which nodes stand between each other. For example, in a telecommunications network, a node with higher betweenness centrality would have more control over the network, because more information will pass through that node.

>### Edge Load Centrality
---

Edge load centrality is a concept in graph theory that measures the importance of an edge based on the number of shortest paths that pass through it. It is loosely based on load centrality in the sense that it counts the number of shortest paths which cross each edge.

The edge load centrality $C_L(e)$ of an edge $e$ is given by the expression:

$C_L​(e) = \sum\limits_{s \neq t \in V} \frac{\sigma_{st}(e)}{\sigma_{st}}​$

Here, $\sigma_{st}$ is the total number of shortest paths from node $s$ to node $t$ and $\sigma_{st}(e)$ is the number of those paths that pass through $e$.

This measure can provide insight into the structure of a network. For example, in a telecommunications network, an edge with higher edge load centrality would have more control over the network, because more information will pass through that edge.

>### All Pairs Node Connectivity
---

All pairs node connectivity is a concept in graph theory that measures the minimum number of nodes that must be removed to disconnect all pairs of nodes in a graph. It is also known as global node connectivity.

The all pairs node connectivity between two distinct and nonadjacent nodes is the minimum number of nodes that must be removed (minimum separating cutset) to disconnect them. By Menger’s theorem, this is equal to the number of node independent paths (paths that share no nodes other than source and target).

Algorithm:
```
1. Take a pair of nodes.
2. Find the shortest path between these nodes.
3. Remove all the edges in the shortest path.
4. Find the path again.
5. Repeat steps 2-4 until all paths are found.
```

>### Average Neighbor Degree
---

Average neighbor degree is a concept in graph theory that measures the average degree of the neighborhood of each node in a graph. It is defined as the average degree of the nodes that are connected to a given node by an edge. 

In an undirected graph, the neighborhood $N(v)$ of node $v$ contains the nodes that are connected to $v$ by an edge.
The average neighborhood degree of a node $v$ is defined as:

$D_N(v) = \frac{1}{|N(v)|} \sum\limits_{u \in N(v)} D(u)$

Here, $N(v)$ are the neighbors of node $v$ and $D(u)$ is the degree of node $u$ which belongs to $N(v)$.

For weighted graphs, an analogous measure can be defined:

$D_{N, w}(v) = \frac{1}{D_W(v)} \sum\limits_{u \in N(v)} w_{vu}.D(u)$

Here, $D_W(v)$ is the weighted degree of node $v$ given by sum of all incident edges to node:

$D_W(v) = \sum\limits_{(u,v) \in E} w_{uv}$

, $w_{ij}$ is the weight of the edge that links $v$ and $u$, and $N(v)$ are the neighbors of node $v$.

>### Average Degree Connectivity
---

The average degree connectivity in a graph is the average nearest neighbor degree of nodes with degree k. For unweighted graphs, the formula is:

$D_N(k) = \frac{1}{|D_k|} \sum\limits_{v \in D_k} D_N(v)$

Here, $D_k$ is the set of all nodes with degree $k$, $D_K(v)$ is average neighbor degree of vertice $v$ defined above.

For weighted graphs, an analogous measure can be defined:

$D_N(k) = \frac{1}{|D_k|} \sum\limits_{v \in D_k} D_{N, w}(v)$

Here, $D_{N, w}(v)$ is average neighbor degree of vertice $v$ defined above.

>### Clustering
---

Clustering in graph theory is a measure of the degree to which nodes in a graph tend to cluster together. The clustering coefficient is a measure of the density of triangles in a graph. There are two versions of this measure: global and local. The global clustering coefficient is based on triplets of nodes, while the local clustering coefficient is based on the neighborhood of a vertex. 

The formula for the global clustering coefficient is:

$C_G = \sum\limits_{u \in V} \frac{T(u)}{2.D(u).(D(u) - 1) - 2.D_{\leftrightarrow}(u)}$

where $T(u)$ is number of triangles directed in graph given by:

$T(u) = trace(A^3)$ where $A$ is adjacency matrix of graph and

and $D_{\leftrightarrow}(u)$ is reciprocal degree of node $u$ given by:

$D_{\leftrightarrow}(u) = $ number of all bidirectional edges

The local clustering coefficient for a vertex is given by the proportion of links between the vertices within its neighborhood divided by the number of links that could possibly exist between them. For a directed graph, there are $|N(u)|*(|N(u)| - 1)$ links that could exist among the vertices within the neighborhood (where $|N(u)|$ is the number of neighbors of a vertex $u$). Thus, the local clustering coefficient for directed graphs is given as:

$C_L(u) = \frac{2e_u}{|N(u)|.(|N(u)| - 1)}$

where $e_u$ is number of edges in neighborhood $N(u)$. Note that $e_u$ = $|N(u)|$ for simple undirected graphs.

These measures are 1 if every neighbor connected to a node $u$ is also connected to every other vertex within its neighborhood, and 0 if no vertex that is connected to node $u$ connects to any other vertex that is connected to node $u$.

>### Degree Assortativity Coefficient
---

The degree assortativity coefficient is a measure of the similarity of connections in the graph with respect to the node degree. It is a Pearson correlation coefficient of some node property f between pairs of connected nodes. If the measured property is a node degree, this is called the degree assortativity coefficient. The formula for the degree assortativity coefficient is:

$C_{DA} = \frac{\sum\limits_{(u, v) \in E} (D(u) - D_{avg, out}).(D(v) - D_{avg, in})}{\sqrt{\sum\limits_{(u, v) \in E} (D(u) - D_{avg, out})^2}.\sqrt{\sum\limits_{(u, v) \in E} (D(v) - D_{avg, in})^2}}$

where $D_{avg}(u)$ are average degrees of node $u$ given by:

$D_{avg, out} = \sum\limits_{(u, v) \in E} \frac{ D(u)}{|E|}$

$D_{avg, in} = \sum\limits_{(u, v) \in E} \frac{ D(v)}{|E|}$

The assortativity coefficient is a Pearson correlation coefficient, which ranges from -1 to +1. A positive assortativity coefficient indicates that nodes tend to connect to other nodes with the same or similar degree, while a negative assortativity coefficient indicates that nodes tend to connect to nodes with different degrees.

>### Degree Pearson Correlation Coefficient
---

The degree Pearson correlation coefficient in a graph, also known as the degree assortativity coefficient, is a measure of the correlation between the degrees of all pairs of nodes connected by an edge. It measures the tendency of nodes to connect with other nodes of similar degree.

The formula for the degree Pearson correlation coefficient r is given by:

$C_{DP} = \frac{|V|.\sum\limits_{(u, v) \in E} D(u).D(v) - \sum\limits_{u \in V} D(u).\sum\limits_{v \in V} D(v)}{\sqrt{|V|.\sum\limits_{u \in V} (D(u)^2 - (\sum\limits_{u \in V} D(u))^2)}.\sqrt{|V|.\sum\limits_{v \in V} (D(v)^2 - (\sum\limits_{v \in V} D(v))^2)}}$

It's value is the same as Degree Assortativity Coefficient.

>### Average Clustering
---

The average clustering coefficient of a graph is a measure of the degree to which nodes in a graph tend to cluster together. It is defined as the average of the local clustering coefficients of all nodes in the graph.

It is simply the average of the individual clustering coefficients $C_L(u)$:

$C_{avg L} = \frac{1}{|V|}.\sum\limits_{ u \in V } C_L(u)$

>### Planarity
---

Planarity in graphs refers to the property of a graph that can be drawn on a plane without any edges crossing each other. In other words, it is possible to represent the graph in two dimensions without any edge intersections.

Euler’s formula is used to determine whether a graph is planar or not. It states that for any connected planar graph with $v$ vertices, $e$ edges, and $f$ faces, we have:

$v - e + f = 2$
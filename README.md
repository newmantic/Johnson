# Johnson


Johnson's algorithm is used to find the shortest paths between all pairs of vertices in a sparse graph. It is particularly useful for graphs that may have negative edge weights but do not contain negative weight cycles. The algorithm efficiently combines the Bellman-Ford algorithm and Dijkstra's algorithm to handle negative weights and compute shortest paths.


Graph Representation:
Let G = (V, E) be a directed graph where:
V is the set of vertices.
E is the set of edges.
Each edge (u, v) in E has a weight w(u, v) which can be negative.

Shortest Path:
The goal is to find the shortest path between all pairs of vertices (u, v) in the graph.


1. Add a New Vertex
Add a new vertex s to the graph G.
Connect s to every other vertex v in V with an edge (s, v) where the weight w(s, v) = 0.

2. Run Bellman-Ford Algorithm
Run the Bellman-Ford algorithm with s as the source to compute the shortest path estimates h(v) from s to every vertex v in V.
If the Bellman-Ford algorithm detects a negative weight cycle, terminate the algorithm because the graph contains a negative cycle.

3. Reweight the Graph
Use the potential function h(v) obtained from the Bellman-Ford algorithm to reweight the original edges of the graph. Define a new weight function w' as follows:
w'(u, v) = w(u, v) + h(u) - h(v)
The reweighting ensures that all the edge weights w'(u, v) are non-negative.

4. Run Dijkstra's Algorithm
For each vertex u in V, run Dijkstra's algorithm on the reweighted graph G' to find the shortest paths from u to all other vertices.
The shortest path distance between vertices u and v in the original graph G can be obtained by:
d(u, v) = d'(u, v) + h(v) - h(u)
where d'(u, v) is the shortest path in the reweighted graph G'.


The time complexity of Johnson's algorithm is O(V^2 * log(V) + V * E), where V is the number of vertices and E is the number of edges. Bellman-Ford runs in O(V * E). Dijkstra's algorithm runs in O(V * log(V) + E) and is executed V times.

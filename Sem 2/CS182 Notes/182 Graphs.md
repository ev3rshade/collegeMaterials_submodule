11-05-2025 16:31

Status:  cs182

Tags: 
# Graph
> Vertices | Edges

##### Vertex (node)
- Primitive object
- Singular node
- ###### Vertex degree
	- Number of neighbors
- ###### Neighborhood
	- Set of all neighbors of a vertex v
	- N(v)
##### Edge (link)
- Unordered pair of vertices
- ###### Endpoints 
	- vertices of an edge
- ###### Adjacent
	- edge and endpoints

##### Subsets
- If A is a subset of V
- N(A) = $\bigcup_{v \in A} N(v)$set of all vertices in G that are adjacent to at least one vertex in A

### Handshake Theorem
>The sum of the degrees of the vertices equals twice the number of edges


## Types of Graphs
### Simple Graph
> No Loops | No multiple edges

### Multigraphs
> Multiple edges

### Pseudographs
> Loops | Multiple edges

### Complete Graph $k_{n}$
> A graph with edges between all pairs of vertices

### Cycle $c_{n}$
> n edges that form a closed simple curve

### Wheel $w_{n}$
> A cycle + a center vertex that is adjacent to all the other vertices

### Hypercube $h_{n}$
> $2^{n}$ vertices representing the $2^{n}$ bit strings of length n
- has $n2^{n - 1}$ edges, with two vertices being adjacent only when the bit strings they represent differ in exactly one bit position
### Dual graph
> Dual vertices are faces and dual edges link vertices whose face share an edge

### Bipartite graphs
> A simple graph that can be partitioned into two disjoint subsets $V_{1}$ and $V_{2}$ such that no edges connect two vertices in $V_{1}$ or $V_{2}$
- coloring the vertices
- #### Complete
	- Has a vertex set partitioned between two subsets and has an edge between two vertices only if one is in the first subset and the other is in the second subset
- #### Matching
	- Every vertex has degree 1


## Planar Graphs
> A graph that can be drawn in the plane without any edges crossing
#### Theorem
- There are an r number of regions in a planar representation of a graph G, 
- r = e - v + 2
##### Collaries
1. A connected planar graph satisfies e <= 3v - 6
2. A connected planar graph has a vertex of degree not exceeding five
3. A connected planar graph with e edges and v vertices with v >= 3 and no circuits of length 3, then e <= 2v - 4

## Playing with Graphs
### Vertex Coloring
> Coloring graph vertices so no two adjacent vertices are the same color
- Complete graph $k_n$ requires n colors
- Cycle $C_n$ requires 2 colors for n even and 3 for n odd
- Bipartite graph requires 2 colors

#### Dual graph coloring
- distinct colors for faces that share a boundary edge
#### Theorem
- The chromatic number of a planar graph is no greater than four
- (no map is greater than four colors)
#### Greedy Algorithm
- use it to color
- 1. create empty color set C
- 2. for each vertex v if C contains a color different from those of v's neighbors assign it the color
- 3. else assign v a new color and add the new color to C
## Properties of Graphs


## Graph Representation
### Matrix Representation
> n by n matrix $m$ where $m_{ij} = 1$ when $v_{i}v{j}$ and 0 otherwise

- The matrix is symmetric
- Space complexity $O(n^{2})$
- Good for dense graphs

### List Representation
> Array of tuples of edge lists
- Space complexity $O(m + n)$
- Good for sparse graphs

# Directed Graphs
> Set of vertices V and set of directed edges E
> Edge (u, v) starts at u and end at v

#### In-degree
- how many edges terminate at a vertex
#### Out-degree
- how many edges start with a specific vertex as their initial vertex

### Theorem
- Sum of in-degrees = sum of out-degrees

# Paths
> Sequence of edges that begin at a vertex and travels from vertex to vertex along edges
- Path from u to v
- (u, x1), (x1, x2), ... , (xk-1, xk) where xk = v
- When a graph is simple
	- vertex sequence
#### Connected
- vertices a and b are connected if there is a path from a to b
- graph is connected if every pair of vertices are connected
- Is an equivalence relation - equivalence classes are called connected components
### Circuit (cycle)
> path that begins and ends on the same vertex
## Simple path (or circuit)
> doesn't contain the same edge more than once
#### Euler path (or circuit)
> simple path or circuit containing every edge of a graph G
##### Theorem
- A connected multigraph has an Euler circuit if and only if each of its vertices has even degree
###### Hierholzer's Algorithm
> 1. Choose a starting vertex
> 2. Form a starting circuit c
> 3. While there exists an edge vw with v in c and w not in c
> 	3.1 Form a circuit d starting from vw using edges not in c
> 	3.2 Append d to c

##### Theorem
- A connected multigraph has an Euler path, but not an Euler circuit if and only if it has exactly two vertices of odd degree

#### Hamilton Path (or circuit)
> a simple path or circuit in a graph that passes through every vertex exactly once
##### Dirac's theorem
- A simple graph with n vertices with n >= 3 such that the degree of circuit is at least n/2 has a Hamilton circuit
##### Ore's theorem
- A simple graph with n vertices with n >= 3 such that deg(u) + deg(v) >= n for every pair of nonadjacent vertices u and v in the graph it has a Hamilton circuit

THESE THEOREMS ARE NOT ALL ENCOMPASSING
###### Trading sales person problem


---

# Active Recall
### Self Made
- Draw a simple graph to represent some data
- What are the four types of special graphs
- Advantages and disadvantages of the two types of representation
- Draw a bipartite graph
- Prove that connection is an equivalence relation
- prove Euler circuit theorem
- Revise dirac's theorem and ore's theorem
- Trading salesperson problem
- What are the application of each type of graph problem and manipulation


# References
### Slide Examples

### Google Notebook LM

KR 10.5 exercises 1 - 47 odd
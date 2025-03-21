Certainly! Below is a simple implementation of **Dijkstra's algorithm in C** for finding the shortest path between nodes in a weighted, directed graph. This algorithm is often used in routing and network optimization.

```c
#include <stdio.h>
#include <stdbool.h>
#include <limits.h>

// Number of vertices in the graph
#define V 6

// Function to find the vertex with the minimum distance value
int minDistance(int dist[], bool sptSet[]) {
    int min = INT_MAX, min_index;
    for (int v = 0; v < V; v++) {
        if (!sptSet[v] && dist[v] <= min) {
            min = dist[v];
            min_index = v;
        }
    }
    return min_index;
}

// Function to print the constructed distance array
void printSolution(int dist[]) {
    printf("Vertex \t Distance from Source\n");
    for (int i = 0; i < V; i++) {
        printf("%d \t %d\n", i, dist[i]);
    }
}

// Dijkstra's algorithm to find the shortest path
void dijkstra(int graph[V][V], int src) {
    int dist[V]; // Stores the shortest distance from src to i
    bool sptSet[V]; // Set to true if vertex i is included in shortest path tree

    // Initialize all distances as INFINITE and sptSet[] as false
    for (int i = 0; i < V; i++) {
        dist[i] = INT_MAX;
        sptSet[i] = false;
    }

    // Distance of source vertex from itself is always 0
    dist[src] = 0;

    // Find shortest path for all vertices
    for (int count = 0; count < V - 1; count++) {
        int u = minDistance(dist, sptSet);
        sptSet[u] = true;

        // Update dist[v] only if it's not in sptSet, there's an edge from u to v,
        // and total weight of path from src to v through u is smaller than current value of dist[v]
        for (int v = 0; v < V; v++) {
            if (!sptSet[v] && graph[u][v] && dist[u] != INT_MAX && dist[u] + graph[u][v] < dist[v]) {
                dist[v] = dist[u] + graph[u][v];
            }
        }
    }

    // Print the solution
    printSolution(dist);
}

int main() {
    int graph[V][V] = {
        {0, 4, 0, 0, 0, 0},
        {4, 0, 8, 7, 0, 0},
        {0, 8, 0, 9, 0, 0},
        {0, 7, 9, 0, 6, 0},
        {0, 0, 0, 6, 0, 10},
        {0, 0, 0, 0, 10, 0}
    };

    int source = 0; // Source vertex
    dijkstra(graph, source);

    return 0;
}
```

In this example, we have a graph with 6 vertices and their corresponding weights. The `dijkstra` function computes the shortest path from the specified source vertex (in this case, vertex 0) to all other vertices. The result is printed in the `printSolution` function.

Feel free to modify the graph and test different scenarios! 🚀.

Source: Conversation with Bing, 3/28/2024
(1) Dijkstra’s Algorithm in C - Code with C. https://www.codewithc.com/dijkstras-algorithm-in-c/.
(2) Maximetinu/Dijkstra-C: Dijkstra algorithm implementation in C - GitHub. https://github.com/Maximetinu/Dijkstra-C.
(3) Dijkstra’s Algorithm in C - Sanfoundry. https://www.sanfoundry.com/c-program-find-shortest-path-between-two-vertices-using-dijkstras-algorithm/.
(4) C / C++ Program for Dijkstra’s shortest path algorithm - GeeksforGeeks. https://www.geeksforgeeks.org/c-program-for-dijkstras-shortest-path-algorithm-greedy-algo-7/.
(5) Dijkstra's Algorithm - Programiz. https://www.programiz.com/dsa/dijkstra-algorithm.
(6) github.com. https://github.com/prakriti0502/Data-Structures/tree/fa40c625a88051c05c57c54194597000e14bb2c0/Algorithms%2FDijkastra.cpp.
(7) github.com. https://github.com/ForeStrikeGallery/Practise-C-/tree/9d2675189831e7b73ecade4ea84ebf70e70a710a/geeksforgeeks%2FGreedy%2Fdijkstras_algorithm_matrix.cpp.
(8) github.com. https://github.com/sshafeez/CUDAfy/tree/37f083ca94d90c2bc84a5238b38a306ab50f52f7/Static_Analysis_OLD%2FCXXfiles%2Fdijkstras.cpp.
(9) github.com. https://github.com/Lina-Liuna/algorithm/tree/a15b20bf3bf8fc211891e0c407f7cb21c47066f4/dijskstra.cpp.
(10) github.com. https://github.com/SreeyaReddy/AlgorithmsProject/tree/3a40a09b61ee48300b8fa1ad97aa7db54d634268/Source%2FGraph.java.
(11) github.com. https://github.com/nitcse2018/daa-PERCY99/tree/1c7b41772fd463f04d7b12bff84bfadee64e3ada/Greedy%20Approach%2FGreedy_Dijsktra.cpp.
(12) github.com. https://github.com/921kiyo/algorithms/tree/94d27453e5b6ab88f519c405fcb49fedbd12234c/ICL%2Fgraph%2Fdijkstra_matrix.cpp.
(13) github.com. https://github.com/MaPDores/edb-1/tree/10bdc3b88561a9fe270917da05eee4dea650f85c/FuncoesMenu%2FSourci.c.
(14) github.com. https://github.com/mitcse/CSE-Labs/tree/759248f2d7c47fbfec8dd5b3c67537c8030fad7b/ALG%20Lab%2FGreedy%20Approach%2FDijkstra%2Fdijkstra2.c.
(15) github.com. https://github.com/hapiznuddin/kuliah_smt2/tree/a01f4e534d8a443208bbee41ea6c1b6154b69633/grap.cpp.
(16) github.com. https://github.com/webdeveloper13/Leetcode_practiceForSDE/tree/04131f2bcf9cf4dd946419275a47e937472d0757/D6-Graphs%2Fdijkstra.cpp.
(17) github.com. https://github.com/kumaramit685/Dijkstra-using-vEB-Tree/tree/811b666cba65c0d05bcc81e0e6e15a95685efbc6/vEB_Dijkstra_tc3.cpp.
(18) github.com. https://github.com/MiichaelD/c_cpp/tree/3585648a8ae6bf5fb117f4f1ff17453cebf85777/graphs%2Fdijkstra.cpp.
(19) github.com. https://github.com/shahidsiddiqui786/DSA_learning/tree/72e1a90660edd2a3f915bfd491aff986178b7f2d/backtracking%2Fkala1.cpp.
(20) en.wikipedia.org. https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm.




Certainly! Below is a Python implementation of **Dijkstra's algorithm** for finding the shortest path between nodes in a weighted, directed graph. We'll create a simple example graph and compute the shortest path from a specified source vertex.

```python
class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.graph = [[0] * vertices for _ in range(vertices)]

    def min_distance(self, dist, spt_set):
        min_dist = float('inf')
        min_index = -1
        for v in range(self.V):
            if not spt_set[v] and dist[v] < min_dist:
                min_dist = dist[v]
                min_index = v
        return min_index

    def dijkstra(self, src):
        dist = [float('inf')] * self.V
        dist[src] = 0
        spt_set = [False] * self.V

        for _ in range(self.V - 1):
            u = self.min_distance(dist, spt_set)
            spt_set[u] = True

            for v in range(self.V):
                if not spt_set[v] and self.graph[u][v] and dist[u] != float('inf') \
                        and dist[u] + self.graph[u][v] < dist[v]:
                    dist[v] = dist[u] + self.graph[u][v]

        self.print_solution(dist)

    def print_solution(self, dist):
        print("Vertex \t Distance from Source")
        for i in range(self.V):
            print(f"{i} \t {dist[i]}")

if __name__ == "__main__":
    graph = Graph(6)
    graph.graph = [
        [0, 4, 0, 0, 0, 0],
        [4, 0, 8, 7, 0, 0],
        [0, 8, 0, 9, 0, 0],
        [0, 7, 9, 0, 6, 0],
        [0, 0, 0, 6, 0, 10],
        [0, 0, 0, 0, 10, 0]
    ]

    source = 0  # Source vertex
    graph.dijkstra(source)
```

In this Python code, we create a `Graph` class that represents the graph structure. The `dijkstra` method computes the shortest path from the specified source vertex (in this case, vertex 0) to all other vertices. The result is printed using the `print_solution` method.

Feel free to modify the graph and test different scenarios! 🚀

Source: Conversation with Bing, 3/28/2024
(1) Implementing Dijkstra’s Algorithm in Python | Udacity. https://www.udacity.com/blog/2021/10/implementing-dijkstras-algorithm-in-python.html.
(2) GitHub - dmahugh/dijkstra-algorithm: simple Python 3 implementation of .... https://github.com/dmahugh/dijkstra-algorithm.
(3) dijkstra · PyPI. https://pypi.org/project/dijkstra/.
(4) GitHub - crixodia/python-dijkstra: Dijkstra's algorithm implementation .... https://github.com/crixodia/python-dijkstra.
(5) Python Program for Dijkstra’s shortest path algorithm - GeeksforGeeks. https://www.geeksforgeeks.org/python-program-for-dijkstras-shortest-path-algorithm-greedy-algo-7/.

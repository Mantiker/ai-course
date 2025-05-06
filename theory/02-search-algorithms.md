# Search algorithms

A **search algorithm** is an algorithm designed to solve a search problem. Search algorithms work to retrieve information stored within particular data structure.

## Common types of search problems include:

- **Uninformed Search**: In uninformed search, the AI system explores the problem space blindly, without any knowledge of the problem structure. Breadth-First Search (BFS) and Depth-First Search (DFS) are typical examples of uninformed search algorithms.

- **Informed Search (Heuristic Search)**: In contrast to uninformed search, informed search algorithms incorporate domain-specific knowledge or heuristics to guide the search process. A* (A-star) algorithm is a well-known example of an informed search algorithm.

- **Adversarial Search**: Adversarial search is employed in games and scenarios where the AI system competes against one or more opponents. Minimax and Alpha-Beta Pruning are commonly used in adversarial search.

## Algorithms

### DFS (Depth-First Search)

Advantages of Depth-First Search:
- Memory Efficiency: DFS has relatively low memory requirements as it explores a single branch in-depth before backtracking. It is well-suited for problems with large state spaces, where memory consumption is a concern.
- Completeness (In Finite Spaces): In problems with finite state spaces, DFS is guaranteed to find a solution if one exists. This property holds because it explores all possible paths.
- Applicability in Certain Scenarios: DFS is particularly useful in scenarios where finding any solution quickly is more important than finding the optimal solution. It is commonly applied in pathfinding and maze-solving scenarios.

Limitations of Depth-First Search:
- Completeness (In Infinite Spaces): DFS may not be complete in infinite state spaces or graphs with loops. In such cases, it can get trapped in cycles and fail to find a solution even if one exists.
- Lack of Optimal Solution: DFS does not guarantee finding the optimal solution. It might find a solution faster, but that solution may not be the most optimal one.
- Memory Usage (In Infinite Spaces): In infinite state spaces or deeply branching problems, DFS may consume a lot of memory due to its depth-first exploration, potentially leading to stack overflow.

### BFS (Breadth-First Search)

Advantages of Breadth-First Search:
- Guaranteed Optimal Solution: BFS guarantees finding the optimal solution (shortest path) for problems with unit path costs, as it explores nodes level by level.
- Completeness (In Finite Spaces): For problems with finite state spaces, BFS is complete, meaning it will find a solution if one exists.
- Suitable for Pathfinding: BFS is particularly useful for finding the shortest path in unweighted graphs, making it ideal for pathfinding scenarios.

Limitations of Breadth-First Search:
- Memory Usage: BFS may consume significant memory, especially in graphs with deep levels or an infinite state space.
- Inefficiency (In Infinite Spaces): In infinite state spaces, BFS may take a long time to explore all nodes at a given level before moving to the next level.


Aspect / Algorithm | DFS | BFS
-------------------|--------------------|--------------------
Approach | Explores as far as possible along each branch before backtracking. <br>It delves deeply into the problem space, focusing on exploring one branch<br> at a time, going as deep as possible before exploring other branches.|Explores all neighbors of the current node before moving on to their respective neighbors.<br> It systematically explores nodes level by level, moving outward from the start node,<br> and forming concentric circles like ripples in water.
Order of Exploration | Follows the Last-In-First-Out (LIFO) order of exploring nodes using a stack data structure | Follows the First-In-First-Out (FIFO) order of exploring nodes using a queue data structure
Completeness | In finite state spaces, DFS is complete, meaning it will find a solution if one exists.<br> However, in infinite state spaces or graphs with loops, it may not terminate or find<br> a solution if one exists.|BFS is complete in finite state spaces and will always find the shortest path in unweighted<br> graphs if one exists.
Memory Usage | DFS typically requires less memory compared to BFS because it explores one branch <br>at a time and uses a stack for backtracking. However, it may consume significant memory<br> in graphs with deep levels<br> or infinite state spaces.| BFS generally requires more memory compared to DFS as it needs to store all nodes <br>at the current level in the queue before moving to the next level.
Optimal Solution | DFS does not guarantee finding the optimal solution, especially in graphs <br>with varying edge weights or costs. It might find a solution faster, but that solution <br> may not be the shortest or most optimal one. | BFS guarantees finding the optimal solution (shortest path) for problems with unit path costs,<br> as it explores nodes level by level.
Use Cases | DFS is well-suited for problems where finding any solution quickly is more important  <br>than finding the optimal one. It is commonly used in maze-solving, puzzle-solving,  <br>and depth-limited search scenarios. | BFS is ideal for finding the shortest path in unweighted graphs and is commonly used  <br>in pathfinding, puzzle-solving, and network traversal scenarios.


### Depth-Limited Search

Depth-Limited Search is a variation of Depth-First Search (DFS) that imposes a maximum depth or level on the search, preventing it from exploring beyond a specified depth limit. It combines the advantages of DFS's memory efficiency with the completeness of BFS within a limited depth range. DLS is particularly useful in scenarios with limited memory resources or infinite state spaces, where traditional DFS may get stuck in infinite loops.

### Iterative Deepening

Iterative Deepening is an intelligent search strategy that uses Depth-Limited Search (DLS) with an incrementally increasing depth limit. It repeatedly applies DLS with increasing depth limits until the goal state is found or a specified maximum depth is reached. This approach combines the benefits of BFS's completeness and DFS's memory efficiency.

### Greedy Best-First Search - Navigating Efficiently with Heuristic Guidance

In the realm of informed search algorithms, Greedy Best-First Search stands out as a powerful technique that combines heuristic guidance with efficiency in exploration. Unlike uninformed search algorithms, Greedy Best-First Search intelligently selects the most promising path based on heuristic evaluation, making it well-suited for optimization problems and situations where finding a quick but not necessarily optimal solution is desirable. Today, we'll delve into the step-by-step algorithm of Greedy Best-First Search, explore heuristic functions and their significance, provide a Python code example, and discuss its advantages and limitations.

Greedy Best-First Search explores the problem space by prioritizing the nodes that appear most promising according to a heuristic evaluation function. This function, often denoted as h(n), estimates the potential cost or distance from a node to the goal state. The algorithm prioritizes nodes with lower heuristic values, believing they are closer to the goal.

**Heuristic functions** are essential components of Greedy Best-First Search. These functions provide an estimation of the remaining cost or distance to reach the goal state from a given node. The quality of the heuristic function influences the algorithm's effectiveness in prioritizing nodes correctly, guiding it towards promising regions of the problem space. A good heuristic function should be admissible, meaning it never overestimates the actual cost to reach the goal. Admissible heuristics guarantee that the Greedy Best-First Search will always find the optimal solution if one exists.

Advantages of Greedy Best-First Search:
- Efficiency: Greedy Best-First Search is generally more efficient than uninformed search algorithms like BFS and DFS due to its intelligent node prioritization based on heuristics.
- Quick Solutions: In certain problem spaces, Greedy Best-First Search can provide quick but not necessarily optimal solutions, making it suitable for scenarios where finding any feasible solution rapidly is essential.
- Space Efficiency: Greedy Best-First Search requires relatively less memory compared to algorithms like BFS because it only keeps track of nodes in the priority queue.

Limitations of Greedy Best-First Search:
- Lack of Optimality: Greedy Best-First Search does not guarantee finding the optimal solution in all cases. The chosen heuristic may lead the algorithm towards a suboptimal path.
- Completeness: Greedy Best-First Search may not be complete in infinite state spaces or problems with no feasible solutions, as it does not explore all possibilities systematically.
- Heuristic Sensitivity: The effectiveness of Greedy Best-First Search heavily relies on the quality of the chosen heuristic function. Poor heuristics may lead to inefficient or incorrect results.


### A* Search Algorithm - Efficient Pathfinding with Heuristic Optimization

A* Search Algorithm is a widely used informed algorithm that combines the benefits of both Dijkstra's algorithm and Greedy Best-First Search. By incorporating a heuristic function that estimates the cost from the start node to the goal node, A* efficiently explores the problem space to find the shortest path.

A* Search Algorithm aims to find the shortest path from the start node to the goal node in a graph or grid. It employs two main factors for each node: the actual cost from the start node to that node (denoted as g(n)), and the estimated cost from that node to the goal node (denoted as h(n)). The key idea behind A* is to prioritize nodes that have the lowest total cost, calculated as the sum of g(n) and h(n). By doing so, A* explores paths that are likely to lead to the optimal solution while avoiding unnecessary exploration.

Aspect / Algorithm | Greedy Best-First Search | A* Search
-------------------|--------------------|--------------------
Completeness | Greedy Best-First Search is not complete, meaning it does not guarantee finding <br> a solution even if one exists. It can get stuck in infinite loops or fail to explore <br>all possible paths.| A* Search is complete when used with an admissible heuristic. <br>It will always find a solution if one exists, provided that the search space<br> is finite.
Optimality | Greedy Best-First Search does not guarantee finding the optimal solution. <br>It tends to prioritize nodes based solely on their heuristic values, which may lead <br>to suboptimal paths.| A* Search guarantees optimality when used with an admissible heuristic. <br>It explores paths with the lowest total cost (actual cost plus heuristic value), <br>ensuring the shortest path is found.
Heuristic | Greedy Best-First Search relies solely on the heuristic function to prioritize nodes.<br> It has no knowledge of the actual cost from the start node, which may result in <br>an overly optimistic or pessimistic assessment.| _A* Search_ incorporates both actual cost `(g(n))` and heuristic value `(h(n))` into <br>its evaluation. This combination allows _A*_ to strike a balance between exploration<br> and exploitation, making more informed decisions.
Efficiency | Greedy Best-First Search is generally more efficient than uninformed search<br> algorithms like BFS and DFS, as it uses heuristic guidance. However, it may not be<br> as efficient as _A*_ in terms of finding the optimal path.| _A* Search_ is efficient in finding the optimal path because it intelligently explores <br>the most promising paths first based on the sum of actual cost and heuristic value. <br>With a good admissible heuristic, A* can often reach the goal faster than other<br> algorithms.
Memory Usage | Greedy Best-First Search requires less memory than algorithms like BFS because it <br>only keeps track of nodes in the priority queue. However, it may still consume <br>considerable memory depending on the size of the search space.| _A* Search_ can consume significant memory due to the need to store information about <br>the nodes in both the open list and closed list. The memory requirements can grow <br>substantially for larger search spaces.
Applicability | Greedy Best-First Search is suitable for scenarios where a quick but not necessarily <br>optimal solution is acceptable. It can be used in pathfinding, route planning, and <br>heuristic optimization problems.|_A* Search_ is ideal for scenarios where finding the optimal solution is crucial.<br> It is commonly used in pathfinding, robotics, game AI, and navigation systems.

### Local Search Algorithms - Hill-Climbing Algorithm - Navigating Local Peaks in Search of the Summit

Hill-Climbing is a popular local search technique employed in optimization problems, where the goal is to find the best possible solution within a restricted neighborhood of the search space. Inspired by the concept of climbing a hill, this algorithm iteratively explores neighboring solutions and moves towards higher-elevation states until reaching a peak, a local optimum.

Types of Hill-Climbing:
- Simple Hill-Climbing In Simple Hill-Climbing, the algorithm always moves to the first neighboring state with a better objective function value. If no such neighbor is found, the algorithm terminates, even if the current state is not a local optimum.
- Steepest-Ascent Hill-Climbing Steepest-Ascent Hill-Climbing, also known as steepest ascent or steepest ascent climbing, evaluates all neighboring states and moves to the state with the best objective function value. It chooses the steepest upward slope, making it less likely to get stuck in local optima.

### Local Search Algorithms - Simulated Annealing

Simulated Annealing is a powerful probabilistic optimization technique inspired by the annealing process in metallurgy. This algorithm mimics the gradual cooling of a material to minimize defects and reach an optimal state. Similarly, Simulated Annealing seeks to find the global optimum of a problem by allowing controlled random movements, which enable it to escape local optima and explore a broader search space.




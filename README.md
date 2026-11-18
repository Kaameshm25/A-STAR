<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: KAAMESH M     </h3>
<h3>Register Number: 212223040080  </h3>

<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>



1.  Initialize the open list
2.  Initialize the closed list
    put the starting node on the open 
    list (you can leave its f at zero)

3.  while the open list is not empty
    a) find the node with the least f on 
       the open list, call it "q"

    b) pop q off the open list
  
    c) generate q's 8 successors and set their 
       parents to q
   
    d) for each successor
        i) if successor is the goal, stop search
        
   ii) else, compute both g and h for successor
          successor.g = q.g + distance between 
                              successor and q
          successor.h = distance from goal to 
          successor (This can be done using many 
          ways, we will discuss three heuristics- 
          Manhattan, Diagonal and Euclidean 
          Heuristics)
          
successor.f = successor.g + successor.h
          
iii) if a node with the same position as 
            successor is in the OPEN list which has a 
           lower f than successor, skip this successor

iV) if a node with the same position as 
            successor  is in the CLOSED list which has
            a lower f than successor, skip this successor
            otherwise, add  the node to the open list
            end (for loop)
  
e) push q on the closed list
end (while loop)



<H3>Program:</H3>

```


from collections import defaultdict

H_dist = {}

def aStarAlgo(start_node, stop_node):
    open_set = set([start_node])
    closed_set = set()
    g = {}
    parents = {}

    g[start_node] = 0
    parents[start_node] = start_node

    while len(open_set) > 0:
        n = None

        for v in open_set:
            if n is None or g[v] + heuristic(v) < g[n] + heuristic(n):
                n = v

        if n is None:
            print("Path does not exist!")
            return None

        if n == stop_node:
            path = []

            while parents[n] != n:
                path.append(n)
                n = parents[n]

            path.append(start_node)
            path.reverse()

            print("Path found: {}".format(path))
            return path

        for (m, weight) in get_neighbors(n):
            if m not in open_set and m not in closed_set:
                open_set.add(m)
                parents[m] = n
                g[m] = g[n] + weight
            else:
                if g[m] > g[n] + weight:
                    g[m] = g[n] + weight
                    parents[m] = n

                    if m in closed_set:
                        closed_set.remove(m)
                        open_set.add(m)

        open_set.remove(n)
        closed_set.add(n)

    print("Path does not exist!")
    return None


def get_neighbors(v):
    return Graph_nodes.get(v, [])


def heuristic(n):
    return H_dist.get(n, 0)


graph = defaultdict(list)

n, e = map(int, input().split())

for _ in range(e):
    while True:
        line = input().strip()
        if line:
            break

    u, v, cost = line.split()
    cost = float(cost)

    graph[u].append((v, cost))
    graph[v].append((u, cost))


for _ in range(n):
    while True:
        line = input().strip()
        if line:
            break

    node, h = line.split()
    H_dist[node] = float(h)


Graph_nodes = graph

start_node = max(H_dist, key=H_dist.get)
goal_node = min(H_dist, key=H_dist.get)

aStarAlgo(start_node, goal_node)
```
<H3>output:</H3>

<img width="730" height="601" alt="image" src="https://github.com/user-attachments/assets/c2206b15-a6e2-4d4f-a019-778bb6a058c8" />




<hr>
<h3>Result:</h3>
<hr>
<p>Thus,The experiment was done successfully.</p>

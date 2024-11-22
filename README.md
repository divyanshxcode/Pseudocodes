# Pseudocodes

Contains pseudocodes of popular algorithms in DAA (CS205n) - Divyansh Singh


### N-Queen Problem

```bash
n_queens(board[][], row, n) {
    if row == n 
        return true
    for col = 0 to n - 1 
    {
        if is_safe(board, row, col, n) 
        {
            board[row][col] = 1 #Mark Queen Present
            if n_queens(board, row + 1, n) #Rec-Call to place Queen in next row
                return true
            board[row][col] = 0
        }
    }
    return false
}

is_safe(board[][], row, col, n){
    for i = 0 to row - 1 
        if board[i][col] == 1 #Check Up 
            return false
    for i = row - 1, j = col - 1 while i >= 0 and j >= 0 #Check Left Diagonal
        if board[i][j] == 1 
            return false
    for i = row - 1, j = col + 1 while i >= 0 and j < n #Check Right Diagonal
        if board[i][j] == 1 
            return false
    return true
}
```
### Dijikstra's Algorithm

```bash
dijkstra(graph[], source)
{
    distance[source] = 0
    for each vertex v in graph
        if v != source
            distance[v] = ∞
        previous[v] = null

    priority_queue = empty             #Min-priority queue
    insert(priority_queue, source, 0)  #Insert source with distance 0

    while priority_queue is not empty
    {
        u = extract_min(priority_queue)    #Extract vertex u of smallest distance

        for each neighbor v of u
        {
            alt = distance[u] + weight(u, v)  #Alternative distance through u
            if alt < distance[v]
            {
                distance[v] = alt
                previous[v] = u
                insert(priority_queue, v, alt)   #Insert v with updated distance
            }
        }
    }

    return distance[], previous[]
}
```
### Kruskal's Algorithm

```bash
kruskal(graph):
    sort edges by weight  
    initialize disjoint-set  
    mst = []  
    for each edge (u, v, weight) in graph:
        if find(u) != find(v):  # Check if in same set
            mst.append((u, v, weight))  # Add to MST
            union(u, v)  # Union sets
    return mst 

find(vertex):
    if parent[vertex] != vertex:  # If not root
        parent[vertex] = find(parent[vertex])  # Path compression
    return parent[vertex]

union(u, v):
    root_u = find(u)  
    root_v = find(v)
    if root_u != root_v:  # If different roots
        if rank[root_u] > rank[root_v]:  
            parent[root_v] = root_u  # Attach root_v to root_u
        else if rank[root_u] < rank[root_v]: 
            parent[root_u] = root_v  # Attach root_u to root_v
        else:
            parent[root_v] = root_u  # Attach root_v to root_u
            rank[root_u] += 1  

```

---

More in the respective text files. 
Something wrong in code? Raise issue :)

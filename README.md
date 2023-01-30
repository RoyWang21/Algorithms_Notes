# Notes for Algorithm and Data Structure Exercises

## Data Structures:

### Arrays:
### Hash Table
### Stack / Queue
### Heap
### Linked List
### Binary Tree
### Graph


## Algorithms:

### Sort:
- Merge sort recursion template:
```
	def merge_sort(list) 
		# base case: if len(list) == 0 or 1, return list
		# code for even splitting
		# list -> list1 + list2
		def merge(list1, list2):
			# compare, select, merge
			return newlist
		return merge(merge_sort(list1), merge_sort(list2))
```

### Linked Lists:
- Traverse template 
```
	newhead = cur = ListNode(-1) 
	cur.next = head
	For :
		cur = cur.next
		…
	return newhead.next
```
- Split template
```
        head2 = break_node.next # rewire
        break_node.next = None # disconnect
```
- Reverse template
```
        prev = None
        current = head
        while current :
            next = current.next
            current.next = prev
            prev = current
            current = next
        head = prev
```

### Breadth First Search(BFS):
- Basic template
```
        queue = [root]
        while queue:
		nq = len(queue) # this is important as queue sizes changes on the fly
		for i in range(nq): # each loop takes care of each level of nodes
			cur_node = queue.pop(0)
			# do sth with cur_node…
			queue.append(cur_node.left) # if exists
			queue.append(cur_node.right) # if exists
```

### Depth Frist Search(DFS):

build graph first - adj list: g[node_i] = [node_j, node_k…]

Returning results via DFS:

```
def dfs(node):
	# search reaches the end
	if end_condition_met:
		return 0
	# iterate over each neighbor of current node
	for i in g[node]:
		output.append(some_func( dfs(i) ))
	return aggregate(output)

 return dfs(root)
```
Cumulating results via DFS
```
def dfs(graph, path):
	nonlocal output
	# search reaches the end
	if end_condition_met:
		# a valid path has been found
		output.append(path)
                return
	for i in g[node]:
		updated_path = some_func(graph)
		graph_rest = some_func_2(graph)
		# search the rest of the graph
                dfs(graph_rest, updated_path)

output = []
dfs(graph, path=[])
return output
```

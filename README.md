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
### Binary Search:
- Binary search template
```
# use case: If we can discover some kind of monotonicity, for example, if condition(k) is True then condition(k + 1) is True, then we can consider binary search.
# Obj: Minimize k , s.t. condition(k) is True
    left, right = min(search_space), max(search_space) #  rule1: include all possible elements
    while left < right:
        mid = left + (right - left) // 2
        if condition(mid): # need careful design
            right = mid
        else:
            left = mid + 1
    return left # or return left - 1. # rule2: after exiting the while loop, left is the minimal k satisfying the condition
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
Cumulating results via DFS:
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
Backtracking template:
```
def backtrack(candidate):
    if find_solution(candidate):
        output(candidate)
        return
    
    # iterate all possible candidates.
    for next_candidate in list_of_candidates:
        if is_valid(next_candidate):
            # try this partial candidate solution
            place(next_candidate)
            # given the candidate, explore further.
            backtrack(next_candidate)
            # backtrack
            remove(next_candidate)
```
- Extend list non-inplace: lis + [I]
- Extend set non-inplace: vis | set([I])
- instead of path.append -> dfs() -> path.pop; do dfs(path+[I]) to save memory

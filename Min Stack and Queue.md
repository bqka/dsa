n this article we will consider three problems: first we will modify a stack in a way that allows us to find the smallest element of the stack in  $O(1)$ , then we will do the same thing with a queue, and finally we will use these data structures to **find the minimum in all subarrays of a fixed length in an array in  $O(n)$**

We want to modify the stack data structure in such a way, that it is possible to find the smallest element in the stack in  $O(1)$  time, while maintaining the same asymptotic behavior for adding and removing elements from the stack. Quick reminder, on a stack we only add and remove elements on one end.

To do this, we will not only store the elements in the stack, but we will store them in pairs: the element itself and the minimum in the stack starting from this element and below.

`stack<pair<int, int>> st;`

![[Pasted image 20260215184935.png]]

## Queue Mod 1

![[Pasted image 20260215185509.png]]


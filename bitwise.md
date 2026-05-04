check power of 2

	n & (n - 1) == 0

remove lowest set bit

	n = n & (n  - 1)

get lowest set bit

	n & -n
	
![[Pasted image 20260503005905.png]]
property of 2's complement

```
12 → 1100
result → 0100 (4)
```

bit masking 

	int mask = 0;
	mask |= (1 << i);   // add element
	mask &= ~(1 << i);  // remove
	mask & (1 << i)     // check


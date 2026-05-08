https://codeforces.com/contest/2217/problem/C
crazy shit

![[Pasted image 20260410200542.png]]

like when it is wrapping, distance between 2 positions = gcd(a, b)
that's why u want gcd = 1 to cover all

cause like if gcd(a, b) = 1, then to make them into the same number, that is the lcm(a, b) = a * b
cause lcm(a, b) = a * b / gcd(a, b)

consider a = 6, b = 10

gcd(a, b) = 2
so, lcm(a, b) = 30 is like the point where the 2 numbers meet in their sequence
6, 12, 18, 24, 30 ...
10, 20, 30..

so anything after that is kind of like a state that has already been achieved

so like if i do 6 * k % 10, after 6 becomes 30, the mod values start repeating
so max states = 5
general formula

$$b.k \text{ mod } a$$
$$states = \frac{a}{gcd(a, b)}$$
# The math behind the project

## The number of lattice paths in an $n\times n$ grid ($n \ge 0$) from one corner to its opposite is $\begin{pmatrix} 2n \\ n \end{pmatrix}$
1. Assume the start is the top left corner and the end is the bottom right corner.
$$
S-*-*\\
|\;\;\;\;\;|\;\;\;\;\;|\\
*-*-*\\
|\;\;\;\;\;|\;\;\;\;\;|\\
*-*-F
$$

2. No cycles are allowed.
3. Using the above rule on cycles, the path *MUST* at each point either go to the right or down.
$$
*\rightarrow*\rightarrow*\\
\downarrow\;\;\;\;\;\,\downarrow\;\;\;\;\;\,\downarrow\\
*\rightarrow*\rightarrow*\\
\downarrow\;\;\;\;\;\,\downarrow\;\;\;\;\;\,\downarrow\\
*\rightarrow*\rightarrow*\\
$$
4. Using the previous rule, the grid can be represented as a tree with only a maximum of two children and a maximum of two parents at each node.
$$
*\\
/\backslash\\
*\;\;*\\
/\backslash\;\,/\backslash\\
*\;\;*\;\;*\\
\backslash/\;\,\backslash/\\
*\;\;*\\
\backslash/\\
*
$$
5. Using the tree representation, each node can be labeled.
$$
1\\
/\backslash\\
2\;\;\;3\\
/\backslash\;\,/\backslash\\
4\;\;\;5\;\;\;6\\
\backslash/\;\,\backslash/\\
7\;\;\;8\\
\backslash/\\
9
$$
6. Using the above rules, the path will always be of length $2n+1$ nodes and $2n$ decisions.
$$
1\rightarrow2\rightarrow4\rightarrow7\rightarrow9\\
1\rightarrow2\rightarrow5\rightarrow7\rightarrow9\\
1\rightarrow2\rightarrow5\rightarrow8\rightarrow9\\
1\rightarrow3\rightarrow5\rightarrow7\rightarrow9\\
1\rightarrow3\rightarrow5\rightarrow8\rightarrow9\\
1\rightarrow3\rightarrow6\rightarrow8\rightarrow9
$$
7. Each decision eliminates the total number of paths possible from that point.
$$
1 : 6\; Possibilities\\
$$
$$
1\\
/\backslash\\
2\;\;\;3\\
/\backslash\;\,/\backslash\\
4\;\;\;5\;\;\;6\\
\backslash/\;\,\backslash/\\
7\;\;\;8\\
\backslash/\\
9
$$
$$
1\rightarrow3 : 3\; Possibilities\\
$$
$$
1\\
\;\,\backslash\\
\;\,\;\;\;3\\
\;\,\;\,\;\,/\backslash\\
\;\,\;\;\;5\;\;\;6\\
\;\,/\;\,\backslash/\\
7\;\;\;8\\
\backslash/\\
9
$$
$$
1\rightarrow3\rightarrow5 : 2\; Possibilities\\
$$
$$
1\\
\;\,\backslash\\
\;\,\;\;\;3\\
\;\,\;\,\;\,/\;\,\\
\;\,\;\;\;5\;\;\;\;\,\\
\;\,/\;\,\backslash\;\,\\
7\;\;\;8\\
\backslash/\\
9\\
$$
$$
1\rightarrow3\rightarrow5\rightarrow7 : 1\; Possibility\\
$$
$$
1\\
\;\,\backslash\\
\;\,\;\;\;3\\
\;\,\;\,\;\,/\;\,\\
\;\,\;\;\;5\;\;\;\;\,\\
\;\,/\;\,\;\,\;\,\\
7\;\;\;\;\,\\
\backslash\;\,\\
9\\
$$
$$
1\rightarrow3\rightarrow5\rightarrow7\rightarrow9\\
$$

8. Taking the number of paths left and putting them in the tree, you can make the center diamond of Pascal's triangle (if you flip all directional arrows).

$$
6\\
/\backslash\\
3\;\;\;3\\
/\backslash\;\,/\backslash\\
1\;\;\;2\;\;\;1\\
\backslash/\;\,\backslash/\\
1\;\;\;1\\
\backslash/\\
1
$$
9. Pascal's Triangle is defined by:
$$
1\\
1,\;1\\
1,\;2,\;1\\
1,\;3,\;3,\;1\\
1,\;4,\;6,\;4,\;1\\
1,\;5,\;10,\;10,\;5,\;1\\
\vdots
$$
$$
\left(\begin{smallmatrix} 0 \\ 0 \end{smallmatrix}\right)\\
\left(\begin{smallmatrix} 1 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 1 \\ 1 \end{smallmatrix}\right)\\
\left(\begin{smallmatrix} 2 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 2 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 2 \\ 2 \end{smallmatrix}\right)\\
\left(\begin{smallmatrix} 3 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 3 \end{smallmatrix}\right)\\
\left(\begin{smallmatrix} 4 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 4 \end{smallmatrix}\right)\\
\left(\begin{smallmatrix} 5 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 4 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 5 \end{smallmatrix}\right)\\
\vdots
$$

## Converting the Binomial locations to usable locations

Coordinates can be made for Pascal's Triangle, if Pascal's Triangle's Coordinate Representation is converted from: 
$$
1\\
1,\;1\\
1,\;2,\;1\\
1,\;3,\;3,\;1\\
1,\;4,\;6,\;4,\;1\\
1,\;5,\;10,\;10,\;5,\;1\\
\vdots
$$
$$
\left(\begin{smallmatrix} 0 \\ 0 \end{smallmatrix}\right)\\
\left(\begin{smallmatrix} 1 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 1 \\ 1 \end{smallmatrix}\right)\\
\left(\begin{smallmatrix} 2 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 2 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 2 \\ 2 \end{smallmatrix}\right)\\
\left(\begin{smallmatrix} 3 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 3 \end{smallmatrix}\right)\\
\left(\begin{smallmatrix} 4 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 4 \end{smallmatrix}\right)\\
\left(\begin{smallmatrix} 5 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 4 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 5 \end{smallmatrix}\right)\\
\vdots
$$
to:
$$
1,\:\;\;1,\:\;\;1,\:\;\;1,\:\;\;1,\ldots\\
1,\:\;\;2,\:\;\;3,\:\;\;4,\:\;\;5,\ldots\\
1,\:\;\;3,\:\;\;6,\;10,\;15,\ldots\\
1,\:\;\;4,\;10,\;20,\;35,\ldots\\
1,\:\;\;5,\;15,\;35,\;70,\ldots\\
\vdots
$$
$$
\left(\begin{smallmatrix} 0 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 1 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 2 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 0 \end{smallmatrix}\right),\ldots\\
\left(\begin{smallmatrix} 1 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 2 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 1 \end{smallmatrix}\right),\ldots\\
\left(\begin{smallmatrix} 2 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 6 \\ 2 \end{smallmatrix}\right),\ldots\\
\left(\begin{smallmatrix} 3 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 6 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 7 \\ 3 \end{smallmatrix}\right),\ldots\\
\left(\begin{smallmatrix} 4 \\ 4 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 4 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 6 \\ 4 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 7 \\ 4 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 8 \\ 4 \end{smallmatrix}\right),\ldots\\
\vdots
$$
$$
\left(\begin{smallmatrix} 0 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 1 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 2 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 4 \end{smallmatrix}\right),\ldots\\
\left(\begin{smallmatrix} 1 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 2 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 4 \end{smallmatrix}\right),\ldots\\
\left(\begin{smallmatrix} 2 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 3 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 6 \\ 4 \end{smallmatrix}\right),\ldots\\
\left(\begin{smallmatrix} 3 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 4 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 6 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 7 \\ 4 \end{smallmatrix}\right),\ldots\\
\left(\begin{smallmatrix} 4 \\ 0 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 5 \\ 1 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 6 \\ 2 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 7 \\ 3 \end{smallmatrix}\right),\;
\left(\begin{smallmatrix} 8 \\ 4 \end{smallmatrix}\right),\ldots\\
\vdots
$$
Cartesian-style coordinates can be used to describe which value is desired (Assuming that only positive integers and zero are used as coordinates). Due to the symmetry in binomials, $ \begin{pmatrix} n \\ k \end{pmatrix} = \frac{n!}{k!\left(n-k\right)!}$ and $ \begin{pmatrix} n \\ n-k \end{pmatrix} = \frac{n!}{k!\left(n-k\right)!}$, the statement $ \begin{pmatrix} a+b \\ a \end{pmatrix} = \begin{pmatrix} a+b \\ b \end{pmatrix} = \left(a,b\right)$ can define this coordinate system.

Using the coordinate system above, the coordinate for the number of lattice paths is $\left(a,b\right)$ for an $a\times b$ grid, therefor, in this case, it should be coordinate $\left(n,n\right)$.

## Factorial is computationally slow, as it is recursive and requires multiplication, time for a different way
Multiplication is one of the slowest operations a computer can do ($O\left(n\;log\left(n\right)\right)$), especially those which require the previous result, as these operations cannot be done in parallel.

$n!$ requires $n-1$ multiplies, $\begin{pmatrix} n \\ k \end{pmatrix} = \frac{n!}{k!\left(n-k\right)!}$ requires $n$ multiplies and one divide, if you keep some of the intermediate results, but this will require loops, which are slow to accomplish this method has complexity of $O\left(n^2\;log\left(n\right)\right)$. Below is an implementation of this method in C.
```c
double binomial(int n, int k) {
	double k_factorial, n_factorial, n_k_factorial;
	if ((k > n) || (k < 0)) {
		return -1;
	}
	if ((n - k) < k) {
		k = n - k;
	}
	n_factorial = 1.0;
	for (int i = 2; i <= k; i++) {
		n_factorial *= i;
	}
	k_factorial = n_factorial;
	for (int i = (k+1); i <= (n-k); i++) {
		n_factorial *= i;
	}
	n_k_factorial = n_factorial;
	for (int i = (n-k+1); i <= n; i++) {
		n_factorial *= i;
	}
	return (n_factorial / (n_k_factorial * k_factorial));
}
```
This representation is not the best that can be done for Binomial, as it is forgetting it relevance to topology. Pascal's triangle is a way of representing stacking in $n$-Dimensions.

- For $a=1$, this is a list of the maximum number of points in a line segment of size $b$ that are of distance $1$ from every other point.

|$b$|$\left(1,b\right)$|Graphical|
|:---:|:---:|:---:|
|0|1|$*$|
|1|2|$*-*$|
|2|3|$*-*-*$|
|3|4|$*-*-*-*$|

- For $a=2$, this is a list of the maximum number of points in a regular triangle of side length $b$ that are of distance $1$ from every other point.
 
|$b$|$\left(2,b\right)$|Graphical|
|:---:|:---:|:---:|
|0|1|$*$|
|1|3|$*\\/\;\,\backslash\\*-*$|
|2|6|$*\\/\;\,\backslash\\*-*\\/\;\,\backslash\;\,/\;\,\backslash\\*-*-*$|
|3|10|$*\\/\;\,\backslash\\*-*\\/\;\,\backslash\;\,/\;\,\backslash\\*-*-*\\/\;\,\backslash\;\,/\;\,\backslash\;\,/\;\,\backslash\\*-*-*-*$|

- For $a=3$, this is a list of the maximum number of points in a tetrahedron of side length $b$ that are of distance $1$ from every other point.

|$b$|$\left(3,b\right)$|Graphical|
|:---:|:---:|:---:|
|0|1|$*$|
|1|4|$*\\/*\backslash\\*-*$|
|2|10|$*\\/*\backslash\\*\,/*\backslash*\\/\,*\,-\,*\,\backslash\\*\;-\;*\;-\;*$|

This can be generalized to a list of the maximum number of points points in an $a$-simplex of side length $b$ that are of distance $1$ from every other point. 

Given that each $a$-dimension will be a stack of the $0$ to $b$ stacks in the $(a-1)$-Dimension, as the added dimension will have an added length $b$, which can fit the extra points.

From this, the formula below can be formed:
$$
(a,b) = \begin{cases}
        \sum^{b}_{\beta=0}{(a-1,\beta)}  & \text{if } a > 0\\
        1 & \text{if } a = 0
    \end{cases}
$$
This formula is faster than the previous method ($O(a\times b)$). 

However, there is a special case of this formula if you are dealing with a whole row of Pascal's Triangle, which can allow for a batch to be done at once:
$$
(a,b) = \begin{cases}
        (a-1,b) + (a,b-1)  & \text{if } a > 0 \text{ and } b > 0\\
        1 & \text{if } a = 0 \text{ or } b = 0
    \end{cases}
$$
This formula has a time complexity of $O(a\times b)$ and a space complexity of $O(b)$ or $O(a)$, as there is a symmetry that $(a,b) = (b,a)$.

This formula has an added benefit that it can save time on calculating multiple values at once. Below is an implementation of this (this program breaks when values that are above the unsigned 64-bit integer limit are generated).

```c++
#include <cstdint>
#include <vector>
#include <map>

using std::pair, std::vector, std::map;
void order_pairs(vector<pair<uint64_t, uint64_t>> &poi, bool compact = false) { // this decreases memory requirements (not really needed)
	if (poi.size() == 0) {
		return;
	}
	uint64_t temp_val = 0;
	vector<pair<uint64_t, uint64_t>> temp;
	bool is_placed = false;
	
	for (int i = 0; i < poi.size(); i++) {
		is_placed = false;
		if (poi[i].first > poi[i].second && compact) {
			temp_val = poi[i].first;
			poi[i].first = poi[i].second;
			poi[i].second = temp_val;
		}
		for (auto j_it = temp.begin(); j_it != temp.end() && !is_placed; j_it++) {
			if (j_it->first == poi[i].first && j_it->second == poi[i].second) { // ignore duplicates
				is_placed = true;
			}
			if (j_it->first == poi[i].first && j_it->second > poi[i].second) {
				is_placed = true;
				temp.insert(j_it, poi[i]);
			}
			if (j_it->first > poi[i].first) {
				is_placed = true;
				temp.insert(j_it, poi[i]);
			}
		}
		if (!is_placed) {
			temp.push_back(poi[i]);
		}
	}
	poi = temp;
}

void build_map(vector<pair<uint64_t, uint64_t>> &poi, vector<uint64_t> &output, map<pair<uint64_t,uint64_t>,uint64_t> &output_map) {
	for (int i = 0; i < poi.size() && i < output.size(); i++) {
		output_map[poi[i]] = output[i];
	}
}

void faster_binomial(vector<pair<uint64_t, uint64_t>> &poi, vector<uint64_t> &output, vector<uint64_t> &row, uint64_t a, uint64_t b, uint64_t &at) {
	if(b == 0) {
		row.resize(0, 1);
		row.resize(a + 1, 1);
		if (poi[at].first == 0 || poi[at].second == 0) {
			output.push_back(1);
			at += 1;
			if (at == poi.size()) {
				at = 0;
			}
			
		}
		return;
	}
	
	faster_binomial(poi, output, row, a, b-1, at);
	
	if (poi[at].first == 0 || poi[at].second == 0) {
		output.push_back(1);
		at += 1;
		if (at == poi.size()) {
			at = 0;
		}
	}
	
	for (uint64_t i = 1; i < row.size(); i++) {
		row[i] = row[i] + row[i - 1];
		if (poi[at].first == b && poi[at].second == i) {
			output.push_back(row[i]);
			at += 1;
			if (at == poi.size()) {
				at = 0;
			}
		}
		if (poi[at].first == 0 || poi[at].second == 0) {
			output.push_back(1);
			at += 1;
			if (at == poi.size()) {
				at = 0;
			}
		}
	}
}

void faster_binomial(vector<pair<uint64_t, uint64_t>> &poi, vector<uint64_t> &output, bool compact = false) {
	if (poi.size() == 0) {
		return;
	}
	order_pairs(poi, compact);
	output.clear();
	
	vector<uint64_t> row;
	uint64_t b = poi[poi.size()-1].first;
	uint64_t a = poi[0].second;
	for (uint64_t i = 1; i < poi.size(); i++) {
		if (a < poi[i].second) {
			a = poi[i].second;
		}
	}
	uint64_t at = 0;
	
	faster_binomial(poi, output, row, a, b, at);
}
```





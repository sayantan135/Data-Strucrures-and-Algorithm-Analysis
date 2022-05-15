# Design Analysis of Algorithm
Design & Analysis of Algorithm Lab

## Assignment List

## Week1:
1. Find second largest and second smallest number simultaneously in an array using Divide &
Conquer Principle.
2. Given a sorted array and a number X, search two elements of array such that their sum is X.
Expected time complexity is O(n).
3. Apply Binary Search on 2D NxM array (A) having numbers stored in non-deceasing order
under row-major scanning.
Hint:
k-th element = A[k/M][k % M] for A[1...N][1...M]
4. Given a sorted array and a number x, write a function that counts the occurrences of x in the
array. Expected time complexity is O(logn).
Hint:
1) Use Binary search to get index of the first occurrence of x in arr[]. Let the index of the
first occurrence be i. if( ( mid == 0 || x > arr[mid-1]) && arr[mid] == x) return mid; else if(x
> arr[mid]) return first(arr, (mid + 1), high, x, n); else return first(arr, low, (mid -1), x, n);
2) Use Binary search to get index of the last occurrence of x in arr[]. Let the index of the last
occurrence be j. if( ( mid == n-1 || x < arr[mid+1]) && arr[mid] == x ) return mid; else if(x
< arr[mid]) return last(arr, low, (mid -1), x, n); else return last(arr, (mid + 1), high, x, n);
3) Return (j – i + 1);
Week2:
1. Median of two sorted arrays: There are 2 sorted arrays A and B; each of size n. Write an
algorithm to find the median of the array obtained after merging the above 2 arrays (i.e.
array of length 2n). The complexity should be O(log(n))
Hint:
1) Calculate the medians m1 and m2 of the input arrays ar1[]and ar2[] respectively.
2) If m1 and m2 both are equal then we are done and return m1 (or m2)
3) If m1 is greater than m2, then median is present in one of the below two subarrays.
a) From first element of ar1 to m1 (ar1[0...|_n/2_|])
b) From m2 to last element of ar2 (ar2[|_n/2_|...n-1])

4) If m2 is greater than m1, then median is present in one of the below two subarrays.
a) From m1 to last element of ar1 (ar1[|_n/2_|...n-1])
b) From first element of ar2 to m2 (ar2[0...|_n/2_|])
5) Repeat the above process until size of both the subarrays becomes 2.
6) If size of the two arrays is 2 then use below formula to get the median. Median =
(max(ar1[0], ar2[0]) + min(ar1[1], ar2[1]))/2
2. A Bitonic Sequence is a sequence of numbers which is first strictly increasing then after a
point strictly decreasing. A Bitonic Point is a point in bitonic sequence before which
elements are strictly increasing and after which elements are strictly decreasing. Find bitonic
point in a bitonic sequence.
Hint:
An efficient solution for this problem is to use modified binary search. If arr[mid-1] <
arr[mid] > arr[mid+1] then we are done with bitonic point. If arr[mid] < arr[mid+1] then
search in right sub-array, else search in left sub-array.
3. Given an array of digits, sort them with time complexity O(n).
4. Apply Merge Sort to count inversion pairs in an array. Two elements a[i] and a[j] form an
inversion pair if a[i] > a[j] and i < j. Example: The sequence 2, 4, 1, 3, 5 has three inversions
(2, 1), (4, 1), (4, 3).
Hint:
int inv_count = 0; i = left; /* i is index for left subarray*/
j = mid; /* j is index for right subarray*/
k = left; /* k is index for resultant merged subarray*/
while ((i <= mid - 1) && (j <= right))
{
if (arr[i] <= arr[j])
{
temp[k++] = arr[i++];
}
else
{
temp[k++] = arr[j++];
inv_count = inv_count + (mid - i);
}
}

Week3:

1. Find neighbors of the median element in an array using partitioning strategy of Quick-
Sorting method.

Hint:
General principle of finding k-th element
j = position of pivot element after partitioning
if (k < j) return doPartition( A[1...j-1])
if (k = j) return j
if (k > j) return doPartition( A[j+1...n])

2. Apply Strassen’s Matrix Multiplication strategy for odd dimensional square matrix.
Hint: Do padding of zeros to make odd dimensional square matrix 2^kx2^k.
3. Arrange a list of words (each of equal length) using dictionary sorting strategy.
Hint: Radix Sort
Week4:
1. Given a value V and infinite supply of coins of m-denominations {C1=1 <
C2<C3<.....<Cm}, we want to make change for Rs. V. Apply DP strategy to find out
minimum number of coins to make the change?
Hint:
Input: coins[] = {25, 10, 5}, V = 30
Output: Minimum 2 coins required
We can use one coin of 25 cents and one of 5 cents
Input: coins[] = {9, 6, 5, 1}, V = 11
Output: Minimum 2 coins required
We can use one coin of 6 cents and 1 coin of 5 cents
If V == 0, then 0 coins required.
If V > 0
minCoin(coins[0..m-1], V) = min {1 + minCoins(V-coin[i])}
where i varies from 0 to m-1
and coin[i] <= V

2. Given a cost 2D-matrix and a position (m, n), write a function that returns cost of minimum
cost-path to reach (m, n) from (0, 0).
Hint:
Each cell of the matrix represents a cost to traverse through that cell. Total cost of a path to
reach (m, n) is sum of all the costs on that path (including both source and destination). You
can only traverse down, right and diagonally lower cells from a given cell, i.e., from a given
cell (i, j), cells (i+1, j), (i, j+1) and (i+1, j+1) can be traversed. You may assume that all costs
are positive integers.

The path to reach (m, n) must be through one of the 3 cells: (m-1, n-1) or (m-1, n) or (m, n-
1). So minimum cost to reach (m, n) can be written as “minimum of the 3 cells plus

cost[m][n]”.
minCost(m, n) = min (minCost(m-1, n-1), minCost(m-1, n), minCost(m, n-1)) + cost[m][n]
3. Given a set of non-negative integers, and a value sum, determine if there is a subset of the
given set with sum equal to given sum.
Hint:
Examples: set[] = {3, 34, 4, 12, 5, 2}, sum = 9
Output: True // There is a subset (4, 5) with sum 9.
isSubsetSum(set, n, sum) = isSubsetSum(set, n-1, sum) ||
isSubsetSum(set, n-1, sum-set[n-1])

Base Cases:
isSubsetSum(set, n, sum) = false, if sum > 0 and n == 0
isSubsetSum(set, n, sum) = true, if sum == 0

Week5:
1. Given an array p[] which represents the chain of matrices such that the i-th matrix Ai is of
dimension p[i-1] x p[i]. We need to write a function that should return the optimal
parenthesizing expression resulting minimum multiplication cost to multiply the chain.
Hint:
Input: p[] = {40, 20, 30, 10, 30}
Output: 26000
There are 4 matrices of dimensions 40x20, 20x30, 30x10 and 10x30.
Let the input 4 matrices be A, B, C and D. The minimum number of multiplications are
obtained by putting parenthesis in following way (A(BC))D --> 20*30*10 + 40*20*10 +
40*10*30
2. Given weights and values of n items, put these items in a knapsack of capacity W to get the
maximum total value in the knapsack. You cannot break an item, either pick the item, or
don’t pick it.
Hint:
To consider all subsets of items, there can be two cases for every item: (1) the item is
included in the optimal subset, (2) not included in the optimal set. Therefore, the maximum
value that can be obtained from n items is max of following two values.
1) Maximum value obtained by n-1 items and W weight (excluding nth item).
2) Value of nth item plus maximum value obtained by n-1 items and W minus weight of the
nth item (including nth item). If weight of nth item is greater than W, then the nth item
cannot be included and case 1 is the only possibility.
Week6:
1. Implement all pairs of Shortest path algorithm for a graph using Floyd-Warshall’s strategy.
2. Implement DP strategy to solve Travelling Salesman Problem(TSP).
Week7:
1. Find the smallest number with given digit sum s and number of digits d?
Input : s = 9, d = 2
Output : 18
There are many other possible numbers like 45, 54, 90, etc with sum of digits as 9 and
number of digits as 2. The smallest of them is 18. There is a Greedy approach to solve the
problem. The idea is to one by one fill all digits from rightmost to leftmost (or from least
significant digit to most significant). We initially deduct 1 from sum s so that we have
smallest digit at the end. After deducting 1, we apply greedy approach. We compare
remaining sum with 9, if remaining sum is more than 9, we put 9 at the current position, else
we put the remaining sum. Since we fill digits from right to left, we put the highest digits on
the right side.
2. Implement a greedy algorithm to solve fractional knapsack problem.
3. Implement greedy algorithm to solve the problem of Job Sequencing with deadlines.
Week8:
1. Implement Dijkstra’s algorithm for finding shortest path.
2. Implement Bellman-Ford’s algorithm for finding shortest path.
3. Implement BFS and DFS for a given undirected graph and starting vertex.

Week9:
1. You are given a 3×3 board with 8 tiles (every tile has one number from 1 to 8 and one space
is empty). The objective is to place the numbers on tiles to match final configuration using
the empty space. We can slide four adjacent (left, right, above and below) tiles into the
empty space.
Initial Configuration Final Configuration
1 2 3
5 6
7 8 4

2. The N Queen is the problem of placing N chess queens on an N×N chessboard so that no
two queens attack each other. For example, following is a solution for 4 Queen-problem.

Q
Q

Q
Q

Hint:
1) Start in the leftmost column
2) If all queens are placed return true
3) Try all rows in the current column. Do following for every tried row.
a) If the queen can be placed safely in this row then mark this [row, column] as part
of the solution and recursively check if placing queen here leads to a solution.
b) If placing queen in [row, column] leads to a solution then return true.
c) If placing queen doesn't lead to a solution then unmark this [row, column]
(Backtrack) and go to step (a) to try other rows.
4) If all rows have been tried and nothing worked, return false to trigger backtracking.

Week10:
1. KMP String Matching: Given a text txt[0..n-1] and a pattern pat[0..m-1], write a function
search(char pat[], char txt[]) that prints all occurrences of pat[] in txt[]. You may assume that
n > m.
Text: A A B A A C A A D A A B A A B A
Pattern: A A B A
2. Write an approximation algorithm for TSP with triangle inequality. Your solution should be
at most twice worst with respect to the optimal solution.

Measures similarity between two sets of data.

Given sets $X$ and $Y$:

$$J(X, Y) = \frac{{|X \cap Y|}}{|X \cup Y|}$$

## Jaccard Distance
This is a measure of dissimilarity (100% - J(X, Y))

```ad-example
$A = {1, 2, 5, 7, 19, 58, 75, 98}$
$B = {1, 6, 12, 17, 75, 86, 91}$

$|A \cap B| = |\{1, 75\}| = 2$
$|A \cup B| = |\{1, 2, 5, 6, 7, 12, 17, 19, 58, 75, 86, 91, 98\}| = 13$

$J(A, B) = \frac{|A \cap B|}{|A \cup B|} = \frac{2}{13} \approx 0.15384$
```

The sets are approximately 15.38% similar.
Jaccard Distance is 0.84618 (84.6%).

## Alternate Visualization
Where possible set values are enumerable, we can visualize this as a binary matrix with all possible inputs, with each data set being listed as containing or not containing the input:

| Input | Doc 1 | Doc 2 | Doc 3 |
| ----- | ----- | ----- | ----- |
| aaaa  | 1     | 1     | 1     |
| aaab  | 0     | 1     | 0     |
| aaac  | 0     | 0     | 0     |
| ...   | 1     | 1     | 0     |
| ...   | 1     | 1     | 0     |
| ...   | 1     | 0     | 0     |
| zzzy  | 0     | 1     | 0     |
| zzzz  | 1     | 1     | 1      |

When comparing two documents, the combinations of matches in the matrix fall into 4 possible classes:

| Type | X contains | Y contains |
| ---- | ---------- | ---------- |
| A    | 1          | 1          |
| B    | 1          | 0          |
| C    | 0          | 1          |
| D    | 0          | 0          |

We can express the Jaccard index by frequency of these types. 
Type A is part of $X \cap Y$ and types A, B, and C are all part of $X \cup Y$.
Type D would not be considered at all.

$\frac{f_A}{f_A + f_B + f_C}$

J(doc1, doc2 = 4/7
J(doc1, doc3) = 2/6
J(doc2, doc3) = 2/6
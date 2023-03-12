

Converts large sets into short signatures while preserving similarity.

```ad-note
$Pr[h(C_1)=h(C_2)] = sim(D_1, D_2)$ 

The probability that two documents sort into the same hash bucket is equal to the degree of similarity between the two documents.
```

## Origin
"Min-wise independent permutations locality sensitive hashing scheme", invented by Andrei Broder and used in the AltaVista search engine to detect and eliminate duplicates.

[Min-Wise Independent Permutations](https://dl.acm.org/doi/pdf/10.1145/276698.276781)

## Many Hash Functions Variant

We have a set of $D$ documents ($D_1...D_n$).

Generate an input matrix:
- Generate sets of [[k-Shingles]] from each document
- Represent in a binary matrix
	- rows are possible shingles
	- columns are documents
	- cells represent the presence of a shingle in a document

Choose the number of "rounds" $r$ to perform for each signature (trade-off: speed for accuracy)

Randomly generate permutation matrices $\pi_1...\pi_r$
- Each contains the numbers 1...$n$ in random order

Combine permutation and input matrices to match up rows.

Generate a signature matrix $M$:
- At the intersection of each document and permutation matrix, record the lowest number in the permutation matrix that corresponds to a "1" (present shingle) in the document.
- This is conceptually reordering the rows at random and selecting the first row where a "1" appears for each document.

> [!EXAMPLE]-
>
> Combined Input and Permuatation Matrices
> 
>| $\pi_1$ | $\pi_2$ | $\pi_3$ | $\pi_4$    | shingle | $D_1$  | $D_2$  | $D_3$  | $D_4$  |
|:------:|:------:|:------:| --- |:-------:|:---:|:---:|:---:|:---:|
| 2      | 4      | 3      |  7   |    a    |  1  | 0   |  1   |  0   |
| 3      | 2      | 4      |  6   |    b    |  1  | 0   |  0   |  1   |
| 7      | 1      | 7      |  5   |    c    |  0  | 1   |  0   |  1   |
| 6      | 3      | 2      |  4   |    d    |  0  | 1   |  0   |  1   |
| 1      | 6      | 6      |  3   |    e    |  0  | 1   |  0   |  1   |
| 5      | 7      | 1      |  2   |    f    |  1  | 0   |  1   |  0   |
| 4      | 5      | 5      |  1   |    g    |  1  | 0   |  1   |  0   |
>
> Signature Matrix
> 
> |         | $D_1$ | $D_2$ | $D_3$ | $D_4$ |
|:-------:|:-----:|:-----:|:-----:|:-----:|
| $\pi_1$ |   2   |   1   |   2   |   1   |
| $\pi_2$ |   2   |   1   |   4   |   1   |
| $\pi_3$ |   1   |   2   |   1   |   2   |
| $\pi_4$ |   1   |   3   |   1   |   3   | 
>
> Similarity (data vs. signatures) 
> 
|  | 1&3  | 2&4  | 1&2 | 3&4 |
| -------------------------------- | ---- | ---- | --- | --- |
| Raw Comparison                   | 0.86 | 0.86 | 0   | 0   |
| [[Jaccard Index 2]] of Data        | 0.75 | 0.75 | 0   | 0   |
| Signatures                       | 0.75 | 1.00 | 0   | 0   | 


----
## Sources
[[EWU CSCD340]]
Sources:: [MinHash - Wikipedia](https://en.wikipedia.org/wiki/MinHash)

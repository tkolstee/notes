 


When finding similar documents or datasets, Locality-Sensitive Hashing (LSH) is a way of screening candidate pairs prior to comparison for similarity, to minimize the time complexity of the overall operation.

Items are sorted into buckets using a hash function. Two items that are sorted into the same bucket are a "candidate pair" which is then subjected to a full comparison.

This is performed repeatedly with different hash functions, which will "catch" different candidate pairs. 

If well-designed, the set of candidate pairs should be much smaller than the total number of possible pairings. 

There may be false negatives - items which would be found to be similar if compared, but which are never found as a candidate pair and so never compared.

Similarity functions such as [[Jaccard Index]] can be expensive when applied to large datasets where we want to find similar documents for duplicate detection or clustering.

Locality sensitive hashing involves sorting  the items into buckets using several different collision prone hash functions. We then examine only pairs of items that share at least one bucket.

If designed correctly, only a fraction of the total pairings are even considered. 

There may be some false negatives - items that are similar but never considered.

## Use case involving k-shingles, Minhashing, and LSH

- We have a collection $D$ of documents $D_1...D_d$
- We have an expensive similarity function $S$
- We want to compare all documents to each other to find those that are similar - $\forall$ S(a, b) | $(a, b) \in D \times D$

Collect [[k-Shingles]] for each document
Generate signatures and similarity scores using [[Minhashing]]

## Use Case:
- We have a collection $X$, containing data sets $x$ ($x_1$, $x_2$, ..., $x_n$)
- We have an expensive function $S()$ which can compare two data sets for similarity
- We want to compare each pair of $x$ ($X \times X$) for similarity

## Naiive solutions
- Use function $S$ on every pair of $a, b: (a, b) \in X \times X$
- Make [[k-Shingles]] from each $x$ and compare using [[Jaccard Index]]

These are $O(n^2)$ solutions.

## Using Locality-Sensitive Hashing




## Overall Process
Documents are first used to produce a set of [[k-Shingles]].

The shingles are then subjected to a [[Minhashing]] function to produce signatures.

Locality sensitive hashing 


## Using k-shingling and minhashing
Produce a set of [[k-Shingles]] from each input

[[Jaccard Index]]

### Minhashing Function
Calculating pairwise matches for all possible shingles is expensive as the inputs grow in number or size, or the size of each shingle increases (and therefore the number of possible shingles).

Instead, let's permute the row order 



----
## Sources
Notes from EWU CSCD340

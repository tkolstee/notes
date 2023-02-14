

## Discussion

A form of robust hashing, this technique can be used to find strings of identical text in documents which are not entirely identical.

The documents need not be retained, only a small representative hash value of variable length and the initialization vectors must be retained in order to hash new documents for comparison.

This would enable the space and time-efficient comparison of a large number of documents with each other.

The algorithm works well on text in particular, and may perform better or worse on certain types of data. Here we will focus on characters, but feel free to use "byte" or other quantitative value chunk instead if the input data type is appropriate.

We produce a collection of hashes for a document, storing only a sample of all hashes produced. Such a set is produced for each input document. The degree to which the sets contain similar hashes is heavily correlated to the degree to which the source documents are similar.

## Initialization and Tuning

Choose values for:

- Sliding window size $\large s$
- An arbitrary prime number $\large p$
- Number of "buckets" to use for matches $\large m$
- A set of one or more criteria to sample which hashes are saved, e.g. "last 5 binary digits are all zeroes" (denoted here as $\large C(h)$).

For each document $\large d$:
> 1. Create a set of hash values, initially empty  $\large H = \{\}$
> 2. Set step number $\large n$ to zero.
> 3. Consider "window" $\large w_0...w_{s-1}$ to span from $\large d_n...d_{s+n}$.
> 4. Find fingerprint $\large f$:  $$\Large f = w_0p^{s-1} + w_1p^{s-2} + ... + w_{s-1}p^0$$
> 5. Find hash $\large h_n = f \mod m$.
> 6. $\large h_n \in H$ iff $\large C(h_n)$ (add the hash to the set if it meets the criteria). 
> 7. If $\large length(d) > s+n+1$, increment $\Large n$ and repeat steps 3-7.

```ad-info
title: Meaning of and shortcuts for calculating values of $\large f$.

$\large f_n$ is a $\Large s$-degree polynomial based upon powers of $\large p$ and coefficients correlating to values within $\large w$. 

----

To calculate a the value for $\large f_{n+1}$, use the prior value of $\large f$:
- Multiply by $\large p$ (moving each coefficient "up" one degree)
- Subtract $\large w_0p^s$ (removing the high-order term)
- Add $\large d_{s+n+1}$ (adding the low-order term)
```


## Comparison

The above steps produce a collection of hash values for each document. 

If we stored each hash value, the collection would be larger than the document itself. By selecting truly arbitrary criteria, we are saving only a selection of hash values as a sample of the total. Only in truly degenerate cases (extremely short documents, large values of m, and/or criteria that select for too many hashes) will we produce a collection that is larger than the document itself.

With the same initial values and algorithm, we can compare hash sets from two different documents. The degree to which the documents share identical character sequences of size $\large s$ is correlated to the degree in which they share generated hash values (and by extension selected samples of those hash values captured by $\large C$).

## Tuning

Choosing values for $\large s$, $\large m$, and $\large C$ can "tune" the algorithm to manipulate sensitivity, degrees of false positives and negatives, and storage size required. Finding optimal values appears to be more an art than a science, and each has tradeoffs to consider.

## Further Discussion

At its essence this algorithm functions similar to a Bloom Filter but with only one hash function and matching on a spectrum from strong to weak instead of a binary result. Each window position is hashed, and only a sample of hashes are saved. Exact matches will produce the exact same set of hashes, but unlike cryptographic hashing functions similar results will produce similar fingerprints.

The calculation of $\large f$ and the associated hash value $\large h$ serve as a sort of pseudorandom number generator (which is why $\large p$ is prime). Robust hash algorithms with more entropy and collision resistance exist which could replace this process. In essence we would still be generating hashes for each possible position of the window, and saving only those that meet a certain criteria as a sample. These improved algorithms would provide a more random sample for almost any conceivable selection criteria.

----
# Sources
Manber, Udi. “Finding Similar Files in a Large File System.” _USENIX Winter_ (1994).

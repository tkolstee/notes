
Measures importance and relevance of terms in a document as part of a larger corpus.

## Term Frequency (TF)

Represents the commonality of term $i$ in document $j$:

$$TF_{ij} = \frac{f_{ij}}{max_{k}f_{kj}}$$
$f_{ij}$ is the frequency of term $i$ in document $j$
$max_{k}f_{kj}$ is the max frequency of any word in document $j$.

The most frequent word in a document has TF=1

## Inverse Document Frequency (IDF)

Zero where word is in every document in the collection, higher for rarer words.

$$IDF_i = log_2 \left( \frac{docs_*}{docs_i} \right)$$
$docs_*$ represents the total number of documents.
$docs_i$ is the number of documents in which term $i$ appears.

## TF-IDF
$$TF_{ij} \times IDF_i$$

The larger the value, the more relevant the search term $i$ is to the document $j$. 

`````ad-info
title: Highest possible TF-IDF

Highest possible TF-IDF is $log_2(n)$

- $i$ is the most common word in one document $j$ $$TF_{ij} = 1$$
- $i$ only appears in document $j$ in the collection of $n$ docs $$IDF = log_2\left(\frac{n}{1}\right)$$ 

`````


```ad-example
We have a corpus of $2^{20}$ (just over 1M) documents.
256 ($2^8$) of them contain the word "octopus".

$$IDF_{octopus} = log_2\left(\frac{2^{20}}{2^8}\right) = log_2(2^{12}) = 12$$

Suppose a particular document contains the word 20 times, and the most frequent word in that document appears 150 times.

$$TF_{ij} = \frac{f_{ij}}{max_{k}f_{kj}} = \frac{20}{150} = \frac{2}{15}$$

$$TF_{ij}IDF_i = 12 \times \frac{2}{15} = \frac{24}{15} = 1.6$$
```

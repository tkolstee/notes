## Euclidian Distance
Given vectors $\vec{a}$ and $\vec{b}$, the difference of each component 

$$d(\vec{a}, \vec{b}) = \sqrt{\sum_{i=1}^{n}(a_i - b_i)^2}$$

## Manhattan Distance
Also known as city block distance.
Typically preferred over euclidian with data of high dimensionality.
Can be visualized as the path via orthogonal lines.

$$d(a, b) = \sum_{i=1}^{n}\vert a_i - b_i \vert$$

## Minkowski Distance
A generalization of Euclidian distance with a tunable exponent.
Where p=2 this is equivalent to Euclidian distance.
Where p=1 this is equivalent to Manhattan distance.
==I don't understand this one yet, but there are a couple of sources [1](https://medium.com/@kunal_gohrani/different-types-of-distance-metrics-used-in-machine-learning-e9928c5e26c7)  [2](https://iq.opengenus.org/minkowski-distance/) that purport to explain it.==

$$\Big( \sum_{i=1}^{n} \vert x_i - y_i \vert^p \Big)^\frac{1}{p}$$

## Hamming Distance
Comparing two binary data strings, gives the number of bit positions that are different.
Take the XOR of the two values ($a \oplus b$) and count the number of 1 bits.


## Cosine Distance

Cosine similarity is the cosine of the angle between two points. At 90 degrees, cosine similarity is 0.

Cosine distance or difference is 1 - the cosine similarity. At 90 degrees the cosine distance is 
The cosine of the angle between two points $cos(\theta)$  represents the **cosine similarity**.
$1 - cos(\theta)$ is the cosine difference
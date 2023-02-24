## Euclidian Distance
Given vectors $\vec{a}$ and $\vec{b}$, the difference of each component 

$$d(\vec{a}, \vec{b}) = \sqrt{\sum_{i=1}^{n}(a_i - b_i)^2}$$

## Manhattan Distance
Also known as city block distance.
Typically preferred over euclidian with data of high dimensionality.
Can be visualized as the path via orthogonal lines.

$$d(a, b) = \sum_{i=1}^{n}\vert a_i - b_i \vert$$

## Minkowski Distance

$$\Big( \sum_{i=1}^{n} \vert x_i - y_i \vert^p \Big)^\frac{1}{p}$$

## Hamming Distance
Comparing two binary data strings. Number of bit positions that are different
Take the XOR of the two values ($a \oplus b$) and count the number of 1 bits.

## Cosine Distance
The cosine of the angle between two points $cos(\theta)$  represents the **cosine similarity**.
$1 - cos(\theta)$ is the cosine difference
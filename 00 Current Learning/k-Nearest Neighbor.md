Classification and regression algorithm

Given a set of pre-classified points on a graph:

1. Calculate the distance of the sample point to all other points
2. Sort the distances to each point and the labels of those points.
3. Find the $k$ nearest points.

For classification, return the most common label among the $k$ points.
For regression, return the average of the distance values.

Variations and parameters include the [[Distance Formulas]] used and the value of $k$. 

| Value of $k$ | Bias | Variance |
| ------------ | ---- | -------- |
| small        | low  | high     |
| large        | high | low         |

A number's square root is the number that, when squared, equals the original number.
$(\sqrt{x})^2 = x$

## Finding Square Roots

### Repeated Subtraction Method
Works only for perfect squares.
Subtract consecutive odd numbers from the operand until we reach zero.
The number of times we subtract is the square root of the operand.
```ad-example
title: Example: $\sqrt{16}$
collapse: true
- $16 - 1 = 15$
- $15 - 3 = 12$
- $12 - 5 = 7$
- $7 - 7 = 0$

4 subtractions, $\therefore \sqrt{16} = 4$
```

### Prime Factorization
Represent the operand as a product of prime numbers by factoring.
Form pairs of factors such that both numbers in the pair are equal.
Take one factor from each pair and find the product of all such factors.
```ad-example
title: Example: $\sqrt{144}$
collapse: true
- $144 = 2 \times 2 \times 2 \times 2 \times 3 \times 3 = (2 \times 2) \times (2 \times 2) \times (3 \times 3)$
- $2 \times 2 \times 3 = 12$
- $\therefore \sqrt{144} = 12$
```

### Estimation and Approximation
- Find nearest perfect squares to operand.
- Square root will lie between these two numbers.
- Find squares of intermediate numbers between these numbers.
```ad-example
collapse: true
title: Example: $\sqrt{15}$

- $3^2 = 9, 4^2 = 16 \therefore 3 \lt \sqrt{15} \lt 4.$
- $3.5^2 = 12.25 \therefore 3.5 \lt \sqrt{15} \lt 4$
- $3.8^2 = 14.44 \therefore 3.8 \lt \sqrt{15} \lt 4$
- $3.9^2 = 15.21 \therefore 3.8 \lt \sqrt{15} \lt 3.9$
- $3.85^2 = 14.8225 \therefore 3.85 \lt \sqrt{15} \lt 3.9$
- $3.875^2 = 15.015625 \therefore 3.85 \lt \sqrt{15} \lt 3.875$
```


### Heron of Alexandria's Formula
Formula for approximating a square root:

To find square root ($y$) of $x$:

- Find a reaonable guess - e.g. the nearest perfect square - this is $\Large y_0$.
- Iteratively find $\Large y_{n+1} = \frac{y_n + \frac{x}{y_n}}{2}$

This converges on a good approximation in very few iterations.
```ad-example
collapse: true
title: Example: $\sqrt{42}$
Let's start with 6.

- $\Large y_0 = 6$
- $\Large y_1 = \frac{6 + \frac{42}{6}}{2} = 6.5$
- $\Large y_2 = \frac{6.5+\frac{42}{6.5}}{2} = 6.480769230769231$


Actual answer is 6.48074069840786, so after 2 iterations we are accurate to 4 decimal places (6.4807). One additional round puts us to at least 14 places of accuracy.
```




----
# Sources
[Square Root - Formula, Examples | How to Find Square Root?](https://www.cuemath.com/algebra/squares-and-square-roots/)
[Extras: Heron’s Method for Computing Square Roots | by Joshua Fitzgerald | Medium](https://medium.com/@joshuafitzgerald/extras-herons-method-for-computing-square-roots-235ccf4f2a33)




## Statement and Predicate

A **statement** is any declarative sentence which is either true or false. 

Whether the statement *is* true or false, or even if its truth value is unknown, is not relevant to whether or not it is a statement.

A **predicate** is a mathematical sentence that contains a **free variable** and so cannot be considered a statement. This cannot be considered a statement until the variable is resolved or quantified. Example: $x \geq 2$

### Atomic vs. Molecular Statements
A statement is **atomic** if it cannot be divided into smaller statements, otherwise it is called **molecular**.

Molecular statements can be made by combining other (atomic or molecular) statements using **[[#Connectives|Logical Connectives]]**


### Examples
Atomic statements
-   Telephone numbers in the USA have 10 digits.
-   The moon is made of cheese.
-   42 is a perfect square.
-   Every even number greater than 2 can be expressed as the sum of two primes.
-   $3+7=12$

Predicates
- $(1 + 3 + 5 + 7 + ... + (2n+1)) > 10$
- $P(n) > 10$
- $x \geq 7$

Not statements:
- Would you like some cake?  (interrogative - cannot be true or false)
- The sum of two squares. (partial statement - does not make a claim)
- Go to your room! (exclamatory - cannot be considered true or false)

## Connectives
Binary connectives connect two statements or predicates. Unary connectives modify a single statement or predicate. Their use forms a new molecular statement or predicate.

### Conjunction (AND)
Binary.
$P \land Q$
True iff both P and Q are true.
Similar to intersection $\cap$ in set theory.

|  P  |  Q  | $P \land Q$ |
|:---:|:---:|:-----------:|
|  F  |  F  |      F      |
|  F  |  T  |      F      |
|  T  |  F  |      F      |
|  T  |  T  |      T      |

### Disjunction (OR)
Binary.
$P \lor Q$
True if either P or Q (or both) are true.
Similar to union $\cup$ in set theory.

|  P  |  Q  | $P \lor Q$ |
|:---:|:---:|:----------:|
|  F  |  F  |     F      |
|  F  |  T  |     T      |
|  T  |  F  |     T      |
|  T  |  T  |     T      |

### Implication (if...then, conditional)
Binary.
$P \rightarrow Q$
True when P is false or Q is true or both.
P is the **hypothesis** or **antecedent**
Q is the **conclusion** or **consequent**

"If Bob gets a 90 or above on the final (P), he will pass the class (Q)".

#### Proving Implications
Assume P is true, and prove why Q must be true as well

#### Converse of Implications
Converse of $P \rightarrow Q$ is $Q \rightarrow P$
Not logically equivalent.
Truth of the converse is independent of the truth of the original implication.
"If a shape is a square, it is a rectangle" (true) becomes "If a shape is a rectangle, it is a square" (false).

#### Contrapositive of Implications
Contrapositive of $P \rightarrow Q$ is $\lnot Q \rightarrow \lnot P$.
Logically equivalent. They are either both true or both false.
"If a shape is a square, it is a rectangle" (true) becomes "if a shape is not a rectangle, it is not a square" (true).

### Biconditional (iff, if and only if)
Binary
$P \leftrightarrow Q$
True when P and Q are both true or both false.

if $(P \rightarrow Q) \land (Q \rightarrow P)$, then $P \leftrightarrow Q$.

### Negation (NOT)
Unary
$\lnot P$
True iff P is false, false iff P is true.

#### Negation of a Statement
Yields another statement that is true iff the original is false and vice versa.

Negation of "Everyone passed the test" is "at least one person did not pass the test", not "everyone failed the test" or "noone passed the test".

#### Negation of a predicate:
Results in a new predicate that is true iff the original predicate is false.

Ex: $\lnot ( x \geq 6 ) \equiv x \lt 6$


## Quantifiers

Two quantifiers are commonly used:

### Existential Quantifier
$\exists$ means "there exists" or "there is".

$$\exists x ( x < 0 )$$
means "there is a value of x such that x is less than 0".
This statement would of course be true.

### Universal Quantifier
$\forall$ means "for all" or "every".
$$\forall x ( x \ge 0 )$$
means "Every number is greater than or equal to zero".
This statement would of course be false.

### Combining Quantifiers
$$\forall x \exists y (y \ge x)$$
"For all values of x there is a y that is greater than or equal to x."

### Quantifiers and Negation
$\lnot \forall x P(x) \equiv \exists x \lnot P(x)$
$\lnot \exists P(x) \equiv \forall x \lnot P(x)$

"If not everything has a property, something doesn't have that property".

## DeMorgan's Law
NOT (p OR q) is equivalent to (NOT p) AND (NOT q)
NOT (p AND q) is equivalent to (NOT p) OR (NOT q)

$\neg (p \lor q) \equiv \neg p \land \neg q$
$\neg(p \land q) \equiv \neg p \lor \neg q$

| $p$ | $q$ | $p \land q$ | $\lnot ( p \land q )$ | $\lnot p \lor \lnot q$ |
| --- | --- | ----------- | --------------------- | ---------------------- |
| F   | F   | F           | T                     | T                      |
| F   | T   | F           | T                     | T                      |
| T   | F   | F           | T                     | T                      |
| T   | T   | T           | F                     | F                      |

| $p$ | $q$ | $p \lor q$ | $\lnot ( p \lor q )$ | $\lnot p \land \lnot q$ |
| --- | --- | ---------- | -------------------- | ----------------------- |
| F   | F   | F          | T                    | T                        |
| F   | T   | T          | F                    | F                        |
| T   | F   | T          | F                    | F                        |
| T   | T   | T          | F                    | F                        |




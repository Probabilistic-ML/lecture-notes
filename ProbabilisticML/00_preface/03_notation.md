<!-- #region -->
# Notation

In the following, we state the most important notations used in the present lecture notes. This collection is certainly not complete. Please draw our attention to expression which should be included into this section. 

A set is a collection of elements. In order to combine sets to a new set, we introduce some usual notations and operations.

Let $A$ and $B$ be two sets which are subsets of a universal set $U$ (i.e., $U$ contains **all** elements of interest). Denote the empty set (i.e., the set with no elements) by $\emptyset$.

- subset: 

$$A \subset B ~ \Leftrightarrow ~\text{each element of $A$ is an element of $B$}$$

- union: 

$$A \cup B := \{x~|~x \in A \text{ or } x \in B \}$$

- intersection:  

$$A \cap B := \{x~|~x \in A \text{ and } x \in B \}$$

- disjoint union:

$$A ~\dot\cup~ B = A \cup B \quad \text{with $A \cap B = \emptyset$ (i.e., $A$ and $B$ have no common elements).}$$


- difference:

$$A \backslash B := \{x~|~x \in A \text{ and } x \notin B \}$$

- complement: 

$$A^c := U \backslash A$$

- partition: a partition of $U$ is a collection of subset $A_1, A_2, \dots$ such that $A_i \cap A_j = \emptyset$ for each $i, j \in \mathbb{N}$ (disjointness) and $U = \cup_{i=1}^{\infty} A_i$. In accordance with the disjoint union of two sets, we write

$$U = ~\dot\cup_{i=1}^{\infty}~A_i$$

$\mathbb{1}_A$ denotes the indicator function which returns $1$ if an input is an element of $A$ and $0$ otherwise:

$$\mathbb{1}_A(x) = \begin{cases} 1 \text{ if } x \in A \\
                                  0 \text{ if } x \notin A
                    \end{cases}$$
<!-- #endregion -->

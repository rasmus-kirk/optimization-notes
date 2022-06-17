---
title: Notes
author: Rasmus Kirk
date: 2022-06-15
---
# P, NP and Cook's theorem
## NP completeness teori
- Model definition:
	- Operates on bits and bites
	- Input size is equal to number of bits in input
	- Time complexity of an algorithm is number of bit operations done.
- Decision problems, yes-no answers from input
- Inputs are bits
- Pair function:
	- $\langle x,y \rangle = x_1 0 \cdots x_n 0 \quad 11 \quad y_1 0 \cdots y_n 0$
- Church-Turing Thesis:
	- **Alanzo Church:** _No computational procedure will be considered as an algorithm unless it can be represented as a Turing Machine._
	- **Polynomial Church-Turing thesis:** A decision problem can be solved in polynomial time **iff** it can be solved in polynomial time by a turing machine.

## Language Complexity
![$P \neq NP$](p!=np.png){ width=50% }

- **P:** All decision problems that can be solved by a deterministic Turing machine in polynomial time.
- **NP:** All decision problems, where the solutions that evaluates to "yes," can be verified in polynomial time.
- **NPC:** A set of decision problems that can all be reduced into one another.
- **NPI:** All `NP` decision problems that are _not_ in `NPC` or `NP`.
- **NP-hard:** All decision problems that are _at least_ as hard as `NPC`.

- $L_1 \leq L_2 \Leftrightarrow (x \in L_1 \Leftrightarrow r(x) \in L_2)$

## SAT & CSAT
- For every boolean function $f(x)$, an equivilant curcuit $C(x)$ exists.
	- **Lemma:** For every boolean function $f : \{0,1\}^n \rightarrow \{0,1\}^m, \;  \exists C \; s.t. \; \forall x \in \{0,1\}^n , C(x) = f(x)$

- **Literals:** 
	- **Positive Literal:** An atom $x$
	- **Negative Literal:** A negation of an atom $\neg x$
- **Clause:** Collection of literals and logical connectives.
- **CNF:** Conjunctive Normal Form is a conjunction (`AND`'s) of clauses.
- **DNF:** Disjunctive Normal Form is a disjunction (`OR`'s) of clauses.
- **SAT:** Can the variables of a given CNF be replaced by either TRUE or FALSE such that the CNF evaluates to TRUE
- **Cook's Theorem:** SAT $\in$ NPC

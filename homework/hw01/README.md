# HW 1

**Due Friday, January 26, at 11am**

**Textbook Exercises:** 1.2.1, 1.3.1, 1.3.2, (1.3.3), (1.4.1),
(1.5.1), 1.6.1, 1.6.2.

In addition to the above listed exercises, please consider the conjecture 
below (which was inspired by questions asked by Jared Louchs and Connor Meredith).

Suppose we are given two signatures of the following form

$\sigma_0 = (\emptyset, \emptyset, \{{r\}}, \sigma_0') \quad \text{ and }
\quad  \sigma_1 = (\emptyset, \{{f\}}, \emptyset, \sigma_1')$,

such that $\sigma_0'(r) = \sigma_1'(f)+1$. To ease notation below, let's 
take $\sigma'_1(f) = n$.

($\sigma_0$ might be called a "purely relational" signature, since it has only 
relation symbols; similarly, $\sigma_1$ is "purely algebraic".)

Now, suppose we have structures $\mathbf{P} = (S, r^{\mathbf{P}})$ 
and $\mathbf{L} = (S, f^{\mathbf{L}})$ of types 
$\sigma_0$ and $\sigma_1$ respectively, defined on the same universe, $S$. 
 
Let's make up a new definition that might be useful in this situation.
Let us say that $\mathbf{P}$ is a **proxy** for $\mathbf{L}$
if each of $r^{\mathbf{P}}$ and $f^{\mathbf{L}}$ can be defined in terms the other
as follows: for all $x_0, x_1, \dots, x_{n-1}, y \in S$, 

$f^{\mathbf{L}}(x_0, x_1, \dots, x_{n-1}) = y \quad \Leftrightarrow 
\quad r^{\mathbf{P}}(x_0, x_1, \dots, x_{n-1}, y).$

**EXERCISE.**
Try to prove, or disprove by counterexample, the following 

**Conjecture:** 
If $\mathbf{P} = (S, r^{\mathbf{P}})$ is a **proxy** for $\mathbf{L} = (S, f^{\mathbf{L}})$,
and if $\mathbf{Q} = (T, r^{\mathbf{Q}})$ is a **proxy** for $\mathbf{M} = (T, f^{\mathbf{M}})$,
then a relational homomorphism $h: \mathbf{P} \to \mathbf{Q}$ is *strong* if and only if the 
map $h: S \to T$ is an algebraic homomorphism from $\mathbf{L}$ to $\mathbf{M}$.

**Further food for thought**  
Do you think the notion of "proxy" defined above captures the sense in which the poset we saw in class can be represeted as a semilattice?  If not, think about alternative definitions of "equivalent" structures of different signatures.  This is an open-ended question that may help you get better aquainted with structures and their signatures, but it is not a central theme of the course.  In other words, it's something to think about over dinner.

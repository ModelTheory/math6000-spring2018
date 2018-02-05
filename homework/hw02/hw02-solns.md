## Math 6000: Homework 2

**Due:** Friday, Feb 2, 11am  

----

**Exercises:** 2.2.1, 2.2.2, 2.2.3, 2.3.1, 2.3.2, 2.5.1, 2.6.1.

-------------------------------------------------

**2.2.1.** Show that any map $h_0$ from $X$ to an $L$-structure $\mathcal{M}$ can be uniquely extended to a homomorphism $h$ from $\operatorname{Term}_L(X)$ to $\mathcal M$.

-------------------------------------------------

**2.2.2.**  Let $h$ and $h_0$ be as above, let 
$\mathbf{x} = (x_0, x_1, \dots, x_{n-1})$, and let 
$t(\mathbf{x})$ be an $L$-term whose variables $\mathbf{x}$ are in $X$.  Prove that $t^{\mathcal{M}}(h_0[\mathbf{x}]) = h(t(\mathbf{x}))$.  (We use $h_0[\mathbf{x}]$ to denote the tuple $(h_0(x_0), h_0(x_1), \dots, h_0(x_{n-1}))$.)

**Solution.** 
This is a trivial consequence of the definition of $h$ we gave in the solution to the previous problem.  Specifically, for variables $x_i \in X$, 
\[h(x_i) = h_0(x_i),\] 
and for terms like $t(\mathbf{x})$,
\[h(t(\mathbf{x})) = t^{\mathcal{M}}(h(x_0), h(x_1), \dots, h(x_{n-1}).\]  
Taken together, these two equalities yield 
$h(t(\mathbf{x})) = t^{\mathcal{M}}(h_0(x_0), h_0(x_1), \dots, h_0(x_{n-1}))$, 
as desired.


-------------------------------------------------

**2.2.3.** (About unique legibility) Prove that no proper initial segment of a term (regarded as a string of symbols of the alphabet) can be a term.  Derive that for every term there is a unique way of building it up from its constituents according to the above recursion.


-------------------------------------------------

**2.3.1.** Verify that there are only finitely many unnested atomic sentences in $L$, provided the signature of $L$ is finite.

**Solution.** Recall, the set of **unnested terms** consists of the constants and the terms of the form $f(x_0, x_1, \dots, x_{n-1})$, where $x_i$ are variables and $f\in \mathbf{F}$. The set of **unnestead formulas** consists of term equations $t_0 = t_1$ such that $t_0$ and $t_1$ are unnested terms, along with unnested relations, that is, relations of the form $R(x_0, x_1, \dots, x_{n-1})$ where $x_i$ are variables and $R\in \mathbf{R}$.
If we assume the signature $\sigma = (\mathbf{C}, \mathbf {F}, \mathbf{R}, \sigma')$ is finite, then $|\mathbf{C}|$, $|\mathbf{F}|$ and $|\mathbf{R}|$ are all finite, and so are $\sigma'(f)$ and $\sigma'(R)$, for all $f \in \mathbf{F}$, $R \in \mathbf{R}$.

To get a precise handle on the cardinality of the set of unnested formulas, let's take a closer look at unnested terms.  If $t_0$ is a nonconstant unnested term, then there is some $f\in \mathbf{F}$ such that $t_0 = f(x_0, \dots, x_{n-1})$, assuming $\sigma'(f) = n$.  So, there are at most $|\mathbf{C}|^n$ distinct constant terms arrising out of nonconstant terms of arity $n$, which we can construct by substituting various constants for the variables in $f$.  Suppose
$t_1$ is another such term, say, $t_1 = g(x_0, x_1, \dots, x_{m-1})$, 
for some $g\in \mathbf{F}$. Then there are 
$|\mathbf{C}|^{m}\cdot |\mathbf{C}|^{n}$ distinct term equations ($t_0 = t_1$) arising from our given unnested constant terms.

As for the cardinality of the set of constant relations arising out of unnested relations


-------------------------------------------------

**2.3.2.** (About unique legibility) Prove that no proper initial segment of a formula (regarded as a string of symbols of the alphabet) can be a formula.  Derive that for every formula there is a unique way of building it up from its constituents according to the above recursion.

----

**2.5.1.** Find a recursive definition of "free variable" that recurses on the syntactic complexity of the formula under consideration.

---

**2.6.1.** What does the notation $\varphi(y, x)$ mean for a given
$\varphi(x,y) \in L_2$?

---

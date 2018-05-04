# Math 6000: Model Theory
## Final Homework (HW 9)

**DUE: Friday, 11 May 2018**

**Motivation.**
This problem set is about proof theory, which requires some preliminaries that we haven't covered in class.  However, these will be presented below.  Since we have spent a lot of time developing a certain (model-theoretic) point of view, we should have by now a fairly sophisticated context or framework, with respect to which we can understand and appreciate (or judge) other approaches to foundations and related areas.

The idea of this homework, then, is to give you a chance to compare some of the basic definitions of model theory (e.g., a theory, entailment, completeness) to their proof-theoretic analogues, and to contrast the points of view taken in these distinct (though not disjoint) branches of logic.

**Intructions.**
Answer Problems 1 through 8 below.  A few of the problems are somewhat open-ended, and you could write extensive essays on the topic, but that is not my intention.  Rather, I would like you to think carefully about each question and then write anywhere from two sentence up to two paragraphs in response.  Your answer should show that you have thought about the question, can appreciating its significance, and can express your thoughts about it intelligently and succinctly.  So, limit your answers to one or two paragraphs; be precise and concise; no b.s.

Typeset your solutions using LaTeX or Markdown.  You may submit solutions electronically as a pdf file via email, or leave a (typed or typeset) hard-copy in my mailbox anytime on or before the deadline. 

---

## A Very Brief Introduction to Proof Theory

### Languages
A **language** $\mathcal L$ (in proof theory) is a tuple $(\mathcal S, \mathcal F , \mathcal P)$
where $\mathcal S$ is a non-empty set of *term sorts* and $\mathcal F$ and $\mathcal P$ are sets whose elements are called *function symbols* and *predicate symbols*, respectively. Each function symbol has an associated arity, which is an $(n + 1)$-tuple of elements of $\mathcal S$, and each predicate symbol has an arity which is an $n$-tuple of elements of $\mathcal S$.

**PROBLEM 1.** Compare/contrast this notion of language and the languages we encountered in model theory.

---

### Terms

Let $\mathcal L$ be a language and $(\mathcal V_s)_{s\in\mathcal S}$ a family of
infinite, pairwise disjoint sets, indexed by term sorts, whose elements are called
*variables*. The set of **terms** of sort $s$ of the language $\mathcal L$, for a given family of sets of variables, is inductively defined as follows.
  - Variables of sort $s$ are terms of sort $s$.
  - If $f$ is a symbol of arity $(s_1, \dots, s_n, s')$ and $t_1, \dots, t_n$ are terms of sorts $s_1, \dots, s_n$, then $f(t_1, \dots, t_n)$ is a term of sort $s'$.

**PROBLEM 2.** Compare/contrast these terms and the terms we encounter in model theory.

---

### Propositions
Let $\mathcal L$ be a language. The set of **propositions** of the language $\mathcal L$, for a given family of sets of variables $(\mathcal V_s)_{s\in\mathcal S}$ is inductively defined as follows.
  - If $P$ is a predicate symbol of arity $(s_1, \dots, s_n)$ and $t_1, \dots, t_n$ are terms of sorts $s_1, \dots, s_n$, then the expression $P(t_1, \dots, t_n)$ is a proposition.
  - $\top$ and $\perp$ are propositions.
  - If $A$ is a proposition, then $\neg A$ is a proposition.
  - If $A$ and $B$ are propositions, then $A ∧ B$, $A ∨ B$ and $A \to B$ are propositions.
  - If $A$ is a proposition and $x$ is a variable of sort $s$, then $∀_s x\, A$ and $∃_s x \, A$ are propositions.
  The notation $A \leftrightarrow B$ will be used as an abbreviation for $(A \to B) ∧ (B \to A)$.

**PROBLEM 3.** Can you find a model theoretic anaolog of "proposition" as defined here?

---

<!-- + **Atomic.** A proposition of the form $P(t_1,\dots, t_n)$ is called *atomic*.
 -->
### Sequents and Natural Deduction
A **sequent** is a pair $\Gamma \vdash A$, where $\Gamma$ is a finite set of propositions and $A$ is a proposition.

The **rules of natural deduction** are the following *axioms*, *introduction rules*, and *elimination rules*:
\[ \frac{}{\Gamma \vdash A}\text{axiom } A \in \Gamma,\qquad \frac{}{\Gamma \vdash \top}\top \text{-intro}, \qquad \frac{\perp}{\Gamma \vdash A}\perp \text{-elim}\]
\[ \frac{\Gamma \vdash A, \qquad \Gamma \vdash B}{\Gamma \vdash A \wedge B}\wedge\text{-intro}, \qquad \frac{\Gamma \vdash A \wedge B}{\Gamma \vdash A}\wedge\text{-elim},\qquad \frac{\Gamma \vdash A \wedge B}{\Gamma \vdash B}\wedge\text{-elim},\]
\[ \frac{\Gamma \vdash A}{\Gamma \vdash A \vee B}\vee\text{-intro}, \quad
\frac{\Gamma \vdash B}{\Gamma \vdash A \vee B}\vee\text{-intro}, 
\quad \frac{\Gamma \vdash A \vee B \quad \Gamma, A \vdash C \quad \Gamma, B \vdash C }{\Gamma \vdash C}\vee\text{-elim},\]
\[ \frac{\Gamma, A \vdash B}{\Gamma \vdash A \to B}\to\text{-intro}, \qquad
\frac{\Gamma \vdash A \to B \qquad \Gamma \vdash A}{\Gamma \vdash B}\to\text{-elim},\]
\[ \frac{\Gamma, A \vdash \perp}{\Gamma \vdash \neg A}\neg\text{-intro}, \qquad
\frac{\Gamma \vdash A \qquad \Gamma \vdash \neg A}{\Gamma \vdash \perp}\neg\text{-elim},\]
\[ \frac{\Gamma \vdash A}{\Gamma \vdash \forall x \,A}\forall\text{-intro}\, (x\notin {\rm FV}(\Gamma)), \qquad
\frac{\Gamma \vdash \forall x \, A}{\Gamma \vdash [t/x]A}\forall\text{-elim},\]
\[ \frac{\Gamma \vdash [t/x]A}{\Gamma \vdash \exists x \,A}\exists\text{-intro}, \quad
\frac{\Gamma \vdash \exists x \, A \quad \Gamma, A \vdash B}{\Gamma \vdash B}\exists\text{-elim}\, (x\notin {\rm FV}(\Gamma, B)),\]
\[\frac{}{\Gamma \vdash A \vee \neg A}\text{ excluded middle}.\]

The set of **provable sequents** is inductively defined by the natural deduction rules, as we now explain.

A **proof** of a sequent $\Gamma \vdash A$ is a derivation of this sequent, that is, a tree where nodes are labelled by sequents and where the root is labelled by $\Gamma \vdash A$, and such that if a node is labelled by a sequent 
$\Delta \vdash B$ and its children are labelled by sequents $\Sigma_1 \vdash C_1, \dots, \Sigma_n \vdash C_n$ then there is a natural deduction rule
that allows us to deduce $\Delta \vdash B$ from $\Sigma_1 \vdash C_1, \dots, \Sigma_n \vdash C_n$.

A sequent $\Gamma \vdash A$ is **provable** if there exists a proof of $\Gamma \vdash A$.


**Example.** If this is your first exposure to formal natural deduction proofs, then you will want to see an example of a *proof tree* (or *derivation tree*) of the kind described in the definition of "proof" above.  But first let's define one more proof principle (because it will help control the size of the proof tree in our example).

+ **Weakening.** The *principle of weakening* asserts that it is possible to add useless hypotheses in a sequent. Precisely, if the sequent $\Gamma \vdash A$ is provable, then the sequent $\Gamma, B \vdash A$ is also provable. (The weakening principle is provable in natural deduction by induction over the structure of a proof of $Γ \vdash A$.)

Here is a natural deduction proof of the sequent $\emptyset \vdash \neg\neg A  \to A$. (Here, $\Gamma = \emptyset$ and in such cases we typically write $\vdash A$ instead of $\emptyset\vdash A$.) Assume we have a proof $\pi$ of the sequent $\vdash \neg \neg A$. Then, we can derive $\vdash A$ as follows:
  \[
  \frac{\frac{}{\vdash A \vee \neg A}{\small \text{excl. mid.}}\quad \frac{}{A \vdash A}{\small \text{axiom}} \quad \frac{\frac{\frac{}{\neg A \vdash \neg A}\qquad \frac{\frac{\pi}{\vdash \neg \neg A}}{\neg A \vdash \neg \neg A}{\text{weakening}}}{\neg A \vdash \perp}\neg\text{-elim}}{\neg A \vdash A}{\small \perp\text{-elim}}}{\vdash A}\vee\text{-elim}
  \]

**PROBLEM 4.** Compare/contrast the binary relation $\vdash$ introduced here and the relation $\vdash$ we use in model theory.

----

### Theories and Theorems
A *theory* is a finite or infinite set of *closed* propositions
  (i.e., propositions with no free variables); the elements of a theory are called *axioms*.
  
  If a theory $\mathcal T$ is finite, we say that a proposition $A$ is a *theorem in* $\mathcal T$, or that the proposition *can be proved in* $\mathcal T$, if the sequent $\mathcal T \vdash A$ is provable.  However, in the general case, the pair $\mathcal T \vdash$ is not a sequent.  We need to give a more general definition.
  
A proposition $A$ is a *theorem* (or *provable proposition*) *in the theory* $\mathcal T$ if there exists a finite subset $\Gamma$ of $\mathcal T$ such that the sequent $\Gamma \vdash A$ is provable.

**PROBLEM 5.**   
a. Compare/contrast a proof theory theory and a model theory theory.  
b. Comment on this definition of "theorem" from the point of view of model theory. (Be sure to say something about finiteness.)

---

### Consistency

A theory $\mathcal T$ is *consistent* if there is some proposition that is not provable in $\mathcal T$.  Otherwise, $\mathcal T$ is *contradictory.*

**PROBLEM 6.** Is this definition of "consistent" the same as ours?

----

### Soundness
One of the motivations for the study of models is that validity in a model is an invariant of provability: provable sequents are valid in all models. 
Thus, if a proposition is provable in a theory, then it is valid in all the models of the theory. This suggests a method to show that a proposition is not provable in a given theory: it is sufficient to show that there is a model of the theory in which the proposition is not valid. The second formulation of the soundness theorem given below states this principle.

**Theorem 1.** If a sequent $A_1, \dots, A_m \vdash B_1, \dots, B_n$ is 
provable in natural deduction, then it is valid in all models.

In the model theory that we studied, many theorems involved validity of a given formula $\varphi$ in a given model, and the proof typically proceeds by induction on the structure (or complexity) of $\varphi$.  Theorem 1 above is about the validity (in all models) of a sequent that is provable in natural deduction. Its proof proceeds by induction *on the structure of a natural deduction proof.*  

**PROBLEM 7.** Can you prove Theorem 1?  (An outline of a proof will suffice, as long as it's clear and well-written.)

The following so-called *soundness theorem* is a consequence of Theorem 1, and it can be formulated in three different (equivalent) ways.

**Theorem 2.** (Soundness) Let $\mathcal T$ be a theory and $A$ a proposition.
1. If $A$ is provable in $\mathcal T$, then $A$ is valid in all the models of $\mathcal T$.
2. If there exists a model of $\mathcal T$ that is not a model of $A$, then $A$ is not provable in $\mathcal T$.
3. If $\mathcal T$ has a model, then $\mathcal T$ is consistent.

---

### Completeness

The soundness theorem tells us that if a proposition $A$ is provable in a theory 
$\mathcal T$ then it is valid in all the models of the theory. The completeness 
theorem, first proved in 1930 by Gödel, is the converse of the soundness theorem.
Similarly to soundness, the completeness theorem can be formulated in
three different (equivalent) ways.

**Theorem 3.** (Completeness) Let $\mathcal T$ be a theory and $A$ a proposition.
1. If $A$ is valid in all the models of $\mathcal T$ then $A$ is provable in $\mathcal T$.
2. If $A$ is not provable in $\mathcal T$, then there exists a model of $\mathcal T$ which is not a model of $A$.
3. If $\mathcal T$ is consistent then $\mathcal T$ has a model.

The first two formulations are trivially equivalent, and version 3 is a consequence
of 2 if we take $A = \perp$. 

**PROBLEM 8.** Show that version 2 of the completeness theorem is a consequence of version 3.
<!-- Consider a theory T and a proposition A not provable in this theory. By Proposition 1.7, the
proposition ⊥ is not provable in the theory T , ¬A. Therefore by (3) the theory
T , ¬A has a model. This model is a model of T but not a model of A. -->



---

<!-- ### Problems from Rothmaler -->
<!-- **3.3.2**, **3.3.4**, **3.6.2**, **4.2.5**,  -->

<!-- **5.6.1.** Prove---without using the Axiom of Choice (or any equivalent, like Zorn's Lemma)---that in a well-ordered boolean algebra, every filter can be extended to an ultrafilter. (Note that this applies to any countable boolean algebra, in particular to the Lindenbaum-Tarski algebras of countable languages (or theories).) -->

<!-- Recall, if $\mathcal M$ is an $L$-structure and $X \subseteq M$, then the **substructure of $\mathcal M$ generated by $X$** is denoted by $\mathcal M_X$ (or by $\langle X \rangle$ when $\mathcal M$ is clear from context), and is defined to be the substructure of $\mathcal M$ with universe $M_X := \bigcap \{N : X \subseteq N, \mathcal N \leq \mathcal M\}$.

**Problem 2.** [Rothmaler 6.3.3.]  
Let $\mathcal{M}$ and $\mathcal{N}$ be $L$-structures and $X \subseteq M$. Suppose $f\colon X \rightarrow N$ satisfies $(\mathcal{M}, X) \equiv_{\mathbf{at}} (\mathcal{N}, f[X])$ (and is thus injective). Extend $f$ to an isomorphism $F\colon \mathcal{M}_X \cong \mathcal{N}_{f[X]}$ and prove $(\mathcal{M}, M_X) \equiv_{\mathbf{at}} (\mathcal{N}, F[M_X]).$ -->

# Course 4: Continuous Domains

*Domain Theory and Fixed-Point Semantics through Arren Mott's Continuous Domain Discipline*

> "He gave passages their meanings" — Arren Mott's epitaph

## Course Overview

This course teaches **domain theory** and **denotational semantics** through the story of Arren Mott (820-901), who solved the problem left by Brennis Mund: how to recover general recursion without sacrificing mathematical rigor.

Where Course 3 (Typed Passages) showed that types prevent non-termination by forbidding the Y combinator, this course shows how to give MEANING to recursive definitions through fixed-point semantics. Mott's insight was that non-termination is not failure but absence of information — and that recursive definitions can be understood as limits of increasing approximations.

## Prerequisites

- Course 1: Pure Passage Calculus (lambda calculus fundamentals)
- Course 3: Typed Passages (understanding of the non-termination problem)

## Learning Objectives

By the end of this course, you will be able to:

1. Explain why types prevent general recursion
2. Define partial orders and the information ordering
3. Construct domains (dcpos) and identify their key properties
4. Apply Scott continuity to characterize computable functions
5. Compute least fixed points through iteration
6. Give denotational semantics to lambda terms
7. State and apply the adequacy theorem
8. Understand how PCF reconciles types with recursion

## Tutorials

| # | Title | Topic | Technical Content |
|---|-------|-------|------------------|
| 01 | The Recursion Problem | Why types ban Y | Y combinator untypability, expressiveness loss |
| 02 | The Information Ordering | Partial orders | ⊥, approximation, flat and lazy domains |
| 03 | Domains and Completeness | dcpos | Directed sets, limits, completeness |
| 04 | Continuous Functions | Scott continuity | Monotonicity, limit preservation |
| 05 | The Least Fixed Point | Fixed-point theorem | Iteration, convergence, fix operator |
| 06 | Denotational Semantics | Meaning of programs | Interpretation function, adequacy |
| 07 | The Continuous Domain Discipline | Mott's synthesis | PCF, reflexive domains, legacy |

## The Scholar: Arren Mott

**Arren Mott** (820-901) joined the Archives in 845 as a junior logician under Brennis Mund. While Brennis focused on safety through types, Mott asked a different question: not "does it terminate?" but "what does it mean?"

Key milestones:
- **857**: Proposes partial order of information
- **865**: Discovers Scott continuity
- **867**: Proves least fixed point theorem
- **877**: Constructs reflexive domains (D ≅ [D→D])
- **880**: Develops denotational semantics
- **890**: Proposes PCF (typed calculus with fixed points)
- **893**: Publishes "The Continuous Domain Discipline"

## Technical Concepts

### The Recursion Problem

Brennis Mund's types prevent Omega by forbidding self-application. But they also forbid the Y combinator:
```
Y = λf.((λx.f(x x))(λx.f(x x)))
```
The Y combinator enables recursion. Without it, typed passages cannot express general recursive functions like Ackermann's function.

### The Information Ordering

Mott's insight: computational values form a **partial order** by information content.
- **⊥** (bottom) = no information (undefined, non-terminating)
- **Flat domains**: ⊥ ⊑ 0, ⊥ ⊑ 1, ⊥ ⊑ 2, ... (no relation between numbers)
- **Lazy domains**: 1:⊥ ⊑ 1:2:⊥ ⊑ 1:2:3:⊥ ⊑ ... (partial lists)

### Domains (dcpos)

A **domain** (directed-complete partial order) is a partial order where every directed set has a limit (supremum). This ensures fixed points exist.

### Scott Continuity

A function f is **Scott-continuous** if it preserves directed limits:
```
f(⊔D) = ⊔{f(d) | d ∈ D}
```
Continuous functions are the computable functions — they only produce information based on finite amounts of input information.

### The Least Fixed Point Theorem

**Theorem**: Every continuous function f on a dcpo has a least fixed point:
```
fix(f) = ⊔{fⁿ(⊥) | n ∈ ℕ}
```

This is constructed by iterating from ⊥:
```
⊥ ⊑ f(⊥) ⊑ f(f(⊥)) ⊑ f(f(f(⊥))) ⊑ ...
```

### Denotational Semantics

The **interpretation function** ⟦M⟧ρ maps lambda terms to domain elements:
- ⟦x⟧ρ = ρ(x)
- ⟦λx.M⟧ρ = λd.⟦M⟧ρ[x↦d]
- ⟦M N⟧ρ = (⟦M⟧ρ)(⟦N⟧ρ)

Key insight: ⟦Ω⟧ = ⊥ — Omega has a well-defined meaning (no information).

### The Adequacy Theorem

**Theorem**: ⟦M⟧ ≠ ⊥ if and only if M terminates.

This connects the mathematical semantics to actual computation.

## Datasets

This course uses datasets derived from the Living Ledger:

| Dataset | Description |
|---------|-------------|
| `domain_elements.csv` | Elements of domains with partial order structure |
| `continuous_functions.csv` | Continuous functions and their properties |
| `fixed_point_computations.csv` | Fixed point iteration traces |
| `denotational_semantics.csv` | Lambda terms with their denotations |

## Living Ledger Integration

This course contributes **25 canonical events** to the Living Ledger, spanning Arren Mott's career from 820-902.

Key events:
- EV-855-001: Partial information insight
- EV-867-001: Least fixed point theorem
- EV-877-001: Reflexive domains discovered
- EV-901-001: Arren Mott dies

## How to Use This Course

Each notebook can be run in Google Colab. Click the badge at the top of each notebook to launch:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

## Connection to Other Courses

- **Course 1** (Pure Passage Calculus): Introduces the Y combinator
- **Course 3** (Typed Passages): Shows Y is untypable, motivating this course
- **Course 5** (Dependent Classifications): Will extend types to carry proofs
- **Course 7** (Equivalence via Passage): Will unify types and domains

## Repository

This course is part of the [densworld-courses](https://github.com/buildLittleWorlds) project.

---

*Types & Computation Series*
*buildLittleWorlds*

# Statistics for Data Science Practical Examination — Question K3
**Student:** Tushar Guleria | **Reg. ID:** GF202459441 | **Topic:** Markov Chains 

---

## Problem Statement
A university website's SEO team wants to know which of its six pages (**Home**, **About**, **Courses**, **Blog**, **Apply**, **Fees**) a random visitor lands on most often, modeled as a Markov Chain using the PageRank algorithm.

### Link Structure
| Page | Outgoing Links |
| :--- | :--- |
| **Home** | About, Courses, Blog |
| **About** | Home |
| **Courses** | Home, Apply, Blog |
| **Blog** | Courses, About |
| **Apply** | Fees, Courses |
| **Fees** | Home |

---

## Environment & Tools Used
* **Execution Environment:** Google Colab (Python 3 Jupyter Notebook)
* **Libraries:**
  * `numpy` — Matrix construction, linear algebra, and power iteration
  * `pandas` — Structured formatting of transition matrices and PageRank result tables
  * `networkx` — Directed graph construction and verification via `networkx.pagerank`
  * `matplotlib` — Grouped bar chart visualization comparing damping factors (*d* = 0.85 vs. *d* = 0.50)

---

## Summary of Numerical Results
* **Formula:** `G = d·P + (1 - d)/6`
* **Convergence Tolerance (L1 Norm):** `1e-8`
* **Iterations to Converge:** `32` iterations at *d* = 0.85 | `17` iterations at *d* = 0.50

| Rank | Page | PageRank (*d* = 0.85) | PageRank (*d* = 0.50) | Difference (*d* = 0.50 − *d* = 0.85) |
| :--- | :--- | :---: | :---: | :---: |
| 1 | **Home** | 0.290229 | 0.254464 | −0.035764 |
| 2 | **Courses** | 0.215275 | 0.194196 | −0.021079 |
| 3 | **About** | 0.178728 | 0.165272 | −0.013456 |
| 4 | **Blog** | 0.168226 | 0.158110 | −0.010116 |
| 5 | **Apply** | 0.085995 | 0.115699 | +0.029705 |
| 6 | **Fees** | 0.061548 | 0.112258 | +0.050710 |

---

## Follow-Up Questions & Answers

### 1. Which page has the highest PageRank and why, given the link structure? Why does "Fees" rank where it does?

**Home** has the highest PageRank (**0.290229** at *d* = 0.85), ahead of **Courses** (**0.215275**) and **About** (**0.178728**). **Home** acts as the central hub of the link structure: **About** and **Fees** have only one outgoing link each, sending 100% of their rank weight directly to **Home**, while **Courses** passes 1/3 of its weight there. **Home** also links outward to **Courses**, **About**, and **Blog**, creating a strong feedback loop that cycles rank back into **Home**.

**Fees** ranks last (6th) with a PageRank of **0.061548** (at *d* = 0.85). Its only inbound link comes from **Apply**, which itself has a low score (**0.085995**) and splits its outgoing weight equally between **Fees** and **Courses**—so **Fees** receives only half of **Apply**'s already small rank. **Apply**, in turn, is reached solely from **Courses**, which splits its rank three ways. Because **Fees** passes 100% of its rank straight to **Home**, it functions as a low-traffic leaf page that feeds the top page.

---

### 2. How did the scores change when *d* fell from 0.85 to 0.5? Explain what the damping factor represents about visitor behaviour.

When *d* fell from 0.85 to 0.50, the scores compressed toward the uniform baseline (1/6 ≈ 0.166667). The top-ranking pages dropped, while the weakly linked pages rose:
* **Home:** 0.290229 → 0.254464 (−0.035764)
* **Courses:** 0.215275 → 0.194196 (−0.021079)
* **About:** 0.178728 → 0.165272 (−0.013456)
* **Blog:** 0.168226 → 0.158110 (−0.010116)
* **Apply:** 0.085995 → 0.115699 (+0.029705)
* **Fees:** 0.061548 → 0.112258 (+0.050710)

The overall ranking order stayed identical (**Home > Courses > About > Blog > Apply > Fees**), but the distribution flattened out and power iteration converged faster (in **17 iterations** instead of **32 iterations**).

The damping factor *d* represents the probability that a random visitor continues browsing by clicking an outgoing link on the current page. The remaining probability (1 − *d*) represents the chance that the visitor stops following links and jumps ("teleports") to a random page on the site—for example, by typing a URL directly or opening a bookmark. At *d* = 0.50, visitors teleport half the time, reducing the influence of link structure and pulling all scores closer to 1/6 ≈ 0.1667. At *d* = 0.85, visitors follow links 85% of the time, amplifying well-connected hubs like **Home** and penalizing poorly linked pages like **Fees**.[cite: 1, 2]

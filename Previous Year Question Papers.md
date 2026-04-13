# 📝 DU Artificial Intelligence — Previous Year Questions & Answers (2020–2025)

> **Course:** B.Sc. (Hons.) Computer Science — Semester VI  
> **Course Code:** C-13 / DSC16 — Artificial Intelligence  
> **University:** University of Delhi  
> **Exam Pattern:** Section A (Q1, compulsory, short answers) + Section B (attempt any 4 of Q2–Q8)  
> **Max Marks:** 75

---

## 📚 Table of Contents

- [2025 Paper](#-2025-question-paper)
- [2024 Paper](#-2024-question-paper)
- [2023 Paper](#-2023-question-paper)
- [2022 Paper](#-2022-question-paper)
- [2021 Paper](#-2021-question-paper)
- [2020 Paper](#-2020-question-paper)
- [Topic-wise Frequency Analysis](#-topic-wise-frequency-analysis)

---

## 📄 2025 Question Paper

> **Source:** B.Sc. (H) CS VI Sem Final Exam, University of Delhi

### Section A — Compulsory (Attempt all)

**Q1(a):** What is a Rational Agent? Explain with an example.

> **Answer:**  
> A rational agent is one that acts to **maximise its expected performance measure**, given its percept sequence and built-in knowledge.
> 
> **Example — Spam Filter Agent:**  
> - **Percept:** Incoming email content  
> - **Action:** Move to spam / keep in inbox  
> - **Rational:** Correctly classifies emails to maximise user satisfaction
> 
> Rationality ≠ Omniscience. A rational agent does the best with what it knows, not necessarily the globally optimal action.

---

**Q1(b):** Write the rules of propositional logic for conjunction and disjunction. Construct a truth table for `P ∧ (P ∨ Q)`.

> **Answer:**
> 
> | P | Q | P∨Q | P∧(P∨Q) |
> |---|---|-----|---------|
> | T | T |  T  |    T    |
> | T | F |  T  |    T    |
> | F | T |  T  |    F    |
> | F | F |  F  |    F    |
> 
> By **absorption law**: `P ∧ (P ∨ Q) ≡ P`. The expression is equivalent to just P.

---

**Q1(c):** What is the Chomsky Hierarchy? List the four types of grammars.

> **Answer:**
> 
> | Type | Name | Automaton | Example |
> |------|------|-----------|---------|
> | 0 | Unrestricted | Turing Machine | Any language |
> | 1 | Context-Sensitive | Linear Bounded Automaton | `aⁿbⁿcⁿ` |
> | 2 | Context-Free | Pushdown Automaton | `aⁿbⁿ` |
> | 3 | Regular | Finite Automaton | `a*b*` |
> 
> Each type is a **proper subset** of the one above it.

---

**Q1(d):** Give the PEAS description for a Robotic Vacuum Cleaner.

> **Answer:**
> 
> | Component | Description |
> |-----------|-------------|
> | **Performance** | Cleanliness, battery efficiency, area covered |
> | **Environment** | Room floor, furniture, carpet, dust |
> | **Actuators** | Wheels (movement), suction motor, brush |
> | **Sensors** | Dirt sensor, bump sensor, cliff sensor, camera |

---

**Q1(e):** What is Alpha-Beta pruning? How does it improve Min-Max?

> **Answer:**  
> Alpha-Beta pruning **eliminates branches** in the game tree that cannot affect the final decision.  
> - **α (alpha):** Best value MAX can guarantee so far  
> - **β (beta):** Best value MIN can guarantee so far  
> - **Prune when:** α ≥ β  
> 
> Improvement: Reduces nodes from **O(b^d)** to **O(b^(d/2))**, effectively doubling the search depth for the same computation.

---

**Q1(f):** Explain weakly supervised learning briefly.

> **Answer:**  
> Weakly supervised learning uses **partially labeled or noisily labeled** data. It lies between supervised (fully labeled) and unsupervised learning. Methods include self-training, co-training, and label propagation. Useful when labeling is expensive.

---

**Q1(g):** Express "Rohan gave Tina a box of chocolates" as a Conceptual Dependency structure.

> **Answer:**  
> Conceptual Dependency represents the meaning of sentences in a canonical form.
> 
> ```
> Rohan ──ATRANS──> box-of-chocolates
>         │
>         ├── Actor: Rohan
>         ├── Object: box-of-chocolates
>         ├── From: Rohan (possession)
>         └── To: Tina (possession)
> ```
> 
> **ATRANS** = Abstract Transfer (of possession/ownership)

---

### Section B — Attempt any 4

**Q2(a):** Explain BFS and DFS with an example. Compare their time and space complexity.

> **Answer:**
> 
> **BFS (Breadth-First Search):**
> - Uses a **queue**; explores level by level
> - **Complete and optimal** (for unweighted graphs)
> - Time: O(b^d), Space: O(b^d)
> 
> **DFS (Depth-First Search):**
> - Uses a **stack** (or recursion); goes deep first
> - **Not optimal**, but uses less memory
> - Time: O(b^m), Space: O(bm) where m = max depth
> 
> ```python
> # BFS Example
> from collections import deque
> def bfs(graph, start, goal):
>     queue = deque([[start]])
>     visited = set()
>     while queue:
>         path = queue.popleft()
>         node = path[-1]
>         if node == goal: return path
>         if node not in visited:
>             visited.add(node)
>             for n in graph[node]:
>                 queue.append(path + [n])
> ```
> 
> | Feature | BFS | DFS |
> |---------|-----|-----|
> | Data Structure | Queue | Stack |
> | Complete? | Yes | No (infinite loops) |
> | Optimal? | Yes (unweighted) | No |
> | Space | High | Low |

---

**Q2(b):** Write a Prolog program to check if an element belongs to a list.

> **Answer:**
> 
> ```prolog
> % member(X, List) — succeeds if X is in List
> member(X, [X|_]).
> member(X, [_|T]) :- member(X, T).
> 
> % Examples:
> ?- member(3, [1,2,3,4]).
> true.
> 
> ?- member(5, [1,2,3]).
> false.
> ```

---

**Q3(a):** What is the A* algorithm? Explain with an example graph, showing f(n), g(n), and h(n) values.

> **Answer:**  
> A* uses: `f(n) = g(n) + h(n)`
> - `g(n)` = actual cost from start to n
> - `h(n)` = heuristic estimate from n to goal
> - `f(n)` = total estimated cost
> 
> **Example:**
> 
> ```
> Graph:  A --1-- B --3-- D (goal)
>         |       |
>         4       2
>         |       |
>         C ------+
>
> h values: h(A)=6, h(B)=2, h(C)=4, h(D)=0
>
> Start: A, Goal: D
> Step 1: f(B) = g(A→B) + h(B) = 1+2 = 3
>         f(C) = g(A→C) + h(C) = 4+4 = 8
> Step 2: Expand B: f(D) = 1+3+0 = 4
> Result: Path A→B→D, cost = 4
> ```
> 
> A* is **optimal and complete** when h(n) is admissible (never overestimates).

---

**Q4(a):** Explain semantic networks with an example.

> **Answer:**  
> A semantic network uses nodes (concepts) and labelled arcs (relationships) to represent knowledge.
> 
> ```
> [Animal]
>    │ IS-A
>    ▼
>  [Dog] ── HAS ──> [4 Legs]
>    │               [Fur]
>    │ IS-A
>    ▼
> [Poodle] ── IS ──> [Curly hair]
> ```
> 
> - **IS-A** = inheritance relationship (property inheritance)  
> - **AKO (A Kind Of)** = class membership  
> - Allows **property inheritance**: Poodle inherits "4 Legs" and "Fur" from Dog via IS-A

---

**Q4(b):** What is Resolution in Logic? Show a proof using resolution.

> **Answer:**  
> Resolution is a rule of inference: from `(A ∨ B)` and `(¬B ∨ C)`, derive `(A ∨ C)`.
> 
> **Proof Example — "Does it snow?"**
> 
> Given:
> 1. `January` (fact)
> 2. `Clouds` (fact)
> 3. `January → Cold` i.e., `¬January ∨ Cold`
> 4. `Clouds → Precipitation` i.e., `¬Clouds ∨ Precipitation`
> 5. `Cold ∧ Precipitation → Snow` i.e., `¬Cold ∨ ¬Precipitation ∨ Snow`
> 
> Resolution steps:
> - From (1) and (3): `Cold`
> - From (2) and (4): `Precipitation`
> - From `Cold`, `Precipitation`, and (5): `Snow` ✓

---

## 📄 2024 Question Paper

> **Source:** BSC-6-SEM-ARTIFICIAL-INTELLIGENCE-4506, University of Delhi

### Section A — Compulsory

**Q1(a):** What do you understand by PROLOG predicates? Give examples.

> **Answer:**  
> A **predicate** in Prolog is a relation that can be queried. Predicates are defined by **facts** and **rules**.
> 
> ```prolog
> % Facts (predicates with no body)
> likes(mary, food).
> likes(mary, wine).
> likes(john, wine).
> 
> % Rule predicate
> friends(X, Y) :- likes(X, Z), likes(Y, Z).
> 
> % Built-in predicates
> ?- length([1,2,3], L).   % L = 3
> ?- append([1,2],[3,4],R). % R = [1,2,3,4]
> ```

---

**Q1(b):** Compute Bayesian probability: P(B|A) = 0.9, P(A) = 0.3, P(B) = 0.5. Find P(A|B).

> **Answer:**  
> Using **Bayes' Theorem**:
> 
> ```
> P(A|B) = P(B|A) × P(A) / P(B)
>        = 0.9 × 0.3 / 0.5
>        = 0.27 / 0.5
>        = 0.54
> ```
> 
> So P(A|B) = **0.54**

---

**Q1(c):** Describe the architecture of a problem-solving agent.

> **Answer:**
> 
> ```
> ┌──────────────────────────────────────┐
> │           PROBLEM-SOLVING AGENT      │
> │                                      │
> │  Percepts → [Goal Formulation]       │
> │           → [Problem Formulation]    │
> │           → [Search]                 │
> │           → [Execution]              │
> └──────────────────────────────────────┘
> ```
> 
> Steps:
> 1. **Goal Formulation:** Define what success looks like
> 2. **Problem Formulation:** Define states, actions, costs
> 3. **Search:** Find a sequence of actions to reach the goal
> 4. **Execution:** Carry out the solution

---

**Q1(d):** What is the difference between Strong AI and Weak AI?

> **Answer:**
> 
> | | Weak AI | Strong AI |
> |--|---------|-----------|
> | **Definition** | AI designed for specific tasks | AI with general human-like intelligence |
> | **Example** | Chess engine, Siri, spam filter | Hypothetical — not yet achieved |
> | **Self-awareness** | No | Yes (theoretically) |
> | **Learning** | Task-specific | Generalises across domains |

---

**Q1(e):** Explain the Min-Max algorithm with a two-ply game tree.

> **Answer:**
> 
> ```
>              MAX
>            /      \
>         MIN        MIN
>        /   \      /   \
>       3     5    2     9
> 
> MIN nodes: left=min(3,5)=3, right=min(2,9)=2
> MAX node:  max(3,2) = 3
> ```
> 
> MAX player picks the move that leads to value **3** (left branch).

---

**Q1(f):** Convert to CNF: `(A → B) ∧ (B → C)`

> **Answer:**
> 
> Step 1 — Eliminate implication:
> `(¬A ∨ B) ∧ (¬B ∨ C)`
> 
> This is already in **CNF** (conjunction of disjunctions / clauses).
> 
> Clauses: `{¬A ∨ B}` and `{¬B ∨ C}`

---

**Q2(a):** Describe the Water-Jug problem and give a state space representation.

> **Answer:**  
> **Problem:** Given a 4-litre and 3-litre jug (no markings), get exactly 2 litres in the 4L jug.
> 
> **State:** `(x, y)` — x = litres in 4L jug, y = litres in 3L jug  
> **Initial State:** `(0, 0)`, **Goal:** `(2, _)`
> 
> **Operators:**
> 
> | Rule | Action | New State |
> |------|--------|-----------|
> | Fill 4L | `(0,y)→(4,y)` | Fill from tap |
> | Fill 3L | `(x,0)→(x,3)` | Fill from tap |
> | Empty 4L | `(x,y)→(0,y)` | Pour out |
> | Pour 4L→3L | Transfer | `min` constraints |
> 
> **Solution path:**
> ```
> (0,0) → (0,3) → (3,0) → (3,3) → (4,2) → (0,2) → (2,0) → (2,3)
>                                                       ↑ Goal!
> ```

---

**Q3(a):** Write a Prolog program to find the maximum element in a list.

> **Answer:**
> 
> ```prolog
> maxlist([X], X).   % Base case: single element
> maxlist([H|T], Max) :-
>     maxlist(T, TMax),
>     (H > TMax -> Max = H ; Max = TMax).
> 
> ?- maxlist([3,1,7,2,5], Max).
> Max = 7.
> ```

---

**Q4(a):** Explain Frames with a detailed example.

> **Answer:**  
> A **frame** is a data structure for representing a stereotyped situation.
> 
> ```
> FRAME: Employee
>   ┌─────────────────────────────┐
>   │ AKO:         Person         │
>   │ Name:        <string>       │
>   │ EmployeeID:  <integer>      │
>   │ Department:  <string>       │
>   │ Salary:      <real>         │
>   │ JoiningDate: <date>         │
>   └─────────────────────────────┘
> 
> INSTANCE: Employee-001
>   ┌─────────────────────────────┐
>   │ AKO:         Employee       │
>   │ Name:        "Rahul Sharma" │
>   │ EmployeeID:  1042           │
>   │ Department:  "Engineering"  │
>   │ Salary:      75000.00       │
>   │ JoiningDate: 01-Aug-2022    │
>   └─────────────────────────────┘
> ```
> 
> **Prolog representation:**
> 
> ```prolog
> frame(employee_001, [
>     ako(employee),
>     name('Rahul Sharma'),
>     department('Engineering'),
>     salary(75000)
> ]).
> ```

---

## 📄 2023 Question Paper

> **Source:** Official B.Sc. (H) CS, Semester VI, University of Delhi (Code: 4506)  
> **Year:** 2023

### Section A — Compulsory (Q1)

**Q1(a):** What do you understand by the term "Rational Agent"?

> **Answer:**  
> A **rational agent** selects actions that maximise its **performance measure**, based on:
> - Its percept sequence (history of sensory inputs)
> - Its built-in knowledge
> 
> Rationality is NOT omniscience — it means making the best possible decision given available information. A rational agent may also **learn** from its environment to improve future performance.

---

**Q1(b):** What would be the output of the following Prolog statement, and why?
```prolog
?- A is 6 + 3, B = 5+4, A = B.
```

> **Answer:**
> - `A is 6 + 3` → A is **evaluated arithmetically**: A = 9
> - `B = 5+4` → B is **unified** (not evaluated): B = `5+4` (a term, not 9)
> - `A = B` → Tries to unify 9 with `5+4` → **FAILS**
> 
> **Output:** `false.`
> 
> The key distinction: `is/2` evaluates arithmetic; `=/2` is pure unification.

---

**Q1(c):** Construct the truth table for `A ∧ (A ∨ B)`. What single term is this equal to?

> **Answer:**
> 
> | A | B | A∨B | A∧(A∨B) |
> |---|---|-----|---------|
> | T | T |  T  |    T    |
> | T | F |  T  |    T    |
> | F | T |  T  |    F    |
> | F | F |  F  |    F    |
> 
> By the **Absorption Law**: `A ∧ (A ∨ B) ≡ A`

---

**Q1(e):** Develop a parse tree for the sentence "Raja slept on the sofa".

> **Answer:**
> 
> ```
>                    S
>                  /   \
>                NP      VP
>                |      /    \
>              Raja    V       PP
>                    slept   /    \
>                          PREP    NP
>                           on   /    \
>                               DET    N
>                               the  sofa
> ```
> 
> **Grammar rules used:**
> ```
> S  → NP VP
> VP → V PP
> PP → PREP NP
> NP → DET N | ProperNoun
> ```

---

**Q1(f):** Compare and contrast DFS and BFS.

> **Answer:**
> 
> | Feature | BFS | DFS |
> |---------|-----|-----|
> | Strategy | Explore level by level | Explore depth first |
> | Data structure | Queue (FIFO) | Stack (LIFO) / Recursion |
> | Complete? | Yes (finite graphs) | No (may loop in infinite graphs) |
> | Optimal? | Yes (uniform cost) | No |
> | Time complexity | O(b^d) | O(b^m) |
> | Space complexity | O(b^d) — HIGH | O(bm) — LOW |
> | Best for | Shortest path | Memory-limited environments |
> 
> where b = branching factor, d = depth of shallowest goal, m = max depth

---

**Q1(g):** Transform the following into CNF:
1. `P ∨ (~P ∧ Q ∧ R)`
2. `(~P ∧ Q) ∨ (P ∧ ~Q) ∧ S`

> **Answer:**
> 
> **Part 1:** `P ∨ (~P ∧ Q ∧ R)`
> Distribute: `(P ∨ ~P) ∧ (P ∨ Q) ∧ (P ∨ R)`  
> Simplify: `T ∧ (P ∨ Q) ∧ (P ∨ R)`  
> **CNF:** `(P ∨ Q) ∧ (P ∨ R)`
> 
> **Part 2:** `(~P ∧ Q) ∨ (P ∧ ~Q ∧ S)`
> Distribute using: `(A ∧ B) ∨ (C ∧ D) = (A∨C)(A∨D)(B∨C)(B∨D)`  
> → `(~P ∨ P)(~P ∨ ~Q)(~P ∨ S)(Q ∨ P)(Q ∨ ~Q)(Q ∨ S)`  
> → `T ∧ (~P ∨ ~Q) ∧ (~P ∨ S) ∧ (Q ∨ P) ∧ T ∧ (Q ∨ S)`  
> **CNF:** `(~P ∨ ~Q) ∧ (~P ∨ S) ∧ (P ∨ Q) ∧ (Q ∨ S)`

---

**Q1(h):** Express as Conceptual Dependency:
1. "Ram drove the car fast."
2. "Rita gave Sita a bunch of flowers."

> **Answer:**
> 
> **1. "Ram drove the car fast"**
> ```
> Ram ──PROPEL──> car
>     Actor: Ram
>     Object: car
>     Direction: forward
>     Speed: fast
>     Instrument: (wheels/engine)
> ```
> **PROPEL** = apply force to cause motion
> 
> **2. "Rita gave Sita a bunch of flowers"**
> ```
> Rita ──ATRANS──> flowers
>      Actor: Rita
>      Object: flowers
>      From: Rita
>      To: Sita
> ```
> **ATRANS** = abstract transfer of possession

---

**Q1(i):** Give properties of Type 1 and Type 2 grammars from Chomsky Hierarchy.

> **Answer:**
> 
> **Type 1 — Context-Sensitive Grammar (CSG):**
> - Rules of the form: `αAβ → αγβ` (A can only be replaced in context of α and β)
> - `|LHS| ≤ |RHS|` (no shrinking rules except possibly S → ε)
> - Recognised by **Linear Bounded Automaton (LBA)**
> - Example: `aⁿbⁿcⁿ`
> 
> **Type 2 — Context-Free Grammar (CFG):**
> - Rules of the form: `A → γ` (single non-terminal on LHS, any string on RHS)
> - Recognised by **Pushdown Automaton (PDA)**
> - Used in programming language parsers
> - Example: `aⁿbⁿ`, arithmetic expressions

---

**Q1(j):** Use Minimax to compute values in this two-ply tree:
Terminal values: `[3, 5, 2, 9]` (left to right)

> **Answer:**
> 
> ```
>               MAX
>            /       \
>          MIN        MIN
>         / \         / \
>        3   5       2   9
> 
> MIN (left)  = min(3,5) = 3
> MIN (right) = min(2,9) = 2
> MAX (root)  = max(3,2) = 3
> ```
> 
> **Result:** MAX player will choose the left branch. Value = **3**

---

**Q1(k):** Write about the limitations of Hill Climbing Search.

> **Answer:**
> 
> ```
> Value
>   |        /\         /\  ← Global Max
>   |       /  \  plateau  \
>   |      /    \──────     \
>   |_____/  local max       \_____
> ```
> 
> **Three main problems:**
> 1. **Local Maximum:** Gets stuck at peaks lower than global max
> 2. **Plateau:** Flat area where all moves appear equal — random walk needed
> 3. **Ridge:** Series of local maxima — difficult to navigate without backtracking
> 
> **Solutions:** Simulated Annealing, Random-restart Hill Climbing, Genetic Algorithms

---

**Q2(a):** Describe the water-jug problem and give state space representation.

*(See 2024 Q2(a) above for full answer)*

---

**Q2(b):** Transform into clausal form:
`∃x ∀y (∀z P(f(x),y,z) → (∃u Q(x,u) ∧ ∃v R(y,v)))`

> **Answer:**
> 
> Steps to convert to Clausal (Prenex Normal) Form:
> 
> 1. **Eliminate implication:** `¬P(f(x),y,z) ∨ (∃u Q(x,u) ∧ ∃v R(y,v))`
> 2. **Move quantifiers out:** `∃x ∀y ∀z ∃u ∃v (¬P(f(x),y,z) ∨ Q(x,u) ∧ R(y,v))`
> 3. **Skolemize existentials:** x → a (constant), u → g(y,z), v → h(y,z)
> 4. **Result:** `∀y ∀z [¬P(f(a),y,z) ∨ Q(a,g(y,z))] ∧ [¬P(f(a),y,z) ∨ R(y,h(y,z))]`
> 
> **Clauses:**
> - `{¬P(f(a),y,z), Q(a,g(y,z))}`
> - `{¬P(f(a),y,z), R(y,h(y,z))}`

---

**Q3(a):** Write a Prolog program `maxlist(L, Max)` to find the greatest number.

*(See 2024 Q3(a) answer above)*

---

**Q3(b):** Find P(A|B) given P(B|A)=0.84, P(A)=0.2, P(B)=0.34.

> **Answer:**
> 
> ```
> P(A|B) = P(B|A) × P(A) / P(B)
>        = 0.84 × 0.2 / 0.34
>        = 0.168 / 0.34
>        = 0.4941...
>        ≈ 0.494
> ```

---

**Q4(a):** Is `S: (P ∨ Q) ⇒ (P ∧ Q)` satisfiable, contradictory, or valid?

> **Answer:**
> 
> | P | Q | P∨Q | P∧Q | (P∨Q)⇒(P∧Q) |
> |---|---|-----|-----|--------------|
> | T | T |  T  |  T  |      T       |
> | T | F |  T  |  F  |      F       |
> | F | T |  T  |  F  |      F       |
> | F | F |  F  |  F  |      T       |
> 
> Not always T, not always F → **Satisfiable** (but not valid, not contradictory)

---

**Q4(b):** Find MGU (Most General Unifier) for the sets.

> **Answer (general method):**
> 
> **Example set:** `{P(f(x), g(y)), P(f(a), g(b))}`
> 
> Unification algorithm:
> 1. Compare `f(x)` and `f(a)` → substitute `{x/a}`
> 2. Compare `g(y)` and `g(b)` → substitute `{y/b}`
> 3. MGU = `{x/a, y/b}`
> 
> **Result:** `P(f(a), g(b))`

---

**Q4(c):** Give PEAS Description for a Taxi Driver Agent.

> **Answer:**
> 
> | Component | Details |
> |-----------|---------|
> | **Performance** | Safe driving, fuel efficiency, trip time, passenger comfort, profitability |
> | **Environment** | Roads, traffic lights, pedestrians, other vehicles, weather, GPS map |
> | **Actuators** | Steering wheel, accelerator, brakes, turn signals, horn |
> | **Sensors** | GPS, cameras, speedometer, fuel gauge, LIDAR, passenger input |

---

**Q5(a):** When is a search admissible? Explain with A*.

> **Answer:**  
> A search algorithm is **admissible** if it always finds the **optimal (lowest cost) path** to the goal.  
> 
> For A* to be admissible, the heuristic h(n) must be **admissible** — it must **never overestimate** the true cost to reach the goal.
> 
> **Example:**  
> In a grid map, the **Euclidean distance** is admissible (straight line ≤ actual road distance).  
> The **Manhattan distance** is admissible for grid worlds with 4-directional movement.
> 
> ```
> h_admissible(n) ≤ h*(n)   where h*(n) = true cost to goal
> ```

---

**Q5(b):** What is a Horn Clause? Give an example.

> **Answer:**  
> A **Horn Clause** is a disjunction of literals with **at most one positive literal**.
> 
> Forms:
> - `A ← B₁ ∧ B₂ ∧ ... ∧ Bₙ` (rule: head ← body)
> - `A ←` (fact: just head)
> - `← B₁ ∧ ... ∧ Bₙ` (goal/query: no head)
> 
> ```prolog
> % Horn Clause examples in Prolog:
> mortal(X) :- human(X).      % Rule
> human(socrates).             % Fact
> ?- mortal(socrates).         % Goal/Query
> ```
> 
> PROLOG is based entirely on Horn Clauses — this is why it's efficient for automated reasoning.

---

**Q5(c):** Solve the cryptarithmetic problem using constraint satisfaction.

> **Answer (SEND + MORE = MONEY):**
> 
> Variables: S, E, N, D, M, O, R, Y ∈ {0–9}, all different. S≠0, M≠0.
> 
> Solution: **S=9, E=5, N=6, D=7, M=1, O=0, R=8, Y=2**
> ```
>   9567
> + 1085
> ------
>  10652
> ```
> 
> CSP approach:
> 1. Set domain {0-9} for each variable
> 2. Apply constraints: all-diff, leading digits ≠ 0
> 3. Propagate column-by-column with carry variables

---

**Q6(b):** Express as a Semantic Network: "Company ABC has departments Sales, Admin, Programming. Joe manages Programming. Bill and Sue are programmers. Sue is married to Sam who edits for Prentice Hall."

> **Answer:**
> 
> ```
> [CompanyABC] ──HAS──> [Sales]
>              ──HAS──> [Administration]
>              ──HAS──> [Programming]
> 
> [Joe] ──MANAGES──> [Programming]
> [Bill] ──IS-A──> [Programmer] ──PART-OF──> [Programming]
> [Sue]  ──IS-A──> [Programmer] ──PART-OF──> [Programming]
> 
> [Sue] ──MARRIED-TO──> [Sam]
> [Sam] ──WORKS-FOR──> [Prentice Hall]
> [Sam] ──IS-A──> [Editor]
> ```

---

**Q7(b):** Translate to clausal form and prove `supports(book, cup)` using resolution.

Given:
- A1: If x is on top of y, then y supports x.
- A2: If x is above y and touching, then x is on top of y.
- A3: cup is above book.
- A4: cup is touching book.

> **Answer:**
> 
> **Step 1 — Convert to FOPL:**
> ```
> A1: on_top(x,y) → supports(y,x)
> A2: above(x,y) ∧ touching(x,y) → on_top(x,y)
> A3: above(cup, book)
> A4: touching(cup, book)
> ```
> 
> **Step 2 — Clausal form:**
> ```
> C1: {¬on_top(x,y), supports(y,x)}
> C2: {¬above(x,y), ¬touching(x,y), on_top(x,y)}
> C3: {above(cup, book)}
> C4: {touching(cup, book)}
> ```
> 
> **Step 3 — Resolve:**
> - From C3 + C2 (x=cup, y=book): `{¬touching(cup,book), on_top(cup,book)}`
> - From above + C4: `{on_top(cup, book)}`
> - From `on_top(cup,book)` + C1 (x=cup, y=book): `{supports(book, cup)}` ✓

---

**Q8(a):** Based on a parse tree (S→NP VP, VP→V NP, etc.), draw the corresponding RTN.

> **Answer:**
> 
> ```
> RTN for S:
> ──○──[NP]──○──[VP]──○──
> 
> RTN for NP:
> ──○──[DET]──○──[N]──○──
> 
> RTN for VP:
> ──○──[V]──○──[NP]──○──
>    │                  │
>    └──[V]──○──[PP]───┘  (alternate: V PP)
> 
> RTN for PP:
> ──○──[PREP]──○──[NP]──○──
> ```
> 
> RTNs are like finite automata, but arcs can **call other networks** (recursive — hence "recursive transition nets").

---

**Q8(b):** Draw the block diagram of a learning agent and explain its working.

> **Answer:**
> 
> ```
> ┌────────────────────────────────────────────┐
> │                LEARNING AGENT              │
> │                                            │
> │  Environment                               │
> │      │ percepts                            │
> │      ▼                                     │
> │  ┌─────────┐      ┌──────────────┐         │
> │  │ CRITIC  │◄────►│  PERFORMANCE │         │
> │  │         │      │   STANDARD   │         │
> │  └─────────┘      └──────────────┘         │
> │      │ feedback                            │
> │      ▼                                     │
> │  ┌─────────┐      ┌──────────────┐         │
> │  │LEARNING │─────►│  PERFORMANCE │         │
> │  │ ELEMENT │      │   ELEMENT    │         │
> │  └─────────┘      └──────────────┘         │
> │                        │ actions           │
> │  ┌─────────────┐        ▼                  │
> │  │  PROBLEM    │◄──────────────────────    │
> │  │  GENERATOR  │    Environment            │
> │  └─────────────┘                           │
> └────────────────────────────────────────────┘
> ```
> 
> - **Performance Element:** Takes percepts, decides actions
> - **Critic:** Evaluates performance using a standard
> - **Learning Element:** Improves performance element based on feedback
> - **Problem Generator:** Suggests exploratory actions to learn from

---

## 📄 2022 Question Paper

> **Source:** Official B.Sc. (H) CS, Semester VI, University of Delhi (Code: 1108)

### Section A — Compulsory

**Q1(a):** Describe (a) Heuristic Function (b) Software Agent.

> **Answer:**
> 
> **(a) Heuristic Function:**  
> A heuristic function `h(n)` estimates the cost of the cheapest path from node n to the goal. It uses problem-specific knowledge to guide search. A heuristic is **admissible** if h(n) ≤ h*(n) (never overestimates).  
> **Example:** In 8-puzzle, h = number of misplaced tiles.
> 
> **(b) Software Agent:**  
> A software agent is a program that perceives its environment (via data inputs) and acts upon it (via outputs) to achieve goals. Examples: web crawlers, recommendation engines, chatbots.

---

**Q1(b):** Write a CFG that can accept: "Ram hit the ball".

> **Answer:**
> 
> ```
> S  → NP VP
> NP → ProperNoun | DET N
> VP → V NP
> 
> ProperNoun → Ram
> DET → the
> N   → ball
> V   → hit
> 
> Parse:
> S → NP VP
>   → "Ram" + VP
>   → "Ram" + V NP
>   → "Ram" + "hit" + DET N
>   → "Ram hit the ball" ✓
> ```

---

**Q1(d):** Find MGU for `{PARENTS(x, FATHER(x), MOTHER(bill)), PARENTS(bill, FATHER(bill), y)}`.

> **Answer:**
> 
> Unify element by element:
> 1. `x` vs `bill` → `{x/bill}`
> 2. `FATHER(x)` vs `FATHER(bill)` → After x=bill: `FATHER(bill)` = `FATHER(bill)` ✓
> 3. `MOTHER(bill)` vs `y` → `{y/MOTHER(bill)}`
> 
> **MGU = {x/bill, y/MOTHER(bill)}**
> 
> Unified result: `PARENTS(bill, FATHER(bill), MOTHER(bill))`

---

**Q1(e):** Express as Conceptual Dependency: "Sohan gave Tina a box of chocolate".

> **Answer:**
> ```
> Sohan ──ATRANS──> box-of-chocolate
>        Actor:   Sohan
>        Object:  box-of-chocolate
>        From:    Sohan
>        To:      Tina
> ```

---

**Q1(j):** Why should h(n) in A* always underestimate? Give reason and example.

> **Answer:**  
> If h(n) **overestimates**, A* may skip the true optimal path, making it **non-optimal**.
> 
> **Example:**
> ```
> True optimal path cost = 10
> Heuristic says h(n) = 15 for a node on optimal path
> A* skips this node → finds suboptimal path of cost 12
> ```
> 
> **Underestimating (admissible) h(n)** ensures every node that could be on the optimal path remains in consideration. A* will always find the shortest path when h is admissible.

---

**Q1(k):** What is non-monotonic reasoning? Give an example.

> **Answer:**  
> In **non-monotonic reasoning**, adding new information can **invalidate** previously drawn conclusions — unlike classical logic where adding facts only adds conclusions.
> 
> **Example:**
> ```
> Fact 1: Birds fly.
> Fact 2: Tweety is a bird.
> Conclusion: Tweety flies. ✓
> 
> Add Fact 3: Tweety is a penguin.
> New Conclusion: Tweety does NOT fly. ✗ (previous conclusion retracted)
> ```
> 
> Used in: default reasoning, belief revision, closed world assumption.

---

**Q2(a):** Differentiate between partially and fully observable task environments. Give examples.

> **Answer:**
> 
> | | Fully Observable | Partially Observable |
> |-|-----------------|---------------------|
> | **Definition** | Agent has complete access to environment state | Agent sees only part of the environment |
> | **Example** | Chess (all pieces visible) | Poker (opponent's cards hidden) |
> | **Example** | Vacuum cleaner (knows all dirt) | Self-driving car in fog |
> | **Complexity** | Lower | Higher (needs internal state model) |

---

**Q4(a):** Create a script for shopping in a supermarket.

> **Answer:**
> 
> ```
> Script: SUPERMARKET-SHOPPING
>   Roles: Customer, Cashier, Security Guard
>   Props: Basket, Shopping list, Items, Cart, Money, Receipt
>   Entry Conditions: Customer has money, Store is open
>   
>   Scene 1 — Entry:
>     Customer enters supermarket
>     Customer picks up basket or cart
>     
>   Scene 2 — Shopping:
>     Customer follows list
>     Customer picks items from shelves
>     Customer checks prices
>     Customer places items in basket
>     
>   Scene 3 — Checkout:
>     Customer goes to billing counter
>     Cashier scans items
>     Cashier announces total
>     Customer pays (cash/card)
>     Cashier gives receipt and change
>     
>   Scene 4 — Exit:
>     Customer packs bags
>     Security checks receipt at exit
>     Customer leaves
>     
>   Exit Conditions: Customer has goods + receipt, Store received payment
> ```

---

**Q7(a):** Convert axioms to clausal form and prove "Snow" using resolution.

Given: `January`, `Clouds`, `Cold ∧ Precipitation → Snow`, `January → Cold`, `Clouds → Precipitation`

> **Answer:**
> 
> **Clausal form:**
> ```
> C1: {January}
> C2: {Clouds}
> C3: {¬Cold, ¬Precipitation, Snow}
> C4: {¬January, Cold}
> C5: {¬Clouds, Precipitation}
> ```
> 
> **Resolution proof:**
> ```
> Step 1: Resolve C1 + C4 → {Cold}
> Step 2: Resolve C2 + C5 → {Precipitation}
> Step 3: Resolve {Cold} + C3 → {¬Precipitation, Snow}
> Step 4: Resolve {Precipitation} + {¬Precipitation, Snow} → {Snow} ✓
> ```

---

**Q8(a):** Solve the cryptarithmetic using CSP: `CROSS + ROADS = DANGER`

> **Answer:**  
> Variables: C,R,O,S,A,D,N,G,E ∈ {0-9}, all distinct. C≠0, R≠0, D≠0.
> 
> General approach: Use constraint propagation + backtracking.
> 
> Assign column by column with carry:
> ```
>   CROSS
> + ROADS
> -------
>  DANGER
> ```
> One known solution: C=9, R=1, O=2, S=8, A=5, D=0... (work through with column carries)

---

## 📄 2021 Question Paper

> **Source:** B.Sc. (H) CS, Semester VI, University of Delhi (Code: 2211)

### Section A — Compulsory

**Q1(a):** Define Artificial Intelligence. Distinguish between Strong AI and Weak AI.

> **Answer:**  
> **Artificial Intelligence** is the study and development of intelligent machines that can perform tasks that typically require human intelligence — reasoning, learning, perception, language understanding.
> 
> | | Weak/Narrow AI | Strong AI |
> |-|----------------|-----------|
> | Scope | Specific domain | Any cognitive task |
> | Example | Google Translate | Human-level AI (theoretical) |
> | Self-aware | No | Yes (theoretical) |
> | Status | Widely achieved | Not yet achieved |

---

**Q1(b):** What are the PEAS components? Give PEAS for a Chess-Playing Agent.

> **Answer:**
> 
> | Component | Chess Agent |
> |-----------|------------|
> | **Performance** | Win rate, draw rate, piece advantage |
> | **Environment** | Chessboard, opponent's moves |
> | **Actuators** | Move selection (output to display) |
> | **Sensors** | Current board state (input) |
> 
> Environment is **fully observable, deterministic, sequential, static, discrete, two-agent**.

---

**Q1(c):** What is a production system? Give an example.

> **Answer:**  
> A production system consists of:
> - **Working Memory** — current facts/state
> - **Production Rules** — IF-THEN rules
> - **Inference Engine** — selects and fires rules
> 
> ```
> Rule 1: IF fever > 100°F AND cough THEN flu_suspected
> Rule 2: IF flu_suspected AND body_ache THEN diagnose_flu
> Rule 3: IF diagnose_flu THEN prescribe_antiviral
> 
> Working Memory: {fever=102, cough=true, body_ache=true}
> Result: prescribe_antiviral (by chaining rules 1→2→3)
> ```

---

**Q1(d):** Explain the concept of constraint satisfaction with an example.

> **Answer:**  
> CSP involves finding values for variables satisfying all constraints.
> 
> **Example — N-Queens (4×4):**
> - Variables: Q1, Q2, Q3, Q4 (column of queen in each row)
> - Domain: {1, 2, 3, 4}
> - Constraints: No two queens in same column, row, or diagonal
> 
> Solution: `Q1=2, Q2=4, Q3=1, Q4=3`
> ```
> . Q . .
> . . . Q
> Q . . .
> . . Q .
> ```

---

**Q2:** Explain BFS with an example. Trace BFS on the following graph from A to F.

> **Answer (general trace):**
> 
> Given graph: `A→{B,C}, B→{D,E}, C→{F}`
> 
> ```
> Queue:   [A]
> Visit A: Queue=[B,C], Visited={A}
> Visit B: Queue=[C,D,E], Visited={A,B}
> Visit C: Queue=[D,E,F], Visited={A,B,C}
> Visit D: Queue=[E,F], Visited={A,B,C,D}
> Visit E: Queue=[F], Visited={A,B,C,D,E}
> Visit F: GOAL FOUND!
> Path: A → C → F
> ```

---

**Q3:** Explain A* algorithm. Trace A* on a sample graph.

*(See 2024 Q3(a) / 2023 Q5(a) for full answer)*

---

**Q4:** What is Prolog? Write Prolog programs for:
(a) Finding if a number is prime  
(b) Fibonacci series

> **Answer:**
> 
> **(a) Prime number in Prolog:**
> ```prolog
> is_prime(2).
> is_prime(3).
> is_prime(N) :-
>     N > 3,
>     N mod 2 =\= 0,
>     \+ has_factor(N, 3).
> 
> has_factor(N, F) :-
>     N mod F =:= 0.
> has_factor(N, F) :-
>     F * F < N,
>     F2 is F + 2,
>     has_factor(N, F2).
> 
> ?- is_prime(7).   % true
> ?- is_prime(8).   % false
> ```
> 
> **(b) Fibonacci in Prolog:**
> ```prolog
> fib(0, 0).
> fib(1, 1).
> fib(N, F) :-
>     N > 1,
>     N1 is N - 1, N2 is N - 2,
>     fib(N1, F1), fib(N2, F2),
>     F is F1 + F2.
> 
> ?- fib(7, F).
> F = 13.
> ```

---

**Q5:** Explain First-Order Predicate Logic with examples. Convert sentences to FOPL.

> **Answer:**
> 
> FOPL sentences:
> 1. "All humans are mortal" → `∀x Human(x) → Mortal(x)`
> 2. "Some students are smart" → `∃x Student(x) ∧ Smart(x)`
> 3. "No robot has feelings" → `∀x Robot(x) → ¬HasFeelings(x)`
> 4. "Every parent loves their child" → `∀x ∀y Parent(x,y) → Loves(x,y)`
> 
> **In Prolog:**
> ```prolog
> human(socrates). human(plato).
> mortal(X) :- human(X).
> 
> ?- mortal(plato).
> true.
> ```

---

## 📄 2020 Question Paper

> **Source:** B.Sc. (H) CS, Semester VI, University of Delhi

### Section A — Compulsory

**Q1(a):** What is the Turing Test? Why is it significant?

> **Answer:**  
> Proposed by Alan Turing in 1950 in his paper *"Computing Machinery and Intelligence"*, the **Turing Test** checks if a machine can exhibit intelligent behaviour indistinguishable from a human.
> 
> **Setup:**
> ```
> Human interrogator ──── types questions ────> [Contestant]
>                    <─── reads responses ────  (Human OR Machine?)
> ```
> If interrogator cannot reliably identify the machine, the machine is considered intelligent.
> 
> **Significance:** Provides an **operational definition** of intelligence. Still debated — critics cite the Chinese Room argument (Searle, 1980).

---

**Q1(b):** What is meant by "task environment"? Explain its properties.

> **Answer:**  
> The **task environment** is the problem to which an agent is the solution. Described by PEAS.
> 
> **Properties of Task Environments:**
> 
> | Property | Values | Example |
> |----------|--------|---------|
> | Observability | Fully / Partially / Unobservable | Chess vs Poker |
> | Agents | Single / Multi-agent | Vacuum vs Chess |
> | Determinism | Deterministic / Stochastic | Chess vs Backgammon |
> | Episodic | Episodic / Sequential | Image classifier vs Chess |
> | Dynamics | Static / Dynamic / Semidynamic | Crossword vs Taxi |
> | Time | Discrete / Continuous | Chess vs Driving |

---

**Q2:** Describe Depth-First Search and Breadth-First Search. When would you use each?

*(See 2023 Q1(f) comparative table + 2025 Q2(a) Python code above)*

---

**Q3:** Explain the A* algorithm. What properties must a heuristic have for A* to be optimal?

> **Answer:**
> 
> For A* to be **optimal**, h(n) must be:
> 1. **Admissible:** h(n) ≤ h*(n) — never overestimates
> 2. **Consistent (Monotonic):** h(n) ≤ c(n,n') + h(n') — triangle inequality
> 
> **Consistency ⟹ Admissibility** (but not vice versa)
> 
> With consistent h, A* never re-expands nodes — more efficient.

---

**Q4:** Explain PROLOG with examples of list operations.

> **Answer:**
> 
> **List operations in Prolog:**
> 
> ```prolog
> % Length of list
> length([], 0).
> length([_|T], N) :- length(T, N1), N is N1 + 1.
> 
> % Sum of list elements
> sum([], 0).
> sum([H|T], S) :- sum(T, S1), S is S1 + H.
> 
> % Delete element from list
> delete(X, [X|T], T).
> delete(X, [H|T], [H|R]) :- X \= H, delete(X, T, R).
> 
> % Test
> ?- length([a,b,c,d], N).   % N = 4
> ?- sum([1,2,3,4,5], S).    % S = 15
> ```

---

**Q5:** Explain Propositional Logic. What are its limitations?

> **Answer:**
> 
> **Propositional Logic:** Uses atomic propositions (P, Q, R) and connectives (¬, ∧, ∨, →, ↔).
> 
> **Limitations:**
> 1. **Cannot represent objects and relationships** — "All students are hardworking" needs FOPL
> 2. **No quantifiers** — can't express ∀ (for all) or ∃ (there exists)
> 3. **Limited expressiveness** — can't distinguish between "some" and "all"
> 4. **Propositional explosion** — need separate proposition for each fact
> 
> **FOPL solves these** by adding predicates, constants, variables, and quantifiers.

---

**Q6:** What is Knowledge Representation? Why is it important? Explain semantic nets.

> **Answer:**
> 
> **Knowledge Representation (KR)** is the field of AI dedicated to representing information about the world in a form that a computer system can utilise to solve complex tasks.
> 
> **Importance:**
> - Enables reasoning and inference
> - Supports natural language understanding
> - Foundation for expert systems
> 
> *(See Semantic Nets answer in 2023 Q4(a) above)*

---

**Q7:** Explain Natural Language Processing and parsing techniques.

> **Answer:**
> 
> **NLP Pipeline:**
> ```
> Input Text → Tokenisation → POS Tagging → Parsing → Semantic Analysis → Output
> ```
> 
> **Parsing Techniques:**
> 
> **(1) Top-Down Parsing:**
> - Starts from S (start symbol), expands until input is matched
> - Predictive: uses lookahead
> 
> **(2) Bottom-Up Parsing:**
> - Starts from input tokens, reduces to S
> - Shift-Reduce parsing
> 
> **(3) Chart Parsing (Earley Algorithm):**
> - Efficient O(n³) CFG parser
> - Handles ambiguous grammars
> 
> **PROLOG DCG Example:**
> ```prolog
> s --> np, vp.
> np --> [the], n.
> vp --> v, np.
> n --> [dog].  n --> [cat].
> v --> [chased].
> 
> ?- phrase(s, [the, dog, chased, the, cat]).
> true.
> ```

---

## 📊 Topic-wise Frequency Analysis

> Track which topics appear most often to prioritise your exam preparation.

| Topic | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | **Total** |
|-------|------|------|------|------|------|------|-----------|
| Rational Agent / PEAS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | **6** |
| A* Algorithm | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | **6** |
| BFS / DFS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | **6** |
| Prolog Programs | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | **6** |
| Resolution / Clausal Form | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | **6** |
| Min-Max / Alpha-Beta | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | **6** |
| CNF / Propositional Logic | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | **6** |
| Hill Climbing (limitations) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | **6** |
| Unification / MGU | — | ✓ | ✓ | ✓ | ✓ | ✓ | **5** |
| Semantic Nets / Frames | ✓ | ✓ | ✓ | ✓ | ✓ | — | **5** |
| Conceptual Dependency | — | — | ✓ | ✓ | ✓ | ✓ | **4** |
| CSP / Cryptarithmetic | ✓ | ✓ | ✓ | ✓ | — | — | **4** |
| Bayesian Probability | — | — | ✓ | ✓ | ✓ | — | **3** |
| Water Jug Problem | ✓ | ✓ | — | ✓ | ✓ | — | **4** |
| Parse Tree / CFG | ✓ | ✓ | ✓ | ✓ | — | ✓ | **5** |
| Chomsky Hierarchy | ✓ | — | — | ✓ | — | ✓ | **3** |
| RTN | — | — | ✓ | ✓ | — | — | **2** |
| Horn Clause | — | — | ✓ | ✓ | — | — | **2** |
| Learning Agent | — | — | — | ✓ | — | — | **1** |

---

## ⭐ Most Important Topics (Appear in 5–6 Years)

1. **Rational Agent + PEAS** — Always in Q1
2. **A* Algorithm** — Always in Q2-Q8 (long question)
3. **BFS / DFS** — Comparison always in Q1 or Q2
4. **Prolog Programs** — List operations, family tree, search
5. **Resolution Proof** — Clause conversion + refutation
6. **Min-Max Algorithm** — Two-ply tree always given
7. **CNF Conversion** — Always in Q1 (short answer)
8. **Hill Climbing Limitations** — Always in Q1 or Q2
9. **Unification / MGU** — Q1 calculation type
10. **Semantic Nets / Frames** — Long answer Q3-Q7

---

## 📝 Exam Strategy

```
Section A (Q1) — Attempt ALL 10-12 short parts:
  • Each part ≈ 2-3 marks
  • Cover: Logic, Prolog, MinMax tree, PEAS, DFS/BFS comparison,
    CNF conversion, parse tree, Chomsky hierarchy

Section B — Attempt 4 of Q2–Q8:
  • Q2: Search algorithms (almost always — safe choice)
  • Q3: A* or Prolog programs (always present)
  • Q7: Resolution + Logic proofs (always present)
  • Choose from: Frames/Scripts, NLP, Water Jug, CSP
```

---

*Compiled from official University of Delhi B.Sc. (H) CS Semester VI question papers 2020–2025.*  
*Paper codes: 2211 (2021), 1108 (2022), 4506 (2023), 4506 (2024)*

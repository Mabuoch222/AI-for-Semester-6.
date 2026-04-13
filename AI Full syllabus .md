# 🤖 Artificial Intelligence — Complete Syllabus Guide (Sem 6)

> **Course:** DSC16/GE6e/DSE — Artificial Intelligence  
> **Credits:** 4 (3 Lecture + 0 Tutorial + 1 Practical)  
> **Pre-requisite:** Programming in C++ / Python / OOP with Python

---

## 📚 Table of Contents

- [Unit 1 — Introduction to AI](#unit-1--introduction-to-ai-6-hours)
- [Unit 2 — Problem Solving & Searching Techniques](#unit-2--problem-solving-and-searching-techniques-12-hours)
- [Unit 3 — Knowledge Representation](#unit-3--knowledge-representation-16-hours)
- [Unit 4 — Understanding Natural Languages](#unit-4--understanding-natural-languages-8-hours)
- [Unit 5 — AI: The Present and Future](#unit-5--ai-the-present-and-future-3-hours)
- [Practical List](#-practical-list)
- [Recommended Books](#-recommended-books)

---

## Unit 1 — Introduction to AI (6 Hours)

### 1.1 What is Artificial Intelligence?

AI is the simulation of human intelligence in machines. It enables computers to **learn**, **reason**, **perceive**, **plan**, and **understand language**.

**Example:** A spam filter that learns to classify "Buy now!" emails as spam — without being explicitly programmed with rules.

---

### 1.2 The Turing Test

Proposed by **Alan Turing (1950)**, the Turing Test checks if a machine can exhibit intelligent behaviour indistinguishable from a human.

**Setup:**

```
Human Interrogator ──asks questions──▶ [Machine / Human]
                   ◀──reads answers──
```

If the interrogator cannot tell whether the responses are from a human or a machine, the machine **passes** the Turing Test.

**Example:**

```
Interrogator: "What do you feel when you hear sad music?"
Machine:      "I feel a sense of melancholy and think of distant memories."
```

---

### 1.3 Types of AI

| Type | Description | Example |
|------|-------------|---------|
| **Weak AI (Narrow AI)** | Designed for a specific task | Siri, Chess engines |
| **Strong AI (AGI)** | General human-like intelligence | Hypothetical — not yet achieved |
| **Artificial General Intelligence (AGI)** | Can learn and reason across any domain | Research goal |
| **Super AI** | Surpasses human intelligence in all areas | Theoretical |

---

### 1.4 Rational Agent Approach

An **agent** is anything that **perceives** its environment via sensors and **acts** upon it via actuators.

```
Environment ──percepts──▶ [AGENT] ──actions──▶ Environment
```

A **rational agent** chooses actions that maximise its **performance measure** based on its percepts and knowledge.

**Example — Thermostat Agent:**

```python
def thermostat_agent(current_temp, target_temp):
    if current_temp < target_temp:
        return "TURN_ON_HEATER"
    elif current_temp > target_temp:
        return "TURN_ON_COOLER"
    else:
        return "DO_NOTHING"
```

---

### 1.5 Intelligent Agents: Structure & PEAS

Every agent is described using **PEAS**:

| Component | Description | Example (Self-Driving Car) |
|-----------|-------------|---------------------------|
| **P**erformance | What success looks like | Safety, speed, fuel efficiency |
| **E**nvironment | Where the agent operates | Roads, traffic, weather |
| **A**ctuators | How the agent acts | Steering, brakes, accelerator |
| **S**ensors | How the agent perceives | Cameras, GPS, LIDAR |

**Types of Agents:**

- **Simple Reflex Agent** — Acts on current percept only
- **Model-Based Reflex Agent** — Maintains internal state
- **Goal-Based Agent** — Acts to achieve goals
- **Utility-Based Agent** — Maximises a utility function
- **Learning Agent** — Improves over time

---

## Unit 2 — Problem Solving and Searching Techniques (12 Hours)

### 2.1 Problem Characteristics

A problem in AI is defined by:
- **Initial State** — starting point
- **Goal State** — desired outcome
- **Actions** — possible moves
- **Path Cost** — cost to reach goal

**Example — 8-Puzzle:**

```
Initial State:       Goal State:
┌─────────────┐     ┌─────────────┐
│  2 │  8 │  3│     │  1 │  2 │  3│
│  1 │  6 │  4│     │  8 │    │  4│
│  7 │    │  5│     │  7 │  6 │  5│
└─────────────┘     └─────────────┘
```

---

### 2.2 Production Systems

A **production system** consists of:
- **Working Memory** — current state
- **Production Rules** — IF condition THEN action
- **Control Strategy** — which rule to fire

**Example:**

```prolog
% Production rule
if temperature > 100 then action = "boil_water".
if temperature < 0  then action = "freeze_water".
```

---

### 2.3 Breadth-First Search (BFS)

Explores nodes **level by level** using a queue. Guarantees shortest path (unweighted).

```
Tree:         A
            /   \
           B     C
          / \   / \
         D   E F   G

BFS Order: A → B → C → D → E → F → G
```

**Python Example:**

```python
from collections import deque

def bfs(graph, start, goal):
    queue = deque([[start]])
    visited = set()

    while queue:
        path = queue.popleft()
        node = path[-1]

        if node == goal:
            return path

        if node not in visited:
            visited.add(node)
            for neighbor in graph[node]:
                queue.append(path + [neighbor])

graph = {'A': ['B', 'C'], 'B': ['D', 'E'], 'C': ['F', 'G'],
         'D': [], 'E': [], 'F': [], 'G': []}
print(bfs(graph, 'A', 'G'))  # ['A', 'C', 'G']
```

---

### 2.4 Depth-First Search (DFS)

Explores nodes **as deep as possible** using a stack. Uses less memory than BFS but may not find shortest path.

**Python Example:**

```python
def dfs(graph, start, goal, visited=None):
    if visited is None:
        visited = set()
    visited.add(start)

    if start == goal:
        return [start]

    for neighbor in graph[start]:
        if neighbor not in visited:
            path = dfs(graph, neighbor, goal, visited)
            if path:
                return [start] + path
    return None
```

---

### 2.5 Hill Climbing

A **greedy local search** that always moves towards higher value (like climbing a hill).

**Variations:**
- **Simple Hill Climbing** — first better neighbour
- **Steepest Ascent** — best neighbour each step
- **Stochastic** — random selection among better neighbours

**Problem:** Can get stuck at **local maxima**.

```
Value
  |       /\      ← Local Maximum (stuck here)
  |      /  \        /\  ← Global Maximum (goal)
  |     /    \      /  \
  |____/      \____/    \____
                     State →
```

**Python Example:**

```python
def hill_climbing(problem, initial_state):
    current = initial_state
    while True:
        neighbors = problem.get_neighbors(current)
        best = max(neighbors, key=problem.value)
        if problem.value(best) <= problem.value(current):
            return current   # stuck at local max
        current = best
```

---

### 2.6 Best-First Search

Uses a **priority queue** ordered by a **heuristic function h(n)** — an estimate of distance to goal.

```python
import heapq

def best_first_search(graph, start, goal, heuristic):
    pq = [(heuristic[start], start, [start])]
    visited = set()

    while pq:
        (h, node, path) = heapq.heappop(pq)
        if node == goal:
            return path
        if node not in visited:
            visited.add(node)
            for neighbor, cost in graph[node]:
                if neighbor not in visited:
                    heapq.heappush(pq, (heuristic[neighbor], neighbor, path + [neighbor]))
```

---

### 2.7 A* Algorithm

Combines actual cost `g(n)` and heuristic `h(n)`:

```
f(n) = g(n) + h(n)
```

- `g(n)` = cost from start to node n
- `h(n)` = estimated cost from n to goal
- `f(n)` = total estimated cost

**A* is optimal and complete** if h(n) is **admissible** (never overestimates).

**Example:**

```
Start: A,  Goal: D
Edges: A→B(1), A→C(4), B→C(2), B→D(5), C→D(1)
h(n):  A=7, B=6, C=2, D=0

Step 1: Expand A → f(B)=1+6=7, f(C)=4+2=6
Step 2: Expand C → f(D)=5+0=5
Step 3: Goal reached! Path: A→B→C→D, cost=4
```

---

### 2.8 Constraint Satisfaction Problem (CSP)

Find values for variables that satisfy all constraints.

**Example — Map Colouring:**

```python
# Variables: WA, NT, SA, Q, NSW, V, T
# Domain: {Red, Green, Blue}
# Constraint: Adjacent regions must have different colours

constraints = {
    ('WA', 'NT'), ('WA', 'SA'),
    ('NT', 'SA'), ('NT', 'Q'),
    ('SA', 'Q'), ('SA', 'NSW'), ('SA', 'V'),
    ('Q', 'NSW'), ('NSW', 'V')
}
```

---

### 2.9 Means-End Analysis

Reduce the **difference** between the current state and the goal state by applying **operators**.

**Example:**

```
Current State: Robot at position A, box at B
Goal State:    Box at position C

Step 1: Move robot to B (reduce distance to box)
Step 2: Pick up box
Step 3: Move robot+box to C (reduce distance to goal)
```

---

### 2.10 Game Playing: Min-Max Algorithm

Used in **two-player zero-sum games**. MAX player maximises score; MIN player minimises it.

```
         MAX
        /    \
      MIN    MIN
     /  \   /  \
    3    5 2    9

MAX chooses: max(5, 2) = 5
MIN on left: min(3, 5) = 3? → MAX gets 5
```

**Python Example:**

```python
def minimax(node, depth, is_maximizing):
    if depth == 0 or is_terminal(node):
        return evaluate(node)

    if is_maximizing:
        best = float('-inf')
        for child in get_children(node):
            best = max(best, minimax(child, depth - 1, False))
        return best
    else:
        best = float('inf')
        for child in get_children(node):
            best = min(best, minimax(child, depth - 1, True))
        return best
```

---

### 2.11 Alpha-Beta Pruning

**Optimisation of Min-Max** — prunes branches that can't affect the final decision.

```
alpha = best value MAX can guarantee
beta  = best value MIN can guarantee

Prune when: alpha >= beta
```

**Example:** In a tree with depth 4, alpha-beta can reduce nodes evaluated from **O(b^d)** to **O(b^(d/2))**.

---

## Unit 3 — Knowledge Representation (16 Hours)

### 3.1 Propositional Logic

Uses symbols (P, Q, R) and logical connectives.

| Symbol | Meaning | Example |
|--------|---------|---------|
| `¬` | NOT | ¬P — "Not raining" |
| `∧` | AND | P ∧ Q — "Raining AND cold" |
| `∨` | OR | P ∨ Q — "Raining OR snowing" |
| `→` | IMPLIES | P → Q — "Rain implies wet ground" |
| `↔` | BICONDITIONAL | P ↔ Q — "Rain iff wet" |

**Example:**

```
P = "It is raining"
Q = "I carry an umbrella"
Rule: P → Q  (If raining, carry umbrella)
Fact: P is TRUE
∴ Q is TRUE (Modus Ponens)
```

---

### 3.2 First-Order Predicate Logic (FOPL)

Extends propositional logic with **quantifiers** and **predicates**.

```prolog
% Predicates
Human(Socrates)       % Socrates is human
∀x: Human(x) → Mortal(x)   % All humans are mortal
∴ Mortal(Socrates)          % Therefore Socrates is mortal
```

**PROLOG Example:**

```prolog
human(socrates).
mortal(X) :- human(X).

?- mortal(socrates).
true.
```

---

### 3.3 Resolution Principle

A **proof technique** for first-order logic — convert to **CNF (Conjunctive Normal Form)** and resolve.

**Example:**

```
Clause 1: ¬P ∨ Q      (P → Q)
Clause 2: P
Resolve:  Q            (Modus Ponens via resolution)
```

---

### 3.4 Unification

The process of finding substitutions that make two logical expressions **identical**.

**Example:**

```prolog
f(X, b) unifies with f(a, Y)
Substitution: {X/a, Y/b}
Result: f(a, b)
```

**PROLOG:**

```prolog
?- f(X, b) = f(a, Y).
X = a, Y = b.
```

---

### 3.5 Semantic Nets

A **graphical representation** of knowledge using nodes (concepts) and edges (relationships).

```
       IS-A          HAS
Animal ──── Dog ──── Legs(4)
            │
            └── IS-A ── Poodle
```

**Example — "A dog is an animal that has 4 legs":**

```
[Poodle] --IS-A--> [Dog] --IS-A--> [Animal]
                   [Dog] --HAS-->  [4 Legs]
```

---

### 3.6 Frames

A **structured representation** of stereotyped situations. Like a record/class in programming.

**Example — Frame for "Car":**

```
FRAME: Car
  ├── AKO (A Kind Of): Vehicle
  ├── Wheels: 4
  ├── FuelType: [Petrol, Diesel, Electric]
  ├── Color: <to be filled>
  └── Speed: <to be filled>

FRAME: Tesla (instance of Car)
  ├── AKO: Car
  ├── FuelType: Electric
  ├── Color: White
  └── Speed: 250 km/h
```

---

### 3.7 Scripts

A **sequence of events** in a stereotyped situation (like a database of scenarios).

**Example — Restaurant Script:**

```
Script: RESTAURANT
  Roles: Customer, Waiter, Cook
  Track: Normal

  Scene 1 (Entering):
    Customer enters restaurant
    Customer finds a table
    Customer sits down

  Scene 2 (Ordering):
    Waiter comes to table
    Customer reads menu
    Customer orders food

  Scene 3 (Eating):
    Cook prepares food
    Waiter serves food
    Customer eats

  Scene 4 (Leaving):
    Customer asks for bill
    Customer pays
    Customer leaves
```

---

### 3.8 Production Rules

**IF-THEN** rules used in expert systems.

**Example — Medical Diagnosis:**

```prolog
% Production Rules
rule1: IF fever AND cough THEN suspect_flu.
rule2: IF suspect_flu AND body_ache THEN diagnose_flu.
rule3: IF diagnose_flu THEN prescribe_antiviral.

% Facts
fever.
cough.
body_ache.

% Inference
?- prescribe_antiviral.  % yes, by chaining rules 1→2→3
```

---

### 3.9 Introduction to PROLOG

PROLOG (PROgramming in LOGic) is based on **Horn clauses**.

**Basic Syntax:**

```prolog
% Facts
parent(tom, bob).
parent(bob, ann).

% Rules
grandparent(X, Z) :- parent(X, Y), parent(Y, Z).

% Queries
?- grandparent(tom, ann).
true.

?- grandparent(tom, Who).
Who = ann.
```

**List Operations:**

```prolog
% Append lists
conc([], L, L).
conc([H|T], L, [H|R]) :- conc(T, L, R).

?- conc([1,2], [3,4], L).
L = [1,2,3,4].

% Reverse a list
reverse([], []).
reverse([H|T], R) :- reverse(T, RT), conc(RT, [H], R).
```

---

## Unit 4 — Understanding Natural Languages (8 Hours)

### 4.1 Components of Communication

Natural Language Processing (NLP) involves multiple levels:

```
Raw Text
   │
   ▼
Phonological Analysis  (sounds)
   │
   ▼
Morphological Analysis (word structure: "running" → run + ing)
   │
   ▼
Syntactic Analysis     (grammar/parse tree)
   │
   ▼
Semantic Analysis      (meaning)
   │
   ▼
Pragmatic Analysis     (context/intent)
```

---

### 4.2 Formal vs Natural Language

| Feature | Formal Language | Natural Language |
|---------|----------------|-----------------|
| Ambiguity | None | High |
| Grammar | Strict | Flexible |
| Context | Independent | Context-dependent |
| Example | Python, SQL | English, Hindi |

**Ambiguity Example:**

```
"I saw the man with a telescope."
→ Did I use a telescope to see the man?
→ Or did I see a man who had a telescope?
```

---

### 4.3 Chomsky Hierarchy of Grammars

A classification of formal languages by generative power:

```
Type 0: Unrestricted Grammar       (most powerful — Turing machines)
  └─ Type 1: Context-Sensitive Grammar
       └─ Type 2: Context-Free Grammar (CFG) ← used in programming languages
            └─ Type 3: Regular Grammar (least powerful — finite automata)
```

| Type | Grammar | Automaton | Example |
|------|---------|-----------|---------|
| 3 | Regular | Finite Automaton | `a*b*` |
| 2 | Context-Free | Pushdown Automaton | `a^n b^n` |
| 1 | Context-Sensitive | Linear Bounded Automaton | `a^n b^n c^n` |
| 0 | Unrestricted | Turing Machine | Any computable language |

---

### 4.4 Context-Free Grammar (CFG)

Grammar rules of the form: **A → α** where A is a non-terminal.

**Example — English Sentence:**

```
S  → NP VP
NP → Det N
VP → V NP
Det → "the" | "a"
N  → "dog" | "cat" | "ball"
V  → "chased" | "ate"

Parse: "the dog chased a cat"
S
├── NP: "the dog"
│    ├── Det: "the"
│    └── N:   "dog"
└── VP: "chased a cat"
     ├── V:  "chased"
     └── NP: "a cat"
          ├── Det: "a"
          └── N:   "cat"
```

---

### 4.5 Parsing Techniques

**Top-Down Parsing:** Start from S, expand until you match input.  
**Bottom-Up Parsing:** Start from tokens, reduce to S.

**PROLOG Parse Tree Example:**

```prolog
% Grammar rules in Prolog (DCG notation)
s --> np, vp.
np --> det, n.
vp --> v, np.
det --> [the].
det --> [a].
n --> [dog].
n --> [cat].
v --> [chased].

?- s([the, dog, chased, a, cat], []).
true.
```

---

### 4.6 Recursive Transition Networks (RTNs)

A **network of nodes and arcs** for parsing. Each arc is labeled with a word, category, or sub-network call.

```
RTN for NP:
  ──[Det]──▶──[N]──▶ (done)
                │
            (optional Adj)

Example: "the big red ball"
  Det="the" → Adj="big" → Adj="red" → N="ball"
```

---

## Unit 5 — AI: The Present and Future (3 Hours)

### 5.1 Symbolic AI vs Data-Driven AI

| | Symbolic AI | Data-Driven AI |
|--|-------------|----------------|
| **Basis** | Logic, rules, knowledge | Statistics, patterns |
| **Example** | Expert Systems, PROLOG | Neural Networks, GPT |
| **Strength** | Explainable, precise | Flexible, scalable |
| **Weakness** | Brittle, hard to scale | Black-box, needs data |

---

### 5.2 Machine Learning (ML)

ML enables systems to **learn from data** without being explicitly programmed.

**Types:**

```
Machine Learning
├── Supervised Learning      (labelled data: spam detection)
├── Unsupervised Learning    (unlabelled data: clustering)
└── Reinforcement Learning   (reward-based: game playing)
```

**Simple ML Example — Linear Regression:**

```python
from sklearn.linear_model import LinearRegression
import numpy as np

X = np.array([[1], [2], [3], [4], [5]])  # hours studied
y = np.array([50, 60, 70, 80, 90])       # marks

model = LinearRegression()
model.fit(X, y)
print(model.predict([[6]]))  # Predict for 6 hours → [100]
```

---

### 5.3 Deep Learning

Uses **artificial neural networks** with many layers (deep architectures).

```
Input Layer → Hidden Layer 1 → Hidden Layer 2 → Output Layer
  (pixels)      (edges)          (shapes)         (cat/dog)
```

**Applications:** Image recognition, speech synthesis, language models (ChatGPT, Gemini).

---

### 5.4 Explainable AI (XAI)

The ability to explain AI decisions in human-understandable terms.

**Example:**

```
Black-box model: "Loan DENIED" (no reason given)

XAI model:       "Loan DENIED because:
                  - Credit score too low (40% influence)
                  - High existing debt (35% influence)
                  - Short employment history (25% influence)"
```

Tools: LIME, SHAP, Attention maps in transformers.

---

### 5.5 Ethics of AI

**Benefits:**
- Healthcare diagnosis (cancer detection)
- Climate modelling
- Accessibility tools (text-to-speech, translation)

**Risks & Concerns:**

| Risk | Example |
|------|---------|
| **Bias** | Facial recognition performing poorly on dark skin |
| **Privacy** | Surveillance and data misuse |
| **Job Displacement** | Automation replacing workers |
| **Autonomous Weapons** | Lethal AI decision-making |
| **Misinformation** | Deepfakes, AI-generated fake news |

**Key Principles of Responsible AI:**
- Fairness
- Transparency
- Accountability
- Privacy
- Safety

---

## 🧪 Practical List

### P1 — Tower of Hanoi in Prolog

```prolog
hanoi(1, From, To, _) :-
    format("Move disk 1 from ~w to ~w~n", [From, To]).

hanoi(N, From, To, Via) :-
    N > 1,
    N1 is N - 1,
    hanoi(N1, From, Via, To),
    format("Move disk ~w from ~w to ~w~n", [N, From, To]),
    hanoi(N1, Via, To, From).

?- hanoi(3, left, right, center).
```

---

### P2 — Hill Climbing in Prolog

```prolog
hill_climbing(State, Goal, Path) :-
    hill_climbing(State, Goal, [State], Path).

hill_climbing(Goal, Goal, Visited, Visited).
hill_climbing(State, Goal, Visited, Path) :-
    move(State, NextState),
    \+ member(NextState, Visited),
    better(NextState, State, Goal),
    hill_climbing(NextState, Goal, [NextState|Visited], Path).
```

---

### P3 — Best First Search in Prolog

```prolog
best_first([[Goal|Path]|_], Goal, [Goal|Path]).
best_first([Path|Paths], Goal, Solution) :-
    expand(Path, NewPaths),
    append(Paths, NewPaths, AllPaths),
    sort_by_heuristic(AllPaths, Sorted),
    best_first(Sorted, Goal, Solution).
```

---

### P4 — A* Search in Prolog

```prolog
astar(Start, Goal, Path) :-
    heuristic(Start, Goal, H),
    astar([[H, 0, Start]], Goal, [], RevPath),
    reverse(RevPath, Path).

astar([[_, _, Goal]|_], Goal, Visited, [Goal|Visited]).
astar([[F, G, Node]|Rest], Goal, Visited, Path) :-
    \+ member(Node, Visited),
    findall([NF, NG, Next],
        (neighbor(Node, Next, Cost),
         NG is G + Cost,
         heuristic(Next, Goal, H),
         NF is NG + H),
        Children),
    append(Rest, Children, All),
    sort(All, Sorted),
    astar(Sorted, Goal, [Node|Visited], Path).
```

---

### P5 — Min-Max Search in Prolog

```prolog
minimax(Pos, Player, BestMove, Val) :-
    moves(Pos, Player, Moves),
    !,
    best(Moves, Player, BestMove, Val).

minimax(Pos, _, _, Val) :- evaluate(Pos, Val).

best([Move], Player, Move, Val) :-
    minimax(Move, Player, _, Val).
best([Move|Moves], Player, BestMove, BestVal) :-
    minimax(Move, Player, _, Val),
    best(Moves, Player, Move2, Val2),
    better(Player, Val, Move, Val2, Move2, BestMove, BestVal).
```

---

### P6 — Water Jug Problem in Prolog

```prolog
% State: state(X, Y) — X in 4L jug, Y in 3L jug
% Goal: Get exactly 2L in 4L jug

goal(state(2, _)).

move(state(X, Y), state(4, Y)) :- X < 4.      % Fill 4L jug
move(state(X, Y), state(X, 3)) :- Y < 3.      % Fill 3L jug
move(state(_, Y), state(0, Y)).                % Empty 4L jug
move(state(X, _), state(X, 0)).                % Empty 3L jug
move(state(X, Y), state(X1, Y1)) :-            % Pour 4L→3L
    Transfer is min(X, 3 - Y),
    X1 is X - Transfer, Y1 is Y + Transfer.
move(state(X, Y), state(X1, Y1)) :-            % Pour 3L→4L
    Transfer is min(Y, 4 - X),
    X1 is X + Transfer, Y1 is Y - Transfer.
```

---

### P8 — Family Tree in Prolog

```prolog
parent(tom, bob).
parent(tom, liz).
parent(bob, ann).
parent(bob, pat).

grandparent(X, Z) :- parent(X, Y), parent(Y, Z).
sibling(X, Y) :- parent(Z, X), parent(Z, Y), X \= Y.
ancestor(X, Y) :- parent(X, Y).
ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y).

?- grandparent(tom, ann).    % true
?- sibling(ann, pat).        % true
?- ancestor(tom, pat).       % true
```

---

### P10 — List Concatenation (conc) in Prolog

```prolog
conc([], L, L).
conc([H|T], L, [H|R]) :- conc(T, L, R).

?- conc([1,2,3], [4,5], L).
L = [1,2,3,4,5].
```

---

### P11 — List Reversal in Prolog

```prolog
reverse_list([], []).
reverse_list([H|T], R) :-
    reverse_list(T, RT),
    conc(RT, [H], R).

?- reverse_list([1,2,3,4], R).
R = [4,3,2,1].
```

---

### P12 — Parse Tree in Prolog (DCG)

```prolog
:- use_module(library(dcg/basics)).

sentence(s(NP, VP)) --> noun_phrase(NP), verb_phrase(VP).
noun_phrase(np(D, N)) --> det(D), noun(N).
verb_phrase(vp(V, NP)) --> verb(V), noun_phrase(NP).
det(det(the)) --> [the].
det(det(a)) --> [a].
noun(n(dog)) --> [dog].
noun(n(cat)) --> [cat].
verb(v(chased)) --> [chased].

?- phrase(sentence(Tree), [the, dog, chased, a, cat]).
Tree = s(np(det(the), n(dog)), vp(v(chased), np(det(a), n(cat)))).
```

---

### P13 — Context-Free Grammar aⁿbⁿ in Prolog

```prolog
% Recognizes strings of the form a^n b^n (n >= 1)
ab([a|T0], T) :- ab(T0, T1), b_list(T1, T).
ab([a|T], T) :- b_list([b|_], _), T = [b|_].

% Simpler using difference lists
s --> [].
s --> [a], s, [b].

?- phrase(s, [a,a,b,b]).    % true (n=2)
?- phrase(s, [a,a,a,b,b,b]). % true (n=3)
?- phrase(s, [a,a,b]).       % false
```

---

## 📖 Recommended Books

| # | Book | Author | Publisher | Edition |
|---|------|--------|-----------|---------|
| 1 | *Artificial Intelligence: A Modern Approach* | Russell & Norvig | Pearson | 4th, 2020 |
| 2 | *Prolog Programming for Artificial Intelligence* | Ivan Bratko | Pearson | 4th, 2012 |
| 3 | *Introduction to A.I. and Expert Systems* | Dan W. Patterson | PHI | 2007 |
| 4 | *Programming in PROLOG* | Clocksin & Mellish | Springer | 5th, 2003 |
| 5 | *Artificial Intelligence* | Saroj Kaushik | Cengage India | 2011 |
| 6 | *Artificial Intelligence* | Rich & Knight | Tata McGraw Hill | 3rd, 2010 |

---

## 🗺️ Topic Summary Mind Map

```
Artificial Intelligence
│
├── Unit 1: Introduction
│     ├── Turing Test
│     ├── Weak / Strong / Narrow / AGI / Super AI
│     └── Agents (PEAS, Types)
│
├── Unit 2: Search
│     ├── Uninformed: BFS, DFS
│     ├── Informed: Hill Climbing, Best-First, A*
│     ├── CSP
│     └── Game Playing: MinMax, Alpha-Beta
│
├── Unit 3: Knowledge Representation
│     ├── Logic: Propositional, FOPL
│     ├── Resolution, Unification
│     ├── Semantic Nets, Frames, Scripts
│     └── PROLOG
│
├── Unit 4: NLP
│     ├── Chomsky Hierarchy
│     ├── CFG, Parsing
│     └── RTNs
│
└── Unit 5: Present & Future
      ├── Symbolic vs Data-Driven AI
      ├── ML & Deep Learning
      ├── Explainable AI
      └── Ethics of AI
```

---

*Generated for Semester 6 — DSC16/GE6e/DSE: Artificial Intelligence*  
*Based on EC (1270) - 27.07.2024 syllabus*

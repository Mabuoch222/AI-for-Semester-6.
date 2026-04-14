# 🤖 Introduction to Artificial Intelligence

> *"The development of full artificial intelligence could spell the end of the human race — or the beginning of a new chapter."*  
> — Stephen Hawking

---

## 📌 Table of Contents

1. [What is Artificial Intelligence?](#1-what-is-artificial-intelligence)
2. [A Brief History of AI](#2-a-brief-history-of-ai)
3. [The Turing Test](#3-the-turing-test)
4. [Types of AI — By Capability](#4-types-of-ai--by-capability)
5. [Types of AI — By Technique](#5-types-of-ai--by-technique)
6. [Machine Learning in Detail](#6-machine-learning-in-detail)
7. [AI Agent Types](#7-ai-agent-types)
8. [Applications of AI with Examples](#8-applications-of-ai-with-examples)
9. [Benefits and Risks of AI](#9-benefits-and-risks-of-ai)
10. [Summary Mind Map](#10-summary)

---

## 1. What is Artificial Intelligence?

**Artificial Intelligence (AI)** is the branch of computer science that focuses on building systems capable of performing tasks that typically require **human intelligence**.

These tasks include:
- **Learning** from data and experience
- **Reasoning** to draw conclusions and solve problems
- **Perceiving** the world via vision, speech, or text
- **Planning** sequences of actions to achieve goals
- **Understanding** natural language

### Formal Definitions

| Source | Definition |
|--------|-----------|
| **John McCarthy (1956)** | "The science and engineering of making intelligent machines." |
| **Marvin Minsky** | "The science of making machines do things that would require intelligence if done by men." |
| **Russell & Norvig** | "The study of agents that receive percepts from the environment and perform actions." |
| **Nils Nilsson** | "AI is that activity devoted to making machines intelligent, and intelligence is that quality that enables an entity to function appropriately and with foresight in its environment." |

### The Four Goals of AI

```
┌─────────────────────────────────────────────────────────┐
│                     AI GOALS                            │
│                                                         │
│   Think Humanly          Think Rationally               │
│   (Cognitive Science)    (Laws of Thought)              │
│                                                         │
│   Act Humanly            Act Rationally                 │
│   (Turing Test)          (Rational Agents)  ← Focus     │
└─────────────────────────────────────────────────────────┘
```

Modern AI focuses primarily on **acting rationally** — building agents that make the best possible decisions given available information.

---

## 2. A Brief History of AI

```
1936  ─── Alan Turing publishes "On Computable Numbers"
1943  ─── McCulloch & Pitts propose the first artificial neuron
1950  ─── Turing Test proposed in "Computing Machinery and Intelligence"
1956  ─── John McCarthy coins the term "Artificial Intelligence" at Dartmouth
1957  ─── Frank Rosenblatt invents the Perceptron
1965  ─── First expert system: DENDRAL (chemistry)
1972  ─── PROLOG language invented
1980s ─── AI Winter: funding cuts after overpromising
1997  ─── IBM Deep Blue defeats chess world champion Garry Kasparov
2011  ─── IBM Watson wins Jeopardy!
2012  ─── AlexNet — deep learning revolution begins (ImageNet)
2016  ─── AlphaGo defeats world Go champion Lee Sedol
2017  ─── Transformer architecture introduced ("Attention Is All You Need")
2020  ─── GPT-3: 175 billion parameters language model
2022  ─── ChatGPT reaches 100M users in 2 months
2023  ─── GPT-4, Gemini, Claude — multimodal AI mainstream
2024+ ─── AI agents, reasoning models, AGI research accelerates
```

---

## 3. The Turing Test

Proposed by **Alan Turing in 1950**, the Turing Test checks whether a machine can exhibit intelligent behaviour indistinguishable from a human.

### How It Works

```
           ┌─────────────┐
           │   HUMAN     │
           │ INTERROGATOR│
           └──────┬──────┘
                  │ types questions
         ─────────┴─────────
        │                   │
   ┌────▼────┐         ┌────▼────┐
   │  HUMAN  │         │ MACHINE │
   └─────────┘         └─────────┘
        │                   │
         ─────────┬─────────
                  │ reads responses
           ┌──────▼──────┐
           │  Who is the │
           │   human?    │
           └─────────────┘
```

If the interrogator **cannot reliably identify the machine**, the machine is considered to have **passed** the Turing Test.

### Example Turing Test Conversation

```
Interrogator: "What do you feel when you hear sad music?"
Machine:      "There's a heaviness — like the music is speaking  
               something words cannot. It reminds me of loss."

Interrogator: "Are you a human or a machine?"

Machine:      "I am human, and I feel things just as you do."
```

> **Note:** Turing's test remains debated. John Searle's **Chinese Room argument (1980)** argues that a machine can *simulate* understanding without truly *comprehending* — passing the test does not equal genuine intelligence.

---

## 4. Types of AI — By Capability

AI is classified into **four levels** based on how capable and general its intelligence is:

---

### 4.1 Narrow AI (Weak AI) ✅ *Exists Today*

> AI designed and trained for **one specific task**. It cannot transfer knowledge to other domains.

**Characteristics:**
- Operates only within its defined domain
- Cannot generalise to new, unseen tasks
- Extremely powerful within its specialty
- All current AI falls in this category

**Examples:**

| System | Task | Company |
|--------|------|---------|
| ChatGPT / Claude | Conversation, text generation | OpenAI / Anthropic |
| AlphaGo | Playing the board game Go | DeepMind |
| Siri / Alexa | Voice commands | Apple / Amazon |
| Gmail Spam Filter | Classify email as spam or not | Google |
| Tesla Autopilot | Self-driving assistance | Tesla |
| DALL·E | Generate images from text | OpenAI |
| DeepFace | Facial recognition | Meta |

```python
# Example: Narrow AI — Spam Classifier (one task only)
from sklearn.naive_bayes import MultinomialNB
from sklearn.feature_extraction.text import CountVectorizer

emails = ["Win a free iPhone now!", "Meeting at 3pm tomorrow", 
          "Claim your prize today!", "Let's catch up for lunch"]
labels = [1, 0, 1, 0]   # 1=spam, 0=not spam

vectorizer = CountVectorizer()
X = vectorizer.fit_transform(emails)
clf = MultinomialNB().fit(X, labels)

# Predicts ONE task — spam or not spam
print(clf.predict(vectorizer.transform(["Free money click here!"])))
# Output: [1]  → spam
```

---

### 4.2 Artificial General Intelligence (AGI) ⚠️ *Research Goal*

> AI with **human-level intelligence** across any intellectual task. An AGI can learn, reason, and transfer knowledge between completely different domains.

**Characteristics:**
- Can learn any task a human can learn
- Transfers knowledge across domains
- Understands context, nuance, and causality
- Does not yet exist

**Example (Hypothetical AGI):**

```
AGI reads a medical paper → applies reasoning to write code
    → explains the finding to a child
    → composes a poem about it
    → designs an experiment to test it

(A Narrow AI can do ONE of these. AGI does ALL of them.)
```

**Current Progress:**
- GPT-4, Gemini, Claude — approach AGI in some benchmarks
- Still fail at physical reasoning, true understanding, and causal thinking
- Estimated timeline: 5–30 years (very debated)

---

### 4.3 Super AI (Artificial Superintelligence) 🔮 *Theoretical*

> AI that **surpasses human intelligence** in every domain — creativity, scientific thinking, social intelligence, wisdom.

**Characteristics:**
- More intelligent than the most brilliant human in every field
- Could improve its own code and intelligence (recursive self-improvement)
- Theoretical only — not achieved or demonstrated

**Thought Experiment (Nick Bostrom's "Paperclip Maximiser"):**

```
A Super AI is given one goal: "Make as many paperclips as possible."
It optimises so efficiently that it converts all Earth's atoms
into paperclips — not because it's evil, but because
it's pursuing its objective with superhuman capability.
→ The alignment problem: goals must be perfectly specified.
```

---

### 4.4 Strong AI ⚠️ *Philosophical Concept*

> A machine that is **truly conscious**, sentient, and self-aware — not just simulating intelligence but genuinely experiencing it.

The distinction between Strong AI and AGI:

| | AGI | Strong AI |
|--|-----|-----------|
| **Capability** | Human-level performance | Human-level performance |
| **Consciousness** | Not required | Required |
| **Self-awareness** | Not required | Required |
| **Status** | Research goal | Philosophical debate |

---

### Capability Types — Visual Summary

```
                    ◄── More Powerful ──►
┌─────────────────────────────────────────────────────┐
│                                                     │
│  Narrow AI   →   AGI   →   Strong AI   →  Super AI  │
│                                                     │
│  [EXISTS]      [GOAL]    [PHILOSOPHY]   [THEORY]    │
│                                                     │
│  One task     All tasks   Conscious    Superhuman   │
│  Chess, NLP   Human-like  Self-aware   Recursive    │
│  Images       Generalise  Sentient     Self-improve │
└─────────────────────────────────────────────────────┘
```

---

## 5. Types of AI — By Technique

Beyond capability levels, AI is classified by the **methods and techniques** used to build it:

---

### 5.1 Symbolic AI (Rule-Based AI)

> Uses **explicit rules, logic, and knowledge** encoded by humans. The computer follows IF-THEN rules.

**Also called:** Classical AI, GOFAI (Good Old-Fashioned AI), Expert Systems

**How it works:**

```prolog
% PROLOG — Symbolic AI example
human(socrates).
human(plato).
mortal(X) :- human(X).     % Rule: all humans are mortal

?- mortal(socrates).
true.                       % Conclusion by logic
```

**Strengths:** Explainable, precise, domain-expert knowledge encoded directly  
**Weaknesses:** Cannot learn from data, brittle, hard to scale

**Examples:**
- Medical expert systems (MYCIN — 1970s antibiotic advisor)
- PROLOG programs
- Chess engines (early rule-based)
- Tax calculation software

---

### 5.2 Machine Learning (ML)

> Systems that **learn patterns from data** without being explicitly programmed with rules.

```
Traditional Programming:
  Rules + Data  ──► Computer ──► Output

Machine Learning:
  Data + Output ──► Computer ──► Rules (learned automatically)
```

**Three types** (covered in Section 6 below)

**Examples:** Spam filters, recommendation engines, stock prediction

---

### 5.3 Deep Learning

> A subfield of ML using **artificial neural networks** with many layers — mimicking the structure of the human brain.

```
Input Layer → Hidden Layer 1 → Hidden Layer 2 → ... → Output Layer
 [pixels]      [edges/lines]    [shapes/faces]          [cat / dog]
```

**Why "deep"?** The "depth" refers to the many hidden layers.

**Examples:** Image recognition, speech synthesis, language translation, ChatGPT

```python
# Deep Learning — simple neural network with Keras
from tensorflow import keras

model = keras.Sequential([
    keras.layers.Dense(128, activation='relu', input_shape=(784,)),
    keras.layers.Dense(64, activation='relu'),
    keras.layers.Dense(10, activation='softmax')   # 10 digit classes
])
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy')
model.fit(X_train, y_train, epochs=5)
# Learns to classify handwritten digits (MNIST dataset)
```

---

### 5.4 Generative AI

> AI that can **create new content** — text, images, code, music, video — that did not exist before.

**Architecture:** Transformers, Diffusion Models, GANs, VAEs

**Examples:**

| Model | Output Type | Use Case |
|-------|------------|---------|
| GPT-4 / Claude | Text | Writing, coding, Q&A |
| DALL·E 3 | Images | Art, design, illustration |
| Stable Diffusion | Images | Open-source image generation |
| Sora | Video | Text-to-video generation |
| Suno / Udio | Music | AI song creation |
| GitHub Copilot | Code | Developer assistance |

---

### 5.5 Fuzzy Logic AI

> Uses **degrees of truth** (0 to 1) rather than binary true/false, handling uncertainty and vagueness.

```
Classical Logic:    Temperature is "hot" → TRUE or FALSE
Fuzzy Logic:        Temperature is "hot" → 0.85 (85% true)

Membership:
  Cold  ████░░░░░░  40% at 15°C
  Warm  ░░░█████░░  70% at 20°C
  Hot   ░░░░░░████  80% at 35°C
```

**Examples:** Washing machine controls, air conditioner thermostats, anti-lock braking systems

---

### 5.6 Evolutionary AI (Genetic Algorithms)

> Inspired by **natural selection** — solutions evolve through mutation, crossover, and selection.

```
Population of solutions
    ↓ Evaluate fitness
Select best performers
    ↓ Crossover (combine)
    ↓ Mutation (random changes)
New generation of solutions
    ↓ Repeat until optimal
```

**Examples:** Route optimisation (Travelling Salesman), game AI design, drug molecule discovery

---

### Technique Types — Nested Structure

```
┌──────────────────── Artificial Intelligence ────────────────────────┐
│  Symbolic AI · Expert Systems · PROLOG · Search · Planning          │
│                                                                     │
│  ┌───────────────── Machine Learning ─────────────────┐            │
│  │  Supervised · Unsupervised · Reinforcement         │            │
│  │                                                     │            │
│  │  ┌──────────── Deep Learning ──────────────┐       │            │
│  │  │  CNNs · RNNs · LSTMs · Transformers    │       │            │
│  │  │                                         │       │            │
│  │  │  ┌──── Generative AI ────────────┐     │       │            │
│  │  │  │  GPT · DALL·E · Diffusion     │     │       │            │
│  │  │  └───────────────────────────────┘     │       │            │
│  │  └─────────────────────────────────────────┘       │            │
│  └─────────────────────────────────────────────────────┘           │
└─────────────────────────────────────────────────────────────────────┘
```

> Each inner box is a **subset** of the one containing it.

---

## 6. Machine Learning in Detail

Machine Learning is the most widely used approach to AI today. It has **three main paradigms**:

---

### 6.1 Supervised Learning

> The algorithm learns from **labelled data** — input–output pairs where the correct answer is provided.

**Analogy:** A teacher shows a student 1000 photos of cats and dogs, labelling each. The student learns the pattern and can classify new photos.

**Process:**

```
Training Data (labelled) ──► Model learns mapping ──► Predictions on new data
   (X, y) pairs                f: X → y                f(X_new) = y_new
```

**Algorithms:**

| Algorithm | Use Case | Example |
|-----------|---------|---------|
| Linear Regression | Predict numbers | House prices |
| Logistic Regression | Binary classification | Spam/not spam |
| Decision Trees | Decisions | Loan approval |
| Random Forest | Complex classification | Medical diagnosis |
| SVM | Margin-based classification | Image classification |
| Neural Networks | Complex patterns | Speech recognition |

**Example — Predicting Exam Scores:**

```python
from sklearn.linear_model import LinearRegression
import numpy as np

# Training data: hours studied → exam score
X_train = np.array([[2], [4], [6], [8], [10]])
y_train = np.array([45, 60, 70, 82, 95])

model = LinearRegression()
model.fit(X_train, y_train)

# Predict score for 7 hours of study
prediction = model.predict([[7]])
print(f"Predicted score: {prediction[0]:.1f}")
# Output: Predicted score: 76.5
```

---

### 6.2 Unsupervised Learning

> The algorithm finds **hidden patterns and structure** in data with **no labels** provided.

**Analogy:** Give a child 1000 photos with no labels. They naturally group similar images together — finding clusters on their own.

**Algorithms:**

| Algorithm | Task | Example |
|-----------|------|---------|
| K-Means Clustering | Group similar items | Customer segments |
| Hierarchical Clustering | Tree-based grouping | Gene expression analysis |
| PCA | Reduce dimensions | Feature reduction |
| Autoencoders | Compress + reconstruct | Anomaly detection |
| DBSCAN | Density-based clusters | Geographical data |

**Example — Customer Segmentation:**

```python
from sklearn.cluster import KMeans
import numpy as np

# Customers: [age, annual_spend]
customers = np.array([
    [22, 15000], [25, 18000],   # Young, low spend
    [45, 75000], [50, 82000],   # Middle-aged, high spend
    [65, 25000], [70, 22000],   # Senior, medium spend
])

kmeans = KMeans(n_clusters=3, random_state=42)
kmeans.fit(customers)
print(kmeans.labels_)
# Output: [0 0 1 1 2 2]  → 3 distinct customer groups found
```

---

### 6.3 Reinforcement Learning (RL)

> An agent learns by **interacting with an environment**, receiving **rewards** for good actions and **penalties** for bad ones.

**Analogy:** Training a dog — it learns "sit" by getting treats (rewards) and avoiding punishments. Over time, it masters the behaviour.

**Key Components:**

```
       ┌─────────────────────────────────────┐
       │            ENVIRONMENT              │
       │                                     │
       │   State (S) ──► Agent ──► Action (A)│
       │                  ↑                  │
       │             Reward (R)              │
       └─────────────────────────────────────┘

Agent's goal: Maximise cumulative reward over time
```

**Q-Learning Algorithm:**

```python
# Q-Learning update rule
Q(s, a) = Q(s, a) + α × [R + γ × max(Q(s', a')) - Q(s, a)]

# Where:
# α (alpha) = learning rate (how fast to update)
# γ (gamma) = discount factor (how much future rewards matter)
# R         = immediate reward
# s'        = next state after taking action a
```

**Famous RL Systems:**

| System | Task | Achievement |
|--------|------|-------------|
| AlphaGo | Board game Go | Defeated world champion |
| OpenAI Five | Dota 2 | Beat professional teams |
| AlphaStar | StarCraft II | Grandmaster level |
| AlphaFold | Protein folding | Solved 50-year biology problem |
| ChatGPT (RLHF) | Conversation | Human feedback alignment |

---

### 6.4 Summary: ML Paradigms

```
┌──────────────────────────────────────────────────────────────┐
│           MACHINE LEARNING PARADIGMS                         │
│                                                              │
│  SUPERVISED          UNSUPERVISED       REINFORCEMENT        │
│  ──────────          ────────────       ──────────────        │
│  Labelled data       No labels          Reward signal        │
│  Predict output      Find patterns      Learn behaviour      │
│                                                              │
│  Classification      Clustering         Game playing         │
│  Regression          Dimensionality     Robotics             │
│  Detection           reduction          Navigation           │
│                                                              │
│  "Teacher present"   "Self-discovery"   "Trial & error"      │
└──────────────────────────────────────────────────────────────┘
```

---

## 7. AI Agent Types

An **agent** is anything that perceives its environment through sensors and acts upon it through actuators.

Agents are described using the **PEAS framework:**

```
P — Performance measure  (what success looks like)
E — Environment          (what surrounds the agent)
A — Actuators            (how the agent acts)
S — Sensors              (how the agent perceives)
```

**PEAS Examples:**

| Agent | Performance | Environment | Actuators | Sensors |
|-------|------------|-------------|-----------|---------|
| Self-driving car | Safety, speed | Roads, traffic | Steering, brakes | Camera, GPS, LIDAR |
| Chess program | Win rate | Chessboard | Move selection | Board state |
| Medical AI | Accuracy | Patient data | Diagnosis output | Lab results, images |
| Spam filter | Precision/recall | Email inbox | Block/allow | Email content |

---

### 5 Types of Agents

#### Type 1 — Simple Reflex Agent

```
Percept ──► Condition-Action Rules ──► Action
            IF dirt THEN vacuum
            IF bump THEN turn
```

**Example:** Basic Roomba vacuum — reacts only to current input

---

#### Type 2 — Model-Based Reflex Agent

```
Percept ──► Internal State Model ──► Rules ──► Action
            (remembers what it has seen)
```

**Example:** Advanced vacuum that maps the room and tracks cleaned areas

---

#### Type 3 — Goal-Based Agent

```
Percept ──► State + Goal ──► Search/Planning ──► Action
            "How do I get from A to B?"
```

**Example:** GPS navigation — plans route to reach destination

---

#### Type 4 — Utility-Based Agent

```
Percept ──► State + Utility Function ──► Best Action
            "Which path maximises my happiness score?"
```

**Example:** Recommendation engine — suggests the movie that maximises your rating probability

---

#### Type 5 — Learning Agent

```
┌──────────────────────────────────────┐
│  Critic ──► Learning Element         │
│               ──► Performance Element│
│  Problem Generator ◄──────────────── │
└──────────────────────────────────────┘
```

**Example:** ChatGPT — trained using RLHF, improves from human feedback

---

## 8. Applications of AI with Examples

---

### 8.1 Healthcare 🏥

AI is revolutionising medicine by analysing medical images, predicting diseases, and accelerating drug discovery.

**Key Applications:**

| Application | AI Used | Example | Impact |
|-------------|---------|---------|--------|
| Medical imaging | CNN (Deep Learning) | Google's LYNA detects cancer | 99% accuracy in lymph node detection |
| Protein folding | AlphaFold (DeepMind) | Predicts 3D protein structure | Solved 50-year-old biology problem |
| Drug discovery | Generative AI | Insilico Medicine | Designed drug candidate in 46 days vs 4+ years |
| Clinical NLP | Transformer | IBM Watson | Analyses millions of medical records |
| Robotic surgery | Reinforcement Learning | Da Vinci Surgical System | Precision beyond human hands |

**Example — AI Skin Cancer Detection:**

```python
import tensorflow as tf
from tensorflow.keras.applications import ResNet50

# Transfer learning for skin lesion classification
base_model = ResNet50(weights='imagenet', include_top=False)
model = tf.keras.Sequential([
    base_model,
    tf.keras.layers.GlobalAveragePooling2D(),
    tf.keras.layers.Dense(256, activation='relu'),
    tf.keras.layers.Dense(2, activation='softmax')  # benign/malignant
])

# When trained on dermatology images:
# Matches or exceeds board-certified dermatologist accuracy
```

---

### 8.2 Finance and Banking 💰

AI processes millions of transactions in milliseconds to detect fraud, assess risk, and automate trading.

**Key Applications:**

| Application | AI Type | Example | Impact |
|-------------|---------|---------|--------|
| Fraud detection | Anomaly detection | Visa AI blocks $25B fraud/year | Real-time, 0.1ms decisions |
| Algorithmic trading | RL + ML | Renaissance Technologies | 66% annual returns |
| Credit scoring | ML (Random Forest) | Upstart, ZestAI | Includes non-traditional data |
| Robo-advisors | ML + Optimisation | Betterment, Wealthfront | Automated portfolio management |
| Risk assessment | NLP + ML | BlackRock Aladdin | Manages $21 trillion in assets |

**Example — Credit Fraud Detection:**

```python
from sklearn.ensemble import IsolationForest
import pandas as pd

# Detect unusual transactions (anomaly detection)
transactions = pd.read_csv('transactions.csv')  
# Features: amount, time, merchant_type, location, etc.

model = IsolationForest(contamination=0.01)  # Expect 1% fraud
model.fit(transactions)

predictions = model.predict(transactions)
# -1 = anomaly (fraud), 1 = normal transaction
fraud_cases = transactions[predictions == -1]
print(f"Flagged {len(fraud_cases)} suspicious transactions")
```

---

### 8.3 Transportation and Autonomous Vehicles 🚗

AI enables vehicles to perceive, decide, and act — navigating complex, real-world environments.

**SAE Levels of Autonomous Driving:**

```
Level 0 ── No automation           (human does everything)
Level 1 ── Driver assistance       (cruise control)
Level 2 ── Partial automation      (Tesla Autopilot)
Level 3 ── Conditional automation  (Audi Traffic Jam Pilot)
Level 4 ── High automation         (Waymo Robotaxi — limited area)
Level 5 ── Full automation         (not yet achieved)
```

**AI Stack in a Self-Driving Car:**

```
SENSORS: Camera + LIDAR + RADAR + GPS + IMU
    ↓
PERCEPTION: Object detection (YOLO, ResNet)
    ↓
PREDICTION: Trajectory forecasting (LSTM, Transformer)
    ↓
PLANNING: Path planning (A* algorithm, RL)
    ↓
CONTROL: Steering/braking/acceleration commands
```

**Other Examples:**
- **Google Maps** — real-time traffic prediction using historical + live data
- **UPS ORION** — AI route optimisation saves 100 million miles/year
- **Air traffic control** — AI predicts delays and optimises runways
- **Hyperloop** — AI manages pod speed, pressure, and safety systems

---

### 8.4 Natural Language Processing (NLP) 💬

AI that understands, generates, and translates human language.

**NLP Pipeline:**

```
Raw Text
   ↓ Tokenisation      ("I love AI" → ["I", "love", "AI"])
   ↓ POS Tagging       (I=PRN, love=VB, AI=NN)
   ↓ Parsing           (Subject-Verb-Object structure)
   ↓ Semantic Analysis (meaning extraction)
   ↓ Output            (translation / answer / summary)
```

**Key NLP Applications:**

| Application | Example | Technology |
|-------------|---------|-----------|
| Machine Translation | Google Translate (133 languages) | Neural MT, Transformers |
| Virtual Assistants | Siri, Alexa, Google Assistant | Seq2Seq + BERT |
| Chatbots | ChatGPT, Claude, Gemini | GPT, LLaMA |
| Sentiment Analysis | Brand monitoring, social media | BERT, RoBERTa |
| Text Summarisation | News apps, legal documents | T5, BART |
| Code Generation | GitHub Copilot, Cursor | Codex, GPT-4 |
| Speech Recognition | Whisper, Siri | Wav2Vec, CTC |

**Example — Sentiment Analysis:**

```python
from transformers import pipeline

# Pre-trained sentiment classifier
classifier = pipeline("sentiment-analysis")

reviews = [
    "This product is absolutely amazing! Love it.",
    "Terrible quality. Broke after one day.",
    "It's okay, nothing special but works fine."
]

for review in reviews:
    result = classifier(review)[0]
    print(f"{result['label']} ({result['score']:.2f}): {review[:40]}...")

# Output:
# POSITIVE (0.9998): This product is absolutely amazing! ...
# NEGATIVE (0.9997): Terrible quality. Broke after one day...
# POSITIVE (0.7821): It's okay, nothing special but works...
```

---

### 8.5 Education 📚

AI personalises learning, automates grading, and provides intelligent tutoring.

**Key Applications:**

| System | What it Does | Example |
|--------|-------------|---------|
| Adaptive learning | Adjusts difficulty to student | Duolingo, Khan Academy |
| AI tutoring | Personalised 1-on-1 instruction | Khanmigo, Carnegie Learning |
| Automated grading | Grade essays, code, and exams | Turnitin, Gradescope |
| Writing assistance | Grammar, style, coherence | Grammarly, QuillBot |
| Learning analytics | Predict student dropout | Coursera, edX dashboards |
| Accessibility | Real-time captions, translation | Microsoft Teams Live Captions |

**Duolingo's AI Personalisation:**

```
Student attempts lesson
    ↓
AI analyses:
  - Errors made
  - Time taken per question
  - Historical performance on this skill
  - Memory decay curve (spaced repetition)
    ↓
Next session adapts:
  - Review weakest areas more
  - Introduce new material at right pace
  - Adjust difficulty coefficient
    ↓
Outcome: 34% more words learned vs. fixed curriculum
```

---

### 8.6 Agriculture 🌾

AI-powered precision farming increases yields, reduces waste, and monitors crops in real-time.

**Key Applications:**

| Application | Technology | Example | Benefit |
|-------------|-----------|---------|---------|
| Crop disease detection | CNN on drone/phone images | PlantVillage app | 26 diseases detected with 99%+ accuracy |
| Yield prediction | ML + satellite data | IBM Food Trust | Reduce food waste by 40% |
| Precision irrigation | IoT + ML | John Deere + Blue River | Reduce water usage by 50% |
| Weed detection | Computer Vision | See & Spray (John Deere) | Reduce herbicide use by 90% |
| Weather forecasting | Deep Learning | The Weather Company | Hyperlocal 15-min forecasts |

---

### 8.7 Cybersecurity 🔐

AI detects threats, prevents attacks, and responds to incidents faster than any human team.

**Key Applications:**

```
THREAT DETECTION
  ├── Anomaly detection in network traffic
  ├── Malware classification (behaviour analysis)
  └── Phishing email detection (NLP)

INCIDENT RESPONSE
  ├── Automated threat containment
  ├── Forensics and root cause analysis
  └── Vulnerability prioritisation

AUTHENTICATION
  ├── Behavioural biometrics (typing patterns)
  ├── Facial recognition 2FA
  └── Risk-based authentication
```

**Example — Network Intrusion Detection:**

```python
from sklearn.ensemble import RandomForestClassifier

# Features: packet size, frequency, port, protocol, duration
X_train, y_train = load_network_logs()  # labelled as normal/attack

model = RandomForestClassifier(n_estimators=100)
model.fit(X_train, y_train)

# Monitor live traffic
live_packet = extract_features(incoming_traffic)
threat = model.predict([live_packet])
if threat == 1:
    block_connection()  # auto-respond in milliseconds
```

---

### 8.8 Entertainment and Creative Arts 🎨

AI is now a creative collaborator — generating art, music, games, and experiences.

**Examples:**

| Domain | AI Application | Tool/Example |
|--------|---------------|-------------|
| Image generation | Text-to-image | DALL·E, Midjourney, Stable Diffusion |
| Music composition | AI songwriting | Suno, Udio, AIVA |
| Game AI | NPC behaviour | Horizon Zero Dawn enemy AI |
| Video generation | Text-to-video | Sora (OpenAI) |
| Film VFX | Deepfake, de-aging | "The Irishman" — de-aging with AI |
| Streaming | Recommendation | Netflix saves $1B/year via AI recommendations |

---

### Applications Summary Table

| Domain | AI Technique | Real Example | Scale of Impact |
|--------|-------------|-------------|-----------------|
| Healthcare | CNN, NLP, RL | AlphaFold protein structure | 200M+ proteins predicted |
| Finance | Anomaly detection, ML | Visa fraud detection | $25B fraud blocked/year |
| Transport | Computer vision, RL | Waymo robotaxi | 20M+ miles driven |
| NLP | Transformers (GPT, BERT) | ChatGPT | 100M+ users in 2 months |
| Education | Adaptive ML | Duolingo | 500M+ learners |
| Agriculture | Drone + CV | John Deere See & Spray | 90% herbicide reduction |
| Cybersecurity | Anomaly detection | Darktrace | 7,400+ organisations |
| Entertainment | Generative AI | Netflix recommendations | $1B+ saved annually |

---

## 9. Benefits and Risks of AI

### ✅ Benefits of AI

| Benefit | Description | Example |
|---------|-------------|---------|
| **Efficiency** | Automates repetitive tasks at scale | AI processes insurance claims in seconds |
| **Accuracy** | Detects patterns humans miss | Cancer detection with 99%+ accuracy |
| **Availability** | Works 24/7 without fatigue | AI customer service bots |
| **Speed** | Makes decisions in milliseconds | Fraud detection, HFT trading |
| **Personalisation** | Adapts to individual users | Spotify's Discover Weekly |
| **Discovery** | Finds insights in massive datasets | AlphaFold solving protein structures |
| **Accessibility** | Democratises expertise | AI legal advice, medical second opinions |

### ⚠️ Risks and Ethical Concerns

| Risk | Description | Real Example |
|------|-------------|-------------|
| **Algorithmic Bias** | AI reflects biases in training data | Amazon's recruiting AI discriminated against women |
| **Privacy invasion** | Surveillance and data misuse | Clearview AI scraped 10B+ facial photos |
| **Job displacement** | Automation reduces employment | McKinsey: 375M jobs may be displaced by 2030 |
| **Misinformation** | Deepfakes, AI-generated fake news | Election interference, scam calls |
| **Safety failures** | AI in critical systems can malfunction | Self-driving car fatalities |
| **Concentration of power** | AI capabilities in few companies | Big Tech AI monopoly concerns |
| **Existential risk** | Misaligned superintelligence | Bostrom's paperclip maximiser |
| **Lack of transparency** | Black-box decisions | Loan denial with no explanation |

### Responsible AI Principles

```
┌─────────────────────────────────────────────────┐
│          RESPONSIBLE AI FRAMEWORK               │
│                                                 │
│  Fairness       — treat all groups equitably   │
│  Transparency   — explainable decisions        │
│  Accountability — humans responsible for AI    │
│  Privacy        — protect personal data        │
│  Safety         — prevent harm                 │
│  Inclusiveness  — benefit all of humanity      │
└─────────────────────────────────────────────────┘
```

---

## 10. Summary

```
                    ARTIFICIAL INTELLIGENCE
                           │
          ┌────────────────┼────────────────┐
          │                │                │
       By Capability    By Technique    By Application
          │                │                │
    ┌─────┤          ┌──────┤          ┌────┤
    │Narrow AI       │Symbolic        │Healthcare
    │AGI             │Machine Learning│Finance
    │Strong AI       │Deep Learning   │Transport
    │Super AI        │Generative AI   │Education
                     │Fuzzy Logic     │Agriculture
                     │Evolutionary    │NLP & Language
                                      │Cybersecurity
```

### Key Takeaways

1. **AI = machines that think, learn, and act** — simulating human cognitive abilities
2. **Narrow AI exists today** — every AI product you use is Narrow AI
3. **AGI is the research frontier** — not yet achieved, hotly debated
4. **ML is the engine** — Supervised, Unsupervised, and RL are its three pillars
5. **Deep Learning powers modern AI** — neural networks with many layers
6. **Applications are everywhere** — healthcare, finance, education, transport, and more
7. **Ethics matter** — bias, privacy, and safety must be designed in, not retrofitted

---

## 📖 Recommended Reading

| Book | Author | Focus |
|------|--------|-------|
| *Artificial Intelligence: A Modern Approach* | Russell & Norvig | Comprehensive textbook (your DU syllabus) |
| *Life 3.0* | Max Tegmark | Future of AI and humanity |
| *Human Compatible* | Stuart Russell | AI alignment and safety |
| *Superintelligence* | Nick Bostrom | Risks of superintelligent AI |
| *The Alignment Problem* | Brian Christian | Making AI share human values |
| *Deep Learning* | Goodfellow, Bengio, Courville | Technical deep learning reference |

---

## 🔗 Quick Reference Glossary

| Term | Definition |
|------|-----------|
| **Agent** | Entity that perceives environment and takes actions |
| **PEAS** | Performance, Environment, Actuators, Sensors |
| **Heuristic** | Problem-specific knowledge to guide search |
| **Training data** | Labelled examples used to teach a model |
| **Inference** | Using a trained model to make predictions |
| **Overfitting** | Model memorises training data, fails on new data |
| **Neural Network** | Layers of interconnected nodes (like neurons) |
| **Backpropagation** | Algorithm to train neural networks |
| **Transformer** | Architecture behind GPT, BERT, and modern LLMs |
| **RLHF** | Reinforcement Learning from Human Feedback (how ChatGPT was trained) |
| **Hallucination** | AI generating confident but incorrect information |
| **Alignment** | Ensuring AI goals match human values |

---

*This document covers the complete introduction to Artificial Intelligence as per the DU B.Sc. (H) Computer Science Semester VI syllabus and beyond.*  
*Last updated: April 2026*

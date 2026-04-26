# Advanced Machine Learning
### Rishihood University, NST — 3rd Year, Semester 6

**Student:** Aman Kumar  
**Roll Number:** 230065  
**Course:** Advanced Machine Learning  

---

## Selected Paper

**Title:** Dual Coordinate Descent Methods for Logistic Regression and Maximum Entropy Models  
**Authors:** Hsiang-Fu Yu, Fang-Lan Huang, Chih-Jen Lin  
**Venue:** Machine Learning (Springer), Vol. 85, pp. 41–75, 2011  
**DOI:** 10.1007/s10994-010-5221-8  
**CORE Rank:** A*  

---

## Repository Structure

```
├── llm_usage_partA.json        # LLM usage disclosure for Part A
├── README.md                   # This file
│
└── partB/
    ├── task 1 1.ipynb          # Q1: Core Contribution / Architecture
    ├── task 1 2.ipynb          # Q1: Key Assumptions
    ├── task 1 3.ipynb          # Q1: What the Paper Claims to Improve
    ├── task 2 1.ipynb          # Q2: Dataset Selection and Setup
    ├── task 2 2.ipynb          # Q2: Reproduction of Core Contribution
    ├── task 2 3.ipynb          # Q2: Result, Comparison & Reproducibility Checklist
    ├── task 3 1.ipynb          # Q3: Two-Component Ablation Study
    ├── task 3 2.ipynb          # Q3: Failure Mode Analysis
    ├── report.pdf              # Final 4-page report synthesising all findings
    ├── requirements.txt        # Python dependencies with version numbers
    ├── llm_task_1_1.json       # LLM disclosure for Task 1.1
    ├── llm_task_1_2.json       # LLM disclosure for Task 1.2
    ├── llm_task_1_3.json       # LLM disclosure for Task 1.3
    ├── llm_task_2_1.json       # LLM disclosure for Task 2.1
    ├── llm_task_2_2.json       # LLM disclosure for Task 2.2
    ├── llm_task_2_3.json       # LLM disclosure for Task 2.3
    ├── llm_task_3_1.json       # LLM disclosure for Task 3.1
    ├── llm_task_3_2.json       # LLM disclosure for Task 3.2
    ├── llm_task_4_1.json       # LLM disclosure for Task 4.1
    ├── llm_task_4_2.json       # LLM disclosure for Task 4.2
    ├── results/
    │   ├── task2_convergence.png       # Primal objective convergence + dual variable distribution
    │   ├── task2_comparison.png        # CDdual vs L-BFGS accuracy comparison
    │   ├── task2_alpha_dist.png        # Alpha distribution plot
    │   ├── task3_ablation1.png         # Ablation 1: Full Newton vs Line Search
    │   ├── task3_ablation2.png         # Ablation 2: Random Permutation vs Sequential
    │   └── task3_failure_mode.png      # Failure mode: large C analysis
    └── data/
        ├── README.md                   # Dataset documentation
        ├── X_train.npy                 # Training features (standardised)
        ├── X_test.npy                  # Test features (standardised)
        ├── y_train.npy                 # Training labels {-1, +1}
        └── y_test.npy                  # Test labels {-1, +1}
```

---

## Part A Summary

The selected paper applies coordinate descent to the **dual form** of logistic regression and maximum entropy models — a direct methodological extension of SVM dual optimisation (Hsieh et al., 2008). The paper qualifies under the SVM/variants category and is published in the Machine Learning journal (Springer), a CORE A* venue.

---

## Part B Summary

### Dataset
**Breast Cancer Wisconsin (Diagnostic)** — 569 instances, 30 features, binary classification. Loaded directly from `sklearn.datasets.load_breast_cancer()`. No manual download required.

### Reproduction (Question 2)
Implemented **Algorithm 5** (CDdual) and **Algorithm 4** (modified Newton sub-problem solver) from scratch in Python. Key results:
- CDdual converged in **39 iterations**
- Train accuracy: **98.68%** — identical to sklearn L-BFGS baseline
- Test accuracy: **98.25%**

### Ablation Study (Question 3)
| Component Ablated | Finding |
|---|---|
| Algorithm 4 → CDdual-ls (line search) | Same accuracy, but **2.3× slower** wall-clock time |
| Random permutation → Sequential order | Same accuracy, but **4.2× more iterations** (39 → 164) |

### Failure Mode (Question 3.2)
CDdual fails to converge within 500 iterations when **C ≥ 100**, with test accuracy dropping from 98.25% to 91–93%. Directly linked to Assumption 1 (interior optimum near boundary) and the catastrophic cancellation issues described in Section 3.3 of the paper.

---

## How to Run

```bash
# Install dependencies
pip install -r partB/requirements.txt

# Open any notebook in Jupyter or VS Code and run all cells
# All notebooks are self-contained and load data programmatically
```

**No GPU required. All experiments run on CPU.**  
**No manual dataset downloads required.**

---

## LLM Usage Disclosure

LLM tools (Claude, Anthropic) were used for reading comprehension, concept clarification, and writing assistance. Full disclosure is provided in the JSON files at the root level (`llm_usage_partA.json`) and within `partB/` for each task (`llm_task_*.json`). All final content was independently verified against the paper and rewritten in the student's own words.

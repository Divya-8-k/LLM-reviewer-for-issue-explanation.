# LLM Reviewer for Issue Explanation

## 📌 Project Overview

This project demonstrates an **LLM-assisted code review workflow** that uses static-analysis tools to identify issues in Python code and then provides explanations, importance, and suggested fixes for those issues.

The project combines:

* Flake8
* Pylint
* Bandit
* Python
* LLM-based issue explanation

The notebook first performs static analysis on a sample Python program, combines the generated reports, and prepares a prompt for an expert code reviewer. A review is then generated for the identified issues. Finally, a fixed version of the program is created and analyzed again.

## 🎯 Objectives

The main objectives are:

* Perform static analysis on Python source code.
* Generate Flake8, Pylint, and Bandit reports.
* Combine multiple analysis reports.
* Prepare an LLM prompt for code review.
* Explain identified issues.
* Explain why the issues matter.
* Suggest fixes for the issues.
* Create a corrected version of the source code.
* Re-run static-analysis tools on the corrected code.

## 🛠️ Technologies Used

| Technology   | Purpose                               |
| ------------ | ------------------------------------- |
| Python       | Source code and analysis              |
| Flake8       | Style and lint analysis               |
| Pylint       | Code quality analysis                 |
| Bandit       | Security analysis                     |
| LLM          | Issue explanation and recommendations |
| Google Colab | Execution environment                 |

## 📂 Project Structure

```text
LLM-Reviewer-for-Issue-Explanation/
│
├── LLM reviewer for issue explanation..ipynb
└── README.md
```

The notebook generates additional files while running:

```text
sample.py
sample_fixed.py
flake8_report.txt
pylint_report.txt
bandit_report.txt
```

## 🔍 Sample Code

The notebook creates the following `sample.py`:

```python
import os

password = "12345"

def divide(a,b):
    return a/b

print(divide(10,0))
```

This code is intentionally used for analysis because it contains multiple issues.

## 🔎 Static Analysis

The notebook installs and uses:

```bash
pip install flake8 pylint bandit
```

The analysis reports are generated using:

```bash
flake8 sample.py > flake8_report.txt
pylint sample.py > pylint_report.txt
bandit -r sample.py > bandit_report.txt
```

The reports are then loaded into Python and combined into a single report.

## 🤖 LLM Review

The notebook creates a review prompt asking an expert code reviewer to:

1. Explain each issue.
2. Explain why the issue matters.
3. Suggest a fix.

The combined Flake8, Pylint, and Bandit reports are included in the prompt.

## 📋 Issues Explained

The notebook's review identifies the following issues.

### Issue 1: Hardcoded Password

**Explanation:**

The password `'12345'` is stored directly in the source code.

**Why it Matters:**

Hardcoded credentials can be exposed if the code is shared publicly.

**Suggested Fix:**

Store sensitive values in environment variables.

### Issue 2: Unused Import

**Explanation:**

The `os` module is imported but never used.

**Suggested Fix:**

Remove the import statement.

### Issue 3: Missing Whitespace After Comma

**Explanation:**

PEP 8 recommends a space after commas.

**Suggested Fix:**

Change:

```python
def divide(a,b)
```

to:

```python
def divide(a, b)
```

## ✅ Fixed Code

The notebook creates `sample_fixed.py`:

```python
def divide(a, b):
    if b == 0:
        return "Cannot divide by zero"
    return a / b


print(divide(10, 2))
```

The notebook also shows an improved version with module and function docstrings:

```python
"""Sample calculator module."""

def divide(a, b):
    """Divide two numbers safely."""
    if b == 0:
        return "Cannot divide by zero"
    return a / b


print(divide(10, 2))
```

## 🔄 Validation

After creating the fixed code, the notebook runs:

```bash
flake8 sample_fixed.py
```

```bash
pylint sample_fixed.py
```

```bash
bandit -r sample_fixed.py
```

Pylint is also run separately on the final version:

```bash
pylint sample_fixed.py
```

This provides a second analysis of the corrected code.

## 🔄 Workflow

```text
        Python Source Code
                ↓
        ┌─────────────────┐
        │    Flake8       │
        ├─────────────────┤
        │    Pylint       │
        ├─────────────────┤
        │    Bandit       │
        └─────────────────┘
                ↓
       Analysis Reports
                ↓
        Combined Report
                ↓
          LLM Prompt
                ↓
       Issue Explanation
                ↓
       Suggested Fixes
                ↓
        Fixed Source Code
                ↓
      Re-run Static Analysis
```

## 📚 Learning Outcomes

This project demonstrates:

* Static code analysis
* Python code-quality checking
* Security vulnerability detection
* Combining multiple analysis reports
* LLM-assisted code review
* Explaining programming issues
* Secure coding practices
* Fixing and validating source code

## 🚀 How to Run

### Step 1: Open the Notebook

Open:

```text
LLM reviewer for issue explanation..ipynb
```

using Google Colab or Jupyter Notebook.

### Step 2: Install the Required Tools

Run:

```python
!pip install flake8 pylint bandit
```

### Step 3: Run the Notebook

Execute the cells in order.

The notebook will:

1. Install Flake8, Pylint, and Bandit.
2. Create `sample.py`.
3. Run static-analysis tools.
4. Save the reports as text files.
5. Load and combine the reports.
6. Create an LLM code-review prompt.
7. Explain the identified issues.
8. Create `sample_fixed.py`.
9. Run static analysis on the fixed code.

## 👩‍💻 Author

**Divya K**

## 📌 Project Type

**LLM-Assisted Static Code Analysis and Code Review**

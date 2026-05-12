# Session 4 Exercise: Diagnosing a Wage Regression

**Course:** Data Science and Econometrics for International Business — Spring 2026 

**Institution:** Europa-Universität Flensburg  

**Session date:** Thursday, 21 May 2026

---

## Overview

In this exercise you work through a complete OLS regression diagnostic workflow applied to a wage regression. You will diagnose functional form, heteroskedasticity, multicollinearity, influential observations, and normality — building each diagnostic plot by hand before verifying with `performance::check_model()`. You will also encounter a case of omitted variable bias and argue about its direction.

The exercise is completed entirely inside **`exercise.qmd`**. Write your code in the provided chunks and your interpretations directly below each task. Aim for complete sentences.

---

## Repository contents

| File | Purpose |
|------|---------|
| `exercise.qmd` | The exercise — open this and work inside it |
| `data/cps-earnings-2014.csv` | The data — already in the repo, no download needed |
| `Session-04-Exercise.Rproj` | RStudio project file — open this first |

---

## Data

`cps-earnings-2014.csv` is a cleaned extract from the 2014 US Current Population Survey (CPS), Monthly Outgoing Rotation Group (MORG), restricted to full-time employed workers. It contains `r nrow(read.csv("data/cps-earnings-2014.csv"))` observations.

| Variable | Description |
|---|---|
| `wage` | Hourly wage (USD) = weekly earnings / usual weekly hours |
| `earnwke` | Weekly earnings (USD) — top-coded at $2,884 |
| `uhours` | Usual hours worked per week |
| `age` | Age in years (16–64) |
| `educ` | Educational attainment (CPS grade92 scale: 31 = less than Grade 1, 46 = doctoral degree) |
| `female` | 1 = female, 0 = male |

Original source: Békés & Kézdi (2021), *Data Analysis for Business, Economics, and Policy*, Cambridge University Press.  
Full dataset and documentation: <https://gabors-data-analysis.com/datasets/cps-earnings>

---

## How to work on this exercise

When you accept the assignment via GitHub Classroom, GitHub creates a personal copy of this repository under your account.

### Option A — Work locally (recommended)

1. Clone your repository to your computer
2. Open `Session-04-Exercise.Rproj` in RStudio
3. Open `exercise.qmd` and work through each task
4. Render to HTML: **Ctrl/Cmd + Shift + K** (or the Render button)
5. Commit and push your changes to GitHub

### Option B — Work in a Codespace

1. On your repository page, click **Code → Open with Codespaces → New codespace**
2. Wait for setup to complete (~5 minutes the first time)
3. Type `rserver` in the VS Code terminal; log in with username and password `rstudio`
4. Open the project, render, commit, and push as above

---

## Required packages

```r
install.packages(c("tidyverse", "broom", "modelsummary",
                   "lmtest", "sandwich", "car",
                   "performance", "see", "patchwork"))
```

---

## Getting help

Post questions in the [course discussion space](https://github.com/data-science-ma/AdvancedDataScience26-Material/discussions). Helping each other is encouraged; sharing complete code solutions is not.

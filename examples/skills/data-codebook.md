# Example Skill: Data Codebook Generator

This is a generalized template for a skill that generates a codebook (data dictionary) for a dataset. Useful for documentation, sharing data with collaborators, and preparing for open science requirements.

---

```markdown
# Data Codebook Generator Skill

## Overview
Generates a structured codebook for a dataset. Reads the data file, extracts
variable information, asks the user to provide descriptions and context, and
produces a formatted codebook document. Invoke when the user asks for a
codebook, data dictionary, or dataset documentation.

## Process

### Step 1: Read the Dataset
Read the data file (CSV, SPSS, Stata, or similar). Extract:
- Variable names
- Variable types (numeric, character, factor, date, etc.)
- Number of observations
- Basic descriptive statistics (mean, SD, min, max for numeric; levels
  and frequencies for categorical)
- Missing data rates per variable

### Step 2: Ask the User for Context
Present the variable list and ask:
1. What is this dataset? (Study name, data source, collection method)
2. For each variable (or groups of related variables):
   - What does this variable measure?
   - What scale or instrument was used? (if applicable)
   - Are there any coding decisions the user wants to document?
     (e.g., "1 = male, 2 = female, 3 = non-binary")
   - Any known issues? (e.g., "This variable has high missingness
     because it was added mid-study")

For datasets with many variables, group them logically (demographics,
IVs, DVs, covariates) rather than going one-by-one.

### Step 3: Generate the Codebook

## Template

# Codebook: [Dataset Name]

## Overview
- **Study:** [study name]
- **Source:** [how data was collected]
- **N:** [number of observations]
- **Variables:** [number of variables]
- **Date generated:** [today's date]

## Variables

### [Variable Name]
- **Label:** [human-readable description]
- **Type:** [numeric / categorical / text / date]
- **Measurement:** [scale or instrument, if applicable]
- **Values:** [range for numeric, levels for categorical]
- **Missing:** [N missing (percent)]
- **Notes:** [any coding decisions, known issues, or context]

[Repeat for each variable or group of variables]

## Coding Decisions
[Document any transformations, recoding, or decisions made during
data processing that affect interpretation]

## Missing Data
[Summary of missing data patterns — which variables have missingness
and why, if known]

## Important Rules
- Never modify the original data file — the codebook is documentation only
- Ask the user to describe variables rather than guessing from variable names
- Flag any variables that look potentially identifiable (names, IDs, dates
  of birth) and remind the user about de-identification
- Include enough detail that a researcher unfamiliar with the study could
  understand the dataset
```

# Agents Module

## Overview

The `agents` folder contains the core AI agents responsible for processing the resume and job description through a multi-agent workflow. Each agent performs a dedicated task and passes its output to the next stage, enabling modular, maintainable, and scalable resume optimization.

The agents are implemented using **LangChain**, **Prompt Templates**, and an **LLM** configured through `llm_config.py`.

---

## Folder Structure

```
agents/
│── __init__.py
│── jd_parser.py
│── resume_evaluator.py
│── gap_analyst.py
└── resume_writer.py
```

---

## Agent Workflow

```
Job Description
       │
       ▼
JD Parser
       │
       ▼
Resume Evaluator
       │
       ▼
Gap Analyst
       │
       ▼
Resume Writer
       │
       ▼
Final Tailored Resume
```

---

# Files Description

## 1. `jd_parser.py`

### Purpose

This agent analyzes the raw Job Description (JD) and converts it into structured JSON data.

### Input

- Raw Job Description text

### Processing

The agent uses a Large Language Model (LLM) to identify:

- Job Role
- Required Skills
- Preferred Skills
- Responsibilities
- Keywords
- Experience Requirements
- Qualifications

### Output

A structured JSON object containing all extracted job information.

### Importance

This structured data is used by all downstream agents for resume evaluation and optimization.

---

## 2. `resume_evaluator.py`

### Purpose

This agent compares the candidate's resume with the parsed Job Description.

### Input

- Resume Text
- Parsed JD JSON

### Processing

The LLM evaluates the resume against the job requirements and generates:

- Overall Resume Score
- Skills Match
- Missing Skills
- Strengths
- Weaknesses
- ATS Compatibility
- Improvement Suggestions

### Output

A detailed evaluation report in JSON format.

### Importance

Provides an objective assessment of how well the resume aligns with the target role.

---

## 3. `gap_analyst.py`

### Purpose

This agent identifies gaps between the resume and the job requirements.

### Input

- Resume Text
- Parsed JD
- Resume Evaluation

### Processing

The model analyzes:

- Missing technical skills
- Missing keywords
- Missing responsibilities
- Skill gaps
- Project gaps

It also generates practical project recommendations to strengthen the resume.

### Output

A structured gap analysis report including:

- Missing Skills
- Company Expectations
- Suggested Projects
- Recommendations

### Importance

Helps candidates understand what improvements are needed to increase their chances of selection.

---

## 4. `resume_writer.py`

### Purpose

Generates an ATS-friendly resume tailored to the target job description.

### Input

- Resume Text
- Parsed JD
- Resume Evaluation
- Gap Analysis
- Project Inclusion Option

### Processing

The agent rewrites the resume while:

- Preserving factual information
- Improving formatting
- Adding relevant keywords
- Enhancing bullet points
- Optimizing ATS compatibility
- Optionally including suggested projects

### Output

A professionally tailored resume in text format, ready for DOCX or PDF conversion.

### Importance

Produces the final optimized resume that aligns closely with employer requirements.

---

## 5. `__init__.py`

### Purpose

Initializes the `agents` package.

### Description

This file is intentionally left empty.

Its presence allows Python to recognize the folder as a package, enabling imports such as:

```python
from agents.jd_parser import parse_job_description
```

Although it contains no executable code, it is required for proper package organization and module imports.

---

# Technologies Used

- Python
- LangChain
- Prompt Templates
- Large Language Models (LLMs)
- JSON
- Regular Expressions (Regex)

---

# Multi-Agent Pipeline

```
Job Description
        │
        ▼
+----------------------+
| JD Parser            |
+----------------------+
        │
        ▼
+----------------------+
| Resume Evaluator     |
+----------------------+
        │
        ▼
+----------------------+
| Gap Analyst          |
+----------------------+
        │
        ▼
+----------------------+
| Resume Writer        |
+----------------------+
        │
        ▼
ATS-Optimized Resume
```

---

# Advantages

- Modular architecture
- Easy to maintain
- Reusable independent agents
- Clear separation of responsibilities
- Easy integration with new agents
- Scalable pipeline
- ATS-focused resume optimization
- Structured JSON communication between agents

---

# Summary

The `agents` module forms the intelligence layer of the Resume Agent system. Each agent performs a specialized task—from parsing the job description to evaluating the resume, identifying skill gaps, and generating an ATS-optimized resume. This modular design improves maintainability, scalability, and the overall quality of resume customization.

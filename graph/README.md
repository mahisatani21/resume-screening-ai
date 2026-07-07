# Graph Module

## Overview

The `graph` folder contains the workflow orchestration logic of the Resume Agent system. It uses **LangGraph** to connect all AI agents into a sequential pipeline, enabling automated resume analysis and optimization.

Instead of calling each agent individually, the graph coordinates the execution flow, manages shared state, and passes outputs from one agent to the next.

---

## Folder Structure

```
graph/
│── __init__.py
└── pipeline.py
```

---

# Workflow

```
Resume + Job Description
            │
            ▼
      Initial State
            │
            ▼
     JD Parser Agent
            │
            ▼
 Resume Evaluator Agent
            │
            ▼
   Gap Analyst Agent
            │
            ▼
   Resume Writer Agent
            │
            ▼
 ATS-Optimized Resume
```

---

# Files Description

## 1. `pipeline.py`

### Purpose

This file builds and executes the complete multi-agent workflow using LangGraph.

It connects all four agents into a sequential pipeline and manages the data shared between them.

---

### Shared State

The pipeline defines a shared state (`ResumeState`) that stores:

#### Inputs

- Resume Text
- Job Description Text
- Include Suggested Projects option

#### Intermediate Outputs

- Parsed Job Description
- Resume Evaluation
- Gap Analysis

#### Final Output

- ATS-Optimized Resume

#### Tracking Information

- Current execution step
- Error message (if any)

---

### Pipeline Nodes

The pipeline consists of four nodes.

#### 1. JD Parser Node

Responsibilities:

- Reads Job Description
- Calls the JD Parser Agent
- Stores parsed job details
- Updates workflow status

---

#### 2. Resume Evaluator Node

Responsibilities:

- Reads Resume
- Reads Parsed Job Description
- Evaluates resume against job requirements
- Stores evaluation report

---

#### 3. Gap Analyst Node

Responsibilities:

- Reads Resume
- Reads Parsed JD
- Reads Evaluation Report
- Identifies missing skills and gaps
- Stores recommendations

---

#### 4. Resume Writer Node

Responsibilities:

- Reads all previous outputs
- Generates ATS-friendly resume
- Stores final optimized resume

---

### Graph Construction

The pipeline is created using **LangGraph StateGraph**.

Execution order:

```
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
END
```

---

### Pipeline Execution

The `run_pipeline()` function serves as the main entry point.

It performs the following tasks:

1. Creates the pipeline.
2. Initializes the shared state.
3. Executes all agent nodes in sequence.
4. Returns the final state containing all outputs.

---

### Error Handling

Each node is wrapped inside a `try-except` block.

If any agent fails:

- Error information is stored in the shared state.
- Remaining nodes are skipped.
- The pipeline returns the current state with the error message.

This prevents the application from crashing unexpectedly.

---

## 2. `__init__.py`

### Purpose

Initializes the `graph` package.

### Description

This file is intentionally left empty.

Its purpose is to allow Python to recognize the folder as a package, enabling imports such as:

```python
from graph.pipeline import run_pipeline
```

Although it contains no executable code, it is required for proper module organization and package imports.

---

# Technologies Used

- Python
- LangGraph
- TypedDict
- StateGraph
- LangChain
- Large Language Models (LLMs)

---

# Pipeline Architecture

```
                 User Input
        (Resume + Job Description)
                    │
                    ▼
          Initialize ResumeState
                    │
                    ▼
        +-------------------------+
        |     JD Parser Node      |
        +-------------------------+
                    │
                    ▼
        +-------------------------+
        | Resume Evaluator Node   |
        +-------------------------+
                    │
                    ▼
        +-------------------------+
        |   Gap Analyst Node      |
        +-------------------------+
                    │
                    ▼
        +-------------------------+
        |  Resume Writer Node     |
        +-------------------------+
                    │
                    ▼
         ATS-Optimized Resume
```

---

# Advantages

- Centralized workflow management
- Modular multi-agent architecture
- Shared state across all agents
- Automatic sequential execution
- Built-in error handling
- Easy scalability for additional agents
- Clear separation of orchestration and business logic
- Simplified integration with Streamlit or other front-end applications

---

# Summary

The `graph` module acts as the orchestration layer of the Resume Agent system. It coordinates the execution of all AI agents using LangGraph, manages shared state, handles errors gracefully, and ensures that data flows seamlessly from job description parsing to resume generation. This design makes the application modular, maintainable, and easy to extend with additional workflow components in the future.

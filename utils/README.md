# Utils Module

## Overview

The `utils` folder contains reusable helper modules used throughout the Resume Agent project. These utility functions provide common functionality such as configuring the Large Language Model (LLM), reading and processing documents, converting file formats, and reducing code duplication across different modules.

Instead of implementing these operations repeatedly, the project centralizes them inside the `utils` package for better maintainability and scalability.

---

## Folder Structure

```
utils/
│── __init__.py
│── llm_config.py
│── document_loader.py
└── docx_generator.py
```

---

# Utility Workflow

```
User Files
     │
     ▼
Document Loader
     │
     ▼
Extract Resume Text
     │
     ▼
LLM Configuration
     │
     ▼
AI Agents
     │
     ▼
Generated Resume
     │
     ▼
DOCX Generator
     │
     ▼
Final Downloadable Resume
```

---

# Files Description

## 1. `llm_config.py`

### Purpose

This module initializes and configures the Large Language Model (LLM) used by all AI agents.

### Responsibilities

- Loads API credentials
- Initializes the LLM
- Configures model parameters
- Creates a reusable model instance
- Provides a centralized configuration for all agents

### Benefits

- Eliminates duplicate LLM initialization
- Ensures consistent model settings
- Simplifies future model upgrades
- Improves code maintainability

---

## 2. `document_loader.py`

### Purpose

This module reads uploaded resume files and extracts their text content.

### Supported File Types

- PDF (.pdf)
- Microsoft Word (.docx)
- Plain Text (.txt)

### Responsibilities

- Load uploaded files
- Extract readable text
- Handle unsupported formats
- Return clean text for downstream processing

### Output

A plain text version of the uploaded resume, ready for AI processing.

---

## 3. `docx_generator.py`

### Purpose

This module converts the AI-generated resume into a professionally formatted Microsoft Word document.

### Responsibilities

- Create a DOCX document
- Apply formatting
- Preserve headings and bullet points
- Save the generated resume
- Produce a downloadable file

### Output

A formatted `.docx` resume suitable for sharing or printing.

---

## 4. `__init__.py`

### Purpose

Initializes the `utils` package.

### Description

This file is intentionally left empty.

Its purpose is to allow Python to recognize the folder as a package, enabling imports such as:

```python
from utils.llm_config import get_llm
```

or

```python
from utils.document_loader import load_document
```

Although it contains no executable code, it is required for proper package organization and module imports.

---

# Technologies Used

- Python
- LangChain
- Python-docx
- PDF Processing Libraries
- Environment Variables (.env)
- Large Language Models (LLMs)

---

# Utility Architecture

```
                Utils Package
                     │
     ┌───────────────┼────────────────┐
     │               │                │
     ▼               ▼                ▼
Document Loader   LLM Config    DOCX Generator
     │               │                │
Extract Text   Initialize LLM   Create Resume File
     │               │                │
     └───────────────┼────────────────┘
                     │
                     ▼
              Resume Agent System
```

---

# Advantages

- Centralized helper functions
- Reusable components
- Reduces code duplication
- Simplifies maintenance
- Consistent LLM configuration
- Easy file handling
- Professional resume generation
- Easy scalability for future utilities

---

# Summary

The `utils` module provides the supporting functionality required by the Resume Agent system. It handles document loading, LLM initialization, and DOCX generation while keeping these reusable operations separate from the business logic. This modular design improves maintainability, readability, and scalability of the overall application.

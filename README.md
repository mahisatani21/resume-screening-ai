# Resume Agent

An AI-powered **Multi-Agent Resume Optimization System** developed using **LangGraph**, **LangChain**, **Streamlit**, and **Large Language Models (LLMs)**. The application analyzes a candidate's resume against a job description, identifies missing skills and keywords, evaluates ATS compatibility, and generates a professionally tailored resume.

---

# Features

- AI-powered Job Description Parsing
- Resume Evaluation and ATS Score Analysis
- Skill Gap Identification
- Keyword Extraction
- Missing Project Suggestions
- ATS-Friendly Resume Generation
- Download Optimized Resume as DOCX
- Interactive Streamlit User Interface
- Modular Multi-Agent Architecture using LangGraph

---

# Project Structure

```
resume-agent/
│
├── __pycache__/
├── .vscode/
├── agents/
│   ├── __init__.py
│   ├── jd_parser.py
│   ├── resume_evaluator.py
│   ├── gap_analyst.py
│   └── resume_writer.py
│
├── graph/
│   ├── __init__.py
│   └── pipeline.py
│
├── resume/
│
├── utils/
│   ├── __init__.py
│   ├── document_loader.py
│   └── docx_generator.py
│
├── .env
├── app1.py
├── final_resume_output.txt (After execution)
├── llm_config.py
├── requirements.txt
├── test_agent1.py
├── test_agent2.py
├── test_agent3.py
├── test_agent4.py
├── test_pipeline.py
└── test_setup.py
```

---

# Technologies Used

- Python 3.x
- Streamlit
- LangChain
- LangGraph
- Groq LLM
- Firecrawl API
- Python-docx
- PDF Processing Libraries
- dotenv

---

# Prerequisites

Before running the project, ensure you have the following installed:

- Python 3.10 or above
- Visual Studio Code
- Git (Optional)

---

# Installation

## Step 1: Download or Clone the Repository

Clone the repository:

```bash
git clone <repository_url>
```

or download the ZIP file and extract it.

---

## Step 2: Open the Project in Visual Studio Code

1. Open **Visual Studio Code**.
2. Select **File → Open Folder**.
3. Browse and open the extracted **resume-agent** folder.

---

## Step 3: Create a Virtual Environment

Open the integrated terminal in Visual Studio Code and run:

```bash
python -m venv venv
```

Activate the virtual environment.

### Windows

```bash
venv\Scripts\activate
```

### Linux / macOS

```bash
source venv/bin/activate
```

---

## Step 4: Install Required Libraries

```bash
pip install -r requirements.txt
```

---

## Step 5: Configure Environment Variables

Create or edit the `.env` file in the project root directory.

Add the following API keys:

```env
GROQ_API_KEY=your_groq_api_key
FIRECRAWL_API_KEY=your_firecrawl_api_key
```

### API Keys Required

- **GROQ_API_KEY** – Used for accessing the Groq Large Language Model (LLM) to perform resume analysis, job description parsing, gap analysis, and resume generation.

- **FIRECRAWL_API_KEY** – Used to scrape and extract structured content from job description URLs when required by the application.

---

# Running the Application

Open the integrated terminal in **Visual Studio Code** and execute the following command:

```bash
streamlit run app1.py
```

After running the command, Streamlit will automatically start the web application.

You will see output similar to:

```
Local URL: http://localhost:8501
```

Open the displayed URL in your web browser if it does not open automatically.

---

# Application Workflow

```
Resume Upload
        │
        ▼
Job Description Input / URL
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
        │
        ▼
Download DOCX Resume
```

---

# Modules

## Agents

Contains all AI agents responsible for:

- Parsing Job Descriptions
- Resume Evaluation
- Gap Analysis
- Resume Generation

---

## Graph

Contains the LangGraph workflow that orchestrates the complete multi-agent pipeline.

---

## Utils

Contains reusable utility modules for:

- Document Loading
- DOCX Resume Generation

---

## Resume

Stores uploaded resumes and generated resume files during execution.

---

# Test Files

The project includes separate test scripts for validating each component.

- `test_agent1.py` – Tests the Job Description Parser Agent
- `test_agent2.py` – Tests the Resume Evaluator Agent
- `test_agent3.py` – Tests the Gap Analyst Agent
- `test_agent4.py` – Tests the Resume Writer Agent
- `test_pipeline.py` – Tests the complete LangGraph pipeline
- `test_setup.py` – Verifies project dependencies and environment configuration

---

# Output

The application generates:

- Parsed Job Description
- Resume Evaluation Report
- Gap Analysis Report
- ATS-Friendly Resume
- Downloadable DOCX Resume
- Final Resume Output (`final_resume_output.txt`)

---

# Future Enhancements

- Multiple Resume Templates
- Cover Letter Generation
- LinkedIn Profile Optimization
- Interview Question Generation
- Multi-language Resume Support
- Cloud Deployment
- Resume Version Comparison

---

# Author

Developed as a **Multi-Agent Resume Optimization System** using **LangGraph**, **LangChain**, **Groq LLM**, **Firecrawl API**, and **Streamlit**.

---

# License

This project is developed for educational and research purposes.

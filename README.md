# AGENETIC-AI

# 🤖 Employee Information Memory Bot

An **Agentic AI Employee Information Memory Bot** that allows users to store fictional employee and project information and ask natural-language questions about the stored information.

The project demonstrates how an **AI agent can use persistent memory** to retrieve relevant information and answer questions using only the information stored in the system.

---

## 📌 Project Overview

The Employee Information Memory Bot is an Agentic AI application designed to act as a digital memory for employee and project information.

Users can:

* Save employee information
* Save project information
* Permanently store information in a JSON file
* Ask questions about stored employees
* Retrieve information using natural language
* View all saved employee information
* Use an interactive Streamlit interface

The core system contains two important functions:

```python
save_memory()
```

and

```python
memory_agent()
```

`save_memory()` stores employee information, while `memory_agent()` uses the stored information to answer user questions.

---

# 🎯 Objectives

The main objectives of this project are:

1. Build an AI-powered employee memory system.
2. Implement persistent memory using JSON.
3. Allow users to store fictional employee information.
4. Allow users to ask natural-language questions.
5. Make the AI agent answer only using stored memory.
6. Demonstrate an Agentic AI workflow.
7. Provide a user-friendly web interface using Streamlit.
8. Integrate an LLM through OpenRouter.

---

# 🧠 What is Agentic AI?

**Agentic AI** refers to AI systems that can perform tasks using tools, memory, reasoning, and actions rather than simply generating a response.

In this project, the AI agent follows a simple workflow:

```text
User
  │
  ▼
Streamlit Interface
  │
  ├───────────────┐
  │               │
  ▼               ▼
Save Employee   Ask Question
  │               │
  ▼               ▼
save_memory()  memory_agent()
  │               │
  └───────┬───────┘
          ▼
 employee_memory.json
          │
          ▼
      OpenRouter
          │
          ▼
     AI Response
```

---

# 🏗️ System Architecture

```text
                 ┌──────────────────────┐
                 │        USER          │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │   STREAMLIT UI       │
                 └──────────┬───────────┘
                            │
              ┌─────────────┴─────────────┐
              │                           │
              ▼                           ▼
    ┌──────────────────┐        ┌──────────────────┐
    │  Save Employee   │        │ Ask Memory Agent │
    └────────┬─────────┘        └─────────┬────────┘
             │                            │
             ▼                            ▼
    ┌──────────────────┐        ┌──────────────────┐
    │  save_memory()   │        │ memory_agent()   │
    └────────┬─────────┘        └─────────┬────────┘
             │                            │
             └─────────────┬──────────────┘
                           ▼
                 ┌──────────────────────┐
                 │ JSON MEMORY STORAGE  │
                 │ employee_memory.json │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │     OpenRouter       │
                 │        LLM           │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │    AI RESPONSE       │
                 └──────────────────────┘
```

---

# 🛠️ Technologies Used

| Technology                   | Purpose                                                |
| ---------------------------- | ------------------------------------------------------ |
| Python                       | Core programming language                              |
| OpenRouter                   | LLM/API integration                                    |
| GPT model through OpenRouter | Natural-language understanding and response generation |
| JSON                         | Persistent employee memory                             |
| Streamlit                    | Web-based user interface                               |
| OpenCode                     | AI-assisted development and coding                     |
| urllib                       | API communication                                      |
| pathlib                      | File handling                                          |

---

# 📂 Project Structure

```text
Employee-Memory-Bot/
│
├── homework.py
│
├── app.py
│
├── homework.json
│
└── README.md
```

If your project uses `employee_memory.json` instead of `homework.json`, the structure will be:

```text
Employee-Memory-Bot/
│
├── homework.py
│
├── app.py
│
├── employee_memory.json
│
└── README.md
```

### File Description

### `homework.py`

Contains the main Employee Memory Bot logic, including:

* OpenRouter API communication
* `save_memory()`
* `memory_agent()`
* Loading memory
* Saving memory
* Employee information processing

### `app.py`

Contains the Streamlit interface.

It provides pages/features such as:

* Dashboard
* Add Employee
* Ask Memory Agent
* View Employee Memory

### `employee_memory.json`

Stores employee and project information permanently.

---

# 👨‍💼 Employee Information

The application can store information such as:

```text
Employee Name
Employee ID
Department
Job Role
Skills
Project Name
Project Description
```

Example:

```json
{
    "employee_name": "Rahul Sharma",
    "employee_id": "EMP101",
    "department": "Artificial Intelligence",
    "job_role": "ML Engineer",
    "skills": "Python, Machine Learning, TensorFlow",
    "project": "Smart Vision",
    "project_description": "AI-based object detection system"
}
```

---

# 💾 `save_memory()`

The `save_memory()` function is responsible for storing employee information.

Conceptually:

```python
def save_memory(employee_information):
    memories = load_memory()
    memories.append(employee_information)

    MEMORY_FILE.write_text(
        json.dumps(
            memories,
            indent=4
        )
    )
```

### Workflow

```text
Employee Information
        ↓
save_memory()
        ↓
Load existing memory
        ↓
Add new employee
        ↓
Convert to JSON
        ↓
Save to memory file
```

This provides **persistent memory**, meaning the information is not lost when the program is closed.

---

# 🧠 `memory_agent()`

The `memory_agent()` function is responsible for answering questions using stored employee information.

Example question:

```text
What project is Rahul working on?
```

The agent receives:

```text
STORED EMPLOYEE MEMORY

Rahul Sharma
Project: Smart Vision
```

and generates:

```text
Rahul Sharma is working on the Smart Vision project.
```

---

# 🔒 Memory-Only Answering

One important feature of the project is that the Memory Agent is instructed to use **only stored employee information**.

The agent should not invent information.

For example:

### Stored:

```text
Employee: Rahul
Department: AI
Project: Smart Vision
```

Question:

```text
What is Rahul's project?
```

Answer:

```text
Rahul is working on the Smart Vision project.
```

But if the user asks:

```text
What is Rahul's salary?
```

and salary is not stored, the agent should respond:

```text
Not found in employee memory.
```

This makes the memory system more reliable and prevents the agent from unnecessarily guessing.

---

# 🌐 Streamlit Interface

The Streamlit application provides a graphical/web interface instead of requiring the user to interact only through the terminal.

The interface contains four major sections.

## 1. Dashboard

Displays:

* Total employees
* Total projects
* Departments
* System information

Example:

```text
Employee Memory Bot

Total Employees: 5
Total Projects: 4
Departments: 3
```

---

## 2. Add Employee

The user can enter:

```text
Employee Name
Employee ID
Department
Job Role
Skills
Project Name
Project Description
```

Then click:

```text
Save Employee
```

The application calls:

```python
save_memory()
```

and stores the information in the JSON file.

---

## 3. Ask Memory Agent

The user enters a natural-language question:

```text
Which project is Rahul working on?
```

The application calls:

```python
memory_agent()
```

The answer is displayed on the web interface.

---

## 4. View Employee Memory

The application reads the JSON memory and displays the stored employees.

Example:

```text
Rahul Sharma
Employee ID: EMP101
Department: AI
Role: ML Engineer
Skills: Python, Machine Learning
Project: Smart Vision
```

---

# 🔄 Application Workflow

The complete workflow is:

```text
1. User opens the Streamlit application
              ↓
2. User adds employee information
              ↓
3. save_memory()
              ↓
4. Information is stored in JSON
              ↓
5. User asks a question
              ↓
6. memory_agent()
              ↓
7. Stored memory is loaded
              ↓
8. Relevant memory is provided to the LLM
              ↓
9. OpenRouter processes the question
              ↓
10. AI generates an answer
              ↓
11. Answer displayed in Streamlit
```

---

# 🔑 OpenRouter Integration

The project uses OpenRouter to communicate with an AI language model.

The Python application sends:

```text
System Instructions
+
Stored Employee Memory
+
User Question
```

to the model.

The model then generates an answer based on the supplied memory.

### Important

Never expose your API key publicly.

Instead of committing an API key directly into GitHub, use an environment variable or `.env` file.

---

# ▶️ Installation

## Step 1: Install Python

Check Python:

```bash
python --version
```

or:

```bash
py --version
```

---

## Step 2: Install Streamlit

```bash
python -m pip install streamlit
```

---

## Step 3: Configure OpenRouter

Add your new OpenRouter API key to the application or preferably configure it through an environment variable.

---

# 🚀 Running the Project

For the terminal version:

```bash
python homework.py
```

For the Streamlit interface:

```bash
python -m streamlit run app.py
```

After starting Streamlit, open the local URL displayed in the terminal, usually:

```text
http://localhost:8501
```

---

# 🧪 Example Usage

### Save employee

```text
Name: Priya
ID: EMP102
Department: Software Engineering
Role: Software Developer
Skills: Python, Java, SQL
Project: Employee Portal
Description: Internal employee management system
```

### Ask the agent

```text
What skills does Priya have?
```

### Response

```text
Priya has Python, Java, and SQL skills.
```

Another question:

```text
Which project is Priya working on?
```

Response:

```text
Priya is working on the Employee Portal project.
```

---

# ⭐ Key Features

* ✅ Persistent employee memory
* ✅ Employee and project information storage
* ✅ Natural-language questions
* ✅ AI-powered memory agent
* ✅ Memory-only responses
* ✅ JSON-based storage
* ✅ OpenRouter LLM integration
* ✅ Streamlit web interface
* ✅ Dashboard
* ✅ Employee information viewer
* ✅ Easy to run locally
* ✅ Built with Python
* ✅ Developed with OpenCode assistance

---

# 🎓 Learning Outcomes

Through this project, the following concepts are demonstrated:

### 1. Agentic AI

Understanding how an AI agent can interact with memory and perform a specific task.

### 2. Persistent Memory

Learning how information can be stored and retrieved across different program sessions.

### 3. LLM Integration

Connecting a Python application to an external language model through an API.

### 4. Prompt Engineering

Giving the Memory Agent clear instructions about how it should use stored information.

### 5. JSON Data Storage

Using JSON as a simple persistent database for fictional employee information.

### 6. Web Application Development

Building a user interface with Streamlit.

### 7. AI-Assisted Development

Using OpenCode to create, modify, test, and debug the application.

---

# 🔮 Future Improvements

The project can be extended with:

* Employee search
* Employee update and delete
* Project-specific memory
* Department-based filtering
* Semantic/vector memory
* Embedding-based retrieval
* Authentication
* Database integration
* PostgreSQL/MySQL support
* ChromaDB or FAISS vector database
* Multiple specialized agents
* Chat history
* Voice-based employee queries
* Role-based access control
* Cloud deployment

---

# ⚠️ Limitations

Currently, the project is designed for **fictional employee/project information** and uses JSON-based storage.

It is not intended to be used as a production HR database without additional:

* Authentication
* Authorization
* Data encryption
* Database security
* Privacy controls
* Access logging

---

# 🏁 Conclusion

The **Employee Information Memory Bot** demonstrates a practical Agentic AI use case where an AI agent can maintain and query persistent employee/project memory.

The project combines:

```text
Python
   +
JSON Memory
   +
OpenRouter LLM
   +
Memory Agent
   +
Streamlit
   +
OpenCode
```

to create an interactive AI-powered employee information system.

The central concept is simple:

```text
SAVE INFORMATION
       ↓
PERSIST MEMORY
       ↓
ASK QUESTION
       ↓
MEMORY AGENT
       ↓
RETRIEVE INFORMATION
       ↓
GENERATE ANSWER
```

This project provides a foundation for developing more advanced **AI agents with persistent memory and tool-based workflows**.

# AI Agent — Local Setup & Run Guide

This project is a simple AI-powered Q&A Chatbot built using **Python**, **OpenAI**, **Streamlit** and **LangChain**. It uses the Open AI GPT4 model to answer questions by the user.

The Interactive Web App UI is designed using **Streamlit**.
We are also setting up **LangSmith" for checking the logs as well as monitoring and debugging our app. 

This guide explains how to set up the application locally on macOS and run it using a Python virtual environment.

---

## Prerequisites

- macOS
- Terminal
- Homebrew
- Internet connection
- A valid **Open AI key**

---

## 1. Check if Python is Installed

Open Terminal and run:

```bash
python3 --version
```

Example:

```text
Python 3.12.6
```

Also check the Python installation path:

```bash
which python3
```

If Python is installed, you can proceed to the next step.

If you see:

```text
command not found: python3
```

install Python using Homebrew.

---

## 2. Install Python Using Homebrew

First check whether Homebrew is installed:

```bash
brew --version
```

If Homebrew is available, install Python:

```bash
brew install python
```

Verify the installation:

```bash
python3 --version
```

Also verify the installation path:

```bash
which python3
```

On Apple Silicon Macs, Python will typically be installed under:

```text
/opt/homebrew/bin/python3
```

---

## 3. Navigate to the Project Directory

Open Terminal and navigate to the directory containing `serve.py`.

For example:

```bash
cd ~/Documents/my-ai-agent
```

Verify that the application files are present:

```bash
ls
```

You should see something similar to:

```text
serve.py
requirements.txt
```

---

## 4. Create a Virtual Environment

Create a Python virtual environment inside the project directory:

```bash
python3 -m venv .venv
```

This creates an isolated Python environment in the `.venv` directory.

Your project will now look similar to:

```text
my-ai-agent/
├── serve.py
├── requirements.txt
└── .venv/
```

The virtual environment keeps this application's Python packages isolated from other Python projects on your Mac.

---

## 5. Activate the Virtual Environment

Activate the virtual environment:

```bash
source .venv/bin/activate
```

After activation, your Terminal prompt should show:

```text
(.venv)
```

For example:

```text
(.venv) user@Mac my-ai-agent %
```

You can verify that Python is now coming from the virtual environment:

```bash
which python
```

The result should point to:

```text
.../my-ai-agent/.venv/bin/python
```

---

## 6. Upgrade pip

With the virtual environment activated, upgrade `pip`:

```bash
python -m pip install --upgrade pip
```

Verify the installed version:

```bash
pip --version
```

---

## 7. Install Dependencies

The application dependencies are listed in `requirements.txt`.

Install them using:

```bash
pip install -r requirements.txt
```

This will install all the Python packages required by the application.

You can verify the installed packages with:

```bash
pip list
```

---

## 8. Create the `.env` File

The application requires a **Groq API key**.

Create a file named:

```text
.env
```

in the root of the project.

Your project should look like:

```text
my-ai-agent/
├── serve.py
├── requirements.txt
├── .env
└── .venv/
```

Add your Groq API key to `.env`:

```text
GROQ_API_KEY=your_groq_api_key_here
```

Replace:

```text
your_groq_api_key_here
```

with your actual Groq API key.

### Important

Do **not** commit `.env` to GitHub because it contains a secret API key.

Add the following to `.gitignore`:

```text
.env
.venv/
__pycache__/
```

---

## 9. Run the Application

Make sure the virtual environment is activated:

```bash
source .venv/bin/activate
```

Then start the application:

```bash
python serve.py
```

If the application starts successfully, you should see output indicating that the FastAPI server is running on:

```text
http://127.0.0.1:8000
```

---

## 10. Open the FastAPI Documentation

Open the following URL in your browser:

[http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

This opens the **FastAPI Swagger UI**, where you can view and test the API endpoints.

You should see the available endpoints exposed by the AI Agent.

---

# Everyday Workflow

Once the application has been set up, you don't need to repeat the installation steps.

Every time you want to run the application:

### 1. Open Terminal

Navigate to the project directory:

```bash
cd ~/Documents/my-ai-agent
```

### 2. Activate the virtual environment

```bash
source .venv/bin/activate
```

### 3. Run the application

```bash
python serve.py
```

### 4. Open the API documentation

[http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

### 5. Stop the application

When you are finished, press:

```text
Ctrl + C
```

### 6. Deactivate the virtual environment

```bash
deactivate
```

---

## Quick Start

For subsequent runs, the entire workflow is:

```bash
cd ~/Documents/my-ai-agent
source .venv/bin/activate
python serve.py
```

Then open:

```text
http://127.0.0.1:8000/docs
```

To stop the application:

```text
Ctrl + C
```

And optionally deactivate the virtual environment:

```bash
deactivate
```

---

## Project Structure

After setup, the project should look approximately like this:

```text
my-ai-agent/
│
├── serve.py              # FastAPI application
├── requirements.txt      # Python dependencies
├── .env                  # Environment variables / API keys
├── .gitignore            # Files excluded from Git
│
└── .venv/                # Python virtual environment
```

> **Note:** `.env` and `.venv/` should not be committed to the Git repository.
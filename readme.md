# AI Health & Calorie Recommendation Platform

An AI-powered health and calorie analysis platform that calculates **BMI, BMR, TDEE, and daily calorie targets** based on user-provided information.

The platform combines traditional health calculations with **Large Language Models (LLMs), Retrieval-Augmented Generation (RAG), Hugging Face models, and OpenAI models** to provide an interactive and informative experience.

> **Note:** This project is intended for educational and informational purposes. The results should not be treated as medical advice or used as a substitute for consultation with a qualified healthcare professional.

---

## 🚀 Project Overview

This platform takes basic user information such as:

* Age
* Gender
* Height
* Weight
* Activity level
* Fitness or calorie goal

and processes the information to calculate:

### BMI

**Body Mass Index (BMI)** estimates the relationship between a person's weight and height.

### BMR

**Basal Metabolic Rate (BMR)** estimates the approximate number of calories the body needs at rest to maintain basic functions.

### TDEE

**Total Daily Energy Expenditure (TDEE)** estimates daily calorie requirements by considering the user's activity level.

### Calorie Target

The platform uses the calculated TDEE and the selected goal to provide a calorie target.

The AI component can then use these results to generate additional explanations and personalized informational responses.

---

## 🧠 Technologies Used

| Technology             | Purpose                               |
| ---------------------- | ------------------------------------- |
| Python                 | Main programming language             |
| Streamlit / Python App | Application interface                 |
| OpenAI                 | LLM-based responses and AI processing |
| Hugging Face           | Open-source AI/LLM models             |
| RAG                    | Retrieval-Augmented Generation        |
| Tokens                 | Measuring and managing LLM usage      |
| Pandas                 | Data processing                       |
| Python Math/Logic      | BMI, BMR, TDEE calculations           |

---

## 📁 Project Structure

```text
AI-Health-Platform/
│
├── app.py
├── rag.py
├── llm_test.py
├── README.md
├── requirements.txt
├── .env
└── other project files
```

---

## 📌 Main Files

### `app.py`

`app.py` is the main application file.

It handles the user interface and accepts information such as:

```text
Age
Gender
Height
Weight
Activity Level
Goal
```

The application then displays the calculated:

```text
BMI
BMR
TDEE
Calorie Target
```

It can also connect the calculated information with the AI/RAG system to provide additional explanations.

---

### `rag.py`

`rag.py` handles the **Retrieval-Augmented Generation (RAG)** part of the project.

RAG combines two major processes:

```text
Retrieval + Generation
```

The retrieval component finds relevant information from the available knowledge source.

The LLM then uses that information to generate a response.

A simplified workflow is:

```text
User Question
      ↓
Retrieve Relevant Information
      ↓
Provide Information to LLM
      ↓
LLM Generates Response
      ↓
Display Answer
```

This approach can help the AI provide responses based on a defined knowledge source rather than relying only on the model's internal knowledge.

---

### `llm_test.py`

`llm_test.py` is used for testing and experimenting with the LLM components before integrating them into the main application.

It can be used to test:

* OpenAI models
* Hugging Face models
* Prompts
* Model responses
* Token usage
* Different LLM configurations

This makes it easier to test the AI functionality separately from the main application.

---

## 🤖 OpenAI and Hugging Face

The project uses both **OpenAI** and **Hugging Face** technologies.

### OpenAI

OpenAI models can be used for:

* Natural language responses
* Health-related informational explanations
* Understanding user questions
* Generating responses from retrieved information

### Hugging Face

Hugging Face provides access to open-source models and NLP/AI tools.

These models can be used for tasks such as:

* Text generation
* Embeddings
* Question answering
* Semantic similarity
* RAG-related processing

The exact model can be changed depending on the requirements of the project.

---

## 🔎 RAG Architecture

The basic architecture of the project can be represented as:

```text
                    ┌──────────────────┐
                    │      User        │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │     app.py       │
                    │  User Interface  │
                    └────────┬─────────┘
                             │
                             ▼
              ┌────────────────────────────┐
              │ BMI / BMR / TDEE / Target │
              │       Calculations        │
              └─────────────┬──────────────┘
                            │
                            ▼
                    ┌──────────────────┐
                    │      rag.py      │
                    │   RAG Pipeline   │
                    └────────┬─────────┘
                             │
                    ┌────────┴─────────┐
                    │                  │
                    ▼                  ▼
             ┌─────────────┐    ┌─────────────┐
             │ Hugging Face│    │   OpenAI    │
             │    Models   │    │    Models   │
             └──────┬──────┘    └──────┬──────┘
                    │                  │
                    └────────┬─────────┘
                             ▼
                    ┌──────────────────┐
                    │  AI Generated    │
                    │     Response     │
                    └──────────────────┘
```

---

## 🧮 Health Calculations

### BMI

BMI is calculated using:

```text
BMI = Weight (kg) / Height² (m²)
```

Example:

```text
Weight = 70 kg
Height = 1.75 m

BMI = 70 / (1.75 × 1.75)
```

The platform uses the calculated value to provide an informational BMI interpretation.

---

### BMR

BMR estimates the calories required by the body at rest.

A commonly used formula is the **Mifflin-St Jeor equation**.

For males:

```text
BMR = 10 × weight + 6.25 × height - 5 × age + 5
```

For females:

```text
BMR = 10 × weight + 6.25 × height - 5 × age - 161
```

Where:

```text
Weight = kg
Height = cm
Age = years
```

---

### TDEE

TDEE estimates the calories burned throughout the day by combining BMR with an activity multiplier.

Conceptually:

```text
TDEE = BMR × Activity Factor
```

Example activity factors may include:

```text
Sedentary
Lightly Active
Moderately Active
Very Active
Extra Active
```

---

### Calorie Target

The calorie target is calculated according to the user's selected goal.

For example:

```text
Maintenance
Weight Loss
Weight Gain
```

The platform uses the calculated TDEE as the starting point and applies the selected calorie adjustment.

---

## 🔐 API Keys and Environment Variables

API keys should **never be directly written inside Python files or uploaded to GitHub**.

Create a `.env` file:

```env
OPENAI_API_KEY=your_openai_api_key
HUGGINGFACE_API_KEY=your_huggingface_api_key
```

Then access the keys through environment variables in Python.

### Important

Add `.env` to `.gitignore`:

```gitignore
.env
__pycache__/
*.pyc
```

Never upload your actual API keys to GitHub.

---

## 🪙 Token Usage

LLM APIs work with **tokens**.

A token is a small piece of text processed by a language model.

For example:

```text
User Input
     ↓
Prompt Tokens
     ↓
LLM Processing
     ↓
Output Tokens
```

Token usage can depend on:

* Length of the prompt
* Retrieved RAG information
* User question
* Model response
* Model type

Monitoring tokens is useful for understanding API usage and controlling costs.

---

## 🔄 Complete Application Workflow

The overall workflow of the platform is:

```text
1. User enters personal data
              ↓
2. Application validates the input
              ↓
3. BMI is calculated
              ↓
4. BMR is calculated
              ↓
5. TDEE is calculated
              ↓
6. Calorie target is calculated
              ↓
7. User can interact with the AI system
              ↓
8. RAG retrieves relevant information
              ↓
9. Retrieved information is provided to the LLM
              ↓
10. OpenAI / Hugging Face model generates response
              ↓
11. Response is displayed to the user
```

---

## 💡 Key Features

* BMI calculation
* BMR calculation
* TDEE calculation
* Calorie target calculation
* Activity-level based calculation
* AI-powered responses
* RAG implementation
* Hugging Face model integration
* OpenAI model integration
* Token usage awareness
* Interactive user interface
* Modular Python structure

---

## 🛠️ Installation

### 1. Clone the repository

```bash
git clone <your-github-repository-url>
```

### 2. Open the project

```bash
cd AI-Health-Platform
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

### 5. Configure environment variables

Create a `.env` file and add your API keys:

```env
OPENAI_API_KEY=your_api_key
HUGGINGFACE_API_KEY=your_api_key
```

### 6. Run the application

If the application uses Streamlit:

```bash
streamlit run app.py
```

The application will then open in your browser.

---

## 📦 Example Requirements

Your `requirements.txt` may contain packages such as:

```text
streamlit
openai
transformers
huggingface_hub
python-dotenv
pandas
```

Add or remove packages according to the libraries actually used in your project.

---

## 📊 Example Input

```text
Age: 25
Gender: Male
Height: 175 cm
Weight: 70 kg
Activity Level: Moderately Active
Goal: Maintenance
```

The system processes these values and produces:

```text
BMI
BMR
TDEE
Daily Calorie Target
```

The AI layer can then explain the results in natural language.

---

## 🎯 Project Objectives

The main objectives of this project are:

1. Calculate important calorie and body-metric values automatically.
2. Create an easy-to-use health analysis interface.
3. Integrate traditional mathematical calculations with AI.
4. Implement RAG for information retrieval.
5. Experiment with both OpenAI and Hugging Face models.
6. Understand LLM token usage.
7. Build a practical end-to-end AI application using Python.

---

## 🔮 Future Improvements

Possible future improvements include:

* Nutrition tracking
* Meal recommendation system
* Exercise recommendation system
* Daily calorie tracking
* Progress dashboard
* User history
* Database integration
* More detailed RAG knowledge base
* Additional open-source LLMs
* Model comparison
* Token and API cost dashboard
* User authentication
* Mobile-friendly interface

---

## ⚠️ Disclaimer

This application provides estimates based on the information entered by the user and the formulas implemented in the application.

BMI, BMR, TDEE, and calorie targets are estimates and may not reflect an individual's actual medical or nutritional needs.

This project is intended for **educational and informational purposes only** and should not replace professional medical or nutritional advice.

---

## 👨‍💻 Project

**AI Health & Calorie Recommendation Platform**

Built using:

```text
Python
OpenAI
Hugging Face
RAG
LLMs
Streamlit
```

The project demonstrates how traditional calculations can be combined with modern AI technologies to build an interactive health-information application.

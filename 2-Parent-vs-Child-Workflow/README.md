# 🌤️ Parent–Child Workflow — n8n Workflow Experiment

A practical **n8n workflow experiment** demonstrating how a workflow can be executed by another workflow and process data passed from its parent workflow.

This project focuses on the **Child Workflow** concept in n8n, using weather data as a simple real-world example.

---

## 📌 Overview

The workflow is designed to be executed by a **Parent Workflow**.

The parent workflow passes a city/query value to the child workflow. The child then:

1. Receives the input from the parent workflow.
2. Requests current weather data from OpenWeatherMap.
3. Extracts relevant weather information.
4. Sends the data to an AI Agent.
5. Generates a simple, readable weather summary.

### Workflow Flow

```text
Parent Workflow
      │
      │ Passes city/query
      ▼
┌─────────────────────────────┐
│     Child Workflow          │
│                             │
│  Workflow Trigger           │
│          ↓                  │
│  HTTP Request               │
│          ↓                  │
│  AI Agent                   │
│          ↓                  │
│  Weather Summary            │
└─────────────────────────────┘
```

---

## 🏗️ Workflow Architecture

### 1. Workflow Trigger

The **When Executed by Another Workflow** node acts as the entry point.

It allows this workflow to be called from another n8n workflow and uses a passthrough input source to receive data from the parent workflow.

---

### 2. HTTP Request

The received query is used to request weather information from the **OpenWeatherMap API**.

The workflow sends:

* City/query
* API key
* Metric units

to the weather API endpoint.

---

### 3. AI Agent

The weather API response is passed to an **AI Agent**.

The Agent is instructed to create a simple, readable paragraph using:

* City name
* Current temperature
* Minimum temperature
* Maximum temperature
* Atmospheric pressure

This converts raw API data into human-readable information.

---

### 4. Groq Chat Model

The AI Agent uses a Groq Chat Model configured with:

```text
Model: openai/gpt-oss-120b
```

The model is connected directly to the AI Agent.

---

## 🔄 Data Flow

```text
Input from Parent
       │
       ▼
┌──────────────────┐
│ Workflow Trigger │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│   HTTP Request   │
│ OpenWeatherMap   │
└────────┬─────────┘
         │
         │ Weather JSON
         ▼
┌──────────────────┐
│    AI Agent      │
│                  │
│ Groq GPT-OSS     │
│      120B        │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│ Readable Weather │
│     Summary      │
└──────────────────┘
```

---

## 🧪 Example

The parent workflow can pass a city/query such as:

```text
Islamabad
```

The child workflow uses that value to request weather information.

The raw API response contains weather fields such as:

```text
City Name
Temperature
Minimum Temperature
Maximum Temperature
Pressure
```

The AI Agent then converts these values into a natural-language weather summary.

---

## 🎯 Purpose of the Experiment

This project was built to understand how **modular workflows** can be created in n8n.

Instead of putting every operation into one large workflow, functionality can be separated into smaller reusable workflows.

For example:

```text
Parent Workflow
      │
      ├── Child Workflow A
      │
      ├── Child Workflow B
      │
      └── Child Workflow C
```

This approach can make larger automation systems easier to organize, maintain, and reuse.

---

## 🧠 Key Concepts Learned

* n8n Execute Workflow Trigger
* Parent–Child workflow architecture
* Passing data between workflows
* HTTP Request nodes
* REST API integration
* OpenWeatherMap API
* AI Agent integration
* Groq LLM integration
* Transforming API data into natural language
* Modular workflow design

---

## ⚙️ Requirements

Before running this workflow, you need:

* [n8n](https://n8n.io/)
* OpenWeatherMap API access
* Groq API access
* Configured credentials in n8n
* A Parent Workflow capable of executing this Child Workflow

> **Security Note:** API credentials should never be committed to GitHub. Use n8n credentials or environment variables instead.

---

## 🚀 How to Use

### 1. Import the Workflow

Import the workflow JSON file into your n8n instance.

### 2. Configure API Credentials

Configure the required API credentials in n8n.

### 3. Connect a Parent Workflow

Use an **Execute Workflow** node in another workflow to call this Child Workflow.

### 4. Pass the Required Input

The child workflow expects the parent workflow to provide a query value that can be used to identify the requested city.

### 5. Execute and Test

Run the Parent Workflow and verify that the Child Workflow:

```text
Receives Input
      ↓
Fetches Weather Data
      ↓
Processes Data with AI
      ↓
Returns Weather Summary
```

---

## 📁 Project Structure

```text
parent-child-workflow/
│
├── parent-workflow.json
├── child-workflow.json
└── README.md
```

> If this repository stores the Parent and Child workflows separately, keep both JSON files in the same project directory so the relationship between them remains clear.

---

## ⚠️ Limitations

This is a **learning/experimental workflow**, not a production-ready weather automation.

The current implementation is intentionally simple and focuses on demonstrating the Parent–Child workflow architecture.

The workflow also relies on external services, so API availability and credentials are required for successful execution.

---

## 🔮 Possible Improvements

Future versions could include:

* Error handling for invalid cities
* API failure handling
* Input validation
* Temperature unit selection
* More detailed weather information
* Multiple child workflows for different tasks
* Reusable child workflows for production automations
* Better structured output between Parent and Child
* Logging and execution monitoring

---

## 📚 Learning Focus

This workflow is part of my **n8n Workflow Experiments** collection, where I build practical workflows to understand automation architecture, AI integrations, APIs, and reusable workflow design.

---

## 📄 License

This project is intended for educational and experimentation purposes.

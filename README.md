# ⚡ n8n Workflow Experiments

A collection of **n8n workflows built for learning, experimentation, and hands-on practice with AI automation, LLMs, APIs, and workflow architecture.**

This repository documents my journey of learning n8n by building small, focused experiments and gradually progressing toward more advanced automation systems.

---

## 📚 Workflows

| #  | Project                                                    | Concepts                                               |
| -- | ---------------------------------------------------------- | ------------------------------------------------------ |
| 01 | [Agent vs Chain Chatbot](./01-agent-vs-chain/)             | AI Agents, LLM Chains, Routing, Memory, Groq           |
| 02 | [Parent vs Child Workflow](./02-parent-vs-child-workflow/) | Workflow Modularity, Execute Workflow, APIs, AI Agents |

---

## 🧠 What This Repository Covers

The experiments in this repository focus on understanding practical n8n concepts such as:

* 🔄 Workflow design and execution
* 🤖 AI Agents
* 🔗 LLM Chains
* 🧠 Conversational memory
* 🌐 API integrations
* 🧩 Parent–Child workflows
* 🔀 Conditional workflow routing
* 📝 Data transformation
* 🛠️ AI automation architecture
* 🔌 Connecting external services with n8n

As the repository grows, more advanced concepts and automation patterns will be added.

---

## 🗂️ Repository Structure

```text
N8n-Workflow-Experiments/
│
├── 01-agent-vs-chain/
│   ├── workflow.json
│   └── README.md
│
├── 02-parent-vs-child-workflow/
│   ├── parent-workflow.json
│   ├── child-workflow.json
│   └── README.md
│
└── README.md
```

Each experiment is kept in its **own directory** with:

* The original n8n workflow JSON file(s)
* A dedicated README explaining the workflow
* Architecture and data-flow documentation
* Setup requirements
* Learning objectives
* Possible improvements

This keeps individual experiments isolated and makes the repository easier to maintain as more workflows are added.

---

## 🚀 How to Use

### 1. Clone the Repository

```bash
git clone https://github.com/habreh007/N8n-Workflow-Experiments.git
cd N8n-Workflow-Experiments
```

### 2. Open an Experiment

Navigate to the workflow you want to explore.

```bash
cd 01-agent-vs-chain
```

### 3. Import the JSON into n8n

Open your n8n instance and import the corresponding `.json` workflow file.

n8n workflows are collections of connected nodes that automate a process, and workflows can be started manually or through trigger nodes.

### 4. Configure Credentials

Some workflows require external services such as:

* Groq
* OpenWeatherMap
* Other APIs or integrations

**Credentials and API keys should never be committed to this repository.**

Configure your own credentials inside n8n before executing a workflow.

---

## ⚠️ Important

These workflows are primarily **learning and experimentation projects**.

They may contain:

* Simplified logic
* Hardcoded test values
* Experimental architectures
* Limited error handling
* Development-oriented configurations

They should **not be treated as production-ready automations without additional testing, security review, error handling, and credential configuration.**

---

## 🎯 Repository Goal

The goal of this repository is not simply to collect n8n JSON files.

It is to **document the progression from basic workflow concepts to more complex AI automation systems.**

The learning path will gradually move toward:

```text
Basic Workflows
      ↓
Workflow Logic
      ↓
API Integrations
      ↓
LLM Workflows
      ↓
AI Agents
      ↓
Multi-Workflow Systems
      ↓
RAG & Tool Calling
      ↓
Advanced AI Automation
      ↓
Production-Oriented Systems
```


## 🛠️ Tech Stack

* **n8n** — Workflow automation
* **Groq** — LLM inference
* **OpenAi** — LLM inference
* **OpenAI-compatible models** — LLM experimentation
* **REST APIs** — External service integration
* **Git & GitHub** — Version control and documentation

---

## 📖 Documentation

Each workflow contains its own README with:

* Overview
* Workflow architecture
* Node-by-node explanation
* Data flow
* Setup requirements
* Usage instructions
* Limitations
* Possible improvements
* Learning objectives

Start with:

### 🔹 Agent vs Chain Chatbot

A comparison between an **AI Agent** and a **Basic LLM Chain**, including routing and short-term memory.

### 🔹 Parent vs Child Workflow

A modular workflow experiment demonstrating how one n8n workflow can execute another workflow and pass data between them.

---

## 📌 Disclaimer

These workflows are created for **educational purposes, experimentation, and portfolio development**.

External APIs, models, services, and n8n features may change over time. Always verify the required configuration before running a workflow.

---

## 👤 Author

**Habib Ur Rehman**

Learning and building with:

**AI Automation • n8n • AI Agents • LLMs • APIs • Data Science**

---

⭐ If you find these experiments useful, feel free to explore the individual workflows and use them as learning references.

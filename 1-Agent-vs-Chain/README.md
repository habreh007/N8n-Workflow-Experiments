# 🤖 Agent vs Chain — n8n Workflow Experiment

A practical **n8n workflow experiment** designed to demonstrate and compare two common approaches to building LLM-powered workflows:

* **AI Agent** — capable of maintaining conversation context through memory.
* **Basic LLM Chain** — a simpler, direct LLM processing pipeline.

The workflow allows the user to choose between the two approaches directly through the chat input.

---

## 📌 Overview

This experiment demonstrates how **AI Agents and LLM Chains differ in an n8n workflow**.

A chat message is received through the n8n Chat Trigger and passed to a **Switch** node. Based on the user's input, the workflow routes the request to either the AI Agent or the Basic LLM Chain.

### Routing

| Input   | Workflow Path   |
| ------- | --------------- |
| `agent` | AI Agent        |
| `chain` | Basic LLM Chain |

For example:

```text
hi agent
```

is routed to the **AI Agent**, while:

```text
hi chain
```

is routed to the **Basic LLM Chain**.

---

## 🏗️ Workflow Architecture

```text
                    ┌─────────────────────┐
                    │   Chat Trigger      │
                    │  Receive Message    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │       Switch        │
                    │  Detect Agent/Chain  │
                    └───────┬───────┬──────┘
                            │       │
                 "agent" ──┘       └── "chain"
                            │       │
                            ▼       ▼
                   ┌────────────┐  ┌──────────────┐
                   │ AI Agent   │  │ Basic LLM    │
                   │            │  │ Chain        │
                   └─────┬──────┘  └──────┬───────┘
                         │                │
                         ▼                ▼
                  ┌────────────┐   ┌────────────┐
                  │ Simple     │   │ Groq Chat  │
                  │ Memory     │   │ Model      │
                  └────────────┘   └────────────┘
```

---

## 🔧 Components

### 1. Chat Trigger

The workflow starts with the **When Chat Message Received** node.

It receives the user's message through the n8n chat interface and passes the input to the routing logic.

### 2. Switch

The **Switch** node determines which workflow path should process the message.

It checks whether the incoming `chatInput` contains:

* `agent`
* `chain`

and routes the execution accordingly.

### 3. AI Agent

The AI Agent path uses n8n's **AI Agent** node.

It is connected to:

* Groq Chat Model
* Simple Memory

This makes it suitable for experimenting with an agent-style architecture and conversational context.

### 4. Basic LLM Chain

The Chain path uses n8n's **Basic LLM Chain** node.

The user's `chatInput` is passed directly as the prompt text and processed by the connected Groq Chat Model.

### 5. Groq Chat Model

Both paths use the Groq Chat Model with:

```text
Model: openai/gpt-oss-20b
```

The AI Agent and Basic LLM Chain each have their own model connection.

### 6. Simple Memory

The AI Agent includes **Simple Memory** with a context window length of `2`.

This provides short-term conversational memory for the Agent path.

---

## 🎯 Purpose of the Experiment

This project was built to understand the practical difference between:

**LLM Chain**

> Input → LLM → Output

and

**AI Agent**

> Input → Agent → LLM + Memory → Response

The experiment provides a simple foundation for understanding when a straightforward LLM chain is sufficient and when an agent-based architecture becomes useful.

---

## 🧪 Example Inputs

### Test the Agent

```text
hi agent
```

The Switch routes the message to:

```text
Chat Trigger → Switch → AI Agent
```

### Test the Chain

```text
hi chain
```

The Switch routes the message to:

```text
Chat Trigger → Switch → Basic LLM Chain
```

---

## ⚙️ Requirements

Before importing the workflow, make sure you have:

* [n8n](https://n8n.io/)
* A Groq API account
* A configured Groq API credential in n8n
* Access to the selected Groq model

> **Note:** API credentials are not included in this repository. Configure your own credentials after importing the workflow.

---

## 🚀 How to Use

### 1. Import the Workflow

Import the JSON workflow file into your n8n instance.

### 2. Configure Credentials

Open the Groq Chat Model nodes and select/configure your own **Groq API credential**.

### 3. Open the Chat Interface

Start the workflow and open the n8n chat interface.

### 4. Test Both Paths

Send messages containing:

```text
agent
```

and

```text
chain
```

to test the two different architectures.

---

## 📁 Project Structure

```text
agent-vs-chain/
│
├── workflow.json
└── README.md
```

---

## 🧠 Key Concepts Learned

* n8n workflow routing
* Switch nodes
* AI Agent architecture
* Basic LLM Chains
* LLM model integration
* Conversational memory
* Groq integration
* Comparing agent-based and chain-based workflows

---

## ⚠️ Limitations

This is a **learning and experimentation workflow**, not a production-ready AI assistant.

The routing currently relies on the message containing the keywords `agent` or `chain`. Messages that do not match either condition are not routed to an AI processing path.

The memory configuration is also intentionally simple and limited to a short context window.

---

## 🔮 Possible Improvements

Future versions could include:

* Dynamic model selection
* Better intent-based routing
* Tool integration with the AI Agent
* Long-term conversation memory
* RAG integration
* Multiple specialized agents
* Error handling and fallback routes
* Performance and response-time comparison
* Token usage and cost comparison

---

## 📚 Learning Focus

This workflow is part of my **n8n Workflow Experiments** collection, where I build small practical automations to understand AI automation concepts and gradually move toward production-oriented workflows.

---

## 📄 License

This project is available for educational and experimentation purposes.

# Phase 2: Immersion (Week 1)

This week serves as an accelerated diagnostic and foundational phase, bridging the gap between theoretical AI architectures and hands-on, production-grade automated systems. 

## 📈 Weekly Objectives
* Conceptualize and deploy decoupling strategies for multi-stage RAG (Retrieval-Augmented Generation) pipelines.
* Design and implement state management architectures integrating LLMs with relational database backends.
* Deploy autonomous conversational agents exposed via production channels (Telegram) using advanced orchestration.

---

## 📚 Technical Log: Lectures & Architecture

### 🧠 Lecture 01: The Agent's Brain — RAG, Embeddings, & n8n
* **Core Concepts:** * Understanding the cognitive mechanics of an autonomous agent and how to extend its knowledge base dynamically.
  * Analyzing the mathematics of high-dimensionality text vectorization via semantic embeddings.
* **Architectural Implementation:**
  * Developed an decoupled, two-part pipeline in n8n:
    1. **Ingestion Layer (ETL):** Automated fetching of raw documents, handling chunking policies, and processing text into vectors using `Cohere Embeddings` to build a localized `Simple Vector Store`.
    2. **Execution Layer (Inference):** Mapping user inputs to an `AI Agent` node powered by a `Cohere Chat Model`, forcing deterministic context retrieval via vector similarity tools.

### 💾 Lecture 02: Memory & Data — Integrating AI with MySQL
* **Core Concepts:**
  * Moving past volatile, short-term in-memory storage (`Simple Memory`) to establish persistent sliding-window historical context.
  * Managing structured enterprise data and execution logs within a relational database management system (RDBMS).
* **Architectural Implementation:**
  * Connecting stateful AI workflows to a `MySQL` instance to handle context retention, session persistence, and transactional logs.

### 🤖 Lecture 03: Real-World Product — Agents with Telegram & Automation
* **Core Concepts:**
  * Transitioning an internal development workflow into an end-user facing conversational product.
  * Event-driven architectures triggered by external application webhooks.
* **Architectural Implementation:**
  * Exposing the orchestrated n8n AI Agent backend via the `Telegram Receiver` API/Webhook infrastructure to handle asynchronous user interactions in real time.

---

## 🛠️ Proof of Work & Source Code
* **Decoupled RAG Workflow Components:**
  * [📥 ETL Ingestion Workflow Schema](./src/pipeline-etl-flow.json) — *Local vectorization pipeline.*
  * [🤖 Conversational Agent Workflow Schema](./src/ai-agent-flow.json) — *Execution layer with memory mechanisms.*
* **Production Channels:** Telegram Bot Integration endpoints and configuration manifests.

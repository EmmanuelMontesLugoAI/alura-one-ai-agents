# Lecture 01

This lecture serves as an accelerated architectural baseline, transitioning from basic API consumption into building decoupled, stateful, and production-ready Retrieval-Augmented Generation (RAG) systems.

## 📈 Weekly Objectives
* **Pipeline Decoupling:** Separate data ingestion routines (ETL) from real-time runtime inferences.
* **State & Memory Management:** Establish persistent relational schemas to move past volatile, short-term conversational memory.
* **Production Deployment:** Bridge internal backend automation with end-user channels via webhooks and external APIs.

---

## 📚 Technical Log: Lecture Breakdowns

### 🧠 Lecture 01: The Agent's Brain — Decoupled RAG & Embeddings
Instead of relying on monolithic architectures, this implementation splits the AI’s cognitive overhead into a specialized, two-tier system orchestrated via **n8n**.

#### A. Primary Workflow: Ingestion & ETL Pipeline
* **Visual Topology:** See `img/primary-etl-pipeline.png`
* **Mechanics:** * **Trigger:** Instantiated via manual or web-hooked execution.
  * **Ingestion:** Fetches unstructured text documents dynamically from remote data layers via an HTTP GET request layer.
  * **Transformation (Chunking):** The `Default Data Loader` parses incoming data stream payloads and enforces text-splitting token limits.
  * **Vectorization:** Text chunks are transformed into vector embeddings via the `Cohere Embeddings` model.
  * **Storage (Load):** Chunks are cached natively inside a localized `Simple Vector Store`.

#### B. Secondary Workflow: Conversational AI Agent with Dynamic Grounding
* **Visual Topology:** See `img/secondary-chat-agent.png`
* **Mechanics:**
  * **Trigger:** Instantiated asynchronously upon user message reception via the chat client interface.
  * **Reasoning Engine:** Powered by the `Cohere Chat Model` for deep intent mapping.
  * **State Management:** Uses `Simple Memory` to retain short-term sliding-window chat history natively inside the workspace execution context.
  * **Tool Routing:** Equipped with a vector search tool pointing directly to the local vector store, ensuring deterministic, factual responses.

---

## 🗂️ Verification & Core Deliverables

### 1. Source Workflows (n8n JSON schemas)
* [📥 01-primary-etl-pipeline.json](./src/01-primary-etl-pipeline.json) — Production canvas orchestration for data fetching, document parsing, semantic chunking, and localized embedding indexation.
* [🤖 02-secondary-chat-agent.json](./src/02-secondary-chat-agent.json) — Runtime execution engine containing LLM parameters, memory structures, and automated similarity-search routing tools.

---
*Maintained by Emmanuel Montes Lugo — Specialist in Scalable Solutions.*

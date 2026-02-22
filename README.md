# Enterprise Agentic RAG Reference Architecture

An enterprise-grade Retrieval-Augmented Generation (RAG) reference implementation using Azure AI Foundry, Azure AI Search (Agentic Retrieval), and GPT-5.

This repository demonstrates:

- Agentic Retrieval architecture
- Multi-LLM orchestration (Query Planner + Response Generator)
- Long-term memory integration
- Secure API exposure
- Manual + Automated evaluation
- AI Red Teaming and risk simulation
- OOTB Enterprise governance - **Tracing /Observability, Monitoring (LLM Ops)**

---

# Executive Summary

This project implements a production-style RAG architecture using Azure AI Foundry and Azure AI Search.

The system:

- Indexes enterprise PDFs from Blob Storage
- Uses Agentic Retrieval for intelligent query planning (using GPT-4.1 mini)
- Grounds responses using retrieved document chunks
- Applies GPT-5 for final reasoning and response synthesis
- Exposes the agent via secure REST endpoint
- Includes structured evaluation and red team validation

---

# High-Level Architecture

## Logical Flow
<p align="center">
  <img src="architecture\High Level Architecture.png" width="1500"/>
</p>
<p align="center"><em>
Figure 1: User Application /workflow → API Gateway → Foundry Agent → Knowledge Base → Knowledge Sources → GPT-5 → Response.
</em></p>

---

# Agentic Retrieval Execution Flow

The system uses Azure AI Search Agentic Retrieval:

1. Application calls Knowledge Base (retrieve action)
2. Query + conversation history sent to GPT-4.1 mini
3. Query broken into structured subqueries
4. Parallel execution against knowledge sources
5. Semantic reranking applied
6. Citations extracted
7. Merged content returned to Agent
8. GPT-5 generates final grounded response

<p align="center">
  <img src="architecture\Execution Flow.png" width="800"/>
</p>
<p align="center"><em>
Figure 2: UML Execution Flow.
</em></p>

---

# Security & API Exposure

The published agent can be exposed via:

- AI Gateway / API Management
- Authentication, Authorization & Audit
- Rate limiting
- Input validation
- Monitoring
- Agent Guardrails /Content Safety

---

# Evaluation Strategy

This prototype evaluates three levels of evaluation:

## Manual Evaluation
- Multi-turn validation
- Citation accuracy checks
- Hallucination detection
- Prompt grounding validation
  
<p align="center">
  <img src="evaluation\screenshots\manual\Manual Evaluation 1.png" width="1500"/>
</p>
<p align="center"><em>
Figure 3: Manual Evaluation.
</em></p>

## Automated Evaluation
- Synthetic dataset evaluation
- Curated JSONL dataset evaluation
- Metric-based scoring

<p align="center">
  <img src="evaluation\screenshots\automated\Auto_Evaluation_Prepared_Dataset_Results.png" width="1500"/>
</p>
<p align="center"><em>
Figure 4: Automated Evaluation.
</em></p>

## AI Red Teaming
- Prompt injection simulation
- Data exfiltration testing
- Prohibited action testing
- Misuse detection

<p align="center">
  <img src="evaluation\screenshots\Red Teaming\Read Teaming Summary.png" width="1500"/>
</p>
<p align="center"><em>
Figure 5: AI Red Team Evaluation.
</em></p>

<p align="center">
  <img src="evaluation\screenshots\Red Teaming\PyRIT Framework.jpg" width="1500"/>
</p>
<p align="center"><em>
Figure 6: Foundry Red Team Agent Framework (PyRIT - Python Risk Identification Tool) .
</em></p>

---

# Disclaimer

This repository demonstrates architecture and engineering practices for enterprise AI systems.  
It does not contain proprietary data or confidential configurations.

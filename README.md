# SiteSight
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> Turn any website into a structured, queryable API using the power of Generative AI.

**[Project Name]** is a modern data extraction platform that overcomes the limitations of traditional, brittle web scrapers. Instead of relying on fragile CSS selectors or XPath, it leverages Large Language Models (LLMs) to understand and parse web content based on natural language instructions.

Define a target, describe the data you need, and get back clean, structured JSON. Then, ask questions about your collected data in plain English.

---

## ✨ Key Features

* **Natural Language Extraction:** Simply tell the system what you want to extract in plain English (e.g., "get the name, price, and rating for all products").
* **Custom Schemas:** Define the exact JSON structure you need for the output, ensuring clean and predictable data.
* **Automated Data Refresh:** Set up scheduled jobs to automatically re-scrape targets and keep your dataset up-to-date.
* **AI-Powered Q&A:** Go beyond raw data. Use a Retrieval-Augmented Generation (RAG) pipeline to ask complex questions about the information you've collected.
* **Resilient & Robust:** Because it understands content semantically, it's far less likely to break when a website's layout changes.
* **API-First Design:** A clean, well-documented API allows for easy integration with other applications and services.

## 🏗️ How It Works: Architecture Overview

This project is built on a modern, event-driven microservices architecture designed for scalability and performance.

1.  **API Gateway & Backend (Go):** A high-performance backend built with Go manages users, targets, schemas, and API requests. It serves as the primary entry point to the system.
2.  **AI Extraction Service (Python):** The core intelligence of the platform. This service, written in Python, uses libraries like `LangChain` and `Playwright` to:
    * Fetch web content from a target URL.
    * Construct a detailed prompt for a Large Language Model (LLM).
    * Call the LLM to perform the semantic extraction and formatting.
3.  **Asynchronous Task Queue (e.g., RabbitMQ / AWS SQS):** To handle long-running scraping jobs without blocking the API, requests are published to a message queue.
4.  **Scheduler (e.g., AWS EventBridge / Google Cloud Scheduler):** Manages cron jobs that periodically trigger data refresh tasks for all active targets.
5.  **Dual Datastores:**
    * **PostgreSQL:** Stores structured user data, target configurations, and the final extracted JSON.
    * **Vector Database (e.g., Weaviate / Pinecone):** Stores embeddings of the extracted data to power the fast, semantic search required for the Q&A feature.

This setup ensures that the system is responsive, resilient, and ready to scale.

---

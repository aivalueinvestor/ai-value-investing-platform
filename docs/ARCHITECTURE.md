# AI Value Investing Platform - Architecture

# Architecture Philosophy

The system should be designed as a Modular Monolith initially while remaining ready for future migration to Microservices.

This approach provides:

* Simpler development
* Lower operational cost
* Faster learning
* Easier debugging
* Future scalability

The system should follow:

* Domain Driven Design
* API First Design
* Clean Architecture Principles
* Plug-and-Play Components
* Cloud Native Practices

---

# High Level Architecture

Frontend

↓

API Layer

↓

Business Modules

↓

Data Layer

↓

Infrastructure Layer

---

# Technology Stack

## Backend

Python

FastAPI

---

## Database

PostgreSQL

---

## Cache

Redis

---

## AI Framework

LangChain

LangGraph

---

## Vector Database

Initial:

ChromaDB

Future:

Pinecone

Weaviate

FAISS

---

## LLM Providers

Supported through abstraction layer.

Examples:

* OpenAI
* Gemini
* Claude
* Ollama
* Future Providers

---

## Deployment

Docker

Docker Compose

GitHub Actions

Future:

Kubernetes

---

# System Modules

## 1. Auth Module

Responsibilities:

* Registration
* Login
* JWT Authentication
* User Management
* Roles and Permissions

Own Components:

* API
* Service
* Repository
* Models

---

## 2. Portfolio Module

Responsibilities:

* Portfolio Management
* Watchlists
* Holdings
* Transactions

Own Components:

* API
* Service
* Repository
* Models

---

## 3. Company Analysis Module

Responsibilities:

* Company Information
* Financial Statements
* Ratios
* Growth Metrics
* Quality Metrics

Own Components:

* API
* Service
* Repository
* Models

---

## 4. Mutual Fund Module

Responsibilities:

* Fund Analysis
* Fund Comparison
* Performance Metrics
* Portfolio Overlap

Own Components:

* API
* Service
* Repository
* Models

---

## 5. Financial Data Module

Responsibilities:

* Data Collection
* ETL Pipelines
* Data Refresh
* Data Validation

Own Components:

* API
* Service
* Repository
* Models

---

## 6. AI Module

Responsibilities:

* Prompt Management
* LLM Communication
* Response Generation
* Tool Calling

Own Components:

* API
* Service
* Provider Layer

---

## 7. RAG Module

Responsibilities:

* Document Ingestion
* Chunking
* Embedding Generation
* Retrieval

Own Components:

* API
* Service
* Vector Store

---

## 8. Agent Module

Responsibilities:

* Research Agent
* Comparison Agent
* Portfolio Agent
* Workflow Management

Own Components:

* API
* Service
* Agent Layer

---

# Backend Folder Structure

backend/

app/

api/

services/

repositories/

models/

schemas/

core/

modules/

tests/

---

# Module Structure Example

modules/

portfolio/

api/

service/

repository/

model/

schema/

tests/

The same structure should be followed for every module.

---

# Database Strategy

Initially:

Single PostgreSQL Instance

Logical Separation:

* users
* portfolios
* companies
* financials
* mutual_funds
* reports

Future:

Separate databases if required.

---

# AI Architecture

Never directly use a specific AI provider.

Wrong:

OpenAI API calls scattered everywhere.

Correct:

LLM Provider Interface

Provider Implementations:

* OpenAI Provider
* Gemini Provider
* Ollama Provider
* Claude Provider

This allows easy migration later.

---

# Vector Database Architecture

Vector Store Interface

Methods:

* insert
* search
* delete

Implementations:

* ChromaDB
* Pinecone
* Weaviate
* FAISS

No business code should depend on a specific vector database.

---

# Deployment Strategy

Development:

Docker Compose

Production:

Cloud VM

Future:

Kubernetes

---

# Monitoring

Phase 1

Application Logs

Phase 2

Metrics

Phase 3

Prometheus

Grafana

---

# CI/CD

GitHub Actions

Pipeline:

* Run Tests
* Build Docker Images
* Static Analysis
* Deployment

---

# Coding Standards

Every Feature Must Have:

* API Layer
* Service Layer
* Repository Layer
* Unit Tests
* Documentation

---

# Branching Strategy

main

develop

feature/*

Examples:

feature/auth

feature/portfolio

feature/rag

feature/agent

---

# Long-Term Scalability Goal

The system should be capable of evolving from:

Single Developer
↓
Small User Base
↓
Thousands of Users
↓
Commercial SaaS Product

without requiring a complete rewrite.
# A2S - AI Interior Design Recommendation Platform

Full-stack AI-powered recommendation system for interior product discovery, filtering, and planning.

## Project Summary

This project is built as a production-style multi-service platform with:
- A React frontend for user interaction and visualization
- A Spring Boot backend for API orchestration and security
- A Python LLM engine for conversational intent handling and recommendation logic
- A structured product catalog pipeline for filtering and ranking

The system supports natural-language queries and converts them into structured constraints (room, budget, style, dimensions, etc.) to return relevant product recommendations.

## Core Features

- Conversational recommendation assistant with context memory
- Multi-criteria catalog filtering and weighted ranking
- Cross-module integration between UI, backend APIs, and AI service
- Product visualization pages, gallery workflows, and 3D workspace modules
- Error boundaries, validation layers, and reusable service abstractions

## System Architecture

The platform follows a layered architecture:

1. Presentation Layer (`frontend/`)
- React + Vite application
- Page-level workflows (home, dashboard, design details, AI consultant, 3D space)
- Reusable UI components and client-side state utilities

2. Service/API Layer (`backend/`)
- Spring Boot REST controllers
- Authentication and user flows
- Product and design endpoints
- Security configuration and JWT support

3. Intelligence Layer (`LLM/`)
- Prompt-driven agent orchestration
- Context manager for multi-turn interactions
- Request-to-filter extraction and response generation

4. Data Layer (`LLM/data/`, `cleaned_dataset.xlsx`)
- Catalog ingestion and normalization
- Filter engine for structured constraint matching
- Ranker for relevance scoring and top-N recommendations

## Workflow Overview

### End-to-End Request Flow

1. User enters query in frontend (example: budget + room + style).
2. Frontend sends request through service adapters.
3. Backend validates/authenticates request and routes to AI/data logic.
4. LLM module interprets natural language into structured filters.
5. Data pipeline applies filters and ranking on catalog data.
6. Ranked products and explanation response are returned.
7. Frontend renders results as cards, detail views, and related workflows.

### Conversation + Filtering Workflow

1. Current user message is appended to session context.
2. Agent merges prior context with new intent.
3. Filters are resolved (numeric + categorical + optional free-text).
4. Candidate products are scored and sorted.
5. Formatted response and product list are returned to UI.

## Repository Structure

```text
.
|-- backend/
|   |-- src/main/java/com/a2s/backend/
|   |   |-- controller/
|   |   |-- model/
|   |   |-- repository/
|   |   `-- security/
|   |-- src/main/resources/
|   `-- pom.xml
|-- frontend/
|   |-- components/
|   |-- pages/
|   |-- services/
|   |-- hooks/
|   `-- package.json
|-- LLM/
|   |-- agent/
|   |-- data/
|   |-- scraper/
|   |-- utils/
|   `-- requirements.txt
|-- cleaned_dataset.xlsx
|-- run.bat
`-- README.md
```

## Technology Stack

- Frontend: React, Vite, JavaScript
- Backend: Java, Spring Boot, Maven
- AI Layer: Python, prompt-based LLM orchestration
- Data Processing: Python (filtering, ranking, transformation)
- Security: JWT-based authentication modules

## Local Setup

### Prerequisites

- Node.js 18+
- Java 17+
- Maven 3.9+
- Python 3.10+

### 1. Clone Repository

```bash
git clone https://github.com/Asha0509/A2S_Design_Ecommerce_Platform.git
cd A2S_Design_Ecommerce_Platform
```

### 2. Run Frontend

```bash
cd frontend
npm install
npm run dev
```

### 3. Run Backend

```bash
cd backend
mvn clean install
mvn spring-boot:run
```

### 4. Run LLM Service

```bash
cd LLM
pip install -r requirements.txt
python app.py
```

## Engineering Highlights (Resume-Oriented)

- Designed and integrated a multi-service architecture across React, Spring Boot, and Python AI modules.
- Implemented context-aware recommendation workflows with structured filter extraction and ranking.
- Built modular frontend systems (pages/components/services/hooks) for maintainable UI scaling.
- Developed backend security and API layers for authentication, product, and user-centric flows.
- Organized data ingestion, filtering, and ranking pipeline for recommendation relevance.

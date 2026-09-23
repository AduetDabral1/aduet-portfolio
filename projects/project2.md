# Zomato Data Engineering & AI Platform

## Project Walkthrough
https://github.com/user-attachments/assets/71e2af11-3765-4256-99d2-8461376a6106

An end-to-end **data engineering + AI project** built using the Zomato
Kaggle dataset and designed to simulate a real-world analytics platform.

The project takes raw Zomato data from **Amazon S3 → Snowflake → dbt →
BI**, and adds an AI layer for **review enrichment, RAG, and
natural-language SQL**.

![Architecture](architecture.png)

------------------------------------------------------------------------

## Overview

The platform brings together a modern data stack into one end-to-end
pipeline:

**Zomato Data → S3 → Snowflake → dbt → AI → Streamlit / SnowSight**

  -----------------------------------------------------------------------
  Area                                What it does
  ----------------------------------- -----------------------------------
  **Data Ingestion**                  Loads Zomato CSV data into Amazon
                                      S3 and Snowflake

  **Data Transformation**             Cleans, models, tests, and prepares
                                      data with dbt

  **AI Enrichment**                   Turns customer reviews into
                                      structured insights

  **RAG**                             Lets users chat with the review
                                      data

  **Text-to-SQL**                     Lets users ask analytical questions
                                      in natural language

  **Orchestration**                   Runs the data + AI pipeline with
                                      Airflow

  **Analytics**                       Serves curated data through
                                      Streamlit and SnowSight
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## Data Architecture

The project follows a Bronze → Silver → Gold approach:

  -----------------------------------------------------------------------
  Layer                   Platform                Purpose
  ----------------------- ----------------------- -----------------------
  **Source**              Kaggle                  Zomato dataset
                                                  containing users,
                                                  restaurants, orders,
                                                  menu, reviews, etc.

  **Lake / Landing**      Amazon S3               Stores the raw CSV
                                                  files before warehouse
                                                  ingestion

  **Bronze**              Snowflake RAW           Raw representation of
                                                  the source data

  **Silver**              Snowflake + dbt STAGING Cleaned, typed,
                                                  standardized, and
                                                  transformed data

  **Gold**                Snowflake + dbt MARTS   Business-ready
                                                  dimensions, facts, and
                                                  analytical marts

  **Serve**               Streamlit               Dashboards,
                                                  exploration, and
                                                  self-service analytics
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## AI Layer

The AI layer adds three different ways to work with the data.

### 1. LLM Enrichment

Customer reviews are processed by an LLM to generate structured insights
that can be stored and analyzed in Snowflake.

``` text
Reviews → LLM → Enriched Insights → Snowflake → Analytics
```

This treats the LLM as a **data transformation step**, rather than only
as a chatbot.

### 2. RAG --- Chat With Your Reviews

Review content is converted into embeddings and stored in a vector store
so users can ask questions about customer feedback.

``` text
Reviews → Embeddings → Vector Store → RAG → Grounded Answers
```

The application retrieves relevant review context before generating the
response.

### 3. Text-to-SQL --- Chat With Your Warehouse

Users can ask questions about the curated warehouse using natural
language.

``` text
Question → Text-to-SQL → SELECT-only Guard → Snowflake → Result
```

The application works against the **Gold / MARTS** layer and is designed
for read-only analytical querying.

------------------------------------------------------------------------

## Orchestration

Apache Airflow orchestrates the main pipeline:

``` text
upload_raw
    ↓
dbt_build_core
    ↓
enrich_reviews
    ↓
dbt_build_all
```

  Task               Purpose
  ------------------ -----------------------------------------------
  `upload_raw`       Moves the source data into the ingestion flow
  `dbt_build_core`   Builds the core Silver / staging layer
  `enrich_reviews`   Runs AI enrichment on reviews
  `dbt_build_all`    Builds the downstream Gold / marts layer

------------------------------------------------------------------------

## Tech Stack

  Category               Technology
  ---------------------- -------------------------------------------------
  **Source**             Zomato Kaggle Dataset
  **Cloud Storage**      Amazon S3
  **Data Warehouse**     Snowflake
  **Transformation**     dbt
  **Orchestration**      Apache Airflow
  **Language**           Python
  **Data Processing**    Pandas
  **LLM**                OpenAI / LLM API
  **Embeddings**         `text-embedding-3-small`
  **Vector Search**      Vector Store
  **AI Applications**    LLM Enrichment, RAG, Text-to-SQL
  **BI / Application**   Streamlit
  **Warehouse UI**       SnowSight
  **Security**           AWS IAM, KMS, Snowflake roles & access controls

------------------------------------------------------------------------

## Project Structure

``` text
zomato-data-platform/
│
├── airflow/
│   └── dags/
│       └── zomato_dag.py
│
├── dbt/
│   └── zomato/
│       ├── models/
│       │   ├── staging/
│       │   └── marts/
│       ├── macros/
│       └── dbt_project.yml
│
├── ai/
│   ├── enrich_reviews.py
│   ├── rag_chat.py
│   └── text_to_sql.py
│
├── snowflake/
│   ├── 01_setup.sql
│   ├── 02_storage_integration.sql
│   ├── 03_stage_and_format.sql
│   ├── 04_raw_table.sql
│   └── 05_copy_into.sql
│
├── streamlit/
│   └── ...
│
└── README.md
```

------------------------------------------------------------------------

## Getting Started

The project is built around **AWS, Snowflake, dbt, Airflow, and
Python**.

At a high level:

1.  Place the Zomato CSV data in S3.
2.  Configure the Snowflake/S3 integration and load the RAW layer.
3.  Run the dbt project to build the Silver and Gold layers.
4.  Configure the AI environment and run review enrichment.
5.  Run the RAG and Text-to-SQL applications through Streamlit.
6.  Use Airflow to orchestrate the complete workflow.

Keep credentials and API keys outside the repository using the
appropriate environment/configuration mechanism.

------------------------------------------------------------------------

## Why This Project?

The goal is to demonstrate how a traditional data platform can evolve
into an **AI-enabled analytics platform**.

Instead of treating AI as a standalone chatbot, the project connects AI
directly to the data lifecycle:

``` text
                  Zomato Data
                       │
                       ▼
                  S3 / Snowflake
                       │
                       ▼
                      dbt
                       │
                       ▼
                Curated Data Layer
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
    LLM Enrichment    RAG      Text-to-SQL
          │            │            │
          └────────────┼────────────┘
                       ▼
                Streamlit / BI
```

It brings together **data engineering, analytics, orchestration, and
AI** in a single end-to-end project.

------------------------------------------------------------------------

## Disclaimer

The base dataset is sourced from Kaggle. The AI-enriched review data is
generated for this project to demonstrate how AI enrichment could be
incorporated into a real-world data pipeline.

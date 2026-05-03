# Uber Real-Time Data Engineering Project

End-to-end data pipeline for processing Uber ride data using Azure services and Apache Spark.

## Overview

This project simulates Uber ride booking events and processes them through a real-time data pipeline:

1. **FastAPI** application to generate and serve ride bookings
2. Send ride events to **Azure Event Hubs**
3. Ingest raw data into **Azure Data Lake Storage** (Bronze layer)
4. Transform and clean data using **Apache Spark** (Silver layer)
5. Create analytics-ready tables (Gold layer)

## Tech Stack

- **FastAPI** - REST API for ride booking
- **Azure Event Hubs** - Real-time event streaming
- **Azure Data Lake Storage (Gen2)** - Cloud storage
- **Apache Spark / PySpark** - Data transformation
- **Python Faker** - Synthetic data generation
- **Azure Synapse Analytics** - SQL queries and analytics

## Setup

1. Clone the repo and create a virtual environment:
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

2. Set up your `.env` file with Azure Event Hub credentials:
```
CONNECTION_STRING=your-event-hub-connection-string
EVENT_HUBNAME=your-event-hub-name
```

3. Run the API:
```bash
python3 api.py
```

Visit `http://localhost:8000/` to access the web interface.

## Project Files

- `api.py` - FastAPI application with ride booking endpoint
- `connection.py` - Azure Event Hub producer to send events
- `data.py` - Data generation using Faker, ride data mappings
- `model.py` - Data models

**Code_Files/** contains the data pipeline:
- `bronze_adls.ipynb` - Reads from Event Hub, stores raw data to ADLS
- `silver_obt.ipynb` - Cleans and transforms data
- `silver_obt.sql` - SQL transformations
- `ingest.py` - Kafka consumer for Event Hub

## How It Works

1. FastAPI endpoint generates synthetic Uber ride data
2. Data is sent to Azure Event Hubs in real-time
3. Spark jobs read from Event Hubs and store raw data to ADLS (Bronze layer)
4. Data is cleaned, deduplicated, and enriched (Silver layer)
5. Analytics-ready tables created for reporting (Gold layer)




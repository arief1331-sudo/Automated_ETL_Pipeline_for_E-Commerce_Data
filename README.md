# Automated ETL Pipeline for E-Commerce Data

## Overview
This project (Milestone 3) demonstrates an automated Extract, Transform, Load (ETL) data pipeline for processing Amazon product data. The pipeline is built using Apache Spark (PySpark) for distributed data processing, Apache Airflow for workflow orchestration, and MongoDB Atlas for NoSQL data storage. The entire setup is containerized using Docker, and data validation is performed using Great Expectations.

## Presentation
[View Canva Presentation](https://www.canva.com/design/DAG_rzX_qXo/vshC0wVkRb98XO7VKf6E8w/edit?utm_content=DAG_rzX_qXo&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

## Tech Stack
- **Data Processing:** Apache Spark (PySpark)
- **Orchestration:** Apache Airflow
- **Database:** MongoDB Atlas (NoSQL)
- **Containerization:** Docker & Docker Compose
- **Data Quality & Validation:** Great Expectations
- **Languages/Libraries:** Python, Pandas

## Project Structure
- `extract.py`: Reads the raw Amazon CSV data (`P2M3_arief_bagus_nugraha_data_raw.csv`) into a PySpark DataFrame.
- `transform.py`: Cleans the data by generating a unique `Transaction_ID`, extracting the `Main_Category`, and using Regex to format numeric fields like `Discounted_Price` and `Rating`.
- `load.py`: Converts the processed PySpark DataFrame to a dictionary format and inserts it into a MongoDB Atlas collection.
- `main.py`: A standalone script to run the entire ETL process sequentially.
- `P2M3_arief_bagus_nugraha_DAG.py`: Apache Airflow DAG script to schedule and orchestrate the ETL tasks automatically.
- `P2M3_arief_bagus_nugraha.ipynb`: Jupyter Notebook detailing data validation rules (e.g., row count checks) using Great Expectations.
- `docker-compose.yaml`: Docker configuration to spin up a PySpark Jupyter Notebook environment.

## ETL Workflow
1. **Extract**: Data ingestion from local raw CSV files.
2. **Transform**: 
   - Feature Engineering (e.g., extracting primary categories).
   - Data Cleaning (removing non-numeric characters from price and rating fields).
   - Identity mapping (creating unique identifiers).
3. **Load**: Pushing the cleaned, validated records into a cloud NoSQL database (MongoDB Atlas).

## How to Run
1. **Start Environment**: Run `docker-compose up -d` in the directory containing `docker-compose.yaml` to spin up the PySpark container.
2. **Run Locally**: Execute `python main.py` to trigger the ETL pipeline directly.
3. **Run via Airflow**: Place the DAG script in your Airflow `dags` folder and turn it on via the Airflow UI to run it according to the schedule.

## Author
**Arief Bagus Nugraha** 
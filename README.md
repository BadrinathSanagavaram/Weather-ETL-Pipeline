# Weather ETL Pipeline

**Author:** Badrinath Sanagavaram  
**Technologies:** Apache Airflow, PostgreSQL, Astro CLI, Docker, Python, Open-Meteo API, DBeaver

## 📌 Project Overview

This project automates the extraction of real-time weather data from the Open-Meteo API, transforms it into a structured format, and loads it into a PostgreSQL database using Apache Airflow. The goal is to demonstrate a real-world ETL pipeline in a containerized environment.

---

## 🔧 Tools and Setup

- **Docker & Docker Compose**: To run PostgreSQL in an isolated container.
- **Astro CLI**: For managing and deploying the Airflow environment locally.
- **Apache Airflow**: For orchestrating and scheduling the ETL tasks.
- **PostgreSQL**: The target database to store transformed weather data.
- **DBeaver**: To connect to the Postgres container and validate the data.

---

## 🧱 DAG Workflow Structure

The Airflow DAG, named `weather_etl_pipeline`, runs daily and consists of three core tasks:

1. **Extract**: Uses `HttpHook` to pull data from the Open-Meteo API.
2. **Transform**: Parses JSON to extract key fields like temperature and windspeed.
3. **Load**: Inserts data into a PostgreSQL table using `PostgresHook`.

All tasks are defined using Airflow's `@task` decorator.

---

## 📈 Process Flowchart

graph TD
    A[Start DAG] --> B[Extract Weather Data from API]
    B --> C[Transform JSON Response]
    C --> D[Create/Insert into PostgreSQL Table]
    D --> E[Validate using DBeaver]
    E --> F[Success]

## 🗃️ Database Design

**Table:** `weather_data`  

**Fields:**
- `latitude` (FLOAT)  
- `longitude` (FLOAT)  
- `temperature` (FLOAT)  
- `windspeed` (FLOAT)  
- `winddirection` (FLOAT)  
- `weathercode` (INT)  
- `timestamp` (TIMESTAMP DEFAULT CURRENT_TIMESTAMP)  

---

## ✅ Validation

Validation was done using DBeaver by connecting to the Postgres container via:

- **Host:** localhost  
- **Port:** 5432  
- **User:** postgres  
- **Password:** postgres  

A SQL `SELECT * FROM weather_data;` confirmed correct data ingestion and schema structure.

---

## 📌 Key Takeaways

- Hands-on experience with Airflow DAGs, hooks, and task orchestration.  
- Real-time API integration with Open-Meteo.  
- Containerized database interaction.  
- SQL-based validation and data auditing with DBeaver.  

---

## 🚀 Future Enhancements

- Add alerting in case of API/data failures.  
- Support multiple geolocations dynamically.  
- Extend transformations with trend analytics or ML predictions.  

---

## 📁 File Structure

- `ETL-Weather.py` – Contains the DAG and ETL logic.  
- `docker-compose.yml` – Defines the Postgres container.  
- `requirements.txt` – Includes Airflow provider dependencies.  
- `airflow_settings.yaml` – Optional connection/variable definitions.

# Output samples:

![Screenshot 2025-05-27 at 2 41 51 AM](https://github.com/user-attachments/assets/e9f646cd-06e3-4941-9c99-88b144313356)


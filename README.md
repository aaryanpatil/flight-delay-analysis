# Flight Delay Data Pipeline (2024)

This project implements a complete data pipeline for analyzing U.S. airline delay data for the year 2024. It covers data ingestion, transformation, storage in multiple formats, and integration with a NoSQL database. The pipeline was developed as part of a graduate-level course on big data systems and demonstrates practical applications of several course modules including virtualization, file formats, NoSQL, and data modeling.

## Objectives

- Ingest monthly CSV files from the Bureau of Transportation Statistics (BTS)
- Clean and transform the data using pandas
- Store the cleaned dataset in both CSV and Parquet formats
- Insert a subset of the data into a MongoDB Atlas cluster (NoSQL)
- Compare performance of CSV vs Parquet in terms of load and analysis time
- Visualize trends in airline delays across months, carriers, and causes

## Dataset

- Source: [Bureau of Transportation Statistics](https://transtats.bts.gov/)
- Period: January–December 2024
- Format: CSV (raw), converted to Parquet
- Size: ~85 MB
- Fields: carrier, airport, arrival flights, delay minutes by cause, etc.

## Technologies Used

- Python (pandas, matplotlib)
- Apache Parquet (via fastparquet)
- MongoDB Atlas (NoSQL database)
- Jetstream2 (cloud VM platform)
- Jupyter Notebook


## Pipeline Summary

1. **Data Ingestion**: 12 monthly CSVs were downloaded, organized, and batch loaded using `glob` and `pandas.concat()` into a single DataFrame.
2. **Transformation**: Created a `reporting_date` field, dropped unnecessary columns, and calculated normalized metrics such as average carrier delay per flight.
3. **Storage**: The dataset was stored in both CSV and Parquet formats. Parquet was used to demonstrate columnar storage efficiency.
4. **MongoDB Integration**: A subset of fields was converted into JSON-like records and inserted into a MongoDB Atlas cloud cluster using PyMongo.
5. **Analysis and Visualization**: Load and query times were benchmarked across formats. Visualizations included top delay months, worst-performing airlines, and causes of delays.

## Key Insights

- Parquet outperformed CSV for both load and analysis time, even on modestly sized data.
- JetBlue and SkyWest showed the highest average carrier delay per flight.
- July and May were the most delay-heavy months, correlating with peak travel.
- NAS and weather-related issues caused the majority of delay minutes.

## Big Data Concepts Demonstrated

- Columnar storage (Parquet)
- Virtualized compute environment (Jetstream2)
- Schema-less document storage (MongoDB)
- Structured + semi-structured data handling
- Pipelining from ingestion to visualization
- Reproducibility via notebook-based reporting

## Limitations

- The dataset was processed on a single-node environment; no distributed cluster was involved.
- Due to Git remote issues on the Jetstream2 VM, the project was uploaded to GitHub from a local machine.

## How to Run

1. Clone the repository
2. Install required packages:
   
   pip install jupyter pandas matplotlib pyarrow pymongo

3. Run the following command:

   jupyter lab
4. Run the flight_delay_pipeline.ipynb Jupyter Notebook
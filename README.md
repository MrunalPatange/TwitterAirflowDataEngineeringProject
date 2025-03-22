# TwitterAirflowDataEngineeringProject


## Overview
This project extracts tweets from a Twitter user account (@elonmusk), processes the extracted data, and stores it as a CSV file. The ETL workflow is managed using Apache Airflow, which schedules and executes the tasks.

## Project Structure
```
├── twitter_commands.sh   # Shell script to set up dependencies
├── twitter_dag.py        # Airflow DAG definition for the ETL pipeline
├── twitter_etl.py        # Python script to fetch and process tweets
└── README.md             # Documentation
```

## Setup Instructions
### Prerequisites
Ensure you have the following installed:
- Python 3
- Apache Airflow
- Required Python libraries (pandas, tweepy, s3fs)

### Installation
Run the following command to install dependencies:
```sh
bash twitter_commands.sh
```
This script will:
- Update package lists
- Install `python3-pip`
- Install Apache Airflow
- Install required Python libraries

## Apache Airflow DAG
The `twitter_dag.py` file defines an Airflow DAG that schedules the Twitter ETL pipeline to run daily.

Key components:
- **DAG Configuration**: Sets up scheduling, retries, and failure notifications.
- **PythonOperator**: Runs the `run_twitter_etl` function.

## Running the ETL Pipeline
1. Start the Airflow scheduler and webserver:
   ```sh
   airflow scheduler &
   airflow webserver -p 8080 &
   ```
2. Trigger the DAG manually:
   ```sh
   airflow dags trigger twitter_dag
   ```
3. Monitor the DAG in the Airflow web UI at `http://localhost:8080`

## Contributing
Contributions are welcome! Feel free to open an issue or submit a pull request.

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.

## License
This project is licensed under the MIT License.


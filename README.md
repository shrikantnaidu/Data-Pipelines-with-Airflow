# Data-Pipelines-with-Airflow

# Context

A music streaming company, Sparkify, has decided that it is time to introduce more automation and monitoring to their data warehouse ETL pipelines and come to the conclusion that the best tool to achieve this is Apache Airflow.

They have decided to bring you into the project and expect you to create high grade data pipelines that are dynamic and built from reusable tasks, can be monitored, and allow easy backfills. They have also noted that the data quality plays a big part when analyses are executed on top the data warehouse and want to run tests against their datasets after the ETL steps have been executed to catch any discrepancies in the datasets.

The source data resides in S3 and needs to be processed in Sparkify's data warehouse in Amazon Redshift. The source datasets consist of JSON logs that tell about user activity in the application and JSON metadata about the songs the users listen to.

# Database schema

#### Table Overview

| Table | Description |
| --- | --- | 
| staging_events | Staging table for events data |
| staging_songs | Staging table for songs data|
| songplays | Table for the songs played |
| users | Table for the user data |
| songs | Table for the songs data |
| artists | Table for the artists data |
| time | Table for time-related data |


#### Staging Tables
- staging_events
- staging_songs

####  Fact Table
- songplays - records in event data associated with song plays i.e. records with page NextSong.  

`songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent`

#### Dimension Tables
- users - users in the app.  

`user_id, first_name, last_name, gender, level`
- songs - songs in music database. 

`song_id, title, artist_id, year, duration`
- artists - artists in music database.

`artist_id, name, location, lattitude, longitude`
- time - timestamps of records in songplays broken down into specific units. 

`start_time, hour, day, week, month, year, weekday`


# Project Structure
Files used on the project:

1. **dags/udac_example_dag.py** - The DAG definition file that defines the DAG schedule, tasks, and task dependencies.
2. **plugins/operators/** - Custom operator plugins used in the DAG.
3. **stage_redshift.py** - Stages data from S3 to Redshift.
4. **load_fact.py** - Loads data into a fact table in Redshift.
5. **load_dimension.py** - Loads data into dimension tables in Redshift.
6. **data_quality.py** - Runs data quality checks on Redshift tables.
7. **plugins/helpers/** - Helper modules used in the plugins.
8. **README.md** - documentation of the process, provides execution information on the project.


# Project: Sparkify Data Warehouse

## Introduction

A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud so that their analytics team can continue finding insights in what songs their users are listening to

## ETL Process:

The data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.
ETL Process will load data from S3 to staging tables on Redshift and execute SQL statements to create the analytics tables from these staging tables.

## Datawarehouse:

STAR Schema with the following fact and dimension tables are created for easier queries on song play analysis:

### Fact Table

songplays - records in event data associated with song plays i.e. records with page NextSong
songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

### Dimension Tables

1.	users - users in the app
user_id, first_name, last_name, gender, level
2.	songs - songs in music database
song_id, title, artist_id, year, duration
3.	artists - artists in music database
artist_id, name, location, lattitude, longitude
4.	time - timestamps of records in songplays broken down into specific units
start_time, hour, day, week, month, year, weekday

## Project Datasets

You'll be working with two datasets that reside in S3. Here are the S3 links for each:
•	Song data: s3://udacity-dend/song_data
•	Log data: s3://udacity-dend/log_data
Log data json path: s3://udacity-dend/log_json_path.json

### Song Dataset

Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.
song_data/A/B/C/TRABCEI128F424C983.json
song_data/A/A/B/TRAABJL12903CDCF1A.json
And below is an example of what a single song file, TRAABJL12903CDCF1A.json, looks like.
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}

### Log Dataset

The second dataset consists of log files in JSON format based on the songs in the dataset above. These are app activity logs from an imaginary music streaming app based on configuration settings.
The log files in the dataset are partitioned by year and month. For example, here are filepaths to two files in this dataset.
log_data/2018/11/2018-11-12-events.json
log_data/2018/11/2018-11-13-events.json





## Project Code Files

The project template includes four files:
•	create_table.py -> creates the  fact and dimension tables for the star schema in Redshift.
•	etl.py ->  loads data from S3 into staging tables on Redshift and then process that data into your analytics tables on Redshift.
•	sql_queries.py -> defines SQL statements, which will be imported into the two other files above.
•	README.md -> discussion on your process and decisions for this ETL pipeline.


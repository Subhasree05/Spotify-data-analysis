# Spotify  SQL Project and Query Optimization 

[Click Here to get Dataset](https://www.kaggle.com/datasets/sanjanchaudhari/spotify-dataset)

![Spotify Logo](https://github.com/Subhasree05/spotify-data-analysis-/blob/main/spotifyylogo.jpg)

## Overview
This project involves analyzing a Spotify dataset with various attributes about tracks, albums, and artists using **SQL**. It covers an end-to-end process of normalizing a denormalized dataset, performing SQL queries  and optimizing query performance.  

```sql
-- create table
DROP TABLE IF EXISTS spotify;
CREATE TABLE spotify (
    artist VARCHAR(255),
    track VARCHAR(255),
    album VARCHAR(255),
    album_type VARCHAR(50),
    danceability FLOAT,
    energy FLOAT,
    loudness FLOAT,
    speechiness FLOAT,
    acousticness FLOAT,
    instrumentalness FLOAT,
    liveness FLOAT,
    valence FLOAT,
    tempo FLOAT,
    duration_min FLOAT,
    title VARCHAR(255),
    channel VARCHAR(255),
    views FLOAT,
    likes BIGINT,
    comments BIGINT,
    licensed BOOLEAN,
    official_video BOOLEAN,
    stream BIGINT,
    energy_liveness FLOAT,
    most_played_on VARCHAR(50)
);
```
## Project Steps

### 1. Data Exploration
The dataset contains attributes such as:
- `Artist`: The performer of the track.
- `Track`: The name of the song.
- `Album`: The album to which the track belongs.
- `Album_type`: The type of album (e.g., single or album).
- Various metrics such as `danceability`, `energy`, `loudness`, `tempo`, and more.

### 2. Querying the Data
After the data is inserted, various SQL queries can be written to explore and analyze the data. 


## Query Optimization Technique 

To improve query performance, the following optimization steps were performed:

Initial Query Performance Analysis Using EXPLAIN

Query performance was first analyzed using the EXPLAIN command.

The query retrieved tracks based on the artist column, with the following performance metrics:

Execution Time (E.T.): 6 ms

Planning Time (P.T.): 0.17 ms

The screenshot below shows the EXPLAIN result before optimization:
      ![EXPLAIN Before Index](https://github.com/Subhasree05/spotify-data-analysis-/blob/main/before_query_optimization.png)

- **Index Creation on the `artist` Column**
  An index was created on the `artist` column to optimize query performance and enable faster retrieval of rows when filtering by artist.
    - **SQL command** for creating the index:
      ```sql
      CREATE INDEX idx_artist ON spotify_tracks(artist);
      ```

- **Performance Analysis After Index Creation**
    - After creating the index,  the same query was run again and observed significant improvements in performance:
        - Execution time (E.T.): **0.153 ms**
        - Planning time (P.T.): **0.152 ms**
    - Below is the **screenshot** of the `EXPLAIN` result after index creation:
      ![EXPLAIN After Index](https://github.com/Subhasree05/spotify-data-analysis-/blob/main/after_query_optimization.png)

- **Graphical Performance Comparison**
    - A graph illustrating the comparison between the initial query execution time and the optimized query execution time after index creation.
    - **Graph view** shows the significant drop in both execution and planning times:
      ![Performance Graph](https://github.com/Subhasree05/spotify-data-analysis-/blob/main/spotify_graphical%20view%203.png)
      ![Performance Graph](https://github.com/Subhasree05/spotify-data-analysis-/blob/main/spotify_graphical%20view%202.png)
      ![Performance Graph](https://github.com/Subhasree05/spotify-data-analysis-/blob/main/spotify_graphical%20view%201.png)

This optimization shows how indexing can drastically reduce query time, improving the overall performance of our database operations in the Spotify project.
---

## Technology Stack
- **Database**: PostgreSQL
- **SQL Queries**: DDL, DML, Aggregations, Joins, Subqueries, Window Functions
- **Tools**: pgAdmin 4 , PostgreSQL 

## How to Run the Project
1. Install PostgreSQL and pgAdmin (if not already installed).
2. Set up the database schema and tables.
3. Insert the  data into the respective tables.
4. Execute SQL queries.



---

## Contributing
If you would like to contribute to this project, feel free to fork the repository, submit pull requests, or raise issues.

---

## License
This project is licensed under the MIT License.

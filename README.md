# Movies-ETL

## Background
The goal for this project is to create an automated pipeline that takes in new data, performs appropriate transformations, and loads the data into existing tables. To do this, one function needs to take in the three files: Wikipedia data, Kaggle metadata, and the MovieLens rating data—and performs the ETL process by adding the data to a PostgreSQL database.

## Requirements and Technology
* Data Source: ETL Deliverable 1, ETL Deliverable 2 and ETL Deliverable 3
* Data Tools: PostgreSQL, pgAdmin
* Software: pgAdmin 4.26, Python 3.8.3, Visual Studio Code 1.50.0, Flask Version 1.0.2

## Overview
* Deliverable 1: Write an ETL Function to Read Three Data Files
* Deliverable 2: Extract and Transform the Wikipedia Data (JSON)
* Deliverable 3: Extract and Transform the Kaggle Data
* Deliverable 4: Create the Movie Database

## Results
### 1. Data preprocessing
A function was written to read in the three data files and creates three separate DataFrames. It converts the Wikipedia JSON file, Kaggle metadata file, and MovieLens ratings file to Pandas DataFrames, and the DataFrame are displayed in the ETL_function_test.ipynb file. All three dataframes are then transformed to be communicable with one another.

### 2. ETL - Wikipedia Data
The extraction and transformation of the Wikipedia metadata using the ETL function does the following:
* TV shows are filtered out, and the wiki_movies_df DataFrame is created.
* A try-except block is used to catch errors while extracting the IMDb IDs with a regular expression and dropping duplicate IDs.

The extraction and transformation of the Wikipedia data in the ETL function does the following:
* A list comprehension is used to keep columns with non-null values.
* The non-null box office data is converted to string values using the lambda and join functions.
* A regular expression is used to match the six elements of "form_one" of the box office data.
* A regular expression is used to match the three elements of "form_two" of the box office data.

The following columns are cleaned in the Wikipedia DataFrame:
* The box office column
* The budget column
* The release date column
* The running time column​

The cleaned Wikipedia data is converted to a Pandas DataFrame, and the DataFrame is displayed in the ETL_clean_wiki_movies.ipynb file.

### 3. ETL - Kaggle Data
The extraction and transformation of the Kaggle metadata using the ETL function does the following:
* The Kaggle metadata is cleaned.
* The Wikipedia and Kaggle DataFrames are merged.

The following is performed on the merged Wikipedia and Kaggle DataFrames to create the movies_df:
* Unnecessary columns are dropped.
* A function is used to fill in the missing Kaggle data.
* The movies_df DataFrame is filtered to keep specific columns.
* The movies_df DataFrame columns are renamed.

The extraction and transformation of the MovieLens ratings data using the ETL function does the following:
* The ratings counts are cleaned.
* The movies_df DataFrame is merged with the cleaned ratings DataFrame to create the movies_with_ratings_df DataFrame.
* The empty values in the movies_with_ratings_df DataFrame are filled with “0”.
* The movies_with_ratings_df and the movies_df DataFrames are displayed in the ETL_clean_kaggle_data.ipynb file.

### 4. ETL - MovieLens Data
The extraction and transformation of the MovieLens metadata using the ETL function does the following:
* The data from the movies_df DataFrame replaces the current data in the movies table in the SQL database, as determined by the movies_query.png.
* The data from the MovieLens rating CSV file is added to the ratings table in the SQL database, as determined by the ratings_query.png.
* The elapsed time to add the data to the database is displayed in the ETL_create_database.ipynb file.


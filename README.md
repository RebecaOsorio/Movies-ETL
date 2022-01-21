# Movies-ETL

The Amazing Prime video team would like to develop an algorithm to predict which low budget movies being released will become popular so that they can buy the streaming rights at a bargain.

The team has asked to create an ETL pipeline strives to automate as much data wrangling as it can. As they are sponsoring a hackathon, providing a clean set to predict the popular pictures will ensure the fun and connection with the local coding community.

## Summary

### `ETL_function_test.ipynb`.

-   A function is written to read in the three data files:
	-   The function converts the Wikipedia **JSON** file to a Pandas DataFrame, and the DataFrame is displayed in the  `ETL_function_test.ipynb`  file.
	-   ​The function converts the **CSVs** files to a Pandas DataFrame, and the DataFrames are displayed in the  `ETL_function_test.ipynb`  file. 

### `ETL_clean_wiki_movies.ipynb`

-   The TV shows are filtered out, and the  `wiki_movies_df`  DataFrame is created. 
-   A  `try-except`  block is used to catch errors while extracting the IMDb IDs with a regular expression and dropping duplicate IDs. 
-   The extraction and transformation of the Wikipedia data in the ETL function does the following:
    -   A list comprehension is used to keep columns with non-null values.  
    -   The non-null box office data is converted to string values using the lambda and join functions.  
    -   A regular expression is used to match the six elements of "form_one" of the box office data.  
    -   A regular expression is used to match the three elements of "form_two" of the box office data.  
    -   The following columns are cleaned in the Wikipedia DataFrame: 
        -   The box office column
        -   The budget column
        -   The release date column
        -   The running time column
-   ​The cleaned Wikipedia data is converted to a Pandas DataFrame, and the DataFrame is displayed in the  `ETL_clean_wiki_movies.ipynb`  file. 

### `ETL_clean_kaggle_data.ipynb`
-   Extract and transform the **Kaggle metadata** using the ETL function does the following:
    -   The Kaggle metadata is cleaned. 
    -   The Wikipedia and Kaggle DataFrames are merged.  
    -  `movies_df`:
	    - Wikipedia and Kaggle DataFrames merged
        -   Unnecessary columns are dropped.
        -   A function is used to fill in the missing Kaggle data with the Wikipedia values.
        -   The  `movies_df`  DataFrame is filtered to keep specific columns.
        -   The  `movies_df`  DataFrame columns are renamed and re-ordered.
-   The extraction and transformation of the **MovieLens Ratings** data using the ETL function does the following:
    -   The ratings counts are cleaned. 
    -   The  `movies_df`  DataFrame is merged with the cleaned ratings DataFrame to create the  `movies_with_ratings_df`  DataFrame.  
    -   The empty values in the  `movies_with_ratings_df`  DataFrame are filled with “0”.  
-   The  `movies_with_ratings_df`  and the  `movies_df`  DataFrames are displayed in the  `ETL_clean_kaggle_data.ipynb`  file.  

### `ETL_create_database.ipynb`

-   The data from the  `movies_df`  DataFrame replaces the current data in the movies table in the SQL database, as determined by the  `movies_query.png`.  
-   The data from the **MovieLens Ratings** CSV file is added to the  `ratings`  table in the SQL database, as determined by the  `ratings_query.png`. 
-   The elapsed time to add the data to the database is displayed in the  `ETL_create_database.ipynb`  file. 
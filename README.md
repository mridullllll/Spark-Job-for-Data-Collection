# Spark-Job-for-Data-Collection
Chess Game Outcome Prediction using Lichess Data

## Introduction
In the data collection phase of our project, we aim to gather chess game records that will inform the model’s expectations about a player’s expected performance given their rating. We leverage the Lichess database, which is publicly available and comprises a series of compressed PGN (Portable Game Notation) files.

Our objective is to download these raw files, decompress them, and parse them into a format suitable for training a machine learning model. This initial phase will focus on processing a manageable subset of the data, specifically the years 2013 to 2015, to ensure efficient iteration and testing. This subset is small enough to handle easily while maintaining the same structure as the full dataset.

The ultimate goal of this phase is to produce a Spark DataFrame with the following columns:

- **black_rating** (int): Elo rating of the Black player
- **white_rating** (int): Elo rating of the White player
- **time_control** (str): Time control of the game
- **result** (int): Outcome of the game (-1 if Black won, 0 if the game was a draw, 1 if White won)

Games without a result are omitted from the dataset. While additional columns can be created if they are expected to improve prediction accuracy, the above columns are essential.

To achieve this, a Spark job will be written to:
1. Read the PGN files from the Lichess database.
2. Parse the PGN files into a DataFrame.
3. Write the resulting DataFrame to a Parquet file for subsequent phases of the pipeline.

This data collection phase sets the foundation for building a sophisticated AI model that can predict the outcomes of chess games, impressing investors with the integration of machine learning into our platform.

## Technical Stack
- **Programming Language:** Python
- **Framework:** Apache Spark
- **Libraries:** PySpark, Pandas, Re (Regular Expressions), OS

## Dataset
The dataset consists of game records from the Lichess database, which include the Elo ratings of the players, the time control of the game, and the outcome. These records are stored in compressed PGN (Portable Game Notation) files.

## Pre-processing
The pre-processing phase involves:
1. Downloading the compressed PGN files from the Lichess database.
2. Decompressing the PGN files.
3. Parsing the PGN files to extract relevant information.

## Spark Job
The Spark job is written to:
1. Initialize a Spark session.
2. Define the schema of the DataFrame.
3. Parse the PGN files to extract relevant game information:
   - `black_rating`: Elo rating of the Black player
   - `white_rating`: Elo rating of the White player
   - `time_control`: Time control of the game
   - `result`: Outcome of the game (-1 for Black win, 0 for draw, 1 for White win)
4. Process each PGN file to extract game data.
5. Combine the extracted data into a single DataFrame.
6. Save the combined DataFrame as a Parquet file for further processing.

## Results
The resulting Spark DataFrame includes:
- Elo ratings for both players.
- Time control of the game.
- Outcome of the game, indicating whether Black won, the game was a draw, or White won.

## Analysis & Insights
- The dataset can be used to train machine learning models to predict game outcomes based on player ratings and other factors.
- This project demonstrates the ability to process large datasets efficiently using Spark, making it scalable for future extensions.

## Challenges & Considerations
- Handling large volumes of data efficiently using Spark.
- Ensuring the correctness of the parsed data from PGN files.
- Dealing with games without results and other anomalies in the dataset.

## Conclusion
This project sets the foundation for integrating advanced Machine Learning techniques into Chess.net. By leveraging Lichess' data, we can develop models to predict game outcomes and showcase the potential of AI in enhancing the chess experience.

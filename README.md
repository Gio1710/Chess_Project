# Chess_Project
Distributed analysis of 6.25M Lichess games using PySpark. Leverages Random Forest for winner prediction (63% acc), K-Means for player segmentation, and FPGrowth for pattern mining.
Ecco il testo in formato Markdown puro.

Puoi copiare tutto il blocco qui sotto e incollarlo direttamente nell'editor del file README.md sul sito di GitHub.

♟️ Distributed Data Analysis of 6.25M Chess Games
A PySpark Project for Distributed Data Analysis and Mining > University of Pisa - Master's Degree in Computer Science

📋 Project Overview
This project leverages Apache Spark (PySpark) to analyze a massive dataset of 6.25 million chess games played on Lichess in July 2016. The goal was to process over 4GB of data in a distributed environment to uncover player behaviors, predict game outcomes, and identify statistical anomalies in opening strategies.

The analysis focuses on three main Research Questions:

Supervised Learning: Can we predict the winner based on ELO ratings and opening moves?

Unsupervised Learning: Can games be clustered into distinct "style profiles" beyond just skill level?

Pattern Mining: Are there specific opening traps that drastically alter win probabilities?

🛠️ Tech Stack
Framework: Apache Spark (PySpark)

Language: Python

Libraries: pyspark.ml (Machine Learning), pyspark.sql (DataFrames), pandas/seaborn (Visualization)

Infrastructure: Kaggle Notebooks (NVIDIA T4 GPU accelerated)

📊 Key Findings
1. Winner Prediction (Random Forest)
Model: Random Forest Classifier (numTrees=20, maxDepth=10).

Result: Achieved ~63% Accuracy.

Insight: EloDiff (Rating Difference) is the single most dominant predictor. Interestingly, GameLength has near-zero correlation with the skill gap, disproving the hypothesis that mismatches result in significantly shorter games.

2. Player Segmentation (K-Means)
Method: K-Means Clustering with k=4 (determined via Elbow Method).

Discovery: Identified distinct game profiles:

Masters: High ELO, standard length.

Beginners: Low ELO, short games (blunders).

Mismatches: Huge ELO gap.

Marathons: A specific cluster of exceptionally long games (~1900 moves string length), proving that duration is a fundamental discriminator independent of skill.

3. Opening Traps (FPGrowth)
Method: Association Rule Mining.

The "Van't Kruijs" Trap: The algorithm discovered a high-confidence rule:

{ Van't Kruijs Opening (1. e3) } => { Black Win }

With a confidence of 53.1%, this passive opening statistically flips the odds in favor of Black, punishing White for failing to control the center.

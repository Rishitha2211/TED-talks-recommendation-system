# Context-Based Recommendation System for TED Talks

This project implements a context-based recommendation system for TED Talks using topic modeling techniques.  It leverages the TED Ultimate Dataset from Kaggle to provide relevant talk recommendations based on user input.

## Table of Contents

* [Project Description](#project-description)
* [Dataset](#dataset)
* [Preprocessing](#preprocessing)
* [Vectorization](#vectorization)
* [Topic Modeling](#topic-modeling)
* [Future Improvements](#future-improvements)
* [Dependencies](#dependencies)

## Project Description

This project aims to provide relevant TED Talk recommendations based on user input.  It utilizes topic modeling techniques (NMF, LSA, and LDA) to understand the content of TED Talk transcripts and generate recommendations based on the similarity between user input and the learned topics. The system handles different types of user input, including speaker names, keywords/topics, and gibberish, providing appropriate recommendations in each case.

## Dataset

The dataset used in this project is the TED Ultimate Dataset, available on Kaggle: [https://www.kaggle.com/datasets/miguelcorraljr/ted-ultimate-dataset?rvi=1](https://www.kaggle.com/datasets/miguelcorraljr/ted-ultimate-dataset?rvi=1)

Only the English language subset of the dataset is used. The following features are extracted and used:

*   `URL`
*   `Transcript`
*   `Speaker_1`
*   `Talk_ID`

## Preprocessing

The `Transcript` column undergoes the following preprocessing steps:

*   Parenthetical word removal
*   Contraction expansion
*   Stop word removal
*   Lemmatization

User input is also preprocessed in the same manner.  A special case is handled for user input that matches a speaker name: in this scenario, the system directly recommends talks given by that speaker.  If the user input is gibberish, three random talks are recommended.

## Vectorization

Both TF-IDF and Count Vectorizer are used to represent the preprocessed transcripts and user input.  Various distance metrics are calculated between the user input vector and the TF-IDF vectors of the transcripts, including:

*   Cosine Similarity
*   KL Divergence
*   Manhattan Distance
*   Jaccard Similarity
*   Hellinger Distance

Cosine similarity was chosen as the primary similarity metric for further analysis and model development.  The recommendation function uses this metric to generate a list of recommended talk titles and URLs.

## Topic Modeling

Three topic modeling models are implemented:

*   Non-negative Matrix Factorization (NMF)
*   Latent Semantic Analysis (LSA)
*   Latent Dirichlet Allocation (LDA)

These models are used to generate recommendations based on the cosine similarity between the user input vector and the topic vectors generated by each model.  t-SNE is used to visualize the topic-word distributions.  An attempt was made to implement Grid Search CV for hyperparameter tuning of the LDA model.


## Future Improvements

*   Implement coherence score calculation to optimize hyperparameters for the topic modeling models.
*   Explore other distance metrics and similarity measures.
*   Experiment with different preprocessing techniques.
*   Develop a user interface (e.g., web application) for easier interaction with the system.
*   Evaluate the performance of the recommendation system using appropriate metrics.

## Dependencies

The project requires the following Python libraries:

*   pandas
*   scikit-learn
*   nltk
*   gensim
*   numpy




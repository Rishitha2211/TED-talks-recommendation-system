# TED-talks-recommendation-system
Context based recommendation system using topic modeling techniques to generate recommendations based on transcripts. 

Preprocessing
-> Dataset is taken from Kaggle: https://www.kaggle.com/datasets/miguelcorraljr/ted-ultimate-dataset?rvi=1 ; only english language dataset is used.
-> Only features used are URL, Transcript, Speaker_1, Talk_ID
-> Transcripts column undergoes text preprocessing( Parenthetical word removal, expanding contractions, stopword removal, lemmatization)
-> User input also undergoes same preprocessing, User input is first checked if its a speaker name, else undergoes preprocessing.

Vectorization
-> Both TFIDF and count vectorizer are used on transcripts and user input
-> various distance measuring metrics like cosine similarity, KL divergence, Manhattan Distance, Jaccard Similarity, Hellinger Distance are calculated between  User input vector and tf-idf vector and generated recommendations as list of Talk titles and urls.
-> Recommendations function works as if the user input is a speaker name, it gives talk titles and respective urls given by speaker, if it's a gibberish word it gives 3 random recommendations, if it's a word or a topic it calculates similarity and generates similar talk recommendations.
-> chose cosine similarity as the similarity metric for further models.

Topic Modeling
-> NMF, LSA and LDA models are used to generate recommendations based on cosine similarity between user input vector and each model vector.
-> t-SNE is used to visualize topic-word distributions.
-> tried to implement grid search CV on LDA 

Can be modified by using coherence score to get hyperparameters for topic modeling models.

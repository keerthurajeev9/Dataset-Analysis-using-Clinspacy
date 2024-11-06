# Dataset Analysis using Clinspacy
This repository contains code snippets and instructions for analyzing a dataset using the Clinspacy library in R. The dataset used in this analysis is available directly from the Clinspacy library.

## Dataset
The dataset used in this analysis is the raw.data dataset obtained from the Clinspacy library. It contains medical transcriptions with the following columns:

note_id: Unique identifier for each note

description: Description of the note

medical_specialty: Medical specialty associated with the note

sample_name: Sample name of the note

transcription: Transcription text of the note

keywords: Keywords associated with the note

### Description of Dataset
To get a sense of the data contained in the dataset, the glimpse function from the dplyr package is used. It provides an overview of the dataset, including the number of rows and columns, and the data types of each column.

## Medical Specialties and Filtering
The dataset contains notes from various medical specialties. To determine the number of unique medical specialties featured in the notes, the n_distinct function from dplyr is used.
In this analysis, we filter the dataset to focus on three specific medical specialties: Orthopedic, Radiology, and Surgery. These specialties are selected using the filter function from dplyr.

## Text Processing
The next step involves preprocessing the transcriptions from the selected specialties. The tidytext package is used to tokenize the free text and remove stop words. The following steps are performed:

Tokenization: The unnest_tokens function is used to tokenize the transcriptions into words. The resulting tokens are stored in the word column.

Cleaning: Non-alphanumeric characters are removed from the tokens using str_replace_all function.

Filtering: Tokens containing numbers are filtered out using the filter function with the str_detect function.

Stop word removal: Stop words, such as "the" and "of," are removed using the anti_join function with the stop_words list.

Grouping and summarizing: The tokens are grouped by note_id, and the tokens for each note are combined into a single string using summarise and paste functions.

Joining: The preprocessed data is joined back with the original dataset using the left_join function.


## Token Frequency Visualization
To visualize the distribution of token frequencies, scatter plots are created using ggplot2 package. Separate plots are generated for unigram tokens (words) and bigram tokens (words occurring in pairs).

## Sentence Analysis
In addition to analyzing words and bigrams, the analysis also involves examining unique sentences in each specialty. The unnest_tokens function is used with the token = "sentences" argument to tokenize the transcriptions into sentences.

## Top Lemmas
To identify the most commonly used lemmas (lemmatized forms of words) within each specialty, the tokens are lemmatized using the lemmatize_words function from the textstem package. The lemmatized tokens are then grouped by medical_specialty and counted using the count function from dplyr. The top lemmas are determined using the slice_max function.

## TF-IDF Analysis
Term Frequency-Inverse Document Frequency (TF-IDF) analysis is performed to identify the most important terms within each specialty. The tidytext and textrecipes packages are used to compute TF-IDF scores for each term. The terms with the highest TF-IDF scores are determined using the slice_max function.

## Conclusion
This analysis provides insights into the dataset using various text processing techniques in R. It covers tokenization, stop word removal, analysis of token frequencies, examination of sentences, identification of top lemmas, and TF-IDF analysis. The code snippets and instructions provided can be used as a starting point for further exploration and analysis of clinical text data using the Clinspacy library.

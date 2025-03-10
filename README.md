# Movie Recommendation System
![image](https://github.com/user-attachments/assets/6086e757-a4a5-4d7e-b391-5ce96af1640b)

## Overview
This repository contains a content-based movie recommendation system that leverages movie metadata including genres and tags to generate personalized movie recommendations. The system uses TF-IDF vectorization and cosine similarity to identify movies with similar content characteristics.
## Features

Content-Based Filtering: Recommends movies based on similar content characteristics
TF-IDF Vectorization: Converts text features into numerical representations
Cosine Similarity: Measures the similarity between movies based on their feature vectors
Tag Relevance: Incorporates tag relevance scores from the MovieLens Genome dataset

## Data Sources
The system uses the following datasets from the MovieLens collection:

movies.csv: Contains movie information including title and genres
genome_scores.csv: Contains relevance scores for movie-tag pairs
genome_tags.csv: Maps tag IDs to tag names
train.csv: Contains user-movie interactions (not directly used in content-based filtering)

## Implementation Details
### Data Preprocessing

### Loading Datasets: Loads movie information, genome scores, and tags
Tag Processing: Merges genome scores with tag information and pivots to create a movie-tag matrix
Feature Creation: Combines genre information with relevant tags for each movie
Index Mapping: Creates a consistent mapping between movie IDs and array indices to ensure proper alignment

### TF-IDF Vectorization
The system uses TF-IDF (Term Frequency-Inverse Document Frequency) to convert the text features into numerical representations. This technique:

- Weighs terms based on their importance to a document
- Reduces the impact of common words that appear across many movies
- Creates a sparse matrix representation of movie features

### Recommendation Algorithm
The recommendation function:

- Accepts a movie title as input
- Finds the corresponding movie in the dataset
- Computes cosine similarity between the selected movie and all other movies
- Returns the top N most similar movies, excluding the input movie itself

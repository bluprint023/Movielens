# Movie Recommendation System
![image](https://github.com/user-attachments/assets/6086e757-a4a5-4d7e-b391-5ce96af1640b)

## Overview
This repository contains a content-based movie recommendation system that leverages movie metadata, including genres and tags, to generate personalized movie recommendations. The system uses **TF-IDF vectorization** and **cosine similarity** to identify movies with similar content characteristics.

## Objective
The objective of this project is to build a movie recommendation system using metadata to suggest similar movies based on content features. Unlike collaborative filtering, which relies on user interactions and ratings, this approach ensures recommendations even for movies with fewer user ratings, making it useful for cold-start scenarios.

## How It Works
The recommendation system follows these steps:
1. Load and preprocess the **MovieLens dataset**.
2. Extract **genres** and relevant **tags** to create feature representations for each movie.
3. Apply **TF-IDF vectorization** to convert text data into numerical values.
4. Compute **cosine similarity** between movie vectors to determine similarity scores.
5. Retrieve and display the top **N** most similar movies for a given input movie.

## Features
- **Content-Based Filtering**: Recommends movies based on similar content characteristics.
- **TF-IDF Vectorization**: Converts movie tags and genres into numerical representations.
- **Cosine Similarity**: Measures similarity between movies based on their feature vectors.
- **Tag Relevance**: Incorporates tag relevance scores from the **MovieLens Genome dataset** for improved recommendations.

## Data Sources
The system utilizes the following datasets from the **MovieLens collection**:
- `movies.csv`: Contains movie information, including title and genres.
- `genome_scores.csv`: Contains relevance scores for movie-tag pairs.
- `genome_tags.csv`: Maps tag IDs to tag names.
- `train.csv`: Contains user-movie interactions (not directly used in content-based filtering).

## Implementation Details
### Data Preprocessing
#### Loading Datasets
The system loads the **movies.csv**, **genome_scores.csv**, and **genome_tags.csv** files and merges relevant columns to create a unified dataset for feature extraction.

#### Handling Missing Data
- Missing genres and tags are replaced with empty strings to avoid issues during vectorization.
- Lowercasing and removing unnecessary characters are performed for consistency.

#### Tag Processing
- Merges `genome_scores.csv` with `genome_tags.csv`.
- Pivots the tag data to create a **movie-tag matrix** with relevance scores.
- Filters only the most relevant tags for each movie.

#### Feature Creation
- Combines **genre information** with the most relevant **tags** for each movie.
- Converts these textual features into a structured format for vectorization.

#### Index Mapping
- A dictionary is created to map **movie titles to indices** for easy lookup during similarity calculations.

### TF-IDF Vectorization
The **TF-IDF (Term Frequency-Inverse Document Frequency)** technique is used to convert textual movie metadata into numerical vectors. This technique:
- Weighs terms based on their importance within a movie’s metadata.
- Reduces the impact of commonly occurring words.
- Creates a **sparse matrix** representation of movie features.

### Recommendation Algorithm
The recommendation function follows these steps:
1. Accepts a **movie title** as input.
2. Retrieves the corresponding movie’s **TF-IDF vector**.
3. Computes **cosine similarity** between the selected movie and all other movies.
4. Returns the **top N most similar movies**, excluding the input movie itself.

## Model Evaluation & Improvements
### Limitations
- **Cold Start Problem**: New movies with minimal metadata may not have good recommendations.
- **No User Preferences**: Since it only considers movie content, it does not personalize recommendations based on user behavior.
- **Fixed Features**: Once the vectorization is done, newly added metadata is not dynamically incorporated.

### Possible Enhancements
- **Hybrid Recommendation**: Combine content-based filtering with collaborative filtering to improve accuracy.
- **Word Embeddings**: Use advanced NLP techniques like **Word2Vec** or **BERT** instead of TF-IDF.
- **Weighted Tag Importance**: Experiment with different weightings for genres and tags.
- **Hosting and a Front-End**: Perhaps the biggest improvement would be hosting the back-end and develop a front-end for ease of use.

## Usage Guide & Example Output
To use the recommendation system, simply call the function with a movie title and the number of recommendations:

### Example Code:
```python
recommend_movies_content("Toy Story (1995)", top_n=5)
```

### Expected Output:
```
1. Toy Story 2
2. A Bug's Life
3. Monsters, Inc.
4. Finding Nemo
5. The Incredibles
```

## Conclusion
This content-based recommendation system provides personalized movie suggestions based on metadata such as genres and tags. While it effectively identifies similar movies, incorporating user preferences through hybrid models could further enhance recommendation quality. Future improvements could also include **deep learning-based embeddings** to refine similarity scoring.

## References & Acknowledgments
- **MovieLens Dataset**: [https://grouplens.org/datasets/movielens/](https://grouplens.org/datasets/movielens/)
- **TF-IDF & Cosine Similarity**: scikit-learn documentation [https://scikit-learn.org/](https://scikit-learn.org/)
- **Recommender Systems**: "Introduction to Recommender Systems" by Charu Aggarwal


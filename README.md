# Cosine Similarity-Based Recommender System

This project implements a content-based recommender system using cosine similarity to suggest products based on user queries. It analyzes product descriptions and compares them to query terms to find the most relevant products.

## Project Structure

The project includes the following components:

*   **Code:** The core logic is implemented in a Python notebook (`Collaborative Filtering.ipynb`).
*   **Datasets:**
    *   `dataset/product.csv`: Contains product information (product ID, description, class).
    *   `dataset/query.csv`: Contains user search queries (query ID, query text, query class).
    *   `dataset/label.csv`: (Further investigation needed) Likely contains ground truth labels for query-product relevance, potentially used for evaluation.
*   **README.md:** This file providing project overview and usage instructions.

## Prerequisites

To run the code, you will need:

*   **Python 3:** The programming language used for implementation.
*   **Required Libraries:** Install them using pip:

    ```bash
    pip install pandas nltk
    ```

    Also, download NLTK resources:

    ```python
    import nltk
    nltk.download("stopwords")
    nltk.download('punkt')
    ```

## How to Run

1.  Clone the project repository.
2.  Open the `Collaborative Filtering.ipynb` notebook using Jupyter Notebook or Google Colab.
3.  Run the cells sequentially.

## System Overview

The recommender system works as follows:

1.  **Data Loading and Preprocessing:** Product and query data are loaded from CSV files. Text preprocessing steps include tokenization, removing non-alphabetic characters, optional stop word removal (currently commented out in the code), and stemming (using the Porter Stemmer).

2.  **Inverted Index:** An inverted index is created for efficient retrieval of products containing specific terms. This index stores term frequencies (TF) and document frequencies (DF).

3.  **Cosine Similarity Calculation:** For each query, the system calculates the cosine similarity between the query and all product descriptions. The formula used is a variation of TF-IDF, incorporating term frequency in the query and inverse document frequency. The similarity score is normalized by the length of the product description.

4.  **Recommendation Generation:** The system returns the top N most similar products for each query.

## Key Concepts

*   **Tokenization:** Splitting text into individual words or tokens.
*   **Stop Words:** Common words (e.g., "the," "a," "is") that are often removed during text processing.
*   **Stemming:** Reducing words to their root form (e.g., "running" to "run").
*   **Inverted Index:** A data structure that maps terms to the documents they appear in, enabling fast search.
*   **TF-IDF (Term Frequency-Inverse Document Frequency):** A weighting scheme that measures the importance of a term in a document relative to a collection of documents.
*   **Cosine Similarity:** A measure of similarity between two non-zero vectors. In this context, the vectors represent term frequencies in the query and product descriptions.

## Areas for Improvement

*   **Stop Word Removal:** Implement stop word removal for potential performance and accuracy gains.
*   **Advanced Text Preprocessing:** Explore more advanced techniques like TF-IDF vectorization or word embeddings (Word2Vec, GloVe, FastText).
*   **Parameter Tuning:** Experiment with different parameters (e.g., the number of top recommendations) to optimize performance.
*   **Evaluation:** Implement proper evaluation metrics (e.g., precision, recall, F1-score, NDCG) using the `label.csv` dataset (after further investigation to understand its structure).
*   **Alternative Recommendation Approaches:** Consider implementing other recommendation algorithms like collaborative filtering.

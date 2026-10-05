# Book Recommendation System

A Python-based book recommendation prototype using **K-Nearest Neighbors (KNN)** and **cosine distance** to identify books with similar user-rating patterns.

## Overview

This project demonstrates how recommendation systems can use historical user ratings to find similar items.

The notebook uses a small simulated book-rating dataset containing users, book titles, and ratings. The ratings are transformed into a book-user matrix and then processed with a sparse matrix representation before applying a K-Nearest Neighbors model.

## How It Works

### 1. Create the Ratings Dataset

The project creates a sample dataset containing:

* `user_id`
* `book_title`
* `rating`

The dataset contains 10 ratings across 5 users and several books.

### 2. Build the Book-User Matrix

A pivot table converts the ratings into a matrix where:

* Rows = books
* Columns = users
* Values = ratings

Missing ratings are filled with `0`.

### 3. Convert to a Sparse Matrix

The book-user matrix is converted to a SciPy sparse matrix using `csr_matrix`.

This provides a more efficient representation for recommendation-system data where many user/book combinations may not have ratings.

### 4. Find Similar Books

A `NearestNeighbors` model from scikit-learn is trained using:

* **Metric:** Cosine distance
* **Algorithm:** Brute-force nearest neighbors

The model compares the rating patterns of books to identify similar titles.

### 5. Generate Recommendations

The `get_recommends()` function accepts a book title and returns the five nearest books along with their calculated cosine distances.

Example:

```python
get_recommends("The Queen of the Damned (Vampire Chronicles (Paperback))")
```

The prototype identifies:

* The Witching Hour
* Interview with the Vampire
* Catch 22
* The Tale of the Body Thief
* The Vampire Lestat

The closest recommendation in the example is **The Witching Hour**, with a cosine distance of approximately `0.293`.

## Technologies

* Python
* Pandas
* NumPy
* Scikit-learn
* SciPy
* Google Colab / Jupyter Notebook

## Key Concepts

* Recommendation systems
* Collaborative filtering concepts
* K-Nearest Neighbors
* Cosine distance
* Sparse matrices
* Pivot tables
* Data transformation
* Similarity-based recommendations

## Project Takeaway

This project demonstrates the basic workflow behind an item-based recommendation system: transform user interaction data into a matrix, represent the data efficiently, measure item similarity, and return the closest matches.

The implementation is intentionally small and serves as a prototype for a larger recommendation system that could use a substantially larger ratings dataset.

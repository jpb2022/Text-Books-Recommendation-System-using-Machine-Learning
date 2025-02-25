# Book Recommendation System

## Overview
The Book Recommendation System is designed to suggest books to users based on their interests and preferences. It utilizes various recommendation techniques, including popularity-based filtering, collaborative filtering, content-based filtering, and hybrid approaches.

### Dataset Source:
The dataset used for this project is available [here](http://www2.informatik.uni-freiburg.de/~cziegler/BX/). It consists of three tables:
- **Books**
- **Users**
- **Ratings**

## 1. Data Cleaning and Preprocessing
Data preprocessing was performed separately for each table to ensure consistency and improve recommendation accuracy.

### Books Table:
- Removed all three Image URL features.
- Handled missing values by replacing null entries with 'Other'.
- Rectified inconsistencies in the "Year of Publication" column, replacing invalid years with the mode (2002).
- Standardized ISBN entries (uppercased and removed duplicates).

### Users Table:
- Addressed missing values in the "Age" column by replacing them with the mean of valid ages (10 to 80 years).
- Split "Location" into separate columns: City, State, and Country, assigning 'Other' where data was missing.
- Eliminated duplicate entries.

### Ratings Table:
- Ensured "User-ID" and "Rating" columns contained only integer values.
- Removed punctuation from ISBN values and retained only valid ISBNs found in the Books dataset.
- Standardized ISBN entries (uppercased) and removed duplicate ratings.

## 2. Implemented Recommendation Algorithms

### 2.1 Popularity-Based Recommendation
- **Overall Popularity**: Recommends books with the highest number of ratings.
- **Location-Based Popularity**: Filters and ranks books by popularity within a specific city, state, or country.
- **Author/Publisher-Based Recommendations**: Suggests books from the same author or publisher based on user preferences.
- **Yearly Popularity**: Groups books by publication year and recommends top-rated books for each year.

### 2.2 Average Weighted Rating Recommendation
- Books are ranked based on a weighted score calculated using the formula:
  \[ \text{score} = \frac{t}{t + m} \times a + \frac{m}{m + t} \times c \]
  Where:
  - *t* = Total ratings for the book
  - *m* = Minimum required ratings for inclusion
  - *a* = Average rating of the book
  - *c* = Mean rating of all books

### 2.3 User-Item Collaborative Filtering
- Uses cosine similarity to analyze user ratings and recommend books based on similar user preferences.
- Considers books with at least 50 ratings to ensure meaningful recommendations.

### 2.4 Correlation-Based Recommendation
- Creates a correlation matrix using books with more than 50 ratings.
- Constructs a user-book rating matrix and suggests books highly correlated with the input book.

### 2.5 Nearest Neighbors-Based Recommendation
- Converts the dataset into a sparse matrix for efficient storage and processing.
- Uses the Nearest Neighbors model with cosine similarity to identify books similar to the user’s preferences.

### 2.6 Content-Based Recommendation
- Utilizes TF-IDF vectorization to analyze book titles.
- Generates recommendations based on title similarity, considering books with at least 80 ratings.

### 2.7 Hybrid Recommendation System
- Combines collaborative filtering and content-based filtering.
- Assigns percentile scores to recommendations from both models and integrates them for final suggestions.

## 3. Libraries Used
- **Data Handling:** pandas, numpy, scipy
- **Machine Learning:** scikit-learn
- **Visualization:** seaborn, matplotlib
- **Development Environment:** Jupyter Notebook (iPython)

## 4. Acknowledgments
This project was developed by **Jitendra Kumar Gupta** (IIT Kanpur) – Machine Learning Engineer | Data Scientist | AI Engineer.


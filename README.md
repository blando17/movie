#  Movie Recommendation System

This project builds a content-based movie recommendation engine using **TF-IDF Vectorization** and **Cosine Similarity**. Given a user's favorite movie, the system suggests a list of movies with similar genres, keywords, cast, and director.

---

##  Project Overview

The goal is to recommend movies that are similar to a user-input movie based on the content metadata. The system compares movie plots, genres, taglines, cast, and director information to find the most relevant matches.

---

##  Technologies Used

| Tool/Library              | Purpose                          |
|---------------------------|----------------------------------|
| Python                    | Programming Language             |
| Pandas & NumPy            | Data manipulation                |
| scikit-learn              | TF-IDF & similarity computation  |
| difflib                   | Fuzzy string matching            |

---

##  Dataset Description

- **Source**: `movies.csv`
- **Total Movies**: 4,803
- **Important Features Used**:
  - `genres`
  - `keywords`
  - `tagline`
  - `cast`
  - `director`

---

##  Data Preprocessing

- Selected relevant metadata columns.
- Replaced missing values with empty strings.
- Combined all features into a single string for each movie:
```python
combined_features = genres + keywords + tagline + cast + director
```

---

##  Feature Extraction

Used **TF-IDF Vectorizer** to convert combined text features into numerical vectors:

```python
vectorizer = TfidfVectorizer()
feature_vectors = vectorizer.fit_transform(combined_features)
```

---

##  Similarity Computation

Used **Cosine Similarity** to compute similarity scores between all movie pairs:

```python
similarity = cosine_similarity(feature_vectors)
```

---

##  Recommendation Logic

1. Accept user input (e.g., `"Batman"`).
2. Use `difflib.get_close_matches()` to find the closest title match.
3. Retrieve the index of the matched movie.
4. Sort all movies based on their cosine similarity to the selected movie.
5. Print the top 30 most similar movie titles.

---

##  Example Output

```
Enter your favourite movie name: Spider man

Movies suggested for you:

1 . Spider-Man  
2 . Spider-Man 3  
3 . Spider-Man 2  
4 . The Notebook  
5 . Seabiscuit  
6 . Clerks II  
7 . The Ice Storm  
8 . Oz: The Great and Powerful  
...
```


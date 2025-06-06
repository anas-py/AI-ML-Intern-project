# 🎬 Movie Recommender System

A **content-based movie recommendation system** that suggests movies similar to the one selected by the user. This project is built using **Python**, **Scikit-learn**, and **Streamlit**, and presents a clean, interactive web interface.

---

## 🚀 Features

- Recommends movies based on similarity using content-based filtering  
- Uses metadata like **genres, cast, crew, and keywords**  
- Interactive UI built with **Streamlit**  
- Fetches movie posters using **TMDb API**  
- Fast, responsive, and easy to use

---

## 📌 Tech Stack

| Component         | Tools / Libraries                           |
|------------------|---------------------------------------------|
| Programming      | Python                                       |
| Libraries        | pandas, numpy, scikit-learn, requests, pickle |
| Web Framework    | Streamlit                                    |
| Dataset          | TMDb Movie Metadata (from Kaggle)            |
| Similarity Model | CountVectorizer + Cosine Similarity          |
| Poster Fetching  | TMDb API                                     |

---

## 🧠 Project Workflow

1. **Data Collection**  
   - Acquired movie metadata including titles, genres, overviews, cast, and crew.

2. **Data Preprocessing**  
   - Cleaned and merged relevant features, handled null values.

3. **Feature Engineering**  
   - Combined genres, keywords, cast, and director into one feature.

4. **Vectorization**  
   - Used `CountVectorizer` to convert text data into numerical vectors.

5. **Similarity Calculation**  
   - Used **Cosine Similarity** to measure similarity between movies.

6. **Recommendation Logic**  
   - Top 5 similar movies are selected and shown to the user.

7. **Poster Integration**  
   - Fetched movie posters via **TMDb API** using movie IDs.

8. **Web UI with Streamlit**  
   - Simple dropdown-based interface to select and view recommended movies.

---

## 📸 Demo

*Add demo screenshot or video link here*

---

## 🛠️ Installation & Run Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/movie-recommender-system.git
   cd movie-recommender-system

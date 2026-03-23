<div align="center">

<h1>🎬 Movie Recommender System</h1>

<p><em>A content-based movie recommendation engine that suggests personalized movie picks using NLP, cosine similarity, and real-time TMDb poster fetching — deployed as a Streamlit web application.</em></p>

![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=flat-square&logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-Web%20App-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)
![TMDb](https://img.shields.io/badge/TMDb-API-01B4E4?style=flat-square)
![NLP](https://img.shields.io/badge/NLP-CountVectorizer-8A2BE2?style=flat-square)
![Cosine Similarity](https://img.shields.io/badge/Cosine-Similarity-00C49F?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Description](#-description)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Dataset](#-dataset)
- [How It Works](#-how-it-works)
- [NLP & Similarity Pipeline](#-nlp--similarity-pipeline)
- [Project Workflow](#-project-workflow)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [TMDb API Setup](#-tmdb-api-setup)
- [Application Usage](#-application-usage)
- [Future Improvements](#-future-improvements)
- [Author](#-author)
- [License](#-license)

---

## 🔍 Overview

This project is a **content-based movie recommendation system** developed during an AI/ML internship. Given any movie selected by the user, the system identifies the **5 most similar movies** by analyzing their metadata — including genres, cast, crew, keywords, and plot overview — and displays recommendations alongside their official movie posters fetched in real time via the **TMDb API**.

The recommendation engine is powered by **Natural Language Processing (NLP)** techniques — specifically `CountVectorizer` and **Cosine Similarity** — and is deployed as a fast, interactive **Streamlit web application** accessible directly from the browser.

---

## 📝 Description

Recommendation systems are at the heart of modern digital experiences. Platforms like Netflix, Amazon Prime, and Spotify rely on sophisticated recommendation engines to drive user engagement and content discovery. This project replicates that core capability in a lightweight, explainable, and easily deployable form.

**Content-based filtering** works by analyzing the *attributes* of items (in this case, movies) rather than relying on user behavior data. This makes it ideal for cold-start scenarios where user history is limited or unavailable.

Here's the core insight: if two movies share similar genres, overlapping cast members, the same director, and related keywords — they are likely to appeal to the same audience. By encoding these attributes as text and computing vector similarity, the system surfaces movies that are semantically close to the user's selection.

**Why this approach?**

- **Interpretable** — Recommendations are based on visible, understandable movie attributes
- **No user data required** — Works without any login, rating history, or behavioral tracking
- **Scalable** — The similarity matrix can be precomputed and cached for fast inference
- **Extensible** — Can be upgraded to a hybrid system by combining with collaborative filtering

> This project was completed as part of an AI/ML internship, demonstrating practical skills in data preprocessing, NLP-based feature engineering, similarity computation, API integration, and web application deployment.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🎯 **Content-Based Recommendations** | Suggests movies based on metadata similarity, not user history |
| 🧠 **NLP Feature Engineering** | Merges genres, cast, crew, and keywords into enriched text features |
| 📐 **Cosine Similarity Engine** | Computes pairwise similarity across the entire movie corpus |
| 🖼️ **Live Poster Fetching** | Retrieves official movie posters from TMDb API in real time |
| 🎛️ **Interactive Streamlit UI** | Dropdown-based selection with instant, visual recommendations |
| ⚡ **Precomputed Similarity Matrix** | Fast inference via pickled model artifacts — no recomputation at runtime |
| 📦 **Lightweight Deployment** | Runs locally on any machine; no GPU required |
| 🔄 **Top-5 Recommendations** | Returns the 5 most similar movies ranked by cosine similarity score |

---

## 🏗️ System Architecture

```
┌──────────────────────────────────────────────────────────────────────┐
│                    Movie Recommender System                          │
│                                                                      │
│  ┌──────────────────┐    ┌─────────────────────┐                    │
│  │   TMDb Movie     │───▶│  Data Preprocessing  │                   │
│  │  Metadata (CSV)  │    │  Merge · Clean · NLP │                   │
│  └──────────────────┘    └──────────┬──────────┘                    │
│                                     │                                │
│                          ┌──────────▼──────────┐                    │
│                          │  CountVectorizer     │                    │
│                          │  Text → Vectors      │                    │
│                          └──────────┬──────────┘                    │
│                                     │                                │
│                          ┌──────────▼──────────┐                    │
│                          │  Cosine Similarity   │                    │
│                          │  Matrix (precomputed)│                    │
│                          └──────────┬──────────┘                    │
│                                     │                                │
│   ┌──────────────────┐   ┌──────────▼──────────┐                    │
│   │   TMDb REST API  │◀──│  Top-5 Movie IDs     │                   │
│   │  (Poster Fetch)  │   │  by Similarity Score │                   │
│   └────────┬─────────┘   └─────────────────────┘                    │
│            │                                                         │
│   ┌────────▼─────────────────────────────────────┐                  │
│   │           Streamlit Web Interface             │                  │
│   │   Dropdown → Select Movie → View 5 Results   │                  │
│   │   with Posters & Movie Titles                 │                  │
│   └──────────────────────────────────────────────┘                  │
└──────────────────────────────────────────────────────────────────────┘
```

---

## 🛠 Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| **Language** | Python 3.9+ | Core development |
| **Data Processing** | Pandas, NumPy | Data cleaning, merging, and manipulation |
| **NLP & ML** | Scikit-learn (`CountVectorizer`, `cosine_similarity`) | Feature vectorization and similarity computation |
| **Model Serialization** | Pickle | Saving/loading precomputed similarity matrix and movie data |
| **API Integration** | Requests + TMDb API | Fetching real-time movie poster images |
| **Web Framework** | Streamlit | Interactive frontend deployment |
| **Dataset** | TMDb Movie Metadata (Kaggle) | Movie titles, genres, cast, crew, keywords, overviews |
| **Notebook** | Jupyter Notebook | Model development, experimentation, and EDA |

---

## 📂 Dataset

The project uses the **TMDb Movie Metadata** dataset, publicly available on Kaggle.

| Property | Details |
|---|---|
| **Source** | TMDb (The Movie Database) via Kaggle |
| **Files Used** | `tmdb_5000_movies.csv`, `tmdb_5000_credits.csv` |
| **Total Movies** | ~5,000 films |
| **Key Columns Used** | `title`, `genres`, `overview`, `keywords`, `cast`, `crew` |
| **Target** | No label — unsupervised similarity-based recommendation |

**Feature Columns Explained:**

- `genres` — Genre tags associated with the movie (e.g., Action, Drama, Comedy)
- `keywords` — Thematic keywords describing the movie's plot and setting
- `cast` — Top billed actors in the movie
- `crew` — Director extracted from crew metadata
- `overview` — Short textual synopsis of the plot

> All five feature columns are combined into a single enriched `tags` column that serves as the basis for vectorization.

---

## 🧠 How It Works

The recommendation logic is based on **content-based filtering** using vector space similarity:

### Step 1 — Feature Fusion
The five metadata columns (`genres`, `keywords`, `cast`, `crew`, `overview`) are cleaned, stemmed, and concatenated into a single `tags` string per movie.

```python
# Example
movie["tags"] = "Action Thriller TomHanks RobertZemeckis Cast Away stranded survival island"
```

### Step 2 — Vectorization
`CountVectorizer` converts all movie `tags` into a **document-term matrix** — a numerical vector representation where each dimension corresponds to a unique word in the vocabulary.

```python
from sklearn.feature_extraction.text import CountVectorizer
cv = CountVectorizer(max_features=5000, stop_words='english')
vectors = cv.fit_transform(movies['tags']).toarray()
```

### Step 3 — Cosine Similarity
The **cosine similarity** between every pair of movie vectors is computed and stored as a precomputed matrix. Cosine similarity measures the *angle* between two vectors — closer to 1 means more similar.

```python
from sklearn.metrics.pairwise import cosine_similarity
similarity = cosine_similarity(vectors)
```

### Step 4 — Recommendation
When a user selects a movie, its index is looked up, and the top 5 most similar movies (by cosine similarity score) are returned — excluding the selected movie itself.

### Step 5 — Poster Fetching
Each recommended movie's TMDb `movie_id` is used to make a REST API call to TMDb, retrieving the official poster image URL displayed in the UI.

---

## ⚙️ NLP & Similarity Pipeline

```
Raw Metadata Columns
(genres · keywords · cast · crew · overview)
          │
          ▼
┌────────────────────────────────────────────┐
│  1. Parse JSON-like strings                │  → ast.literal_eval for genres/cast/crew
│  2. Extract top 3 cast members             │  → Limit to most prominent actors
│  3. Extract Director from crew             │  → filter job == "Director"
│  4. Remove spaces from names               │  → "Tom Hanks" → "TomHanks" (avoid split)
│  5. Concatenate all into tags              │  → Single enriched text field per movie
│  6. Apply Porter Stemming                  │  → "dancing" → "danc", "loved" → "love"
│  7. CountVectorizer (max 5000 features)    │  → Sparse matrix: movies × vocabulary
│  8. Cosine Similarity Matrix               │  → Shape: (5000, 5000), precomputed
└────────────────────────────────────────────┘
          │
          ▼
   Serialized with Pickle → Loaded at app runtime
```

---

## 🔄 Project Workflow

| Step | Stage | Description |
|---|---|---|
| 1 | **Data Collection** | Acquired TMDb movie metadata (titles, genres, overview, cast, crew) from Kaggle |
| 2 | **Data Preprocessing** | Merged two CSV files, dropped nulls, extracted structured fields from JSON strings |
| 3 | **Feature Engineering** | Combined genres, keywords, top 3 cast, director, and overview into a single `tags` column |
| 4 | **NLP Vectorization** | Applied `CountVectorizer` with stemming to convert `tags` into numerical vectors |
| 5 | **Similarity Computation** | Built the full cosine similarity matrix across all ~5,000 movies |
| 6 | **Model Serialization** | Saved movie DataFrame and similarity matrix using `pickle` for fast app-time loading |
| 7 | **API Integration** | Integrated TMDb API to fetch live movie poster images using `movie_id` |
| 8 | **Streamlit Deployment** | Built interactive UI with a dropdown selector, recommendation grid, and poster display |

---

## 📁 Project Structure

```
AI-ML-Intern-project/
│
├── app.py                            # Streamlit web application (main entry point)
├── movie-recommernder-system.ipynb   # Full notebook: EDA, preprocessing, model building
├── requirements.txt                  # Python dependencies
├── .gitattributes                    # Git LFS / line ending config
│
└── README.md                         # Project documentation
```

> **Note:** The precomputed `similarity.pkl` and `movies.pkl` files are generated by running the notebook and must be present in the root directory before launching `app.py`.

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9 or higher
- A free [TMDb API key](https://www.themoviedb.org/settings/api)
- `pip` package manager
- Virtual environment (recommended)

### 1. Clone the Repository

```bash
git clone https://github.com/anas-py/AI-ML-Intern-project.git
cd AI-ML-Intern-project
```

### 2. Create & Activate a Virtual Environment

**Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**macOS / Linux:**
```bash
python -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Generate Model Artifacts

Run the Jupyter notebook to preprocess data and generate the required pickle files:

```bash
jupyter notebook movie-recommernder-system.ipynb
```

Execute all cells — this will create `movies.pkl` and `similarity.pkl` in the project root.

### 5. Launch the Streamlit App

```bash
streamlit run app.py
```

Open your browser at **[http://localhost:8501](http://localhost:8501)**

---

## 🔑 TMDb API Setup

The app fetches live movie posters using the TMDb REST API. To enable this:

1. Visit [https://www.themoviedb.org](https://www.themoviedb.org) and create a free account
2. Navigate to **Settings → API** and request an API key (v3 auth)
3. Open `app.py` and locate the `fetch_poster()` function
4. Replace the placeholder with your API key:

```python
def fetch_poster(movie_id):
    url = f"https://api.themoviedb.org/3/movie/{movie_id}?api_key=YOUR_API_KEY&language=en-US"
    response = requests.get(url)
    data = response.json()
    return "https://image.tmdb.org/t/p/w500/" + data['poster_path']
```

> ⚠️ Never commit your API key to a public repository. Use environment variables or a `.env` file in production.

---

## 🖥️ Application Usage

Once the app is running:

1. A **dropdown menu** displays all ~5,000 movie titles from the dataset
2. Select any movie you like from the dropdown
3. Click **"Recommend"**
4. The app instantly displays **5 similar movie recommendations** in a grid layout
5. Each recommendation includes the **movie title** and its **official TMDb poster**

**Example:**
> Select: *The Dark Knight* → Recommendations: *Batman Begins*, *The Dark Knight Rises*, *Iron Man*, *Spider-Man*, *Avengers*

---

## 🚀 Future Improvements

| Improvement | Description |
|---|---|
| 🤝 **Hybrid Filtering** | Combine content-based with collaborative filtering for personalized recommendations |
| ⭐ **Ratings & Reviews** | Display TMDb ratings, release year, and user reviews alongside posters |
| 🔍 **Search Functionality** | Add a search bar with fuzzy matching for easier movie discovery |
| ☁️ **Cloud Deployment** | Host on Streamlit Cloud, Heroku, or HuggingFace Spaces for public access |
| 🔐 **User Profiles** | Allow users to save preferences and get personalized recommendation histories |
| 🎭 **Genre Filters** | Add sidebar filters to narrow recommendations by genre, year, or language |
| 📊 **Similarity Scores** | Display the cosine similarity score alongside each recommendation for transparency |

---

## 👤 Author

**Mohd Anas**
M.Sc. Artificial Intelligence & Machine Learning
Jamia Millia Islamia, New Delhi

[![GitHub](https://img.shields.io/badge/GitHub-anas--py-181717?style=flat-square&logo=github)](https://github.com/anas-py)

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

Made with ❤️ by [anas-py](https://github.com/anas-py) · AI/ML Internship Project

⭐ If you found this project helpful, consider giving it a star!

</div>

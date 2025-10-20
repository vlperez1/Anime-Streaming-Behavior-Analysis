cat > README.md << 'EOF'
# 🎥 Anime Streaming Behavior Analysis  

**Goal:** Analyze user engagement differences between *subbed* and *dubbed* content for an anime streaming platform — uncovering audience patterns, optimizing engagement, and informing localization strategy.  

---

## 🧠 Project Overview  

This project replicates the workflow of a **Product or Data Analyst** at a streaming platform (like Crunchyroll or Netflix Anime).  
It covers data cleaning, user segmentation, recommendation systems, and A/B testing — built fully in Python and Power BI.  

**Key Objectives:**  
- 🧩 Identify unique **user segments** based on genre preferences and rating behavior  
- 🤖 Build a simple **recommendation engine prototype**  
- 🧪 Run an **A/B testing simulation** comparing *Subbed vs. Dubbed* engagement  

---

## 📂 Dataset Description  

Two main datasets were used:  

| File | Description |
|------|--------------|
| `anime.csv` | Anime titles, genres, type, average rating, and total members |
| `rating_sampled.csv` | User-level anime ratings (sampled to fit GitHub’s size limit) |

After cleaning and merging, the dataset contained **40,558 records × 9 columns**, representing unique user-anime interactions.

---

## 🧹 Data Cleaning Steps  

1. Checked for missing values and duplicates  
2. Filled or dropped incomplete `genre` and `type` entries  
3. Merged `anime.csv` and `rating_sampled.csv` on `anime_id`  
4. Renamed columns for clarity (`rating_x → user_rating`, `rating_y → avg_rating`)  
5. Saved clean dataset → `anime_merged_clean.csv`  

---

## 📊 Exploratory Data Analysis (EDA)  

**Key Findings:**  
- Most common genres: *Action*, *Comedy*, *Drama*, *Fantasy*  
- *TV series* and *Movies* achieved the highest median ratings  
- Positive correlation between **popularity (members)** and **average rating consistency**  


## 🧩 User Segmentation (Clustering)

### 🎯 Objective  
Group anime users by their rating behavior and genre preferences to uncover viewing personas and support content personalization.

### 🧮 Methodology  
1. Expanded multi-genre strings into lists and exploded rows.  
2. Built a **user–genre matrix** (users as rows, genres as columns).  
3. Scaled features using `StandardScaler`.  
4. Applied **K-Means clustering** (`n_clusters=5`).  
5. Interpreted each cluster based on their top 5 average-rated genres.

### 🧠 Cluster Insights

| Cluster | Persona Label | Genre Preference Highlights |
|----------|----------------|------------------------------|
| 0 | 🎭 Complex Thinkers | Psychological, Action, Comedy |
| 1 | 💞 Emotional Adventurers | Supernatural, Adventure, Romance |
| 2 | ⚔️ Shōnen Core Fans | Action, Fantasy, Ecchi |
| 3 | 🔎 Social Slice Enthusiasts | Mystery, Comedy, Harem, Drama |
| 4 | 🎓 Everyday Story Lovers | Drama, Shounen, Slice of Life |

**Interpretation:**  
Each cluster reveals a unique audience type, which can guide **recommendation strategies**, **UI customization**, and **targeted marketing**.

### 🤖 2️⃣ Recommendation Engine Prototype Section

## 🤖 Recommendation Engine Prototype

### 🎯 Objective  
Build a simple recommendation system using **collaborative filtering** to suggest similar anime titles based on user rating patterns.

### 🧮 Methodology  
1. Created a **User–Anime matrix** from `user_id` × `anime_name`.  
2. Filled missing ratings with zeros.  
3. Computed **cosine similarity** between anime titles.  
4. Built a function to return the top 5 similar titles.


## 🧪 A/B Testing Simulation — Subbed vs Dubbed Engagement

### 🎯 Objective  
Evaluate whether *Subbed* or *Dubbed* anime achieves higher completion rates and user engagement.

### 🧮 Methodology  
- Simulated **5,000 users** divided evenly between “Subbed” and “Dubbed.”  
- Modeled completion rates as normal distributions with different means.  
- Performed an **independent t-test** to assess statistical significance.  


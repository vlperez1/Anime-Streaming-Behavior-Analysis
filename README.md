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

Example visualization:  
```python
sns.barplot(x='type', y='avg_rating', data=anime)
plt.title('Average Rating by Anime Type')

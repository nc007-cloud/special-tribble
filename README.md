# special-tribble

# Music Mood Classification: A Precursor Pipeline to Building Robust Mood-Based Music Recommendation Systems
# Dataset: https://drive.google.com/drive/folders/1D3cXbMS_znaZb0Y46jEaos-7lD3QaQEP
# Music Mood Classification and Recommendation System Pipeline

**Author:** Nilovna Chatterjee, PhD  
**GitHub:** [https://github.com/nc007-cloud](https://github.com/nc007-cloud)

---

## 1. Define the Problem Statement

### Goal & Motivation

Modern music streaming services strive to provide personalized listening experiences. The challenge is accurately classifying songs into “mood” categories (e.g., Mellow, Powerful Calm, Upbeat, Groovy Dance) to recommend tracks that match a user's current mood or preferences. This project aims to build a **Music Mood Classification and Recommendation System** that leverages both unsupervised and supervised machine-learning techniques to group songs by mood and predict these mood labels for new or untagged tracks.

### Benefits & Challenges

**Benefits:**
- **Enhanced User Experience:** Match music to a user’s mood or activity.
- **Improved Music Discovery:** Generate mood-based playlists and recommendations.
- **Context-Aware Recommendations:** Tailor suggestions based on workout, study, or commute scenarios.

**Challenges:**
- High overlap between musical features (e.g., loudness vs. energy).
- The subjective nature of “mood” labeling.
- Ensuring robust classification performance for new or unseen music.

---

## 2. Model Outcomes or Predictions

### Types of Learning
- **Unsupervised:**  
  - Clustering songs into mood-based groups using **K-Means** and **Gaussian Mixture Models (GMM)**.
- **Supervised:**  
  - Training a **Neural Network** classifier to predict the mood cluster for any given track.

### Output
- Each song receives a mood label (e.g., *Mellow Acoustic*, *Powerful Calm*, *Upbeat*, *Groovy Dance*) or a soft cluster assignment (probabilities for each mood category).
- The final system can recommend tracks based on these mood labels.

---

## 3. Data Acquisition

### Sources & Rationale
- **Million Song Dataset / Spotify:**  
  Merged multiple data sources containing audio features such as tempo, valence, energy, loudness, danceability, and acousticness.
  
- **Dataset Access:**  
  - [Music Dataset](#) (Google Drive Link)  
  - [Mood Recommender on Kaggle](#)

- **Simulated or Augmented Data:**  
  For cases where specific features (e.g., energy, danceability) were missing, we generated or imputed them for demonstration.

### Visualization of Potential
- **Distribution Plots:**  
  Visualize distributions of key features like loudness, tempo, and energy.
- **Correlation Heatmaps:**  
  Highlight inter-feature relationships (e.g., loudness vs. energy).

---

## 4. Data Preprocessing/Preparation (EDA)

### Cleaning & Consistency
- Removed missing or inconsistent values.
- Converted feature columns to numeric (`float32`) and handled any string or categorical anomalies.

### Splitting the Data
- Separated data into training and test sets (commonly an 80/20 split).
- Used k-fold cross-validation to robustly evaluate model performance.

### Encoding & Analysis
- For unsupervised methods, used raw or scaled numeric features.
- For supervised methods, ensured the target (mood cluster) was integer-encoded.
- Applied **StandardScaler** to normalize numeric features, enhancing model stability.

---

## 5. Modeling

### Unsupervised Algorithms
- **K-Means:**  
  - Created hard clusters for each track and labeled these clusters with descriptive mood tags based on cluster centroids.
  
- **Gaussian Mixture Model (GMM):**  
  - Generated soft (probabilistic) cluster assignments, allowing partial membership in multiple clusters.

### Supervised Algorithm
- **Neural Network Classifier:**
  - **Architecture:**  
    Two hidden layers (64 and 32 neurons) with **ReLU** activation and dropout regularization.
  - **Output:**  
    Softmax layer for multi-class classification.
  - **Training:**  
    Used the Adam optimizer and `sparse_categorical_crossentropy` loss.

### Feature Engineering
- **Ratios & Interactions:**  
  e.g., `energy_loudness_ratio`, `dance_energy_interaction`.
- **Transformations:**  
  e.g., log-transform of tempo.
- **Optional:**  
  Genre encoding, tempo variability, etc.

---

## 6. Model Evaluation

### Models Considered
1. **K-Means Clustering:**  
   - Evaluated via the Elbow Method and Silhouette Score.
   - Provided initial hard labels for each cluster.
  
2. **Gaussian Mixture Model (GMM):**  
   - Evaluated via posterior probabilities and Silhouette Score.
   - Allowed soft (fuzzy) cluster assignments.
  
3. **Neural Network Classifier:**  
   - **Accuracy:**  
     Achieved ~97–98% test accuracy (and similar cross-validation accuracy).
   - **Cross-Validation:**  
     5-fold CV showed consistent performance (e.g., average 97.30% ± 0.93%).
   - **Feature Importance:**  
     Explored via logistic regression coefficients (post-K-Means) and GMM centroid variation.

### Optimal Model
- For mood prediction, the **Neural Network** with advanced feature engineering achieved the highest accuracy (~97–98%).
- GMM provided nuanced, soft cluster assignments valuable for recommendation logic.

---

## 7. Conclusion & Future Work

### Key Findings
- Advanced feature engineering (ratios, log transforms, interactions) significantly boosted classification performance.
- A two-layer neural network with dropout, trained on scaled features, consistently achieved high accuracy across folds.
  
### Next Steps
- **Hyperparameter Tuning:**  
  Fine-tune layer sizes, dropout rates, and learning rates.
  
- **External Validation:**  
  Test on new datasets to ensure model generalization.
  
- **Recommendation Integration:**  
  Combine user preferences and context (e.g., time of day, activity) with the mood classifier for a comprehensive recommendation pipeline.
  
- **Explainability & User Feedback:**  
  Use tools like SHAP or LIME and incorporate real-time feedback to refine mood labels over time.


## Business Value

In today's competitive music streaming market, delivering a unique and engaging user experience is paramount. **Music Mood Classification** offers a powerful foundation for:

- **Personalized Playlists & Recommendations:**  
  Generate mood-based playlists that resonate with user emotions, increasing engagement, session duration, and customer retention.

- **Context-Aware Music Services:**  
  Adapt music recommendations in real time based on user context (e.g., workout, relaxation, study), ensuring that the right mood is always delivered.

- **Efficient Content Curation:**  
  Automate tagging large music catalogs with mood labels, reducing manual effort and operational costs.

- **Enhanced User Experience:**  
  Enable marketing and advertising strategies that match brand identity with the right musical mood, fostering deeper connections with audiences.

## Key Features

- **Advanced Audio Feature Extraction:**  
  Utilizes fundamental audio attributes such as valence, danceability, energy, acoustics, tempo, and loudness.

- **Engineered Interactions & Transformations:**  
  Incorporates additional features like energy-to-loudness ratio, valence-acousticness interaction, and log-transformed tempo to capture complex relationships in music.

- **Dual Clustering Approach:**  
  Combines traditional K-Means for crisp mood assignments with Gaussian Mixture Models for fuzzy, probabilistic clustering.

- **High-Performance Neural Network:**  
  A well-tuned deep learning model achieves over 97% accuracy in predicting mood clusters, ensuring reliable classification.

- **Robust Validation:**  
  Extensive cross-validation confirms the model's stability and generalizability across diverse data splits.

## Use Cases

- **Streaming Services:**  
  Platforms like Spotify, Apple Music, and Tidal can leverage mood classification to offer highly personalized, context-aware playlists.

- **Music Licensing & Production:**  
  Automated mood tagging accelerates finding the perfect track for films, ads, and video games.

- **Retail, Hospitality & Wellness:**  
  Dynamic background music systems that adjust based on customer mood or time of day, enhancing overall user experience.

- **Marketing & Branding:**  
  Agencies can match music to brand messaging, ensuring that advertising campaigns strike the right emotional chord.

## Why This Matters

This project is not just about classifying music moods—it’s about laying the groundwork for a next-generation recommendation system that blends technical rigor with business impact. By understanding the subtle interplay of musical features and moods, companies can offer more engaging, personalized experiences that drive customer loyalty and revenue growth.

## Final Note

While this project serves as a crucial building block, it is part of a larger ecosystem for music recommendation systems. The insights and techniques developed here can be integrated with user behavior data, contextual signals, and additional metadata to build a comprehensive, state-of-the-art music recommendation engine.

---

*This repository includes all the necessary code, documentation, and configuration files (e.g., `environment.yml,` CI workflows) to reproduce and extend the project. Feel free to explore, contribute, or adapt this work for your own music recommendation and mood classification needs.*

### Final Note
This project demonstrates a comprehensive approach to music recommendation. It blends unsupervised clustering to discover natural groupings with a supervised neural network to predict mood labels. The high accuracy and robust validation indicate that the system is well-positioned for real-world deployment and continuous improvement.

---

*This repository includes all code, data processing scripts, Jupyter Notebooks, and configuration files (e.g., `environment.yml,` CI workflows) necessary to reproduce and extend this work. 

You can explore, contribute, or adapt this project to your needs.*


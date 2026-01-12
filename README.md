# 🤖 AI Career Advisor: ML-Based Recommendation Engine

## ✨ Project Vision
This project is an MVP (Minimum Viable Product) for a personalized career guidance system. It utilizes Machine Learning to recommend the most relevant job roles and specific learning paths based on a user's skills, interests, and career goals.

## 🧠 Model & Approach
The advisor uses a **two-stage recommendation pipeline**:

1.  **Feature Engineering (TF-IDF):** User skills and role requirements are converted into weighted numerical vectors using **TF-IDF (Term Frequency-Inverse Document Frequency)**. This ensures specialized skills (e.g., Deep Learning) contribute more to the similarity score than common skills (e.g., Excel).
2.  **Ranking (Logistic Regression):** A **Logistic Regression** model is trained on synthetic data to learn the optimal weights for three key features (Skill Similarity, Skill Gap Count, and Goal Alignment). This model predicts the final **"Fit Score"** (probability of a good fit, from 0.0 to 1.0).

## 💻 Tech Stack
* **Core Language:** Python 3
* **ML Libraries:** pandas, scikit-learn, joblib
* **Web Framework:** Flask
* **Interface:** Basic HTML/JavaScript (calls the Flask API)

## ⚙️ Setup and Installation

### Prerequisites
1.  Python 3.8+ installed.

### Installation Steps
1. Clone this repository (once you push it to GitHub) or download the files.
2. Navigate into the project directory.
3. Install required libraries:
    ```bash
    pip install -r requirements.txt
    ```

### Running the Advisor

1.  **Generate Training Data:** Run the script to create the features CSV and train the Logistic Regression model:
    ```bash
    python train_data.py
    ```
2.  **Start the Server:** Start the Flask API and web interface:
    ```bash
    python app.py
    ```
3.  **Access the Advisor:** Open your web browser and navigate to: **`http://127.0.0.1:5000/`**

## 🤝 API Contract (Example Endpoint)
The core logic is exposed via a simple API endpoint:

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/recommend` | Returns top 5 ranked roles, fit scores, and suggested learning paths. |

**Example Body (JSON):**
```json
{
    "user_skills": ["SQL", "Python", "Data Visualization"],
    "user_career_goal": "Data Science"
}

# YouTube Comment Sentiment Intelligence

This project analyzes **YouTube video comments** to understand how viewers feel about a video.  
It combines **machine learning**, **Flask APIs**, **a Chrome extension frontend**, and **MLOps tools (DVC, ML FLOW, AWS)** to build a practical, production-style sentiment analysis system. 

> 🔎 **One-line summary:**  
> An end-to-end MLOps project that predicts sentiment (positive/negative/neutral) for YouTube comments and exposes the model as an API + Chrome extension UI.

---

## 🎯 Key Features

- Fetch and analyze **YouTube comments** for a given video.
- Preprocess text data and perform **sentiment classification**.
- Serve predictions via a **Flask API** endpoint (`/predict`). 
- Example JSON request for multiple comments (Postman / any client):

  ```json
  {
    "comments": [
      "This video is awesome! I loved it a lot",
      "Very bad explanation. Poor video"
    ]
  }
Chrome extension frontend (folder: yt-chrome-plugin-frontend) to integrate with the YouTube page UI. 
GitHub
+1

End-to-end pipeline tracked with DVC (dvc.yaml, dvc.lock, .dvc/, params.yaml). 
GitHub

Ready for deployment on AWS (using aws configure + Docker/EC2-style flow ). 
GitHub
## 🏗️ Project Structure

```text
Sentiment-Intelligence-for-YouTube-Comments/
├── .dvc/                       # DVC metadata and cache configurations
├── flask_app/                  # Flask REST API for model serving
├── yt-chrome-plugin-frontend/  # Chrome extension source code
├── src/                        # Modular source code (Data, Model, Pipeline)
├── scripts/                    # Utility scripts for automation
├── notebooks/                  # Jupyter notebooks for EDA & Experiments
├── dvc.yaml                    # DVC pipeline stage definitions
├── dvc.lock                    # Locked pipeline state and data hashes
├── params.yaml                 # Parameters for training & preprocessing
├── requirements.txt            # Project dependencies
└── confusion_matrix_Test.png   # Model evaluation visualization

AWS: Cloud Deployment (EC2, ECR)

Docker: Containerization

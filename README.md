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

Ready for deployment on AWS (using aws configure + Docker/EC2-style flow as taught in the MLOps course). 
GitHub

🏗️ Project Structure
Approximate structure of this repo: 
GitHub

bash
Copy code
Sentiment-Intelligence-for-YouTube-Comments/
├── flask_app/                   # Flask API for serving the model
├── yt-chrome-plugin-frontend/   # Chrome extension frontend
├── src/                         # Core source code (data, model, utils, pipeline)
├── scripts/                     # Helper scripts / pipeline steps
├── notebooks/                   # Jupyter notebooks for EDA & experiments
├── .dvc/                        # DVC metadata
├── dvc.yaml                     # Pipeline stages definition
├── dvc.lock                     # Locked pipeline + artifacts
├── params.yaml                  # Training / preprocessing parameters
├── requirements.txt             # Python dependencies
├── confusion_matrix_Test Data.png
├── README.md
└── ...
You can update this tree later if you add/remove folders.

⚙️ Tech Stack
Language: Python 3.11 
GitHub

ML / Data: (likely) pandas, numpy, scikit-learn or similar (as defined in requirements.txt)

Backend API: Flask (flask_app/)

Frontend: Chrome extension (yt-chrome-plugin-frontend/)

MLOps:

DVC for data & model versioning (dvc.yaml, .dvc, params.yaml)

AWS for cloud deployment (EC2 + ECR style, configurable via aws configure) 
GitHub

🚀 Getting Started
1. Clone the repository
bash
Copy code
git clone https://github.com/RajT393/Sentiment-Intelligence-for-YouTube-Comments.git
cd Sentiment-Intelligence-for-YouTube-Comments
2. Create and activate a conda environment
bash
Copy code
conda create -n youtube python=3.11 -y
conda activate youtube
3. Install dependencies
bash
Copy code
pip install -r requirements.txt
🔄 Working With DVC
The project uses DVC to manage the pipeline and data. Basic commands: 
GitHub

bash
Copy code
# Initialize (if not already done)
dvc init

# Reproduce the entire pipeline (data → training → evaluation → artifacts)
dvc repro

# Visualize pipeline DAG
dvc dag
Make sure your remote storage (e.g., Google Drive, S3, etc.) is configured if you are pulling large data or models.

🌐 Running the Flask API
Navigate to the Flask app directory (if required):

bash
Copy code
cd flask_app
Start the Flask server (example):

bash
Copy code
python app.py
Test the /predict endpoint (e.g. using Postman or curl):

URL:

text
Copy code
http://localhost:5000/predict
Sample JSON body:

json
Copy code
{
  "comments": [
    "This video is awesome! I loved it a lot",
    "Very bad explanation. Poor video"
  ]
}
The API will return sentiment predictions for each comment.

🧩 Chrome Extension (Frontend)
The folder yt-chrome-plugin-frontend contains a Chrome extension that can be loaded in Developer Mode to interact with the backend API and display sentiment directly on YouTube: 
GitHub
+1

Basic steps:

Go to chrome://extensions in Chrome.

Enable Developer mode (top-right).

Click “Load unpacked” and select the yt-chrome-plugin-frontend folder.

Open a YouTube video and use the extension to trigger sentiment analysis.

Make sure your Flask API is running before using the extension.

☁️ AWS Deployment (High-Level)
Following the MLOps course pattern: 
GitHub

Typical steps:

aws configure – configure your AWS CLI with access keys.

Build a Docker image for the Flask app.

Push the Docker image to Amazon ECR.

Launch an EC2 instance.

Pull the image from ECR on EC2.

Run the container and expose the API publicly.

(You can document your exact commands here as you complete deployment.)

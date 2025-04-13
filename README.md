🎬 Movie Recommender System

This is a simple and interactive Movie Recommender System built using Streamlit, TMDB API, and Python. It recommends movies based on similarity and displays their posters using TMDB.

🚀 Features

Get top 5 similar movies for any selected title

Fetch movie posters using TMDB API

Interactive UI built with Streamlit

Lightweight and beginner-friendly

Dockerized for easy deployment

📦 Installation (Step by Step)

1. 🧱 Clone the project

git clone https://github.com/sujalgp/movie-recommender.git
cd movie-recommender

2. 🐍 Create and activate virtual environment (optional but recommended)

python -m venv venv
venv\Scripts\activate  # On Windows
# OR
source venv/bin/activate  # On macOS/Linux

3. 📥 Install Python libraries

pip install -r requirements.txt

4. ▶️ Run the app

streamlit run app.py

Then open your browser and go to:👉 http://localhost:8501

🐳 Docker Usage (Optional)

1. 📦 Build the Docker image

docker build -t sujalgp/movie-app .

2. ▶️ Run the Docker container

docker run -p 8501:8501 sujalgp/movie-app

Then visit:👉 http://localhost:8501

🔄 GitHub Actions (CI/CD)

You can add a GitHub Action workflow to automatically build and push your Docker image:

Create this file:

.github/workflows/docker-publish.yml

And add:

name: Build and Push Docker image

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Log in to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKER_USERNAME }}
          password: ${{ secrets.DOCKER_PASSWORD }}

      - name: Build and push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: sujalgp/movie-app:latest

🔧 Tech Stack

Python

Streamlit

Pandas

Requests

TMDB API

Docker

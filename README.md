🎬 Movie Recommender System

A content-based Movie Recommender System built using Streamlit and Python. The system recommends movies based on similarity and displays their posters using TMDB API.

Working link:https://sujal2806-movie-recommendation-system-app-6qsn2s.streamlit.app/

🚀 Features

- Content-based movie recommendations
- Get top 5 similar movies for any selected title
- Fetch movie posters using TMDB API
- Interactive UI built with Streamlit
- Pre-computed similarity matrix for fast recommendations
- Dockerized for easy deployment

📦 Installation

1. Clone the repository
```bash
git clone https://github.com/yourusername/movie-recommender.git
cd movie-recommender
```

2. Create and activate virtual environment (optional but recommended)
```bash
python -m venv venv
venv\Scripts\activate  # On Windows
# OR
source venv/bin/activate  # On macOS/Linux
```

3. Install dependencies
```bash
pip install -r requirements.txt
```

4. Run the application
```bash
streamlit run app.py
```

The application will be available at http://localhost:8501

🐳 Docker Deployment

1. Build the Docker image
```bash
docker build -t movie-recommender .
```

2. Run the container
```bash
docker run -p 8501:8501 movie-recommender
```

🔄 GitHub Actions (CI/CD)

This project includes GitHub Actions workflow for automated Docker image building and deployment. The workflow automatically builds and pushes the Docker image to Docker Hub when changes are pushed to the main branch.

To set up GitHub Actions:

1. Create the following file: `.github/workflows/docker-publish.yml`
2. Add your Docker Hub credentials to GitHub repository secrets:
   - `DOCKER_USERNAME`: Your Docker Hub username
   - `DOCKER_PASSWORD`: Your Docker Hub access token

The workflow configuration:
```yaml
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
          tags: ${{ secrets.DOCKER_USERNAME }}/movie-recommender:latest
```

🔧 Tech Stack

- Python 3.x
- Streamlit - Web application framework
- Pandas - Data manipulation
- NumPy - Numerical computations
- Requests - HTTP requests for TMDB API
- TMDB API - Movie data and posters
- Docker - Containerization

📝 Project Structure

- `app.py` - Main application file
- `movie_list.pkl` - Preprocessed movie dataset
- `similarity.pkl` - Pre-computed similarity matrix
- `requirements.txt` - Python dependencies
- `Dockerfile` - Docker configuration

🔑 Environment Variables

The application uses TMDB API. You'll need to replace the API key in `app.py` with your own:
```python
api_key = "your_tmdb_api_key"
```

📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

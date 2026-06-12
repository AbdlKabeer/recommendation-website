# Recommendation Web Platform Backend

This repository contains the backend service for a recommendation-driven learning platform. Built with Django and Django REST Framework (DRF), this platform provides robust APIs to serve educational content such as articles, videos, and quizzes to students. The system is augmented by a custom machine learning hybrid recommendation engine.

## Key Features

- **Educational Content Management**: Robust models and viewsets to handle Articles, Videos, and Quizzes.
- **Student & Account Management**: Authentication endpoints, JWT support, and student profiles.
- **Hybrid Recommendation Engine**: Incorporates both content-based filtering (TF-IDF & Cosine Similarity) and collaborative filtering (Surprise SVD) to suggest the most relevant content types to users based on titles and viewing history.
- **Export Capabilities**: Commands available for exporting videos and quizzes to excel/csv files.

## Tech Stack

- **Framework**: Django, Django REST Framework
- **Database**: SQLite (default configuration), PostgreSQL (supported)
- **Machine Learning**: `scikit-learn` (TF-IDF), `scikit-surprise` (SVD), `pandas`, `numpy`
- **Data Scraping & Parsing**: `newspaper3k`, `beautifulsoup4`
- **Authentication**: `djangorestframework-simplejwt`

## Installation and Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/AbdlKabeer/recommendation-website.git
   cd recommendation-website
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```

3. **Install the dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run migrations:**
   ```bash
   python manage.py migrate
   ```

5. **Create a superuser (optional):**
   ```bash
   python manage.py createsuperuser
   ```

6. **Start the development server:**
   ```bash
   python manage.py runserver
   ```

## Exporting Data

You can easily export your existing data using custom management commands:

- **Export Videos:**
  ```bash
  python manage.py export_videos_to_excel --format=csv
  ```

- **Export Quizzes:**
  ```bash
  python manage.py export_quizzes_to_excel --format=csv
  ```

## Recommendation Engine

The core recommendation logic is located in `prediction_model.py`. It provides hybrid recommendations combining content attributes (tags, titles, descriptions) and mock collaborative filtering.

## API Endpoints Overview

- `POST /api/account/auth/login` - Obtain JWT Token
- `POST /api/account/auth/register` - Register a new user
- `GET /api/articles` - List articles
- `GET /api/admin/videos` - Manage videos
- `GET /api/admin/quizzes` - Manage quizzes

*(View `api/urls.py` and the respective viewsets for complete endpoint definitions)*

## License

This project is licensed under the MIT License.

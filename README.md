# Landscape Classifier

An AI-powered image classifier that identifies landscape categories from uploaded photos. Classifies images into: **Buildings, Forests, Mountains, Glacier, Street, Sea**.

## How It Works

- **Backend**: Flask API (`app.py`) loads a pre-trained Keras model (`model.h5`) and exposes a `/predict` endpoint
- **Frontend**: Static HTML/CSS/JS (`web/`) that sends images to the backend and displays the top 3 predictions with confidence scores

## Requirements

- Python 3.11 (TensorFlow does not support Python 3.12+ yet)
- `model.h5` is included in the repository

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/kenzitjandra/LandscapeClassifier.git
cd LandscapeClassifier
```

### 2. Create a virtual environment with Python 3.11

```bash
py -3.11 -m venv venv
```

### 3. Activate the virtual environment

**Windows:**
```bash
venv\Scripts\activate
```

**Mac/Linux:**
```bash
source venv/bin/activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

## Running the App

```bash
python app.py
```

Then open `http://localhost:5000` in your browser. Upload an image and click **Classify Image**.

## Project Structure

```
LandscapeClassifier/
├── app.py          # Flask backend + prediction logic
├── model.h5        # Trained Keras model (not in repo)
└── web/
    ├── index.html  # Frontend UI
    └── style.css   # Styles
```

## API

**POST** `/predict`

Accepts a multipart form upload with a field named `file`.

```json
{
  "top_predictions": [
    { "label": "Forests", "confidence": 92.4 },
    { "label": "Mountains", "confidence": 5.1 },
    { "label": "Sea", "confidence": 1.3 }
  ]
}
```

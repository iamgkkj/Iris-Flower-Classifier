# Iris Flower Classifier API & Web UI

A streamlined MLOps pipeline that trains a Random Forest model using scikit-learn, wraps it in a Flask web API, and containerizes the entire environment with Docker. It includes an elegant front-end interface built with Tailwind CSS for making real-time interactive predictions.

## Developer Info
* **Name:** Gopal Krishn Khoth
* **Registration Number:** 23BCE10669

### 📱 Access on Mobile

Scan the QR code below to quickly open the live application on your mobile device:
<p align="center">
  <img src="https://raw.githubusercontent.com/iamgkkj/Iris-Flower-Classifier/79596e2b0d25fe1c6bd1207d5dcb5af909905e9f/static/qr.png" alt="Live App QR Code" width="200">
</p>

---

### 💻 Desktop View

Here is a look at the live application running on a desktop:

<p align="center">
  <img src="https://raw.githubusercontent.com/iamgkkj/Iris-Flower-Classifier/de7c132e082565e42625a8a8e900716ca95ae487/static/desktop.png" alt="Desktop View Screenshot" width="700">
</p>

---

## Project Structure
The repository contains the following core files and directories:
```text
iris-api/
├── templates/
│   └── index.html      # Frontend user interface
├── app.py              # Flask API server & inference endpoints
├── train.py            # Model training and serialization script
├── iris_model.pkl      # Serialized random forest model weights
├── Dockerfile          # Container environment configuration
├── requirements.txt    # Application dependencies
└── .gitignore          # Version control file exclusions

```

---

## Local Setup & Installation

### 1. Environment Configuration

Create and activate an isolated development environment using Conda:

```bash
conda create -n iris-mlops python=3.12 -y
conda activate iris-mlops

```

### 2. Dependency Installation

Install the necessary project dependencies listed in the requirements file:

```bash
pip install -r requirements.txt

```

* Dependencies include `flask`, `gunicorn`, `scikit-learn`, `joblib`, and `numpy` .

---

## Execution Guide

### 1. Train the Model

Generate a freshly trained model binary by executing the training script:

```bash
python train.py

```

* This loads the native scikit-learn Iris dataset, trains a classification model, and dumps it to `iris_model.pkl` .



### 2. Run the App Locally

Fire up the Flask server in your terminal environment:

```bash
PORT=5001 python app.py

```

* Open `http://127.0.0.1:5001` in your web browser to access the interactive web dashboard.

---

## Running with Docker

### 1. Build the Docker Image

Compile the isolated application runtime using the Dockerfile configuration:

```bash
docker build -t iris-api .

```

### 2. Start the Container

Spin up the container instance by mapping the internal environment port to your local machine:

```bash
docker run -e PORT=5001 -p 5001:5001 iris-api

```

* Access the web platform natively at `http://localhost:5001`.

---

## API Documentation

### Health Check Route

* **Endpoint:** `GET /`
* **Description:** Renders the frontend UI form dashboard.

### Prediction Route

* 
**Endpoint:** `POST /predict` 


* 
**Headers:** `Content-Type: application/json` 


* 
**Payload Format:** 


```json
{
  "sepal_length": 5.1,
  "sepal_width": 3.5,
  "petal_length": 1.4,
  "petal_width": 0.2
}

```


* 
**Success Response (200 OK):** 


```json
{
  "class": "Setosa"
}

```

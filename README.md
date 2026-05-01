# Titanic Survival Prediction API

A production-style machine learning API that predicts passenger survival on the Titanic using a Random Forest classifier. The model is served via FastAPI and deployed using Docker.

This project demonstrates an end-to-end machine learning workflow including data preprocessing, model training, evaluation, and API deployment.

---

## 🧠 Tech Stack

* Python
* FastAPI
* Scikit-learn
* Pandas / NumPy
* Docker

---

## 🚀 Features

* Predict passenger survival using a trained ML model
* REST API built with FastAPI
* Batch prediction support
* Dockerized for easy deployment
* Interactive API documentation via Swagger

---

## ⚙️ Quick Start

### Run the API locally

```bash
docker pull messycannn/titanic-survival-api:latest
docker run -p 8000:8000 messycannn/titanic-survival-api:latest
```

---

### Use the API

Visit:

http://localhost:8000/docs

---

## 📡 Example Prediction

```bash
curl -X POST "http://localhost:8000/predict" \
     -H "Content-Type: application/json" \
     -d '{
       "Pclass": 1,
       "Sex": "female",
       "Age": 30.0,
       "SibSp": 0,
       "Parch": 0,
       "Fare": 50.0,
       "Embarked": "S"
     }'
```

---

## 📈 Example Response

```json
{
  "survived": 1,
  "survival_probability": 0.95,
  "prediction_confidence": "High",
  "passenger_profile": {
    "class": "Class 1",
    "gender": "female",
    "age_group": "Adult",
    "family_size": 1,
    "traveling_alone": true,
    "fare_level": "High",
    "embarkation_port": "Southampton"
  }
}
```

---

## 📊 Model Performance

* Algorithm: Random Forest Classifier
* Accuracy: 85%+ on test data
* Features used:

  * Passenger class
  * Sex
  * Age
  * Family size
  * Fare
  * Embarkation port

---

## 🔌 API Endpoints

* `GET /` → Health check
* `POST /predict` → Single passenger prediction
* `POST /predict-batch` → Batch predictions
* `GET /model-info` → Model metadata

---

## 📥 Input Parameters

| Parameter | Type  | Description               | Example  |
| --------- | ----- | ------------------------- | -------- |
| Pclass    | int   | Passenger class (1, 2, 3) | 1        |
| Sex       | str   | Gender ('male', 'female') | 'female' |
| Age       | float | Age in years              | 30.0     |
| SibSp     | int   | Siblings/spouses aboard   | 0        |
| Parch     | int   | Parents/children aboard   | 0        |
| Fare      | float | Ticket fare               | 50.0     |
| Embarked  | str   | Port ('S', 'C', 'Q')      | 'S'      |

---

## 🛠️ Development

### Training Environment

```bash
cd training
docker build -t titanic-training .
docker run -p 8888:8888 -v "$(pwd):/home/jovyan/work" titanic-training
```

---

### Local Development

```bash
cd serving
pip install -r requirements.txt
python app.py
```

---

## 📌 Project Structure

```bash
titanic-ml-project/
  serving/        # FastAPI application
  training/       # Model training pipeline
  models/         # Saved model artifacts
  README.md
  .gitignore
```

---

## 🔮 Future Improvements

* Model versioning
* Improved feature engineering
* Cloud deployment (AWS / GCP)
* Authentication and rate limiting

---

## License

This project is for educational purposes.

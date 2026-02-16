# Insurance-Premium-Prediction API
This project provides a production-ready RESTful API developed to predict insurance premium categories based on individual health and demographic metrics. It demonstrates a structured software engineering approach to machine learning deployment using FastAPI, Pydantic, and Docker.

Key Frameworks & Technologies:
1. FastAPI: High-performance web framework for building APIs with Python 3.11+.
2. Pydantic: Data validation and settings management using Python type annotations to ensure rigorous schema enforcement.
3. Uvicorn: An ASGI web server implementation for high-concurrency performance.
4. Docker: Used for containerizing the application to ensure consistent deployment environments.
5. Scikit-Learn: Core library used for the underlying predictive model logic.

##  Project Structure

```text
├── config/             # Configuration files
├── model/              # Trained .pkl files
├── schema/             # Pydantic validation models
├── app.py              # FastAPI main entry point
├── predict.py          # Prediction logic
├── Dockerfile          # Docker configuration
└── requirements.txt    # Project dependencies

Implementation Details & Separation of Logic:
1. Advanced Data Validation (Pydantic)
Input data is strictly validated using Pydantic schemas to ensure the API only processes valid data types:
A. Field Validators: Custom logic handles categorical features such as city and occupation.
B. Schema Enforcement: Centralized models in the schema/ directory prevent data inconsistency.

2. Modular ML Pipeline
The prediction logic is decoupled from API routes to allow for easier model maintenance:
A. predict.py: Manages model loading and feature transformation.
B. Health Monitoring: A dedicated /health route tracks system status, versioning, and model_loaded state.

3. Production Reliability
A. Error Handling: Global try-catch blocks capture input validation errors and model inference edge cases.
B. Transparency: The API provides not just a prediction, but also confidence scores and class_probabilities.

Usage Example
Sample Request
The API accepts demographic and health-related features via a POST request to /predict:
{
  "age": 65,
  "weight": 79,
  "height": 1.72,
  "income_lpa": 10,
  "smoker": true,
  "city": "Gurgaon",
  "occupation": "business_owner"
}

Sample Response
The model returns a categorical risk assessment with detailed probabilities:
{
  "predicted_category": {
    "predicted_category": "High",
    "confidence": 0.68,
    "class_probabilities": {
      "High": 0.68,
      "Low": 0.08,
      "Medium": 0.24
    }
  }
}

Skills Demonstrated:
1. Backend Engineering: Scalable API design using FastAPI and modular logic.
2. Data Integrity: Robust input/output validation with Pydantic.
3. DevOps: Optimized Docker workflow for ML services.
4. MLOps: Implementing confidence-aware predictions and system health checks.


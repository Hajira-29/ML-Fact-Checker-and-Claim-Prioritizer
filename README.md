# ML Fact Checker and Claim Prioritizer

## Group Project (Team of 4)

An AI-powered claim analysis platform that evaluates public perception, predicts claim credibility, and prioritizes disputed claims using Machine Learning and statistical feature engineering.

---

## Project Overview

Information shared on digital platforms is often influenced by public perception and misinformation. Traditional fact-checking systems focus only on determining whether a claim is true or false, but they fail to analyze how people perceive those claims.

This project introduces a perception-aware claim analysis framework that combines:

- Claim Verification
- Perception Bias Analysis
- Disputability Measurement
- Machine Learning-based Classification

The system helps identify claims that are:

- Factually Incorrect
- Commonly Misunderstood
- Highly Controversial

---

## Key Features

### O1 - False Claims Detection
Identifies claims predicted as false by the trained machine learning model.

### O2 - Most Misperceived Claims
Detects claims where public perception significantly differs from the predicted truth.

### O3 - Most Disputed Claims
Ranks claims based on disagreement among users using a disputability score.

### Statistical Feature Engineering

Extracts the following statistical features from perception data:

- Mean
- Median
- Variance
- Skewness

### Perception Bias Analysis

Calculates Total Perception Bias (TPB) to measure deviation between perceived truth and predicted truth.

### Interactive Dashboard

Provides a user-friendly interface for uploading datasets and visualizing results.

---

## System Architecture

Frontend (React.js)

↓

FastAPI Backend

↓

Data Preprocessing

↓

Feature Extraction

- Mean
- Median
- Variance
- Skewness

↓

Feature Scaling (StandardScaler)

↓

Random Forest Classification

↓

TPB Calculation

↓

Disputability Score Calculation

↓

Output Categorization (O1 / O2 / O3)

↓

Frontend Dashboard

---

## Technology Stack

### Frontend
- React.js
- Vite
- Axios
- Tailwind CSS

### Backend
- FastAPI
- Python

### Machine Learning
- Scikit-learn
- Random Forest Classifier
- StandardScaler

### Data Processing
- Pandas
- NumPy

---

## Dataset Format

### Claims Dataset

```csv
claim_id,claim
1,The Earth has a flat shape
2,Climate change is not real
```

### Perceptions Dataset

```csv
claim_id,perception
1,False
1,Mostly False
1,False
2,True
2,Mostly True
```

---

## Perception Mapping

| Perception | Value |
|------------|--------|
| True | 1 |
| Mostly True | 0.5 |
| Mixture | 0 |
| Mostly False | -0.5 |
| False | -1 |

---

## Feature Extraction

For every claim, the system computes:

### Mean
Average perception score.

### Median
Middle perception value.

### Variance
Measures spread of opinions.

### Skewness
Measures asymmetry of user perceptions.

These features are used as inputs to the Random Forest model.

---

## Feature Scaling

The extracted features are normalized using StandardScaler before prediction.

Benefits:

- Brings all features to the same scale
- Improves model performance
- Prevents dominance of larger-valued features

---

## Machine Learning Model

### Random Forest Classifier

The project uses a Random Forest classifier trained on statistical perception features.

The model predicts:

- Claim Truth (True / False)
- Total Perception Bias Level

### Why Random Forest?

- High accuracy
- Robust to noise
- Handles non-linear relationships
- Reduces overfitting

---

## Total Perception Bias (TPB)

TPB measures the difference between actual truth and perceived truth.

**Formula:**

```text
TPB = | Ground Truth Level - Perceived Truth Level |
```

Higher TPB indicates stronger public misperception.

---

## Disputability Score

Measures disagreement among users.

**Formula:**

```text
D(Ci) = |Pi - Ni| / (Pi + Ni)
```

Where:

- Pi = Number of Positive Perceptions
- Ni = Number of Negative Perceptions

Claims with higher disputability are considered more controversial.

---

## Output Categories

### O1 - False Claims
Claims predicted as False.

### O2 - Most Misperceived Claims
Claims having high TPB.

### O3 - Most Disputed Claims
Claims ranked according to disputability score.

---

## API Endpoint

### Analyze Dataset

```http
POST /analyze_dataset
```

Uploads:

- claims_file.csv
- perceptions_file.csv

Returns:

```json
{
  "false_claims": [],
  "most_misperceived_claims": [],
  "most_disputed_claims": []
}
```

---

## Installation

### Backend Setup

```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload
```

Backend runs at:

```text
http://127.0.0.1:8000
```

Swagger Documentation:

```text
http://127.0.0.1:8000/docs
```

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Frontend runs at:

```text
http://localhost:5173
```

---

## Project Workflow

1. Upload Claims CSV
2. Upload Perceptions CSV
3. Convert textual perceptions into numerical values
4. Extract statistical features
5. Scale features using StandardScaler
6. Predict claim truth using Random Forest
7. Calculate Total Perception Bias (TPB)
8. Calculate Disputability Score
9. Categorize claims into O1, O2, and O3
10. Display results on the dashboard

---

## Future Enhancements

- Real-time social media claim analysis
- NLP-based claim understanding
- Explainable AI for prediction reasoning
- Sentiment analysis integration
- Advanced visualization dashboards

---

## My Contributions

- Contributed to backend development and feature implementation in collaboration with team members
- Assisted in FastAPI backend integration and API testing
- Frontend development, UI enhancements, and React.js modifications
- Merge conflict resolution and code integration
- Testing, debugging, and validation of project outputs
- Dataset preparation and perception data validation
- Supported end-to-end integration between frontend, backend, and machine learning components

---

## Project Team

This project was developed as a team of four members as part of a Machine Learning Mini Project.

My primary contributions included:
- Backend development support
- Frontend development and UI enhancements
- Integration and testing
- Debugging and validation

---

## Acknowledgement

This repository is maintained as part of my personal portfolio and showcases my contributions to a collaborative Machine Learning project focused on claim verification, perception analysis, and claim prioritization.
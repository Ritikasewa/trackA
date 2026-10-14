# Track A : Explainable AI for Cardiovascular Risk Assessment

An ML-powered web application that estimates the probability of coronary artery disease and provides interpretable predictions through feature explanations and interactive visualization.

## Live Demo

**Try the application:** https://track-a-frontend-phi.vercel.app/ [WAIT FOR 30-60 SEC AFTER RUNNING ASSESS FOR FIRST TIME AS FREE RENDER DEPLOYMENT TAKES SOME TIME TO WAKE UP]

**Technical Documentation:** [View Project Documentation](https://drive.google.com/file/d/1ToG8NTINcEmNpkT52QhsVUTK9tyRiVi1/view?usp=drivesdk)

## About the Project

Cardiovascular diseases are a major health concern, and machine learning can help explore patterns in clinical data. However, predictions are more useful when users can understand how a model arrives at its estimates.

Cardiobuddy is a web application designed to estimate coronary artery disease (CAD) risk using patient clinical parameters. It also estimates the likelihood of disease involving three major coronary arteries: the left anterior descending artery (LAD), left circumflex artery (LCX), and right coronary artery (RCA).

The project combines machine learning, explainable AI, and interactive visualization to make predictions easier to explore and understand.

## Features

- **Four prediction models:** Separate models for CAD, LAD, LCX, and RCA.
- **Interactive assessment:** Enter patient clinical parameters through a web interface.
- **Explainable predictions:** Explore feature contributions that influence model outputs.
- **3D heart visualization:** View anatomical context for the coronary arteries.
- **Model evaluation:** Evaluate predictive performance using cross-validation, ROC-AUC, and Brier scores.
- **Responsible AI:** Communicate model limitations and the importance of professional medical assessment.

## Dataset

The project uses the **UCI Z-Alizadeh Sani dataset**, containing 303 patient records and 59 features.

The dataset includes demographic information, symptoms, clinical measurements, and other patient characteristics relevant to coronary artery disease.

Due to the small dataset size and differences in outcome distributions, the models' results must be interpreted cautiously.

## Machine Learning Approach

We developed separate models for CAD, LAD, LCX, and RCA rather than assuming a single model would perform equally well for every outcome.

The models were evaluated using repeated 5-fold cross-validation, with hyperparameter tuning performed within the training folds.

We used ROC-AUC to assess the models' ability to distinguish between outcome classes and Brier scores to evaluate predicted probability quality.

### Validation Results

| Prediction task | ROC-AUC |
|---|---:|
| CAD | 0.925 |
| LAD | 0.830 |
| LCX | 0.734 |
| RCA | 0.712 |

Performance varies across the four prediction tasks. These results represent cross-validation performance and do not establish clinical validity.

## Technology Stack

| Component | Technologies |
|---|---|
| Frontend | React, Vite, TypeScript |
| Backend | Python, FastAPI |
| Machine Learning | Scikit-learn, XGBoost |
| Explainability | SHAP and model-specific feature contributions |
| Visualization | Interactive 3D heart visualization |
| Frontend Deployment | Vercel |

## System Architecture

The application uses a frontend-backend architecture:

1. The user enters clinical parameters through the frontend.
2. The frontend sends the assessment request to the backend API.
3. The backend processes the inputs and runs the corresponding trained model.
4. The API returns model-estimated probabilities.
5. The frontend presents the results alongside available explanations and visualizations.

## Repository Structure

The repository contains the frontend and backend code in separate directories.

```text
TrackA/
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── ...
├── backend/
│   ├── app/
│   ├── artifacts/
│   ├── tests/
│   ├── requirements.txt
│   └── ...
├── docs/
│   └── technical_documentation.pdf
├── README.md
```

*The structure above illustrates the intended organization. Actual filenames and directories may vary.*

## Running Locally

The frontend and backend must be configured and started separately.

### Backend Setup

1. Navigate to the backend directory.
2. Create and activate a Python virtual environment.
3. Install dependencies from the backend's requirements file or project configuration.
4. Configure the required environment variables and model artifact paths.
5. Start the FastAPI server using the backend's documented command.

### Frontend Setup

1. Navigate to the frontend directory.
2. Install dependencies using the project's package manager.
3. Configure the backend API URL.
4. Start the Vite development server.

Refer to the configuration files and project documentation for the exact commands and environment variables.

## Limitations

- The dataset contains only 303 patient records and may not represent broader populations.
- Model performance varies across prediction tasks.
- External validation on larger, independent datasets is needed.
- Feature contributions explain model behavior but do not establish causation.
- Model-estimated probabilities should not be interpreted as confirmed individual disease probabilities.

## Future Improvements

- Validate the models on larger and more diverse datasets.
- Further evaluate calibration and subgroup performance.
- Improve feature explanations and visualization.
- Conduct usability testing and strengthen safety messaging.

## Disclaimer

This project is intended for educational and research purposes only. It is not a medical diagnostic tool and must not replace professional medical advice, clinical testing, or evaluation by a qualified healthcare professional. Do not use its predictions to make medical decisions or delay seeking care.

## Acknowledgements

We acknowledge the creators of the UCI Z-Alizadeh Sani dataset and the open-source technologies used to develop this project.

# Agentic Data Science Copilot

This project is a friendly, practical example of how AI agents can support a real data science workflow.

Instead of using one notebook cell after another manually, this project uses a small CrewAI agent team to help plan the analysis, prepare the data, train a machine learning model, evaluate the result, and explain the most important features behind the prediction.

The project uses a supplement sales dataset and trains a Random Forest regression model to predict `Units Sold`.

---

## Business Statement

Businesses often collect useful sales data, but turning that data into a working machine learning model can take time. A data scientist usually needs to inspect the dataset, clean the data, choose the target column, prepare features, split the data, train a model, evaluate the results, and explain what the model learned.

This project shows how an AI agent workflow can help automate those steps.

The goal is to make the data science process faster, more repeatable, and easier to follow while still keeping the user in control of the final interpretation.

---

## What This Project Does

The Agentic Data Science Copilot:

- Loads supplement sales data from a CSV file.
- Uses CrewAI agents to plan the machine learning workflow.
- Inspects and preprocesses the dataset.
- Creates training and testing data.
- Trains a `RandomForestRegressor` model.
- Evaluates the model using regression metrics.
- Shows the most important features used by the model.
- Uses a custom notebook execution tool so agents can generate and run Python code inside the notebook.

---

## Model Insight

The workflow trains one model: a Random Forest regression model.

In the notebook run, the model produced:

- R-squared of about `0.7810`
- MAE of about `160.05`
- RMSE of about `286.86`

This means the model explains a meaningful amount of the variation in `Units Sold`, although there is still room to improve the predictions.

The feature importance results show that `Price` is the strongest predictor of `Units Sold`, followed by `Discount`. This suggests that pricing and discount strategy have a strong relationship with sales volume in this dataset.

---

## Project Workflow

### 1. Environment Setup

The notebook loads environment variables from a local `.env` file.

Required variable:

```text
OPENAI_API_KEY=
```

### 2. Data Loading

The project loads the included CSV file:

```text
Supplement_Sales_Weekly.csv
```

The data is stored in a shared pandas dataframe called `shared_df`, which the agents can use during the workflow.

### 3. Custom Notebook Executor Tool

The project includes a helper file:

```text
notebookExecutor.py
```

This file defines a custom CrewAI tool that allows agents to execute Python code inside the notebook environment.

This is important because the agents do not only describe what should happen. They can generate code, run it, and use variables already created in the notebook, such as `shared_df`, `X_train`, and `y_train`.

### 4. Multi-Agent Workflow

The notebook uses CrewAI to define a small data science team.

Agents include:

- Planner Agent: Creates the machine learning plan.
- Data Analysis and Preprocessing Agent: Inspects the dataset, cleans it, encodes features, and creates train/test variables.
- Modeling and Evaluation Agent: Trains the Random Forest model, evaluates performance, and reports feature importance.

### 5. Model Training and Evaluation

The modeling agent trains a `RandomForestRegressor` using the prepared training data.

The model is evaluated with:

- MAE
- MSE
- RMSE
- R-squared

The workflow also prints the top feature importances so the result is easier to interpret.

---

## Practice Purpose

This notebook is designed as a learning and portfolio project.

To understand it well, you should have some basic to intermediate experience building a machine learning model from scratch. Helpful background knowledge includes:

- Loading data with pandas
- Choosing a target column
- Preparing features
- Splitting data into train and test sets
- Training a model
- Evaluating regression metrics
- Interpreting feature importance

---

## Current Limitation

This project is currently tailored to the supplement sales dataset.

It expects columns such as:

- `Units Sold`
- `Date`
- `Product Name`
- `Platform`

The workflow could be made more reusable by allowing the user to provide:

- Dataset path
- Target column
- Problem type
- Date column
- Columns to drop
- Preferred models to compare

With those changes, the same agent workflow could work across many different datasets.

---

## Technologies Used

- CrewAI
- OpenAI models
- Python
- Pandas
- NumPy
- scikit-learn
- Pydantic
- python-dotenv
- Jupyter Notebook

---

## Requirements

Install dependencies with:

```bash
pip install -r requirements.txt
```

Main dependencies:

- `crewai`
- `pandas`
- `numpy`
- `scikit-learn`
- `python-dotenv`
- `pydantic`
- `jupyter`
- `ipython`

---


## Author

Patrick Edosoma

LinkedIn: [https://www.linkedin.com/in/patrickedosoma/](https://www.linkedin.com/in/patrickedosoma/)

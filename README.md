# Swish-Analytics-Soccer-Challenge

# Soccer Analytics Challenge: Foul-Winning Probability Model

## Project Overview

This project builds a machine learning model to estimate the probability that a soccer player wins a foul after a `Ball Receipt` or `Ball Recovery` event.

The goal was to create a full data science workflow using soccer event data, from target creation and feature engineering to exploratory analysis, model training, evaluation, and interpretation.

This was completed as part of the Swish Analytics Soccer Challenge.

## Objective

The main objective of this project was to predict whether a player would win a foul after receiving or recovering the ball during a possession.

Because foul-winning events are rare, the project focuses on probability-based and ranking-based evaluation metrics rather than accuracy.

## Dataset

The project uses EPL event data and match-level information.

Main data sources used in the notebook:

- `epl_event_data_15.csv`
- `epl_matches_15.csv`

The event data includes information such as event type, player, team, position, location, pressure, possession, and play pattern.

## Methodology

The project follows these main steps:

1. Load and inspect the event and match datasets.
2. Create a custom target variable, `foul_won`.
3. Identify `Ball Receipt` and `Ball Recovery` events as starting actions.
4. Link future `Foul Won` events back to the previous relevant action by the same player within the same possession.
5. Engineer features such as:
   - Pitch location
   - Pitch zones
   - Match time
   - Pressure indicator
   - Event type
   - Player position
   - Team
   - Referee
   - Play pattern
6. Perform exploratory data analysis.
7. Train and compare machine learning models.
8. Evaluate models using metrics appropriate for rare events.
9. Interpret model results using feature importance.

## Models Used

The project compares three models:

- Logistic Regression
- Random Forest
- XGBoost

Logistic Regression was used as a baseline model, while Random Forest and XGBoost were used to capture more complex patterns in the data.

## Evaluation Metrics

Since the target event is rare, accuracy was not the main evaluation metric.

The models were evaluated using:

- ROC AUC
- Average Precision
- Log Loss
- Brier Score

These metrics better capture ranking quality and probability quality for an imbalanced classification problem.

## Key Findings

The exploratory analysis and model results showed that foul-winning probability depends strongly on game context.

Some of the most important factors were:

- Whether the player was under pressure
- Whether the event was a `Ball Recovery` or `Ball Receipt`
- Pitch location
- Player position
- Play pattern, especially counterattacks

The XGBoost model performed slightly better than the Random Forest model across the main evaluation metrics.

Feature importance showed that `under_pressure_clean` was the most important feature by a large margin, followed by counterattacks, event type, pitch area, and position-related features.

## Main Takeaways

This project demonstrates how soccer domain knowledge can be combined with data science techniques to build a predictive model.

The model does not prove causation, but it helps identify which event-context features are most useful when estimating foul-winning probability.

Overall, the project shows that pressure, transition situations, player role, and pitch context are important signals for predicting whether a player wins a foul.

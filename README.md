# Power System Load Type Prediction

## Objective
The primary goal of this project is to develop a machine learning pipeline capable of predicting the "Load_Type" of a power system based on historical energy consumption data. The target variable is categorized into three classes: `Light_Load`, `Medium_Load`, and `Maximum_Load`.

## Dataset Features
The dataset contains continuous-time data recorded on the first of the month, including:
* **Usage_kWh:** Industry Energy Consumption (Continuous kWh)
* **Lagging Current:** Reactive power (Continuous kVarh)
* **Leading Current:** Reactive power (Continuous kVarh)
* **CO2:** Carbon dioxide emissions (Continuous ppm)
* **NSM:** Number of Seconds from Midnight (Continuous S)
* **Load Type (Target):** Categorical (Light Load, Medium Load, Maximum Load)

## Methodology
The project workflow follows a complete data science pipeline:
1. **Data Preprocessing & EDA:** Handled missing values via median imputation, formatted datetime features, and encoded the categorical target variable. Explored feature distributions and class imbalances.
2. **Feature Scaling:** Applied `StandardScaler` to continuous features (fitted strictly on the training set to prevent data leakage).
3. **Model Selection:** Implemented a **Random Forest Classifier** to capture complex, non-linear relationships between power metrics and load types.

## Validation Strategy
To accurately assess the model's ability to generalize to recent, unseen data, a **chronological time-based split** was implemented. Rather than a random split, the very last month of recorded data (December 2018) was isolated exclusively as the test set, while all preceding months were used for training.

## Evaluation & Results
The model's performance was evaluated using classification-specific metrics:
* **Overall Accuracy:** ~72.5%
* **Detailed Metrics Evaluated:** Precision, Recall, and F1-score for each specific load class.
* **Feature Importance:** Time of day (`NSM`) and Energy Consumption (`Usage_kWh`) were identified as the strongest predictors of load type.

## Tools & Libraries Used
* Python 3
* Pandas & NumPy (Data manipulation)
* Scikit-Learn (Modeling, Scaling, Evaluation)
* Matplotlib & Seaborn (Data Visualization)

## How to Run
1. Clone the repository.
2. Ensure the dataset `load_data.csv` is located in the `data/` directory.
3. Open `load_type_prediction.ipynb` in Jupyter Notebook or VS Code.
4. Run all cells sequentially to reproduce the preprocessing, model training, and evaluation reports.

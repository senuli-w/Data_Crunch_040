# Data_Crunch_040
Predicting Nature's Shifts - Data Crunch by CodeJam, CSE UOM

## Technical Guide for Running the Data Analysis Jupyter Notebook on Your Laptop

### Prerequisites
Before running the notebook, ensure that you have the following installed:

#### 1. Install Python
- Download and install Python (preferably version 3.8 or later) from [python.org](https://www.python.org/downloads/).
- Verify installation by running:
  ```sh
  python --version
  ```

#### 2. Install Jupyter Notebook
- Install Jupyter Notebook using:
  ```sh
  pip install notebook
  ```
- Verify the installation by running:
  ```sh
  jupyter notebook --version
  ```

#### 3. Install Required Python Packages
- Ensure all necessary Python libraries are installed:
  ```sh
  pip install pandas numpy matplotlib seaborn scipy scikit-learn xgboost
  ```

#### 4. Download the Notebook File
- Save the provided notebook file (`v1.ipynb`) to a directory where you want to work.

### Running the Notebook
Follow these steps to execute the notebook:

1. **Open a Terminal or Command Prompt**
   - On Windows: Press `Win + R`, type `cmd`, and press `Enter`.
   - On macOS/Linux: Open the Terminal from the applications menu.

2. **Navigate to the Notebook Directory**
   - Use `cd` to change to the directory where `v1.ipynb` is saved:
     ```sh
     cd /path/to/your/notebook/
     ```

3. **Launch Jupyter Notebook**
   - Start Jupyter Notebook by running:
     ```sh
     jupyter notebook
     ```
   - This will open Jupyter Notebook in your default web browser.

4. **Open the Notebook**
   - Locate `v1.ipynb` in the Jupyter Notebook interface and click on it to open.

5. **Run the Notebook Cells**
   - Click `Kernel > Restart & Run All` to execute all cells.
   - Alternatively, run each cell one by one using `Shift + Enter`.

### Understanding the Notebook Components

#### Data Loading and Validation
- The notebook loads two CSV files (`train.csv` and `test.csv`) using `pandas.read_csv()`.
- It verifies the data structure using `.info()` and checks for missing values with `.isnull().sum()`.
- It ensures consistency in the `kingdom` field and checks if all have equal record counts.
- The date fields (`Year`, `Month`, `Day`) are formatted correctly and converted into a proper datetime format.
- The script detects missing dates within the dataset and reports any anomalies.

#### Data Visualization
- The notebook generates time-series plots using `seaborn.lineplot()` for various features like:
  - Avg_Temperature
  - Rain_Amount
  - Wind_Speed
- It provides detailed insights into seasonal trends and possible data inconsistencies.
- A helper function `plot_all_kingdoms(feature)` is defined to visualize features across all kingdoms.

#### Identifying Data Issues
- The notebook detects potential inconsistencies in temperature units (Celsius vs. Kelvin) and provides a conversion formula:
  ```sh
  Celsius = Kelvin - 273.15
  ```

#### XGBoost Model and Grid Search
- The notebook uses the `XGBoost Regressor` (`xgb.XGBRegressor`) for predictive modeling.
- A grid search was conducted to tune hyperparameters, but the model yielded low predictive accuracy.
- Due to the poor performance, the XGBoost model was ignored in further analysis.
- Future work could explore feature engineering or alternative models to improve accuracy.

### Troubleshooting Common Issues

#### 1. ModuleNotFoundError
**Error:** `ModuleNotFoundError: No module named 'pandas'`
**Solution:** Install the missing package using:
```sh
pip install pandas
```

#### 2. FileNotFoundError
**Error:** `FileNotFoundError: [Errno 2] No such file or directory: 'train.csv'`
**Solution:** Ensure `train.csv` is in the correct directory.

#### 3. Date Conversion Issues
**Error:** Some dates may be invalid and converted to `NaT` (Not a Time).
**Solution:** Check the `invalid_dates` output for incorrect `Year`, `Month`, or `Day` values.


By following this guide, you should be able to successfully run the Jupyter Notebook, analyze weather data, and troubleshoot common issues.


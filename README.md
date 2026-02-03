# Mobile Price Prediction - Multiple Linear Regression Analysis

## Project Overview

This project demonstrates **multiple linear regression** using Python to predict cellphone prices based on their technical specifications. The analysis explores correlations between various hardware features and pricing patterns in the mobile phone market.

## Dataset

**File:** `Cellphone.csv`

The dataset contains information about 163 mobile phones with 14 features:

| Column | Description | Unit |
|--------|-------------|------|
| Product_id | Unique phone identifier | - |
| **Price** | Phone price (target variable) | Currency units |
| Sale | Number of units sold | Units |
| Weight | Phone weight | Grams |
| Resolution | Screen resolution | Inches |
| PPI | Pixels Per Inch (screen density) | PPI |
| CPU Core | Number of processor cores | Count |
| CPU Freq | CPU frequency | GHz |
| Internal Mem | Internal storage capacity | GB |
| RAM | Random Access Memory | GB |
| RearCam | Rear camera quality | Megapixels |
| Front_Cam | Front camera quality | Megapixels |
| Battery | Battery capacity | mAh |
| Thickness | Phone thickness | mm |

## Project Structure

```
analysis_with_celphone/
├── README.md                 # Project documentation
├── Cellphone.csv            # Dataset
├── celphone.ipynb           # Jupyter notebook with analysis
└── .venv/                   # Python virtual environment
```

## Analysis Workflow

### 1. **Data Loading & Exploration**
   - Load data using pandas
   - Check dataset shape, data types, and missing values
   - Display basic statistics with `df.describe()`

### 2. **Exploratory Data Analysis (EDA)**
   - **Correlation Analysis:** Compute correlation matrix for all numerical features
   - **Correlation Heatmap:** Visualize feature relationships using a coolwarm color map
   - **Scatter Plots:** Examine individual feature-price relationships for:
     - PPI vs Price
     - CPU Frequency vs Price
     - CPU Cores vs Price
     - Thickness vs Price

### 3. **Data Splitting**
   - Split data into 80% training and 20% testing sets
   - Use random masking to ensure reproducibility

### 4. **Model Training**
   - Train a **LinearRegression** model using scikit-learn
   - Features used: `ppi`, `cpu freq`, `cpu core`, `ram`, `RearCam`, `Front_Cam`, `battery`
   - Extract model parameters:
     - Y-intercept
     - Coefficients for each feature

### 5. **Model Evaluation**
   - Generate predictions on test set
   - Calculate evaluation metrics (if applicable)

## Key Findings

### Strong Positive Correlations with Price:
- **RAM (0.90)**: More RAM → Higher price
- **Price & PPI (0.82)**: Better screen resolution → Higher price
- **Internal Memory (0.78)**: More storage → Higher price
- **CPU Frequency (0.73)**: Faster processor → Higher price
- **Cameras (0.68-0.74)**: Better cameras → Higher price

### Strong Negative Correlations:
- **Thickness & Price (-0.72)**: Thinner phones tend to be more expensive
- **Thickness & CPU Cores (-0.70)**: High-performance phones are thinner
- **Thickness & Other Specs**: Negative correlation across most performance features

### Weak Correlations:
- **Sales**: Weak correlation with all features, indicating sales are driven by factors beyond specs
- **Weight & Resolution (0.89)**: Larger screens may require heavier bodies

## Dependencies

Install required packages using:

```bash
pip install pandas seaborn matplotlib scikit-learn numpy
```

Or use the notebook cells to install:
```python
pip install pandas
pip install seaborn
pip install matplotlib
pip install scikit-learn
```

## Running the Analysis

1. **Open the Jupyter Notebook:**
   ```bash
   jupyter notebook celphone.ipynb
   ```

2. **Execute cells sequentially** from top to bottom to:
   - Load and explore data
   - Generate visualizations
   - Train the regression model
   - Display results

## Model Formula

The fitted linear regression model takes the form:

```
Price = intercept + (coef_1 × ppi) + (coef_2 × cpu_freq) + ... + (coef_7 × battery)
```

The specific coefficients are displayed in the notebook output.

## Insights & Interpretation

1. **Performance Metrics Matter:** RAM, CPU frequency, and PPI are the strongest price predictors
2. **Design Tradeoff:** Thinner phones correlate with better specs and higher prices
3. **Sales Independence:** Product specifications don't directly determine sales volume
4. **Linear Relationships:** Correlation doesn't imply causation; many factors influence pricing

## Correlation Matrix Interpretation

- **Red (Dark):** Strong positive correlation (close to 1)
- **Blue (Dark):** Strong negative correlation (close to -1)
- **White/Light:** Weak correlation (close to 0)

## Future Enhancements

- Model evaluation metrics (R², MSE, RMSE)
- Feature scaling and normalization
- Polynomial regression for non-linear relationships
- Cross-validation for robust model assessment
- Residual analysis and diagnostic plots
- Feature importance ranking

## Notes

- The analysis uses a simple linear regression model; polynomial or ensemble methods might improve predictions
- Thickness shows interesting inverse relationship with price, suggesting premium phones prioritize thinness
- The dataset is relatively small (163 samples); consider collecting more data for production models

## Author

Data Science Project - Multiple Linear Regression Analysis

## License

Educational use only
# cellphone-price-prediction

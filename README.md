# Carbon_Emission_Prediction
This project aims to **analyze country-level data** and build a predictive model to estimate **CO₂ emissions per capita** using socio-economic, environmental, and energy-based indicators. The dataset spans from **1990 to 2011**, covering global countries and diverse development metrics.


##  Dataset Overview

* **Years Covered**: 1990–2011

* **Geographic Scope**: Worldwide
  
* **Total Rows**: \~1700
  
* **Features Include**:

  * Greenhouse gas emissions (CO₂, CH₄, N₂O)
    
  * Population statistics (urban, total, growth rates)
    
  * Economic indicators (GDP, GNI, FDI)
    
  * Energy usage
    
  * Land & agriculture metrics
    
  * Climate statistics
    
  * Health indicators


## Project Workflow

### Stage 1: Data Cleaning and Preparation

* Imported and reviewed raw datasets
  
* Handled missing values and inconsistent formats
  
* Renamed and formatted columns
  
* Converted categorical/numeric types properly
  
* Transformed datasets using melting and reshaping
  
* Final clean file exported as `data_cleaned.csv`


### 📊 Stage 2: Data Exploration & Visualization

* Analyzed global patterns in CO₂ emissions

* Conducted correlation and multicollinearity analysis (VIF)
  
* Visualizations:

  * Line plot (Global CO₂ per capita trend)
  * Scatter plots (e.g., emissions vs population)
  * Pair plots and 4D visualizations
* Outlier detection and removal (e.g., UAE)
* Key insights:

  * Strong correlation: `energy_use_per_cap` ↔ `co2_per_cap`
  * GNI and urban population growth show nonlinear effects
  * Population count was low-relevance and excluded


### Stage 3: Model Building (Random Forest)

#### Objective:

Predict **CO₂ emissions per capita** using country-specific development indicators.

#### Hypothesis:

CO₂ emissions can be effectively predicted based on features like **energy use, GNI, urbanization**, and **land protection**.

#### Selected Features:

* **Dependent Variable**:

  * `co2_per_cap`: CO₂ emissions per capita (metric tons)

* **Independent Variables**:

  * `cereal_yield`
  * `fdi_perc_gdp`
  * `gni_per_cap`
  * `en_per_cap`
  * `pop_urb_aggl_perc`
  * `prot_area_perc`
  * `gdp`
  * `pop_growth_perc`
  * `urb_pop_growth_perc`

#### Train-Test Split:

* 80% Training / 20% Testing
* Set `random_state` for reproducibility

####  Feature Selection:

* Used **RFECV (Recursive Feature Elimination with Cross-Validation)** based on R² score
* Reduced multicollinearity and improved generalization

#### Hyperparameter Tuning:

Used **RandomizedSearchCV** to tune:

* `n_estimators`
* `max_features`
* `max_depth`
* `min_samples_split`
* `min_samples_leaf`


## Model Evaluation

### Training (10-Fold Cross-Validation):

* **R² Score**: 0.986
* **Std Dev**: 0.004 → High consistency and low variance.
* The narrow R² range and very low standard deviation (0.004) indicate the model performs consistently and generalizes well across different data splits.

### Testing (Unseen Data):

* **R² Score**: 0.982
* **Mean Squared Error** and **RMSE** confirmed excellent prediction alignment
* No major outliers or overfitting observed


## Long-Term Trend Analysis — CAGR

### Purpose:

To assess **growth trends** of core development indicators from 1991–2008.

### CAGR Calculated For:

* `cereal_yield`
* `gni_per_cap`
* `en_per_cap`
* `pop_urb_aggl_perc`
* `prot_area_perc`
* `pop_growth_perc`
* `urb_pop_growth_perc`

### Sample Country Insights:

**India (IND)**
• GNI: +6.85% | Energy Use: +2.12% | Urban Agglomeration: +1.26%

**USA**
• GNI: +4.26% | Energy Use: -0.12% | Urban Growth: -2.15%

**Russia (RUS)**
• GNI: +7.41% | Energy Use: -0.61% | Protected Area: +0.46%

## Emission Forecast Visualization

Projected 20-year trends for:

* 🇺🇸 USA: Declining emissions from \~17 t/cap
* 🇷🇺 Russia: Slight downward trend
* 🇳🇿 NZL: Gradual increase
* 🇮🇳 India & 🇵🇰 Pakistan: Rising trends from \~1.5–2 t/cap

## Conclusion

*USA:Starts with the highest CO₂ emissions per capita (~17 metric tons) but shows a steady decline over time. Despite the drop, it remains the highest emitter per person.

*RUS:Has relatively stable emissions with a slight downward trend, indicating moderate policy or behavioral changes. 

*NZL:Shows gradual growth in emissions per capita, which may suggest increased industrial or transport-related emissions.

*IND & PAK:Begin with very low per capita emissions (~1.5–2 metric tons) but display a gradual upward trend.This suggests economic growth and development, which often correlate with increased energy use.

Developed nations (like the USA and Russia) are reducing their per capita emissions, likely due to energy transition policies and technology upgrades.

Developing countries (like India and Pakistan) are on an upward trajectory, likely due to industrialization and increased energy demand.

This indicates a global convergence of emissions, but with differing starting points and growth rates.


##  Tech Stack

* **Languages**: Python
* **Libraries**: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `statsmodels`
* **Model**: Random Forest Regressor




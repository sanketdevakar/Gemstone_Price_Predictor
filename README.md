# Gemstone Price Prediction

### Introduction About the Data :

**The dataset** The goal is to predict `price` of given diamond (Regression Analysis).

There are 10 independent variables (including `id`):

* `id` : unique identifier of each diamond
* `carat` : Carat (ct.) refers to the unique unit of weight measurement used exclusively to weigh gemstones and diamonds.
* `cut` : Quality of Diamond Cut
* `color` : Color of Diamond
* `clarity` : Diamond clarity is a measure of the purity and rarity of the stone, graded by the visibility of these characteristics under 10-power magnification.
* `depth` : The depth of diamond is its height (in millimeters) measured from the culet (bottom tip) to the table (flat, top surface)
* `table` : A diamond's table is the facet which can be seen when the stone is viewed face up.
* `x` : Diamond X dimension
* `y` : Diamond Y dimension
* `x` : Diamond Z dimension

Target variable:
* `price`: Price of the given Diamond.

Dataset Source Link :
[https://www.kaggle.com/datasets/colearninglounge/gemstone-price-prediction?select=cubic_zirconia.csv](https://www.kaggle.com/datasets/colearninglounge/gemstone-price-prediction?select=cubic_zirconia.csv)

### It is observed that the categorical variables 'cut', 'color' and 'clarity' are ordinal in nature


# Approach for the project 

1. Data Ingestion : 
    * The raw data is read from a CSV file.
    * The dataset is then split into training and testing sets.
    * These sets are saved as separate CSV files for further processing. 

2. Data Transformation : 
    * A ColumnTransformer pipeline is created to preprocess the data.
    * For numeric features:
        - Missing values are imputed using SimpleImputer with the median strategy.
        - The features are scaled using StandardScaler.
    * For categorical features:
        - Missing values are imputed using SimpleImputer with the most frequent strategy.
        - Features are encoded using OrdinalEncoder.
    * Encoded values are also scaled with StandardScaler.
    * The complete preprocessor pipeline is saved as a pickle (.pkl) file for reuse.

3. Model Training :   
    * Initial testing is done with various base models, with CatBoost Regressor showing the best performance.
    * Hyperparameter tuning is performed on CatBoost and KNN models to optimize performance.
    * A final Voting Regressor is built by combining predictions from CatBoost, XGBoost, and KNN models.
    * This ensemble model is saved as a pickle file for deployment.

4. Prediction Pipeline : 
    * This pipeline converts given data into dataframe and has various functions to load pickle files and predict the final results in python.

5. Flask App creation : 
    * Flask app is created with User Interface to predict the gemstone prices inside a Web Application.

# Exploratory Data Analysis Notebook

Link : [EDA Notebook](notebook\1_EDA_Gemstone_price_Predictor.ipynb)

# Model Training Approach Notebook

Link : [Model Training Notebook](notebook\2_Model_Training_Gemstones.ipynb)


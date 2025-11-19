# Weather Data Analysis

## About
I analysed weather patterns using the “weather.csv” dataset which contained various meteorological measurements. The dataset required cleaning as it had missing values that needed to be addressed.  My goal was to predict daily mean temperatures, which ranged from -7.6°C to 29°C, using various weather-related features like pressure, precipitation, radiation, and seasonal indicators.

Dataset: 15,341 rows and 10 columns

Programming Language: Python

Python Libraries: Pandas, NumPy, Seaborn, Matplotlib, Scikit-learn

Other imports: train_test_split, LogisticRegression, metrics, accuracy_score, classification_report, confusion_matrix, precision_score, recall_score, and f1_score.

Machine Learning Model: Logistic Regression Multiclass Classification

## Data
| # | Variable | Description |
|---|----------|-------------|
| 1 | date | Month, day, and year of every weather observation |
| 2 | cloud_cover | The area covered by clouds in the sky  |
| 3 | sunshine | Duration of sunshine measured in hours |
| 4 | global_radiation | Amount of energy from the sun that reached the ground |
| 5 | max_temp | Maximum temperature of the day |
| 6 | mean_temp | Mean temperature of the day |
| 7 | min_temp | Minimum temperature of the day |
| 8 | precipitation | Amount of rainfall measured in millimeters |
| 9 | pressure | Atmospheric pressure |
| 10 | snow_depth | Depth of snow on the ground |

Initial dataset: 15,341 rows and 10 variables

Cleaned dataset: 13,843 rows x 10 variables
* Dropped rows with null values
* Added 12 columns: month_January, month_February, month_March, month_April, month_May, month_June, month_July, month_August, month_September, month_October, month_November, month_December
* Converted the data type of date from "integer" to "date"

## Key Features Created
| # | Variable | Description |
|---|----------|-------------|
| 1 | month_January | "1" means January, "0" means not January |
| 2 | month_February | "1" means February, "0" means not February |
| 3 | month_March | "1" means March, "0" means not March |
| 4 | month_April | "1" means April, "0" means not April |
| 5 | month_May | "1" means May, "0" means not May |
| 6 | month_June | "1" means June, "0" means not June | 
| 7 | month_July | "1" means July, "0" means not July |
| 8 | month_August | "1" means August, "0" means not August |
| 9 | month_September | "1" means September, "0" means not September |
| 10 | month_October | "1" means October, "0" means not October |
| 11 | month_November | "1" means November, "0" means not November |
| 12 | month_December | "1" means December, "0" means not December |

Final dataset with added key features: 13,843 rows with 22 columns

## Findings
To arrive at the end result, I performed the following steps:

The mean temperature is the target or y variable. The maximum temperature for the mean temperature is 29 and the minimum temperature is negative 7.6. From there, the mean temperature was divided into three parts and they are low, moderate, and high. 

The predictors or X variables used are cloud cover, sunshine, global radiation, snow depth, and all the months. Stepwise backward selection was used in choosing the best features to use that will improve the model accuracy. I started with all the features and removed one by one those features that were not useful or important. 80% of the data is used for training and 20 percent for testing the model. 

I used the lbfgs for the solver to get the local minimum and multinomial for the multiclass as there are three classes: low, moderate, and high. 

The confusion matrix shows that the model is doing good. The diagonal elements showing the values 352, 87, and 1708 mean that the model correctly labeled the predicted class. The off-diagonal elements display the wrong predictions that the model classified. In the first row, the model correctly classified 352 mean temperatures as high out of all the 503 high mean temperatures but misclassified 151 as moderate. In the second row, the model correctly classified 87 mean temperatures as low out of all the 369 low mean temperatures but labeled 282 as moderate. In the third row, the model correctly classified 1708 mean temperatures as moderate out of all the 1897 moderate mean temperatures but misclassified 143 as high and 46 as low. All in all, the total number of correct predictions is 2147 and the total number of incorrect predictions is 622. 

Result: 
* Overall Accuracy or Error Rate: 77.43% (Low, Moderate, High)
* Overall Precision: 71.74%
* Overall Recall: 61.10%
* Overall F1 Score: 63.15%
  
The model is 77.43% accurate in performing correct predictions across the entire dataset. The overall precision rate is 71.74%, overall recall rate is 61.10%, and overall F1 score is 63.15% which gives a lower value. It means that the model is performing well in predicting the mean temperatures of each day but may have issues in determining classes correctly.

## Code
See weather.ipynb for full analysis including data cleaning, feature engineering, visualisations, and modelling

## Practical Takeaways
* **Model performs moderately well with 77% accuracy** The logistic regression model correctly classifies temperature categories (Low, Moderate, High) about 3 out of 4 times, which is reasonable for weather prediction with basic meteorological features.
* **Better at determining patterns than catching all cases.** The model has higher precision (71.74%) than recall (61.10%), which means the model is more conservative and accurate when it does make predictions, but misses some temperature patterns.
* **Data quality is essential** Removing 1,498 rows with missing values (about 10% of data) was necessary to make sure that the predictions are reliable, which highlights the significance of complete weather records
* **Feature engineering adds value.** Breaking down the date into monthly categories helped the model capture seasonal temperature variations better than using raw dates.
* **There is room for improvement.** With an F1 score of 63.15%, there's potential to enhance predictions by exploring more advanced algorithms, adding more features, or refining the temperature categories.

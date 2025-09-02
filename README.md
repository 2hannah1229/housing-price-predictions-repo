# HPI predictor 
This project analyzes the FHFA House Price Index (FHFA HPI), which is a set of publicly available indexes tracking changes in single-family home values across the US. It represents the movement of single-family house prices, and it uses data from all 50 states and over 400 cities, dating back to the mid-1970s, and is based on millions of home sales and refinancings.

## Project Structure 

### Data Loading
I downloaded data from https://www.fhfa.gov/data/hpi/datasets?tab=annual-data. There are 2556 rows, each of the 50 states being represented. However, I selected 9 states (CA, TX, NY, FL, PA, IL, OH, GA, and NC) based on economic significance and population.


**Columns**
- State: Name of U.S. state (50)
- Abbreviation: Standard two-letter postal abbreviation. I used this column the most to refer to the states in my hpi predictor.
- FIPS: Federal Information Processing Standards code
- Year: Calendar year for the data entry
- Annual Change: The percentage change in the house price index compared to the previous year
- HPI: The raw house price index value for that state and year
- HPI with 1990 Base: The HPI value normalized to a base value of 100 in the year 1990, allowing for comparison across states and years.
- HPI with 2000 Base: The HPI value normalized to a base value of 100 in the year 2000, providing an alternative reference point for comparison.

I cleaned unused columns as necessary. 

## Visualization 
I plotted HPI trends for key states for both the 1990 base and 2000 base to compare house price movements over time. I observed that some states had lines that were more closely correlated than others, so I created a seaborn plot to visualize correlations between states to identify similar housing market dynamics for predictive analytics. I also made a bar chart to better visualize which states had the highest vs. lowest correlations based on the seaborn plot. 

## Modeling
I implemented different machine learning models (Linear Regression, Ridge Regression, Random Forest, Neural Network) to predict HPI values of another state based on a closely correlated state pair. For correlation metrics, I calculated the following values: 
- Mean Squared Error (MSE): measures the average squared difference between the actual and predicted HPI values, with a lower difference corresponding to more accurate prediction
- R^2 Score: variance explained by the model/total variance of the data, with a value closer to 1 corresponding to a more accurate prediction
- Accuracy: proportion of correct predictions (both increases and decreases).
- Precision: of all predicted increases, how many were actually increases?
- Recall: Of all actual increases, how many were correctly predicted?
- F1 Score: harmonic mean of precision and recall, balancing both metrics.
- Confusion Matrix:a  table showing counts of true positives, true negatives, false positives, and false negatives.
- Classification Report: detailed summary of precision, recall, F1 score, and support (number of samples) for each class



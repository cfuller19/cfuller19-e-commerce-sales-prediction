# E-Commerce Sales Prediction Using Random Forest Regression

<b>This is the code file of my capstone project for completing my graduate degree at Western Governors University. I was awarded the WGU Capstone Excellence Award for my work on this project.The executive summary for this project is given below.</b>

<b>Statement of the Problem</b><br>
	The United States pet industry is quickly growing, with sales projected to increase to $200 billion by 2030 (“Global Pet Industry”, 2023),  and with a large portion of those sales conducted online (Polyn, 2023). Understanding features of an e-commerce marketplace that factor into customer buying decisions can help retailers maximize online sales and remain competitive. Prior research has identified product star rating, the number of reviews, and price as important features that customers consider before purchasing (Sung et al., 2023). Using these features, this analysis aims to build a random forest regression (RFR) model that can predict pet product sales on an e-commerce platform with an accuracy of at least 70%.<br>
<b>Hypothesis</b><br>
	The null hypothesis for this analysis was that an RFR model with an accuracy of at least 70% cannot be constructed from the available data. The alternative hypothesis was that an RFR model with at least 70% accuracy can be constructed from the available data. If the alternative hypothesis is supported, sellers can use the results of this analysis to examine the impact of changing star rating, number of reviews, and price on the sales of a product.<br> 
<b>Summary of Data Analysis Process</b><br>
The dataset used in this analysis was downloaded from Kaggle.com (Asaniczka, 2023) and consisted of data obtained from a popular e-commerce platform. The data were filtered only to contain pet product observations of star rating, number of reviews, price, best-seller status, and the number of products bought in the last month. This provided 5,432 observations for the RFR model. The data were prepared for analysis as follows:<br>
- Data were cleaned to remove duplicate and null values.
- The categorical variable, “isBestSeller,” was encoded to 1/0 for best-seller/not best-seller status.
- Exploratory data analysis was conducted to identify important patterns and potential anomalies present in the data. This was done to confirm the choice of RFR for the predictive model.
- For the RFR model, the feature variables were defined as ‘stars,’ ‘reviews,’ ‘price,’ and ‘isBestSeller’. The target variable was defined as ‘boughtInLastMonth.’
- Data were split 75/25 into a training set for training the model and a testing set for validating the model on unseen data.
<br>
An initial RFR model was built using the default parameters in scikit-learn’s RandomForestRegressor. Then, hyperparameter tuning was conducted to improve model performance. Each model was evaluated based on mean absolute error (MAE) and R2 values for the training and testing sets. The final model was selected based on maximizing the R2 of testing data and having a low MAE while reducing the model's overfitting on the training data as much as possible.<br> 
<b>Summary of Analysis Results</b><br>
	The data used in this analysis had non-normal distributions with non-linear/weakly linear relationships. Outliers were present, causing the left-skew and right-skew distributions seen in the plots below. RFR is robust towards outliers (Sahota, 2022), so they were left in the data, as they appeared to be legitimate observations.<br>
<img width="467" alt="image" src="https://github.com/cfuller19/cfuller19-e-commerce-sales-prediction/assets/101231073/eb1efef8-2259-4796-b11e-1a1979e4c3be"><br>
The strongest linear relationship was between the number of reviews and bought in last month, with a correlation coefficient of 0.41 (p-value < 0.05).<br>
<img width="313" alt="image" src="https://github.com/cfuller19/cfuller19-e-commerce-sales-prediction/assets/101231073/5ccec158-fbbd-486f-98e5-734b716ccf47"><br>
Five RFR models using different parameters of n_estimators, max_depth, and max_features were fit on the training data and evaluated using the testing data. A summary of each model is given in the table below.<br>
<img width="576" alt="image" src="https://github.com/cfuller19/cfuller19-e-commerce-sales-prediction/assets/101231073/3bf09355-d2be-4d71-839e-ea85dca331ca"><br>
The tuned 3 model (highlighted yellow above) was selected as the final model for this analysis because it demonstrated the best overall performance when considering accuracy (R2 of the testing set), mean absolute error, and overfitting of the model on the training data (difference between R2 values for training and testing set). Based on this final model, an RFR model with an accuracy of 24.9% was constructed, so the null hypothesis for this analysis cannot be rejected.<br>
Feature importance in the RFR model was also examined. The number of reviews was most important in the model’s predictions, followed by price, best-seller status, and stars. This corresponds with the exploratory data analysis findings, in which the number of reviews had the strongest positive linear relationship with the number of products sold.<br>
<img width="396" alt="image" src="https://github.com/cfuller19/cfuller19-e-commerce-sales-prediction/assets/101231073/45c5dfa3-b7fc-4177-9b96-91489a392afe"><br>

<b>Sources Cited</b><br>
Asaniczka. (2023). USA Optimal Product Price Prediction Data set [Data set]. Kaggle. https://doi.org/10.34740/KAGGLE/DS/3893031 
(2023, March 24). Global Pet Industry To Grow To $500 Billion By 2030, Bloomberg Intelligence Report Finds. Bloomberg. Retrieved November 16, 2023, from https://www.bloomberg.com/company/press/global-pet-industry-to-grow-to-500-billion-by-2030-bloomberg-intelligence-finds/
Muller, A. C., & Guido, S. (2017). Introduction to Machine Learning with Python: A Guide for Data Scientists. O'Reilly.
Polyn, G. (2023, January 9). Packaged Facts: E-Commerce Pet Product Sales Surpassed $30B in 2022. Pet Age. Retrieved November 17, 2023, from https://www.petage.com/packaged-facts-e-commerce-pet-product-sales-surpassed-30b-in-2022/ 
Sahota, H. (2022, January 27). Can't Decide Between a Linear Regression or a Random Forest? Here, Let Me Help. Artificialis. Retrieved November 15, 2023, from https://medium.com/artificialis/cant-decide-between-a-linear-regression-or-a-random-forest-here-let-me-help-ab941b94da4c#:~:text=In%20general%2C%20if%20the%20relationship,opt%20for%20a%20random%20forest. 
Sung, E., Chung, W. Y., & Lee, D. (2023). Factors that affect consumer trust in product quality: A focus on online reviews and shopping platforms. Humanities & Social Sciences Communication, 10(766). https://doi.org/10.1057/s41599-023-02277-7


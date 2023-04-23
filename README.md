# Iron-Hack-Final-Project-2
**benned nedben**  
**IronHack, Berlin 21 Apr 2023**

# Overview

* Analysis of different  rental prices in Germany based on data from kaggle.com. The data set was processed in 11 Jupyter Notebooks.

## Programs used:

- Jupyter Notebook
- PyCharm
- Excel
- LibreOffice
- Power Point
- Adobe Photoshop

## Libaries used:

- pandas
- numpy
- matplotlib
- seaborn
- warnings
- BeautifulSoup
- sklearn
- train_test_split
- OneHotEncoder
- make_column_transformer
- StandardScaler
- MinMaxScaler
- r2_score
- mean_squared_error
- mean_absolute_error
- MLPRegressor
- LinearRegression
- LogisticRegression
- neighbors
- KMeans
- PCA
- VarianceThreshold
- RFE
- cross_val_score
- DecisionTreeRegressor
- RandomForestClassifier
- RandomForestRegressor
- confusion_matrix
- cluster
- re
- nltk
-  word_tokenize
- WordNetLemmatizer
- PorterStemmer
- wordnet
- stopwords
- FreqDist
- CountVectorizer



  
# 01 Overview.ipynb

Various data sets are available for download on the kaggle.com website.

The following website could be used to download the used dataset:

[Apartment rental offers in Germany](https://www.kaggle.com/datasets/corrieaar/apartment-rental-offers-in-germany)

On the website it says:

Where is the data from?
The data was scraped from Immoscout24, the biggest real estate platform in Germany. Immoscout24 has listings for both rental properties and homes for sale, however, the data only contains offers for rental properties.
The scraping process is described in this blog post and the corresponding code for scraping and minimal processing afterwards can be found in this Github repo.
At a given time, all available offers were scraped from the site and saved. This process was repeated three times, so the data set contains offers from the dates 2018-09-22, 2019-05-10 and 2019-10-08.

Content
The data set contains most of the important properties, such as living area size, the rent, both base rent as well as total rent (if applicable), the location (street and house number, if available, ZIP code and state), type of energy etc. It also has two variables containing longer free text descriptions: description with a text describing the offer and facilities describing all available facilities, newest renovation etc. The date column was added to give the time of scraping.
[...]


The Jupiter Notebook (01 Overview.ipynb) gives an overview of the dataset, the column names, a discription of the column names, NaN-values, data types, actions on NaN-values, droped rows, units, used models, scores, feature selections and some value counts for specific columns.


# 02 Data cleaning.ipynb

The Jupiter Notebook (02 Data cleaning.ipynb) includes the process of data cleaning of the dataset (immo_data.csv from kaggle) named above. 

Two new columns where added ([Euro/m2] and [price_class]) as target for following models

A cleaned dataset with the two new columns was created with the command: .to_csv('immo.csv')
A uncleaned dataset (with all null values and without droped rows) including the two new columns was created with the command: .to_csv('alt_immo.csv')


# 03 Data Analysis.ipynb

Different plots were made for each column to get an overview of the data set. 
One of the following plot types was chosen according to the data:

- .plot
- .barplot
- .displot
- .countplot
- .boxplot
- .scatterplot

# 04 Berlin.ipynb

In this jupyter notebook the same thing was done as in the previous one, only the focus was on my hometown Berlin instead of Germany.
The rents were broken down into the postcodes for the individual districts.

# 05 Search App.ipynb

An app was written to retrieve various statistical values for individual regions based on user input. 
The menu has the following structure:

MAINMENU "INFO BASE RENT GERMANY".
Press [1] Info base rent germany.
Press [2] Postal code search.
Press [3] City search.
Press [4] Federal state search..
Press [5] deep City search.
Press [6] to exit the program.

# 06 Scaping.ipynb

For Jupiter Notebook 04 Berlin.ipynb it was necessary to assign individual postal codes of Berlin to the existing districts. 
The following page was used to scrape the required data from the web:

[Postal codes](https://www.dastelefonbuch.de/Postleitzahlen/Berlin)

# 07 Model.ipynb

In this notebook, models were used to predict either price per square meter [Euro/m2] or the price class [price_class].
The following models were applied:

- LinearRegression
- MLPRegressor
- LogisticRegression
- KNeighbors

The MLPRegressor delivered the best results with a score of 72,5% accuracy.
On average, it was 1.65 Euros/m² away from the actual square meter price, which fluctuates between 0 and 50 Euros in the cleaned data set.

Various columns with categorical values have been converted to numeric values for use in the following notebook.

# 08 Model_cat.ipynb

In this notebook, the same models were applied as before, only additional features were processed for the predictions, which were previously converted from categorical to numeric values.

The MLPRegressor delivered again the best results with a score of 78,8% accuracy.
On average, it was 1.40 Euros/m² away from the actual square meter price.

# 09 Clusters.ipynb

A Principal Component Analysis (PCA) based on KMEans clusters where made in this Notebook. 
Unfortunately, it was not possible to finish the work because of version problems.

# 10 more Models .ipynb

In this notebook, models were used to predict the price class [price_class].
The following models were applied:

- Random Forest Classifier
- Cross Validation
- Variance Threshold
- PCA
- Random Forest Regressor

The RandomForestRegressor delivered the best results with a score of 75,2% accuracy.
On average, it was 1.07 classes away from the actual price class, which fluctuates between 1 and 15 in the cleaned data set.

# 11 Text Analysis.ipynb
The goal of this notebook was to find the 100 most used words in the ['description'] column. Keywords can be used to enhance the model. It could be shown that apartments with the keyword 'Einbauküche'(fitted kitchen) have a higher base rent than those without this word in the description.


# Conclusion

Many factors determine the base rent of an apartment. 
Many assumptions could be confirmed. 
The location of the property has the greatest influence. 
In addition, the following circumstances also have a influence on the base rent:
- service Charge
- newlyConst
- balcony
- cellar
- picture count
- year constructed
- number of park spaces
- has Kitchen
- living space
- lift
- last refurbish
- garden
- type of flat
- heating type
- firing type
- condition
- interior quality
- pets allowed
- number of rooms
- energy efficiency class

The housing market remains tense in Germany. Analyzing data can help people make the right decisions.

# Features preprocessing
## numeric features:
### Scaling
Tree-based models doesn't depend on scaling.
Non-tree based models hugely depend on scaling.
Different features scalings result in different models quality.  
``` python
sklearn.preprocessing.StandardScaler - to mean==0, std ==1
MinMaxScaler - to [0,1]
```
### Outliers
``` python
sklearn.preprocessing.RobustScaler
```
### Rank transformation  
Rank transformation will move the outliers closer to other objects  
### Log and sqrt
1. Log transform:
```
np.log(1+x)
```
2. Raising to the power < 1:
```
np.sqrt(x + 2/3)
```
Sometimes we can concatenated dataframe produced by different preprocessings.
Or mix models trained on differnetly preprocessed data.

## Categorical and ordinal features  
### Label Encoding
#### For Tree-based models
```
sklearn.preprocessing.LabelEncoder
pandas.factorize()
# Or Frequency encoding
```
#### For Non-tree-based models
Using One-hot encoding
```
pandas.get_dummies()
sklearn.preprocessing.OneHotEncoder
```

# Feature generation
Creativity and data understanding are the keys to productive feature generation.
a. Prior knowledge
b. Exploratory data analysis

## Datetime  
### Periodicity
Day number in week, month, season, year, hour, second, minute  
### Time since
1. Row-independent moment
For example: since 1970-1-1  
2. Row-dependent important moment
Number of days left until next holidays/time passed after last holiday.  
### Difference between dates  
datetime_feature_1, datetime_feature_2  

## Coordinates  
1. Interesting places from train/test data  
2. Centers of clusters  
3. Aggregated statistics  

# Data Augmentation
[Pseudo labeling](https://www.kaggle.com/cdeotte/pseudo-labeling-qda-0-969)

# Missing values    
The missing data could be not a number, empty string, -1, 99 and so on.
Using histogram to identify the hidden NANs.
  
## Fillna approaches  
1. -999, -1, etc -- good for: Tree models but linear model can suffer from this
2. mean, median -- good for linear models and NNs but bad for tree models
3. Reconstruct value -- adding new feature 'ISNULL'. good for tree and NNs, 
						but will double the numbers of columns.
Missing values imputation may screw up the feature we are constructing.
The way to handle this case is to avoid filling nans before feature generation.
  
# Feature extraction from text and images  
## Text to vector  
1. Bag of words: (BOW)  
1.1 TFiDF(Term frequency/Inverse Document Frequency) for scaling
```
sklearn.feature_extraction.text.TfidVectorizer
```    
1.2 N-grams: help to use local context
```
sklearn.feature_extraction.text.CountVectorizer:
Ngram_range, analyzer
```
2. Embeddings(~word2vec)

BOW and w2v comparison:
1. BOW: 
a. Very large vectors
b. meaning of each value in vector is known

2. Word2Vec:
a. relatively small vectors
b. values in vector can be interpreted only in some case
c. The words with similar meaning often have similar embeddings

## Texts preprocessing  
1. Lowercase
2. Lemmatization
3. Stemming
4. Stopwords

## Image to vector  
CNN  
a. features can be extracted from different layers  
b. careful choosing of pretrained network can help  
c. Finetuning allows to refine pretrained models  
d. Data augmentation can improve the model


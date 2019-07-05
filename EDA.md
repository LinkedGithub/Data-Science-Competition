# Exploratory Data Analysis(EDA)  
## Visualization  
Visualization -> Idea : Patterns lead to question
Idea -> Visualization : Hypothesis testing  

1. Get domain knowledge  
2. Check if data is intuitive  
3. Understand how the data was generated(To set up a proper validation)  

### Explore individual features 

| Tools| Examples|
| :-------:   	  | :---------: |  
|Histogram    	  | plt.hist(x)|  
|Index vs value   | plt.plot(x,'.')|  
|Color code the points  | plt.scatter(range(len(x)), x, c=y)|  
|Feature statistics| df.describe()  x.mean()  x.var()|  
|Other tools| x.value_counts()  x.isnull()|

### Explore feature relations  
- Pairs
```
plt.scatter(x1,x2)
pd.scatter_matrix(df)
df.corr()
plt.matshow()
```  
- Groups  
```
df.mean().plt(style='.')
df.mean().sort_values().plt(style='.')
```

### Explore anonymized data  
1. Explore individual features  
- Guess the meaning or types of the columns  
```
df.dtypes  df.info  x.value_counts()  x.isnull()
```

2. Explore feature relations  
- Find relations between pairs  
- Find feature groups  

## Dataset cleaning and other things to check  
### Duplicated and constant features  
```
train.nunique(axis=1) == 1
traintest.T.drop_duplicates()  
```  

### Duplicated rows  
- check if same rows have same label  






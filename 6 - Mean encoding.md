# Mean Encoding  
![](https://github.com/LinkedGithub/Data-Science-Course/blob/master/Figures/mean%20encoding.JPG)  
![](https://github.com/LinkedGithub/Data-Science-Course/blob/master/Figures/label%20vs%20mean%20encoding.JPG) 
1. Label encoding gives random order. No correlation with target  
2. Mean encoding helps to seperate zeros from ones.  
 
So we can reach a better loss with shorter trees.  

## Ways to use target variable  
Goods - number of ones in a group,  
Bads - number of zeros  
- Likelihood = Goods/(Goods + Bads) = mean(target)  
- Weight of Evidence = ln(Goods/Bads) * 100  
- Count = Goods = sum(target)  
- Diff = Goods - Bads  

### Method 1  
``` python
# Calculate a mapping: {item_id: target_mean}
item_id_target_mean = all_data.groupby('item_id').target.mean()

# *map* the computed means to the `item_id`'s
all_data['item_target_enc'] = all_data['item_id'].map(item_id_target_mean)

# Fill NaNs
all_data['item_target_enc'].fillna(0.3343, inplace=True) 
```
### Method 2  
``` python
'''
Differently to `.target.mean()` function `transform` 
will return a dataframe with an index like in `all_data`.
Basically this single line of code is equivalent to the first two lines from of Method 1.
'''
all_data['item_target_enc'] = all_data.groupby('item_id')['target'].transform('mean')
```  

## Regularization (To deal with overfitting)  
CV loop or Expanding mean for practical tasks  
### 1. CV loop inside training data  
- Robust and intuitive  
- Usually decent results with 4-5 folds across different datasets  
- Need to be careful with extreme situations like Leave-One-Out(Potential target leakage)  

![](https://github.com/LinkedGithub/Data-Science-Course/blob/master/Figures/CV%20loop.JPG)  

### 2. Smoothing  
- Alpha controls the amount of regularization  
- Only works together with some other regularization method  

![](https://latex.codecogs.com/gif.latex?\frac{mean(target)&space;*&space;nrows&space;&plus;&space;globalmean&space;*&space;alpha}{nrows&space;&plus;&space;alpha})  

### 3. Adding random noise  
- Noise degrades the quality of encoding  
- Usually used together with LOO  
- Hard to make it work since it's pretty unstable  

### 4. Sorting and calculating expanding mean  
- Use only rows from zero to n-1 to calculate encoding for row n.
- least amout parameters  
- Downside: Irregular encoding quality  
- Built-in in CatBoost  
```
cumsum = df_tr.groupby(col)['target'].cumsum() - df_tr['target']  
cumcnt = df_tr.groupby(col).cumcount()
train_new[col + 'mean_target'] = cumsum/cumcnt
```

## Extensions and generalizations  
### Regression and multiclass  
- More statistics for regression tasks. Percentiles, std, median, distribution bins  
- Introducing new information for one vs all classifiers in multi-class tasks.  

### Many-to-many relations  
- cross product of entities  
- statistics from vectors  

### Time series  
- Time structure allows us to make a lot of complicated features  
- Rolling statistics of target variable  

### Interactions and numerical features  
- Analyzing fitted model  
- Binning numeric and selecting interactions  

## Correct validation reminder  
![](https://github.com/LinkedGithub/Data-Science-Course/blob/master/Figures/Correct%20validation%20reminder.JPG)  

## End  
1. Main advantages:  
- Compact transformation of categorical variables  
- Powerful basis for feature engineering  

2. Disadvantages:  
- Need careful validation, there a lot of ways to overfit  
- Significant improvements only on specific datasets  

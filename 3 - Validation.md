# Validation 
## Validation strategies  
1. Holdout: ngroups = 1  
```
sklearn.model_selection.ShuffleSplit
```  

2. K-fold: ngroups = k  
```
sklear.model_selection.KFold
```  

3. Leave-one-out: ngroups = len(train)
```
# helpful if we have too little data and fast enough models
sklearn.model_selection.LeaveOneOut
```  

## Data splitting strategies  
validation should always mimic train/test split made by organizers
1. Random, rowwise  
2. Timewise  - Moving window validation  
3. By id
4. combined  

## Validation problems  
### validation stage  
causes of different scores and optimal parameters  
- 1. Too little data  
- 2. Too diverse and inconsistant data  
- 3. Incorrect train/test split
We should do extensive validation  
- 1. Average scores from different KFold split  
- 2. Tune model on one split, evaluate score on the other  

### Submission stage  
We can observe that:
- LB score is consistently higher/lower that validation score  
- LB score is not correlated with validation score at all  
We should  
- check if too little data in public LB  
- Check if overfitted  
- Check if we chose correct splitting strategy  
- Check if tran/test have different distribution
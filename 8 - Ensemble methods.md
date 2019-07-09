# Ensemble methods  
## Averaging (or blending)  
- (model 1 + model 2)/2  

Weighted averaging:  
- (model 1 * 0.7 + model 2 * 0.3)  

Conditional averaging:  
- model 1 if condition 1 else model 2  

## Bagging  
### What is Bagging  
It means averaging slightly different versions of the same model to improve accuracy.  
Application: Random Forest

### Why Bagging  
- There are 2 main sources of errors in modelling:  
   - Errors due to Bias(underfitting)  
   - Errors due Variance(overfitting)  
   
### Parameters that control bagging  
- Changing the seed  
- Row (sub)sampling or Bootstrapping  
- Shuffling  
- Column (Sub)sampling  
- Model-specific parameters  
- Number of models(bags)  
- (Optionally) parallelism  

### Examples  
#### BaggingClassifier and BaggingRegressor from Sklearn  
```
model = RandomForestRegressor()  
bags = 10  
seed = 1  
bagged_prediction = np.zeros(test.shape[0])  

for n in range(0,bags):
	model.set_params(radom_state = seed + n)  #Update seed  
	model.fit(train, y)  
	preds = model.predict(test)  
	bagged_prediction += preds  
	
bagged_prediction /= bags
```  

## Boosting  
### What is Boosting  
A form of weighted averaging of models where each model is built sequentially via  
taking into account the past model performance  

### Main boosting types  
#### Weight based  
![](https://github.com/LinkedGithub/Data-Science-Course/blob/master/Figures/Weight%20based%20boosting%20-1.JPG)  

##### Parameters  
- Learning rate(or shrinkage or eta)  
   - prediciton N = pred0 * eta + pred1 * eta +...+ predN * eta  
- Number of estimators  
- Input model - can be anything that accepts weights  
- Sub boosting type: AdaBoost in sklearn  

#### Residual based  
![](https://github.com/LinkedGithub/Data-Science-Course/blob/master/Figures/Residual%20based%20boosting.JPG) 
 
##### Parameters  
- Learning rate(or shrinkage or eta)  
   - prediciton N = pred0 + pred1 * eta +...+ predN * eta  
- Number of estimators  
- Row (sub) sampling  
- Column (sub) sampling  
- Input model - better be trees.  
- Sub boosting type:  
   - Fully gradient based: XgBoost, Lightgbm, Catboost, sklearn's GBM  
   - Dart  

## Stacking  
### What is Stacking  
It means making predictions of a number of models in a hold-out set and then  
using a different (Meta) model to train on these prediction.  

### Things to be mindful of  
- With time sensitive data - respect time  
- Diversity as important as performance  
- Diversity may come from:  
   - Different algorithms  
   - Different input features  
- Performance plateauing after N models  
- Meta model is normally modest  




# Hyperparameter tuning  
## Tree-based models  
1. GBDT  

|XGBoost|LightGBM|  
| :-:   | :-:    |
|max_depth|max_depth/num_leaves|
|subsample|bagging_fraction|
|colsample_bytree<br>colsample_bylevel|feature_fraction|
|min_child_weight<br>lambda<br>alpha|min_data_in_leaf<br>lambda_l1<br>lambda_l2|
|eta<br>num_round|learning_rate<br>num_iterations|
|seed|*_seed|  

2. sklearn.RandomForest/ExtraTrees  
- N_estimators  
- max_depth(start from 7)  
- max_features  
- min_samples_leaf  

Others:  
- criterion(Gini or Entropy)  
- random_state  
- n_jobs  

## Dense Neural Nets  
- Number of neurons per layer  
- Number of layers  
- Optimizers:  
   - SGD + momentum  
   - Adam/Adadelta/Adagrad/..(In practice, lead to more overfitting)  
- Batch size  
- Learning rate  
- Regularization:  
   - L2/L1 for weights  
   - Dropout/Dropconnect  
   - Static dropconnect  

## Linear models  
- Regularization parameter(alpha, lambda)  
- Regularization type  
   - L1/L2/L1+L2 try each  
   - L1 can be used for feature selection  


	


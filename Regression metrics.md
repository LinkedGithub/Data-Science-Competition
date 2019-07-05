# Regression metrics  
## MSE: Mean Square Error  
Best constant: target mean  
![](https://latex.codecogs.com/gif.latex?MSE&space;=&space;\frac{1}{N}\sum_{i=1}^{N}\left&space;(&space;y&space;-&space;\widehat{y}&space;\right&space;)^{2})  

## RMSE: Root mean square error  
![](https://latex.codecogs.com/gif.latex?RMSE&space;=&space;\sqrt{\frac{1}{N}\sum_{i=1}^{N}\left&space;(&space;y&space;-&space;\widehat{y}&space;\right&space;)^{2}}&space;=&space;\sqrt{MSE})  

![](https://latex.codecogs.com/gif.latex?MSE\left&space;(&space;a&space;\right&space;)>&space;MSE\left&space;(&space;b&space;\right&space;)\Leftrightarrow&space;RMSE\left&space;(&space;a&space;\right&space;)>&space;RMSE\left&space;(&space;b&space;\right&space;))  

![](https://latex.codecogs.com/gif.latex?\frac{\partial&space;RMSE}{\partial&space;\widehat{y}}&space;=&space;\frac{1}{2\sqrt{MSE}}\frac{\partial&space;MSE}{\partial&space;\widehat{y}})  

## R-squared:      
![](https://latex.codecogs.com/gif.latex?R^{2}&space;=&space;1&space;-&space;\frac{MSE}{\frac{1}{N}\sum_{i=1}^{N}\left&space;(&space;y_{i}&space;-&space;\bar{y}\right&space;)^{2}})  

For reasonable models : ![](https://latex.codecogs.com/gif.latex?R^{2}&space;\in&space;\left&space;(&space;0,1&space;\right&space;))

![](https://latex.codecogs.com/gif.latex?\bar{y}&space;=&space;\frac{1}{N}\sum_{i=1}^{N}&space;y_{i})  

MSE = 0, R-squared = 1  
MSE = (MSE over constant model), R-squared = 0  

## MAE: Mean Absolute Error  
Best constant: target median  
![](https://latex.codecogs.com/gif.latex?MAE&space;=&space;\frac{1}{N}\sum_{i=1}^{N}\left&space;|&space;y_{i}-&space;\widehat{y}_{i}\right&space;|)  

MAE vs MSE:  
MAE is more robust than MSE, since it is not influenced by the outliers.  
IF the data contains outliers:  
-Use MAE   
Or they are just unexpected values we should still care about:  
-Use MSE  

## From MSE, MAE to MSPE and MAPE:  
## MSPE: Mean Squared Percentage Error  
Best constant: weighted target mean  
![](https://latex.codecogs.com/gif.latex?MSPE%3D%5Cfrac%7B100%5C%25%7D%7BN%7D%5Csum_%7Bi%3D1%7D%5E%7BN%7D%5Cleft%28%5Cfrac%7By_%7Bi%7D-%5Cwidehat%7By_%7Bi%7D%7D%7D%7By_%7Bi%7D%7D%5Cright%29%5E%7B2%7D)  

## MAPE: Mean Absolute Percentage Error  
Best constant: weighted target median   
![](https://latex.codecogs.com/gif.latex?MSPE%3D%5Cfrac%7B100%5C%25%7D%7BN%7D%5Csum_%7Bi%3D1%7D%5E%7BN%7D%5Cleft%7C%5Cfrac%7By_%7Bi%7D-%5Cwidehat%7By_%7Bi%7D%7D%7D%7By_%7Bi%7D%7D%5Cright%7C)  

(R)MSLE: Root Mean Square Logarithmic Error  
![](https://latex.codecogs.com/gif.latex?RMSLE%3D%5Csqrt%7B%5Cfrac%7B1%7D%7BN%7D%5Csum_%7Bi%3D1%7D%5E%7BN%7D%5Cleft%28%5Clog%28y_%7Bi%7D&plus;1%29-%5Clog%28%5Cwidehat%7By%7D_%7Bi%7D&plus;1%29%29%5Cright%29%5E%7B2%7D%7D%3DRMSE%5Cleft%28%5Clog%28y_%7Bi%7D&plus;1%29%2C%5Clog%28%5Cwidehat%7By%7D_%7Bi%7D&plus;1%29%29%5Cright%29%3D%5Csqrt%7BMSE%5Cleft%28%5Clog%28y_%7Bi%7D&plus;1%29%2C%5Clog%28%5Cwidehat%7By%7D_%7Bi%7D&plus;1%29%5Cright%29%7D)  

Best constant:  
- Best constant in log space is a mean target value  
- We need to exponentiate it to get an answer  

RMSLE is frequently considered as better metrics than MAPE, since it is less  
biased towards small targets, yet works with relative errors.







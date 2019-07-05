# Classification metrics  
N - is number of objects  
L - is number of classes  
[a = b] - indicator function  
Soft labels(predictions) are classifier's scores  
Hard labels (predictions):  
- ![](https://latex.codecogs.com/gif.latex?\arg&space;\underset{i}{\max}&space;f_{i}\left&space;(&space;x&space;\right&space;))  
- ![](https://latex.codecogs.com/gif.latex?\left&space;[&space;f\left&space;(&space;x&space;\right&space;)&space;>&space;b\right&space;]), b - threshold  

## Accuracy Score:  
- ![](https://latex.codecogs.com/gif.latex?Accuracy&space;=&space;\frac{1}{N}\sum_{i=1}^{N}\left&space;[&space;y_{i}&space;=&space;\widehat{y}_{i}\right&space;])  
- How frequently our class prediction is correct  
- Best constant : the most frequent class  
Dataset:  
10 cats  ------ Predict always dog:  
90 dogs  ------ Accuracy = 0.9  
So it works with hard predictions.  

## Logarithmic loss (logloss)  
### Binary:  
- ![](https://latex.codecogs.com/gif.latex?LogLoss&space;=&space;-\frac{1}{N}\sum_{i=1}^{N}y_{i}\log&space;\left&space;(&space;\widehat{y}_{i}&space;\right&space;)&space;&plus;&space;\left&space;(&space;1&space;-&space;y_{i}&space;\right&space;)\log&space;\left&space;(&space;1&space;-&space;\widehat{y}_{i}&space;\right&space;))  
- ![](https://latex.codecogs.com/gif.latex?y_{i}&space;\epsilon&space;\mathbb{R},&space;\widehat{y}_{i}&space;\epsilon&space;\mathbb{R})  

### Multiclass:  
- ![](https://latex.codecogs.com/gif.latex?LogLoss&space;=&space;-\frac{1}{N}\sum_{i=1}^{N}\sum_{i=1}^{L}&space;y_{il}\log&space;\left&space;(&space;\widehat{y}_{il}&space;\right&space;))  
- ![](https://latex.codecogs.com/gif.latex?y_{i}&space;\epsilon&space;\mathbb{R^{L}},&space;\widehat{y}_{i}&space;\epsilon&space;\mathbb{R^{L}})  

### In practice:  
- ![](https://latex.codecogs.com/gif.latex?LogLoss&space;=&space;-\frac{1}{N}\sum_{i=1}^{N}\sum_{i=1}^{L}&space;y_{il}\log&space;\left&space;(&space;\min&space;\left&space;(&space;\max&space;\left&space;(&space;\widehat{y}_{il},&space;10^{-15}\right&space;)&space;,&space;1-&space;10^{-15}&space;\right&space;)&space;\right&space;))  

Best constant:  
set a(i) to frequency of i-th class  
Dataset:  
10 cats  ------ a = [0.1, 0.9]  
90 dogs  ------  

## Area Under Curve (AUC ROC)  
- only for binary tasks  
- Depends only on ordering of the predictions, not on absolute values  
- Best constant:  All constants give same score  
- Random predictions lead to AUC = 0.5 (baseline)  





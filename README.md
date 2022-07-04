[toc]

# 中文版本：[简体中文](README_zh.md)

# ESE_MSc_Thesis

The raw data is obtained from [Kaggle](https://www.kaggle.com/datasets/wordsforthewise/lending-club), which contains the period from 2007 to 2018. I only selected the year 2016-2018 due to computing power.  The data has over 150 features originally, the variable description is provided [here](./Data/LCDataDictionary.xlsx) .

## 1.  Data Clean

The source code for this part is provided here &rarr; [Part1_Data_Clean.ipynb](./Code/Part1_Data_Clean.ipynb)

## 2. Data Preparation

After the first stage data clean, I did further feature engineering in this part to prepare different version of data for final model implementation. The source code for this part is provided here. &rarr; [Part2_Data_Preparation_Wrangling.ipynb](./Code/Part2_Data_Preparation_Wrangling.ipynb)

## 3. Models

> All models are applied using several versions of data set to compare the results. E.g., SMOTE and without SMOTE,  with outliers and without outliers.

### 3.1 Logistic Model

Logistic model is provided here &rarr; [Part3_Logistic_Model.ipynb](./Code/Part3_Logistic_Model.ipynb). In this file, I also tried panelized logistic regression(LASSO) to compare the results.  

### 3.2 Random Forest Model

The random forest model is provided &rarr; [Part4_RF_Model.ipynb](../Code/Part4_RF_Model.ipynb)

### 3.3 Deep Neural Network Model

DNN model is provided here &rarr; [Part5_DNN_Model.ipynb](../Code/Part5_DNN_Model.ipynb).  The resulting DNN parameters are as following:

|   Parameter   |    Value     |    Notes     |
| :-----------: | :----------: | :----------: |
|   optimizer   |     Adam     |              |
| Nodes(Layer1) |  (116,200)   |     relu     |
| Nodes(Layer2) |  (200, 300)  |     relu     |
| Nodes(Layer3) |   (300, 2)   |   softmax    |
| loss function | CrossEntropy |              |
| learning rate |    0.001     |              |
|     Epoch     |     100      | threshold:90 |



### 3.4  Results

<table>
<thead>
  <tr>
    <th></th>
    <th>SMOTE</th>
    <th>Outliers</th>
    <th colspan="2">Confusion Matrix</th>
    <th>MCC</th>
    <th>F1</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="8"><strong>Logit</strong></td>
    <td rowspan="2">N</td>
    <td rowspan="2">Y</td>
    <td>765</td>
    <td>8,063</td>
    <td rowspan="2">0.14</td>
    <td rowspan="2">0.15</td>
  </tr>
  <tr>
    <td>988</td>
    <td>46,245</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">Y</td>
    <td>5,650</td>
    <td>3,178</td>
    <td rowspan="2">0.22</td>
    <td rowspan="2">0.37</td>
  </tr>
  <tr>
    <td>16,242</td>
    <td>30,991</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">N</td>
    <td>4,625</td>
    <td>2,553</td>
    <td rowspan="2">0.21</td>
    <td rowspan="2">0.36</td>
  </tr>
  <tr>
    <td>13,908</td>
    <td>25,208</td>
  </tr>
  <tr>
    <td rowspan="2">N</td>
    <td rowspan="2">N</td>
    <td>39</td>
    <td>7,139</td>
    <td rowspan="2">0.02</td>
    <td rowspan="2">0.01</td>
  </tr>
  <tr>
    <td>83</td>
    <td>39,033</td>
  </tr>
      <tr>
    <td rowspan="8"><strong>RF</strong></td>
    <td rowspan="2">N</td>
    <td rowspan="2">Y</td>
    <td>829</td>
    <td>7,999</td>
    <td rowspan="2">0.14</td>
    <td rowspan="2">0.15</td>
  </tr>
  <tr>
    <td>1,064</td>
    <td>46,169</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">Y</td>
    <td>1,677</td>
    <td>7,151</td>
    <td rowspan="2">0.16</td>
    <td rowspan="2">0.25</td>
  </tr>
  <tr>
    <td>3,142</td>
    <td>44,091</td>
  </tr>
  <tr>
    <td rowspan="2">N</td>
    <td rowspan="2">N</td>
    <td>484</td>
    <td>6,694</td>
    <td rowspan="2">0.12</td>
    <td rowspan="2">0.12</td>
  </tr>
  <tr>
    <td>615</td>
    <td>38,501</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">N</td>
    <td>1,155</td>
    <td>6,023</td>
    <td rowspan="2">0.14</td>
    <td rowspan="2">0.22</td>
  </tr>
  <tr>
    <td>2,312</td>
    <td>36,804</td>
  </tr>
      <tr>
    <td rowspan="8"><strong>DNN</strong></td>
    <td rowspan="2">N</td>
    <td rowspan="2">Y</td>
    <td>310</td>
    <td>8,518</td>
    <td rowspan="2">0.1</td>
    <td rowspan="2">0.07</td>
  </tr>
  <tr>
    <td>371</td>
    <td>46,862</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">Y</td>
    <td>5,737</td>
    <td>3,091</td>
    <td rowspan="2">0.32</td>
    <td rowspan="2">0.44</td>
  </tr>
  <tr>
    <td>11,263</td>
    <td>34,970</td>
  </tr>
  <tr>
    <td rowspan="2">N</td>
    <td rowspan="2">N</td>
    <td>75</td>
    <td>7,103</td>
    <td rowspan="2">0.04</td>
    <td rowspan="2">0.02</td>
  </tr>
  <tr>
    <td>114</td>
    <td>39,002</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">N</td>
    <td>4,202</td>
    <td>2,976</td>
    <td rowspan="2">0.23</td>
    <td rowspan="2">0.38</td>
  </tr>
  <tr>
    <td>11,019</td>
    <td>28,097</td>
  </tr>
</tbody>
</table>






## 4 Questions

**June 6**: How to create confusion matrix when using PyTorch to build up deep learning model.  Because the outputs are probability, we can't directly compare with test target values.  I tried to convert them using `argmax() `, but in the end the problem is still not solved. 

>**June 6 Question SOLVED**: we need to transform `y_pred` from numpy ndarray to tensor, and then apply `argmax()` to save it as a new long tensor. In the end, we can use `ConfusionMatrix` from `torchmetrics` to do it directly. 

```python
from torchmetrics import ConfusionMatrix

Y_PREDICT = torch.argmax(torch.tensor(y_pred), dim=1)

confmat = ConfusionMatrix(num_classes=2)
confmat(Y_PREDICT, y_test)
```



**June 17**: Why the performance for NO SMOTE is worse than with SMOTE in logistic model. In most cases, SMOTE will decrease the performance when we have imbalanced data but increase the CALL score. I don't understand why in logistic model it is the other way around. 



**June 18**: No outliers and no SMOTE for DNN, why FP and TN are all 0?  This is very strange. 



**June 19**: How to speed up SHAP computing for DNN model. 

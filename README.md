[toc]

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
    <th>AUC</th>
    <th>F1</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="8"><strong>Logit</strong></td>
    <td rowspan="2">N</td>
    <td rowspan="2">Y</td>
    <td>46,245</td>
    <td>988</td>
    <td rowspan="2">0.53</td>
    <td rowspan="2">0.91</td>
  </tr>
  <tr>
    <td>8,063</td>
    <td>765</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">Y</td>
    <td>30,991</td>
    <td>16,242</td>
    <td rowspan="2">0.65</td>
    <td rowspan="2">0.76</td>
  </tr>
  <tr>
    <td>3,178</td>
    <td>5,650</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">N</td>
    <td>25,208</td>
    <td>13,908</td>
    <td rowspan="2">0.64</td>
    <td rowspan="2">0.75</td>
  </tr>
  <tr>
    <td>2,553</td>
    <td>4,625</td>
  </tr>
  <tr>
    <td rowspan="2">N</td>
    <td rowspan="2">N</td>
    <td>39,033</td>
    <td>83</td>
    <td rowspan="2">0.50</td>
    <td rowspan="2">0.92</td>
  </tr>
  <tr>
    <td>7,139</td>
    <td>39</td>
  </tr>
      <tr>
    <td rowspan="8"><strong>RF</strong></td>
    <td rowspan="2">N</td>
    <td rowspan="2">Y</td>
    <td>46,169</td>
    <td>1,064</td>
    <td rowspan="2">0.54</td>
    <td rowspan="2">0.91</td>
  </tr>
  <tr>
    <td>7,999</td>
    <td>829</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">Y</td>
    <td>44,091</td>
    <td>3,142</td>
    <td rowspan="2">0.56</td>
    <td rowspan="2">0.90</td>
  </tr>
  <tr>
    <td>7,151</td>
    <td>1,677</td>
  </tr>
  <tr>
    <td rowspan="2">N</td>
    <td rowspan="2">N</td>
    <td>38,501</td>
    <td>615</td>
    <td rowspan="2">0.53</td>
    <td rowspan="2">0.91</td>
  </tr>
  <tr>
    <td>6,694</td>
    <td>484</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">N</td>
    <td>36,804</td>
    <td>2,312</td>
    <td rowspan="2">0.55</td>
    <td rowspan="2">0.90</td>
  </tr>
  <tr>
    <td>6,023</td>
    <td>1,155</td>
  </tr>
      <tr>
    <td rowspan="8"><strong>DNN</strong></td>
    <td rowspan="2">N</td>
    <td rowspan="2">Y</td>
    <td>46,862</td>
    <td>371</td>
    <td rowspan="2">0.894</td>
    <td rowspan="2">0.91</td>
  </tr>
  <tr>
    <td>8,518</td>
    <td>310</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">Y</td>
    <td>33,470</td>
    <td>12,763</td>
    <td rowspan="2">0.759</td>
    <td rowspan="2">0.80</td>
  </tr>
  <tr>
    <td>3,991</td>
    <td>4,837</td>
  </tr>
  <tr>
    <td rowspan="2">N</td>
    <td rowspan="2">N</td>
    <td>39,116</td>
    <td>0</td>
    <td rowspan="2">0.893</td>
    <td rowspan="2">0.92</td>
  </tr>
  <tr>
    <td>7,178</td>
    <td>0</td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">N</td>
    <td>27,597</td>
    <td>11,519</td>
    <td rowspan="2">0.747</td>
    <td rowspan="2">0.79</td>
  </tr>
  <tr>
    <td>3,376</td>
    <td>3,802</td>
  </tr>
</tbody>
</table>





### 3.5 Questions

**June 6**: How to create confusion matrix when using PyTorch to build up deep learning model.  Because the outputs are probability, we can't directly compare with test target values.  I tried to convert them using `argmax() `, but in the end the problem is still not solved. 

>**June 6 Question SOLVED**: we need to transform `y_pred` from numpy ndarray to tensor, and then apply `argmax()` to save it as a new long tensor. In the end, we can use `ConfusionMatrix` from `torchmetrics` to do it directly. 

```python
from torchmetrics import ConfusionMatrix

Y_PREDICT = torch.argmax(torch.tensor(y_pred), dim=1)

confmat = ConfusionMatrix(num_classes=2)
confmat(Y_PREDICT, y_test)
```



**June 17**: Why the performance for NO SMOTE is worse than with SMOTE in logistic model. In most cases, SMOTE will decrease the performance when we have imbalanced data but increase the CALL score. I don't understand why in logistic model it is the other way around. 

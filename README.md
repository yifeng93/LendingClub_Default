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

DNN model is provided here &rarr; [Part5_DNN_Model.ipynb](../Code/Part5_DNN_Model.ipynb). 

### 3.4  Results

<table>
<thead>
  <tr>
    <th></th>
    <th>SMOTE</th>
    <th>Outliers</th>
    <th colspan="2">Confusion Matrix</th>
    <th>AUC</th>
    <th>f1</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="8">Logit</td>
    <td rowspan="2">N</td>
    <td rowspan="2">N</td>
    <td></td>
    <td></td>
    <td rowspan="2"></td>
    <td rowspan="2"></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td rowspan="2">Y</td>
    <td rowspan="2">N</td>
    <td></td>
    <td></td>
    <td rowspan="2"></td>
    <td rowspan="2"></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td rowspan="2">N</td>
    <td rowspan="2">Y</td>
    <td></td>
    <td></td>
    <td rowspan="2"></td>
    <td rowspan="2"></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td rowspan="2">N</td>
    <td rowspan="2">N</td>
    <td></td>
    <td></td>
    <td rowspan="2"></td>
    <td rowspan="2"></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
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



**June 17**: Why the performance for 

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
    <td rowspan="4">Logit</td>
    <td>N</td>
    <td>N</td>
    <td>12</td>
    <td>32</td>
    <td>1</td>
    <td>13</td>
  </tr>
  <tr>
    <td>Y</td>
    <td>N</td>
    <td>432</td>
    <td>232</td>
    <td>2</td>
    <td>14</td>
  </tr>
  <tr>
    <td>N</td>
    <td>Y</td>
    <td>a</td>
    <td>b</td>
    <td>3</td>
    <td>15</td>
  </tr>
  <tr>
    <td>Y</td>
    <td>Y</td>
    <td>c</td>
    <td>d</td>
    <td>4</td>
    <td>16</td>
  </tr>
  <tr>
    <td rowspan="4">RF</td>
    <td>N</td>
    <td>N</td>
    <td>e</td>
    <td>f</td>
    <td>5</td>
    <td>17</td>
  </tr>
  <tr>
    <td>Y</td>
    <td>N</td>
    <td>g</td>
    <td>h</td>
    <td>6</td>
    <td>18</td>
  </tr>
  <tr>
    <td>N</td>
    <td>Y</td>
    <td>i</td>
    <td>j</td>
    <td>7</td>
    <td>19</td>
  </tr>
  <tr>
    <td>Y</td>
    <td>Y</td>
    <td>k</td>
    <td>l</td>
    <td>8</td>
    <td>20</td>
  </tr>
  <tr>
    <td rowspan="4">Logit</td>
    <td>N</td>
    <td>N</td>
    <td>m</td>
    <td>n</td>
    <td>9</td>
    <td>21</td>
  </tr>
  <tr>
    <td>Y</td>
    <td>N</td>
    <td>o</td>
    <td>p</td>
    <td>10</td>
    <td>22</td>
  </tr>
  <tr>
    <td>N</td>
    <td>Y</td>
    <td>q</td>
    <td>r</td>
    <td>11</td>
    <td>23</td>
  </tr>
  <tr>
    <td>Y</td>
    <td>Y</td>
    <td>s</td>
    <td>t</td>
    <td>12</td>
    <td>24</td>
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

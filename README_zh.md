[toc]

## 人工智能实战应用-LendingClub

此仓库包含着两个部分的内容： 1. IT私塾数据清洗专项课程的直播课源代码和数据集。  2. 完整的一个人工智能机器学习+深度学习实战项目的录课视频源码: Lending Club用户违约智能预测。

根据自己的需要，在文件列表里找相应的文件。

### 数据集简介

原始数据很大，包含了2007年到2018年的LendingClub用户数据，大约220万行。解压之后的csv文件有1.55GB，建议各位下载原数据后先切片到某一年的数据拿来练习或者测试。下载地址 &rarr; [Kaggle](https://www.kaggle.com/datasets/wordsforthewise/lending-club)。 对于每一行的用户数据，LendingClub最多提供了150个特征。每个变量的具体解释提供在这里 &rarr; [变量词典](./Data/LCDataDictionary.xlsx) 。

### 文件列表

1. IT私塾数据清洗专项课：数据清洗jupyter notebook
2. IT私塾数据清洗专项课：逻辑回归jupyter notebook
3. IT私塾数据清洗专项课：LendingClub 2018年数据

### 模型成绩

<table>
<thead>
  <tr>
    <th></th>
    <th>SMOTE</th>
    <th>Outliers</th>
    <th colspan="2">混淆矩阵</th>
    <th>MCC</th>
    <th>F1</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="8"><strong>逻辑回归</strong></td>
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
    <td rowspan="8"><strong>随机森林</strong></td>
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
    <td rowspan="8"><strong>神经网络</strong></td>
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


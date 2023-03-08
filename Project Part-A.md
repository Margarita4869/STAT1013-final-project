---
jupyter:
  colab:
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

<div class="cell markdown" id="9xZnRXM7x0Cv">

# CUHK-STAT1013: Practical Assignment Part 1: Sharing Your Idea and Data

</div>

<div class="cell markdown" id="9Fy05KAkyJI0">

## Starbucks satisfactory survey dataset background

**Description**:

Dataset describing the comment of some customers to Starbucks.

**Github**:
<https://raw.githubusercontent.com/prasertcbs/basic-dataset/master/Starbucks%20satisfactory%20survey%20encode%20cleaned.csv>

For not encoded data,please check at:
<https://github.com/prasertcbs/basic-dataset/blob/master/Starbucks%20satisfactory%20survey.csv>

**Sample size**: 113

**Feature documentation**:

| Feature                |     | Dtype |
|:-----------------------|:----|:------|
| Id                     |     | int64 |
| gender                 |     | int64 |
| age                    |     | int64 |
| status                 |     | int64 |
| income                 |     | int64 |
| visitNo                |     | int64 |
| method                 |     | int64 |
| timeSpend              |     | int64 |
| location               |     | int64 |
| membershipCard         |     | int64 |
| itemPurchaseCoffee     |     | int64 |
| itempurchaseCold       |     | int64 |
| itemPurchasePastries   |     | int64 |
| itemPurchaseJuices     |     | int64 |
| itemPurchaseSandwiches |     | int64 |
| itemPurchaseOthers     |     | int64 |
| spendPurchase          |     | int64 |
| productRate            |     | int64 |
| priceRate              |     | int64 |
| promoRate              |     | int64 |
| ambianceRate           |     | int64 |
| wifiRate               |     | int64 |
| serviceRate            |     | int64 |
| chooseRate             |     | int64 |
| promoMethodApp         |     | int64 |
| promoMethodSoc         |     | int64 |
| promoMethodEmail       |     | int64 |
| promoMethodDeal        |     | int64 |
| promoMethodFriend      |     | int64 |
| promoMethodDisplay     |     | int64 |
| promoMethodBillboard   |     | int64 |
| promoMethodOthers      |     | int64 |
| loyal                  |     | int64 |

</div>

<div class="cell markdown" id="k85zO7zxys4H">

## Hypothesis

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
    -   Does more employed join the starbucks membership than students?
-   What two groups you are comparing:
    -   **G1**: starbucks membership rate of students; **G2**: starbucks
        membership rate of employed
-   What you will be measuring (i.e., what your response variable will
    be)
    -   `membershipCard`
-   Is your response variable quantitative rather than categorical?
    -   `membershipCard` is binary data, with the order `1 > 0`, which
        can be regarded as a quantitative variable.
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
    -   We'd expect that **G2** \> **G1** as employed people usually has
        more money to spend and more need on coffee.
-   Talk about how you will gather your data
    -   From Github link:
        <https://raw.githubusercontent.com/prasertcbs/basic-dataset/master/Starbucks%20satisfactory%20survey%20encode%20cleaned.csv>
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
    -   \(i\) Attempt to collect more data of starbucks customers at
        different shops; (ii)Collect data from clustered sampling and
        try to avoid simple random sampling.

</div>

<div class="cell markdown" id="pm1N8AVFxGSr">

</div>

<div class="cell markdown" id="3GOdPWT03PQB">

## Prepare your dataset

</div>

<div class="cell code" execution_count="1"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:300}"
id="mUxJb4hxvpHQ" outputId="8420b121-1341-45cf-a708-4bdaa2111897">

``` python
  {"tags":["hide-input",]}
## load dataset from github

import pandas as pd

df = pd.read_csv('https://raw.githubusercontent.com/prasertcbs/basic-dataset/master/Starbucks%20satisfactory%20survey%20encode%20cleaned.csv')
df.head(5)
```

<div class="output execute_result" execution_count="1">

       Id  gender  age  status  income  visitNo  method  timeSpend  location  \
    0   1       1    1       0       0        3       0          1         0   
    1   2       1    1       0       0        3       2          0         1   
    2   3       0    1       2       0        2       0          1         2   
    3   4       1    1       0       0        3       2          0         2   
    4   5       0    1       0       0        2       2          1         1   

       membershipCard  ...  chooseRate  promoMethodApp  promoMethodSoc  \
    0               0  ...           3               1               1   
    1               0  ...           2               1               1   
    2               0  ...           3               1               1   
    3               1  ...           3               1               1   
    4               1  ...           3               1               1   

       promoMethodEmail  promoMethodDeal  promoMethodFriend  promoMethodDisplay  \
    0                 1                1                  1                   1   
    1                 1                1                  1                   1   
    2                 1                1                  1                   1   
    3                 1                1                  1                   1   
    4                 1                1                  1                   1   

       promoMethodBillboard  promoMethodOthers  loyal  
    0                     1                  1      0  
    1                     1                  1      0  
    2                     1                  1      0  
    3                     1                  1      1  
    4                     1                  1      0  

    [5 rows x 33 columns]

</div>

</div>

<div class="cell markdown" id="55xAIxVa3hpQ">

-   Tell us what groups you want to compare in the dataset
    -   **G1** (membershipCard = 1 \| status = 0) vs. **G2**
        (membershipCard = 1 \| status = 2 )

</div>

<div class="cell markdown" id="13PdL3ht3902">

-   Print first 5 records of each group, respectively.

</div>

<div class="cell code" execution_count="9"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:143}"
id="UNL0WXav3hLj" outputId="bf4784d9-ca7c-4e26-c27b-cd9adde51782">

``` python
## First 5 records of G1 (student)
df= pd.read_csv('https://raw.githubusercontent.com/prasertcbs/basic-dataset/master/Starbucks%20satisfactory%20survey%20encode%20cleaned.csv')
A=df['membershipCard']=='1'
B=df['status']=='0'
df[(A)&(B)].head(5)
```

<div class="output execute_result" execution_count="9">

    Empty DataFrame
    Columns: [Id, gender, age, status, income, visitNo, method, timeSpend, location, membershipCard, itemPurchaseCoffee, itempurchaseCold, itemPurchasePastries, itemPurchaseJuices, itemPurchaseSandwiches, itemPurchaseOthers, spendPurchase, productRate, priceRate, promoRate, ambianceRate, wifiRate, serviceRate, chooseRate, promoMethodApp, promoMethodSoc, promoMethodEmail, promoMethodDeal, promoMethodFriend, promoMethodDisplay, promoMethodBillboard, promoMethodOthers, loyal]
    Index: []

    [0 rows x 33 columns]

</div>

</div>

<div class="cell code" execution_count="7"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:143}"
id="dhe52HVB4T1O" outputId="740c1d2d-1a73-4578-d27b-289cf47ec0a6">

``` python
## First 5 records of G2 (employed)
A=df['membershipCard']=='1'
C=df['status']=='2'
df[(A)&(C)].head(5)
```

<div class="output execute_result" execution_count="7">

    Empty DataFrame
    Columns: [Id, gender, age, status, income, visitNo, method, timeSpend, location, membershipCard, itemPurchaseCoffee, itempurchaseCold, itemPurchasePastries, itemPurchaseJuices, itemPurchaseSandwiches, itemPurchaseOthers, spendPurchase, productRate, priceRate, promoRate, ambianceRate, wifiRate, serviceRate, chooseRate, promoMethodApp, promoMethodSoc, promoMethodEmail, promoMethodDeal, promoMethodFriend, promoMethodDisplay, promoMethodBillboard, promoMethodOthers, loyal]
    Index: []

    [0 rows x 33 columns]

</div>

</div>

<div class="cell code" id="zEgfWXaKGvNC">

``` python
## Any other data description and visualization you want to add.

## Open question, be flexible and no example can be provided.
```

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:611}"
id="gTpimKFH_twY" outputId="efd44958-95c0-4e2e-dc64-b1a4f610b8b1">

``` python
import matplotlib.pyplot as plt
import seaborn as sns
plt.rcParams['figure.figsize'] = [1,10]
sns.histplot(df, x='membershipCard')
sns.set()
```

<div class="output display_data">

![](a7850b26f51aed66862c8c40820ccedce2b30fa3.png)

</div>

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:339}"
id="Lk1xKlenn7x5" outputId="63e2ab52-c9ba-4afa-b851-75f44d990547">

``` python
import matplotlib.pyplot as plt
import seaborn as sns
plt.rcParams['figure.figsize'] = [10, 5]
sns.histplot(df, x='status')
sns.set()
```

<div class="output display_data">

![](d5cd6bc437daa0c3ea4d8a6b7e9a11db0edc2f97.png)

</div>

</div>

##Dataset poreparation

</div>

<div class="cell code" execution_count="1"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:300}"
id="mUxJb4hxvpHQ" outputId="8420b121-1341-45cf-a708-4bdaa2111897">

``` python
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

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:300}"
id="UNL0WXav3hLj" outputId="706d6bfd-f938-4096-ac96-83441697c51e">

``` python
## First 5 records of G1 (student)
df= pd.read_csv('https://raw.githubusercontent.com/prasertcbs/basic-dataset/master/Starbucks%20satisfactory%20survey%20encode%20cleaned.csv')
df[(df['status']==0) & (df['membershipCard']==1)].head(5)
```

<div class="output execute_result" execution_count="21">

        Id  gender  age  status  income  visitNo  method  timeSpend  location  \
    3    4       1    1       0       0        3       2          0         2   
    4    5       0    1       0       0        2       2          1         1   
    5    6       1    1       0       0        3       0          1         2   
    10  11       1    1       0       0        3       0          0         2   
    11  12       1    1       0       0        3       0          1         2   

        membershipCard  ...  chooseRate  promoMethodApp  promoMethodSoc  \
    3                1  ...           3               1               1   
    4                1  ...           3               1               1   
    5                1  ...           4               1               1   
    10               1  ...           4               1               1   
    11               1  ...           4               1               1   

        promoMethodEmail  promoMethodDeal  promoMethodFriend  promoMethodDisplay  \
    3                  1                1                  1                   1   
    4                  1                1                  1                   1   
    5                  1                1                  1                   1   
    10                 1                1                  1                   1   
    11                 1                1                  1                   1   

        promoMethodBillboard  promoMethodOthers  loyal  
    3                      1                  1      1  
    4                      1                  1      0  
    5                      1                  1      0  
    10                     1                  1      0  
    11                     1                  1      1  

    [5 rows x 33 columns]

</div>

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:300}"
id="dhe52HVB4T1O" outputId="58c70309-4726-4dd5-9433-2b551bba2549">

``` python
## First 5 records of G2 (employed)
df[(df['status']==2) & (df['membershipCard']==1)].head(5)
```

<div class="output execute_result" execution_count="22">

        Id  gender  age  status  income  visitNo  method  timeSpend  location  \
    9   10       0    1       2       0        2       2          0         2   
    21  22       1    1       2       0        3       0          0         0   
    22  23       0    1       2       1        3       0          4         0   
    26  27       0    2       2       4        3       1          0         1   
    32  33       1    2       2       1        3       2          0         2   

        membershipCard  ...  chooseRate  promoMethodApp  promoMethodSoc  \
    9                1  ...           4               1               1   
    21               1  ...           5               1               1   
    22               1  ...           3               1               1   
    26               1  ...           2               1               1   
    32               1  ...           5               1               1   

        promoMethodEmail  promoMethodDeal  promoMethodFriend  promoMethodDisplay  \
    9                  1                1                  1                   1   
    21                 1                1                  1                   1   
    22                 1                1                  1                   1   
    26                 1                1                  1                   1   
    32                 1                1                  1                   1   

        promoMethodBillboard  promoMethodOthers  loyal  
    9                      1                  1      0  
    21                     1                  1      0  
    22                     1                  1      1  
    26                     1                  0      1  
    32                     1                  1      0  

    [5 rows x 33 columns]

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

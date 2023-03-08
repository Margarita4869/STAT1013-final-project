
# CUHK-STAT1013: Final project

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

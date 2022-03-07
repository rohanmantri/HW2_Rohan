## Question 1. Data Visualization

![](HW2_R_files/figure-markdown_strict/unnamed-chunk-3-1.png) ## On
weekdays, the average number of boardings is roughly the same, and on
weekends, it drops as expected. On weekdays, the peak hour of boarding
numbers remains consistent between 3 and 5 pm for all three months,
owing to the fact that classes normally complete around that time. The
average boardings on Mondays in September are lower due to Labor Day,
which falls on the first Monday of the month, and those on Wednesdays,
Thursdays, and Fridays in November due to the Thanksgiving holidays)

![](HW2_R_files/figure-markdown_strict/unnamed-chunk-5-1.png) ##
Question 2. Saratoga house prices

## The linear model seems better at achieving lower out-of sample mean-squared error. This model is particularly useful since it allows us to identify which variables have a substantial impact on property prices. House prices are influenced by factors such as lot size, land value, living area, waterfront, and central air conditioning. All of them have a positive relationship with home prices.

## Output for linear regression model is as follows:

    ## 
    ## Call:
    ## lm(formula = price ~ . - pctCollege - sewer - newConstruction + 
    ##     rooms:bathrooms, data = .)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -225593  -34740   -4847   27123  458507 
    ## 
    ## Coefficients:
    ##                          Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)             1.898e+05  2.296e+04   8.267 2.93e-16 ***
    ## lotSize                 9.593e+03  2.199e+03   4.362 1.37e-05 ***
    ## age                    -7.492e+01  6.163e+01  -1.216 0.224289    
    ## landValue               8.887e-01  4.907e-02  18.111  < 2e-16 ***
    ## livingArea              6.167e+01  4.928e+00  12.513  < 2e-16 ***
    ## bedrooms               -4.565e+03  2.710e+03  -1.685 0.092232 .  
    ## fireplaces              2.441e+03  3.144e+03   0.776 0.437709    
    ## bathrooms               4.942e+03  7.932e+03   0.623 0.533382    
    ## rooms                  -2.831e+03  2.150e+03  -1.316 0.188214    
    ## heatinghot water/steam -8.562e+03  4.450e+03  -1.924 0.054511 .  
    ## heatingelectric        -1.182e+03  1.310e+04  -0.090 0.928116    
    ## fuelelectric           -7.475e+03  1.286e+04  -0.581 0.561037    
    ## fueloil                -3.308e+03  5.065e+03  -0.653 0.513769    
    ## waterfrontNo           -1.220e+05  1.622e+04  -7.521 9.17e-14 ***
    ## centralAirNo           -1.324e+04  3.674e+03  -3.603 0.000324 ***
    ## bathrooms:rooms         2.594e+03  9.904e+02   2.619 0.008903 ** 
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 59030 on 1539 degrees of freedom
    ## Multiple R-squared:  0.6483, Adjusted R-squared:  0.6449 
    ## F-statistic: 189.1 on 15 and 1539 DF,  p-value: < 2.2e-16

## Question 3. Classification and retrospective sampling

![](HW2_R_files/figure-markdown_strict/unnamed-chunk-11-1.png)

    ##         (Intercept)            duration              amount         installment 
    ##                0.51                1.03                1.00                1.23 
    ##                 age         historypoor     historyterrible          purposeedu 
    ##                0.98                0.30                0.13                1.74 
    ## purposegoods/repair       purposenewcar      purposeusedcar       foreigngerman 
    ##                1.31                2.46                0.41                0.20

    ##    yhat
    ## y     0   1
    ##   0 159   8
    ##   1  61  22

<table>
<thead>
<tr class="header">
<th style="text-align: left;">history</th>
<th style="text-align: right;">count</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">good</td>
<td style="text-align: right;">89</td>
</tr>
<tr class="even">
<td style="text-align: left;">poor</td>
<td style="text-align: right;">618</td>
</tr>
<tr class="odd">
<td style="text-align: left;">terrible</td>
<td style="text-align: right;">293</td>
</tr>
<tr class="even">
<td style="text-align: left;">total</td>
<td style="text-align: right;">1000</td>
</tr>
</tbody>
</table>

## The ‘historypoor’ variable multiplies odds of default by 0.39 in this logistic regression model, while the ‘historyterrible’ variable multiplies odds of default by 0.19. This means that having poor or terrible credit actually decreases the probability of default. This contradicts common sense; we believe the dataset is insufficient for developing a predictive model of defaults, particularly if the program’s goal is to screen potential borrowers and identify them as having a “high” or “low” risk of default. It’s due to the data sampling procedure. Instead of random sample, the bank chose defaulted loans and looked for similar loans during the data sampling procedure. This most certainly resulted in a significant bias in the data collection process: as previously stated, defaulted loans are likely to have low or horrible credit histories, and there would be insufficient datasets with good credit histories. In fact, just 89 observations out of 1000 had a decent credit history. Even though there would be a small number of defaulted loans, I would advise the bank to employ a random sample method. Increasing the size of the observations, if possible, will be really beneficial.

## Question 4. Children and hotel reservations

<table>
<thead>
<tr class="header">
<th style="text-align: left;">model</th>
<th style="text-align: right;">TPR</th>
<th style="text-align: right;">FPR</th>
<th style="text-align: right;">thresh</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">baseline1</td>
<td style="text-align: right;">0.0000000</td>
<td style="text-align: right;">0.0000000</td>
<td style="text-align: right;">0.7</td>
</tr>
<tr class="even">
<td style="text-align: left;">baseline2</td>
<td style="text-align: right;">0.0536451</td>
<td style="text-align: right;">0.0015956</td>
<td style="text-align: right;">0.7</td>
</tr>
<tr class="odd">
<td style="text-align: left;">LPM</td>
<td style="text-align: right;">0.0286107</td>
<td style="text-align: right;">0.0008220</td>
<td style="text-align: right;">0.7</td>
</tr>
<tr class="even">
<td style="text-align: left;">baseline1</td>
<td style="text-align: right;">0.0000000</td>
<td style="text-align: right;">0.0000000</td>
<td style="text-align: right;">0.5</td>
</tr>
<tr class="odd">
<td style="text-align: left;">baseline2</td>
<td style="text-align: right;">0.0872077</td>
<td style="text-align: right;">0.0032153</td>
<td style="text-align: right;">0.5</td>
</tr>
<tr class="even">
<td style="text-align: left;">LPM</td>
<td style="text-align: right;">0.0847318</td>
<td style="text-align: right;">0.0033362</td>
<td style="text-align: right;">0.5</td>
</tr>
<tr class="odd">
<td style="text-align: left;">baseline1</td>
<td style="text-align: right;">0.0000000</td>
<td style="text-align: right;">0.0000725</td>
<td style="text-align: right;">0.2</td>
</tr>
<tr class="even">
<td style="text-align: left;">baseline2</td>
<td style="text-align: right;">0.1342503</td>
<td style="text-align: right;">0.0114831</td>
<td style="text-align: right;">0.2</td>
</tr>
<tr class="odd">
<td style="text-align: left;">LPM</td>
<td style="text-align: right;">0.1248968</td>
<td style="text-align: right;">0.0113139</td>
<td style="text-align: right;">0.2</td>
</tr>
</tbody>
</table>

## This table has the TPR and FPR of the models when the threshold is set at 0.7, 0.5, and 0.2. Across various threshold values, baseline 1 displays low TPRs. We can see that the baseline 2 and LPM has higher TPRs. We choose baseline2 for further analysis.

## Step 1 for Model validation

![](HW2_R_files/figure-markdown_strict/unnamed-chunk-20-1.png) ## Step 2
for Model validation

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: left;">Predicted</th>
<th style="text-align: left;">Actual</th>
<th style="text-align: left;">Difference</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">Fold01</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold02</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">26</td>
<td style="text-align: left;">5</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold03</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">-3</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold04</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">24</td>
<td style="text-align: left;">5</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold05</td>
<td style="text-align: left;">24</td>
<td style="text-align: left;">24</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold06</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">15</td>
<td style="text-align: left;">-7</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold07</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">23</td>
<td style="text-align: left;">3</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold08</td>
<td style="text-align: left;">23</td>
<td style="text-align: left;">29</td>
<td style="text-align: left;">6</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold09</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">16</td>
<td style="text-align: left;">-5</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold10</td>
<td style="text-align: left;">25</td>
<td style="text-align: left;">24</td>
<td style="text-align: left;">-1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold11</td>
<td style="text-align: left;">23</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold12</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold13</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">-3</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold14</td>
<td style="text-align: left;">18</td>
<td style="text-align: left;">15</td>
<td style="text-align: left;">-3</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold15</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">16</td>
<td style="text-align: left;">-5</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold16</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold17</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold18</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold19</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">14</td>
<td style="text-align: left;">-5</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold20</td>
<td style="text-align: left;">17</td>
<td style="text-align: left;">16</td>
<td style="text-align: left;">-1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Total</td>
<td style="text-align: left;">421</td>
<td style="text-align: left;">402</td>
<td style="text-align: left;">19</td>
</tr>
</tbody>
</table>

## The model does the prediction pretty well. It only got 19 predictions wrong in total out of 4999 observations though if you look at each folds individually there is a difference as in sometimes we have negative and sometimes positive values, but in total it all averages out to 19.

## Question 1. Data Visualization

![](HW2_RM_files/figure-markdown_strict/unnamed-chunk-3-1.png) ## On
weekdays, the average number of boardings is roughly the same, and on
weekends, it drops as expected. On weekdays, the peak hour of boarding
numbers remains consistent between 3 and 5 pm for all three months,
owing to the fact that classes normally complete around that time. The
average boardings on Mondays in September are lower due to Labor Day,
which falls on the first Monday of the month, and those on Wednesdays,
Thursdays, and Fridays in November due to the Thanksgiving holidays)

![](HW2_RM_files/figure-markdown_strict/unnamed-chunk-5-1.png) ##
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
    ## -230160  -35021   -5491   27874  459587 
    ## 
    ## Coefficients:
    ##                          Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)             1.983e+05  2.269e+04   8.742  < 2e-16 ***
    ## lotSize                 8.102e+03  2.253e+03   3.596 0.000333 ***
    ## age                    -8.154e+01  6.139e+01  -1.328 0.184344    
    ## landValue               8.559e-01  4.961e-02  17.253  < 2e-16 ***
    ## livingArea              6.522e+01  5.062e+00  12.885  < 2e-16 ***
    ## bedrooms               -7.803e+03  2.776e+03  -2.810 0.005010 ** 
    ## fireplaces              3.358e+03  3.180e+03   1.056 0.291261    
    ## bathrooms               2.507e+03  8.080e+03   0.310 0.756352    
    ## rooms                  -2.372e+03  2.197e+03  -1.079 0.280557    
    ## heatinghot water/steam -8.652e+03  4.490e+03  -1.927 0.054182 .  
    ## heatingelectric        -2.308e+03  1.264e+04  -0.183 0.855194    
    ## fuelelectric           -7.484e+03  1.241e+04  -0.603 0.546642    
    ## fueloil                -4.187e+03  5.082e+03  -0.824 0.410168    
    ## waterfrontNo           -1.250e+05  1.581e+04  -7.906 5.03e-15 ***
    ## centralAirNo           -1.221e+04  3.702e+03  -3.297 0.001001 ** 
    ## bathrooms:rooms         2.693e+03  1.011e+03   2.662 0.007842 ** 
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 59500 on 1539 degrees of freedom
    ## Multiple R-squared:  0.645,  Adjusted R-squared:  0.6415 
    ## F-statistic: 186.4 on 15 and 1539 DF,  p-value: < 2.2e-16

## Question 3. Classification and retrospective sampling

![](HW2_RM_files/figure-markdown_strict/unnamed-chunk-11-1.png)

    ##         (Intercept)            duration              amount         installment 
    ##                0.37                1.02                1.00                1.22 
    ##                 age         historypoor     historyterrible          purposeedu 
    ##                0.99                0.36                0.20                1.83 
    ## purposegoods/repair       purposenewcar      purposeusedcar       foreigngerman 
    ##                1.13                2.18                0.44                0.32

    ##    yhat
    ## y     0   1
    ##   0 153   8
    ##   1  59  30

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
<td style="text-align: right;">0.0506190</td>
<td style="text-align: right;">0.0015956</td>
<td style="text-align: right;">0.7</td>
</tr>
<tr class="odd">
<td style="text-align: left;">LPM</td>
<td style="text-align: right;">0.0275103</td>
<td style="text-align: right;">0.0008703</td>
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
<td style="text-align: right;">0.0830812</td>
<td style="text-align: right;">0.0032153</td>
<td style="text-align: right;">0.5</td>
</tr>
<tr class="even">
<td style="text-align: left;">LPM</td>
<td style="text-align: right;">0.0822558</td>
<td style="text-align: right;">0.0037713</td>
<td style="text-align: right;">0.5</td>
</tr>
<tr class="odd">
<td style="text-align: left;">baseline1</td>
<td style="text-align: right;">0.0002751</td>
<td style="text-align: right;">0.0000242</td>
<td style="text-align: right;">0.2</td>
</tr>
<tr class="even">
<td style="text-align: left;">baseline2</td>
<td style="text-align: right;">0.1298487</td>
<td style="text-align: right;">0.0117007</td>
<td style="text-align: right;">0.2</td>
</tr>
<tr class="odd">
<td style="text-align: left;">LPM</td>
<td style="text-align: right;">0.1243466</td>
<td style="text-align: right;">0.0124260</td>
<td style="text-align: right;">0.2</td>
</tr>
</tbody>
</table>

## This table has the TPR and FPR of the models when the threshold is set at 0.7, 0.5, and 0.2. Across various threshold values, baseline 1 displays low TPRs. We can see that the baseline 2 and LPM has higher TPRs. We choose baseline2 for further analysis.

## Step 1 for Model validation

![](HW2_RM_files/figure-markdown_strict/unnamed-chunk-20-1.png) ## Step
2 for Model validation

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
<td style="text-align: left;">19</td>
<td style="text-align: left;">17</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold02</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">15</td>
<td style="text-align: left;">-5</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold03</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold04</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold05</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">18</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold06</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold07</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">25</td>
<td style="text-align: left;">3</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold08</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">13</td>
<td style="text-align: left;">-6</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold09</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">26</td>
<td style="text-align: left;">5</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold10</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold11</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">2</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold12</td>
<td style="text-align: left;">23</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">-3</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold13</td>
<td style="text-align: left;">18</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">2</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold14</td>
<td style="text-align: left;">23</td>
<td style="text-align: left;">15</td>
<td style="text-align: left;">-8</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold15</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">18</td>
<td style="text-align: left;">-1</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold16</td>
<td style="text-align: left;">23</td>
<td style="text-align: left;">26</td>
<td style="text-align: left;">3</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold17</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">3</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold18</td>
<td style="text-align: left;">26</td>
<td style="text-align: left;">25</td>
<td style="text-align: left;">-1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold19</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">-3</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold20</td>
<td style="text-align: left;">18</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">2</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Total</td>
<td style="text-align: left;">417</td>
<td style="text-align: left;">402</td>
<td style="text-align: left;">15</td>
</tr>
</tbody>
</table>

## The model does the prediction pretty well. It only got 15 predictions wrong in total out of 4999 observations though if you look at each folds individually there is a difference as in sometimes we have negative and sometimes positive values, but in total it all averages out to 15.

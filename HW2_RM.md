## Question 1. Data Visualization

![](HW2_RM_files/figure-markdown_strict/unnamed-chunk-3-1.png)

# On weekdays, the average number of boardings is roughly the same, and on weekends, it drops as expected. On weekdays, the peak hour of boarding numbers remains consistent between 3 and 5 pm for all three months, owing to the fact that classes normally complete around that time. The average boardings on Mondays in September are lower due to Labor Day, which falls on the first Monday of the month, and those on Wednesdays, Thursdays, and Fridays in November due to the Thanksgiving holidays)

![](HW2_RM_files/figure-markdown_strict/unnamed-chunk-5-1.png)

## Question 2. Saratoga house prices

# The linear model seems better at achieving lower out-of sample mean-squared error. This model is particularly useful since it allows us to identify which variables have a substantial impact on property prices. House prices are influenced by factors such as lot size, land value, living area, waterfront, and central air conditioning. All of them have a positive relationship with home prices.

# Output for linear regression model is as follows:

    ## 
    ## Call:
    ## lm(formula = price ~ . - pctCollege - sewer - newConstruction + 
    ##     rooms:bathrooms, data = .)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -228042  -35648   -5116   28079  459564 
    ## 
    ## Coefficients:
    ##                          Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)             1.956e+05  2.299e+04   8.508  < 2e-16 ***
    ## lotSize                 7.471e+03  2.376e+03   3.144  0.00170 ** 
    ## age                    -7.902e+01  6.020e+01  -1.313  0.18954    
    ## landValue               8.468e-01  4.924e-02  17.198  < 2e-16 ***
    ## livingArea              6.371e+01  4.897e+00  13.010  < 2e-16 ***
    ## bedrooms               -7.814e+03  2.694e+03  -2.900  0.00378 ** 
    ## fireplaces              4.092e+03  3.061e+03   1.337  0.18148    
    ## bathrooms               3.400e+03  7.946e+03   0.428  0.66883    
    ## rooms                  -1.736e+03  2.157e+03  -0.805  0.42087    
    ## heatinghot water/steam -9.351e+03  4.349e+03  -2.150  0.03171 *  
    ## heatingelectric        -3.960e+03  1.407e+04  -0.281  0.77843    
    ## fuelelectric           -4.961e+03  1.388e+04  -0.357  0.72082    
    ## fueloil                -6.032e+03  5.014e+03  -1.203  0.22909    
    ## waterfrontNo           -1.276e+05  1.656e+04  -7.706 2.32e-14 ***
    ## centralAirNo           -9.585e+03  3.601e+03  -2.662  0.00785 ** 
    ## bathrooms:rooms         2.669e+03  9.934e+02   2.686  0.00730 ** 
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 58030 on 1539 degrees of freedom
    ## Multiple R-squared:  0.6542, Adjusted R-squared:  0.6508 
    ## F-statistic: 194.1 on 15 and 1539 DF,  p-value: < 2.2e-16

## Question 3. Classification and retrospective sampling

![](HW2_RM_files/figure-markdown_strict/unnamed-chunk-11-1.png)

    ##         (Intercept)            duration              amount         installment 
    ##                0.52                1.03                1.00                1.20 
    ##                 age         historypoor     historyterrible          purposeedu 
    ##                0.97                0.37                0.20                2.37 
    ## purposegoods/repair       purposenewcar      purposeusedcar       foreigngerman 
    ##                0.97                2.52                0.51                0.49

    ##    yhat
    ## y     0   1
    ##   0 165  14
    ##   1  57  14

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

# The ‘historypoor’ variable multiplies odds of default by 0.39 in this logistic regression model, while the ‘historyterrible’ variable multiplies odds of default by 0.19. This means that having poor or terrible credit actually decreases the probability of default. This contradicts common sense; we believe the dataset is insufficient for developing a predictive model of defaults, particularly if the program’s goal is to screen potential borrowers and identify them as having a “high” or “low” risk of default. It’s due to the data sampling procedure. Instead of random sample, the bank chose defaulted loans and looked for similar loans during the data sampling procedure. This most certainly resulted in a significant bias in the data collection process: as previously stated, defaulted loans are likely to have low or horrible credit histories, and there would be insufficient datasets with good credit histories. In fact, just 89 observations out of 1000 had a decent credit history. Even though there would be a small number of defaulted loans, I would advise the bank to employ a random sample method. Increasing the size of the observations, if possible, will be really beneficial.

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
<td style="text-align: right;">0.0517194</td>
<td style="text-align: right;">0.0016197</td>
<td style="text-align: right;">0.7</td>
</tr>
<tr class="odd">
<td style="text-align: left;">LPM</td>
<td style="text-align: right;">0.0288858</td>
<td style="text-align: right;">0.0007978</td>
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
<td style="text-align: right;">0.0833563</td>
<td style="text-align: right;">0.0029010</td>
<td style="text-align: right;">0.5</td>
</tr>
<tr class="even">
<td style="text-align: left;">LPM</td>
<td style="text-align: right;">0.0850069</td>
<td style="text-align: right;">0.0035054</td>
<td style="text-align: right;">0.5</td>
</tr>
<tr class="odd">
<td style="text-align: left;">baseline1</td>
<td style="text-align: right;">0.0000000</td>
<td style="text-align: right;">0.0000242</td>
<td style="text-align: right;">0.2</td>
</tr>
<tr class="even">
<td style="text-align: left;">baseline2</td>
<td style="text-align: right;">0.1259972</td>
<td style="text-align: right;">0.0109513</td>
<td style="text-align: right;">0.2</td>
</tr>
<tr class="odd">
<td style="text-align: left;">LPM</td>
<td style="text-align: right;">0.1215956</td>
<td style="text-align: right;">0.0117732</td>
<td style="text-align: right;">0.2</td>
</tr>
</tbody>
</table>

## This table has the TPR and FPR of the models when the threshold is set at 0.7, 0.5, and 0.2. Across various threshold values, baseline 1 displays low TPRs. We can see that the baseline 2 and LPM has higher TPRs. We choose baseline2 for further analysis.

\*\* Step 1 for Model validation

![](HW2_RM_files/figure-markdown_strict/unnamed-chunk-20-1.png) \*\*
Step 2 for Model validation

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
<td style="text-align: left;">19</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold02</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">13</td>
<td style="text-align: left;">-6</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold03</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">18</td>
<td style="text-align: left;">-3</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold04</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">-1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold05</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">18</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold06</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">-1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold07</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">26</td>
<td style="text-align: left;">4</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold08</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">18</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold09</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">-1</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold10</td>
<td style="text-align: left;">18</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">3</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold11</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold12</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">2</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold13</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">14</td>
<td style="text-align: left;">-8</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold14</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">15</td>
<td style="text-align: left;">-4</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold15</td>
<td style="text-align: left;">19</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">3</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold16</td>
<td style="text-align: left;">21</td>
<td style="text-align: left;">28</td>
<td style="text-align: left;">7</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold17</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">24</td>
<td style="text-align: left;">4</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold18</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">24</td>
<td style="text-align: left;">2</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fold19</td>
<td style="text-align: left;">26</td>
<td style="text-align: left;">24</td>
<td style="text-align: left;">-2</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fold20</td>
<td style="text-align: left;">22</td>
<td style="text-align: left;">18</td>
<td style="text-align: left;">-4</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Total</td>
<td style="text-align: left;">413</td>
<td style="text-align: left;">402</td>
<td style="text-align: left;">11</td>
</tr>
</tbody>
</table>

# The model does the prediction pretty well. It only got 11 predictions wrong in total out of 4999 observations though if you look at each folds individually there is a difference as in sometimes we have negative and sometimes positive values, but in total it all averages out to 11.

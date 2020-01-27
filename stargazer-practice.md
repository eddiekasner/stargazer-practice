Stargazer
---------

Here’s a link to the [stargazer vingette on
CRAN](https://cran.r-project.org/web/packages/stargazer/vignettes/stargazer.pdf).
[This recent reddit
thread](https://www.reddit.com/r/rstats/comments/8qn43z/what_is_the_best_package_for_displaying_tables_in/)
discusses packages for displaying tables in R, including kabeExtra,
pander, DT, Huxtable, and stargazer. Some users report that stargazer is
fast and works easily with a set of regression model objects to produce
near-publication quality tables, and can make it pretty siple to compare
multiple models side-by-side. Other users, however, have reported
challenges related to [hard coding, API, and
layout](https://www.reddit.com/r/rstats/comments/6o9v9h/whats_your_favorite_relatively_obscure_r_package/dkgw9q1/).

Presentation
------------

    ## Warning: package 'pacman' was built under R version 3.6.2

### Step 1

    ##   Sepal.Length    Sepal.Width     Petal.Length    Petal.Width   
    ##  Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
    ##  1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300  
    ##  Median :5.800   Median :3.000   Median :4.350   Median :1.300  
    ##  Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199  
    ##  3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800  
    ##  Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500  
    ##        Species  
    ##  setosa    :50  
    ##  versicolor:50  
    ##  virginica :50  
    ##                 
    ##                 
    ## 

    ## 
    ## % Table created by stargazer v.5.2.2 by Marek Hlavac, Harvard University. E-mail: hlavac at fas.harvard.edu
    ## % Date and time: Mon, Jan 27, 2020 - 11:02:49 AM
    ## \begin{table}[!htbp] \centering 
    ##   \caption{} 
    ##   \label{} 
    ## \begin{tabular}{@{\extracolsep{5pt}}lccccccc} 
    ## \\[-1.8ex]\hline 
    ## \hline \\[-1.8ex] 
    ## Statistic & \multicolumn{1}{c}{N} & \multicolumn{1}{c}{Mean} & \multicolumn{1}{c}{St. Dev.} & \multicolumn{1}{c}{Min} & \multicolumn{1}{c}{Pctl(25)} & \multicolumn{1}{c}{Pctl(75)} & \multicolumn{1}{c}{Max} \\ 
    ## \hline \\[-1.8ex] 
    ## Sepal.Length & 150 & 5.843 & 0.828 & 4.300 & 5.100 & 6.400 & 7.900 \\ 
    ## Sepal.Width & 150 & 3.057 & 0.436 & 2.000 & 2.800 & 3.300 & 4.400 \\ 
    ## Petal.Length & 150 & 3.758 & 1.765 & 1.000 & 1.600 & 5.100 & 6.900 \\ 
    ## Petal.Width & 150 & 1.199 & 0.762 & 0.100 & 0.300 & 1.800 & 2.500 \\ 
    ## \hline \\[-1.8ex] 
    ## \end{tabular} 
    ## \end{table}

#### Hard-coded (copy and paste from above chunk) works for pdf (but not html)

    ## 
    ## <table style="text-align:center"><tr><td colspan="8" style="border-bottom: 1px solid black"></td></tr><tr><td style="text-align:left">Statistic</td><td>N</td><td>Mean</td><td>St. Dev.</td><td>Min</td><td>Pctl(25)</td><td>Pctl(75)</td><td>Max</td></tr>
    ## <tr><td colspan="8" style="border-bottom: 1px solid black"></td></tr><tr><td style="text-align:left">Sepal.Length</td><td>150</td><td>5.843</td><td>0.828</td><td>4.300</td><td>5.100</td><td>6.400</td><td>7.900</td></tr>
    ## <tr><td style="text-align:left">Sepal.Width</td><td>150</td><td>3.057</td><td>0.436</td><td>2.000</td><td>2.800</td><td>3.300</td><td>4.400</td></tr>
    ## <tr><td style="text-align:left">Petal.Length</td><td>150</td><td>3.758</td><td>1.765</td><td>1.000</td><td>1.600</td><td>5.100</td><td>6.900</td></tr>
    ## <tr><td style="text-align:left">Petal.Width</td><td>150</td><td>1.199</td><td>0.762</td><td>0.100</td><td>0.300</td><td>1.800</td><td>2.500</td></tr>
    ## <tr><td colspan="8" style="border-bottom: 1px solid black"></td></tr></table>

### Step 2

Exercise
--------

    ##       mpg             cyl             disp             hp       
    ##  Min.   :10.40   Min.   :4.000   Min.   : 71.1   Min.   : 52.0  
    ##  1st Qu.:15.43   1st Qu.:4.000   1st Qu.:120.8   1st Qu.: 96.5  
    ##  Median :19.20   Median :6.000   Median :196.3   Median :123.0  
    ##  Mean   :20.09   Mean   :6.188   Mean   :230.7   Mean   :146.7  
    ##  3rd Qu.:22.80   3rd Qu.:8.000   3rd Qu.:326.0   3rd Qu.:180.0  
    ##  Max.   :33.90   Max.   :8.000   Max.   :472.0   Max.   :335.0  
    ##       drat             wt             qsec             vs        
    ##  Min.   :2.760   Min.   :1.513   Min.   :14.50   Min.   :0.0000  
    ##  1st Qu.:3.080   1st Qu.:2.581   1st Qu.:16.89   1st Qu.:0.0000  
    ##  Median :3.695   Median :3.325   Median :17.71   Median :0.0000  
    ##  Mean   :3.597   Mean   :3.217   Mean   :17.85   Mean   :0.4375  
    ##  3rd Qu.:3.920   3rd Qu.:3.610   3rd Qu.:18.90   3rd Qu.:1.0000  
    ##  Max.   :4.930   Max.   :5.424   Max.   :22.90   Max.   :1.0000  
    ##        am              gear            carb      
    ##  Min.   :0.0000   Min.   :3.000   Min.   :1.000  
    ##  1st Qu.:0.0000   1st Qu.:3.000   1st Qu.:2.000  
    ##  Median :0.0000   Median :4.000   Median :2.000  
    ##  Mean   :0.4062   Mean   :3.688   Mean   :2.812  
    ##  3rd Qu.:1.0000   3rd Qu.:4.000   3rd Qu.:4.000  
    ##  Max.   :1.0000   Max.   :5.000   Max.   :8.000

    ## Warning: glm.fit: fitted probabilities numerically 0 or 1 occurred

    ## 
    ## <table style="text-align:center"><tr><td colspan="5" style="border-bottom: 1px solid black"></td></tr><tr><td style="text-align:left"></td><td colspan="4"><em>Dependent variable:</em></td></tr>
    ## <tr><td></td><td colspan="4" style="border-bottom: 1px solid black"></td></tr>
    ## <tr><td style="text-align:left"></td><td colspan="3">Miles/(US) gallon</td><td>Fast car (=1)</td></tr>
    ## <tr><td style="text-align:left"></td><td colspan="3"><em>OLS</em></td><td><em>logistic</em></td></tr>
    ## <tr><td style="text-align:left"></td><td>(1)</td><td>(2)</td><td>(3)</td><td>(4)</td></tr>
    ## <tr><td colspan="5" style="border-bottom: 1px solid black"></td></tr><tr><td style="text-align:left">Gross horsepower</td><td>-0.068<sup>***</sup></td><td>-0.052<sup>***</sup></td><td>-0.064<sup>***</sup></td><td>-0.397</td></tr>
    ## <tr><td style="text-align:left"></td><td>(0.010)</td><td>(0.009)</td><td>(0.011)</td><td>(1.358)</td></tr>
    ## <tr><td style="text-align:left"></td><td></td><td></td><td></td><td></td></tr>
    ## <tr><td style="text-align:left">Rear axle ratio</td><td></td><td>4.698<sup>***</sup></td><td>3.510<sup>*</sup></td><td>4.248</td></tr>
    ## <tr><td style="text-align:left"></td><td></td><td>(1.192)</td><td>(1.851)</td><td>(21.106)</td></tr>
    ## <tr><td style="text-align:left"></td><td></td><td></td><td></td><td></td></tr>
    ## <tr><td style="text-align:left">Four foward gears</td><td></td><td></td><td>-0.276</td><td></td></tr>
    ## <tr><td style="text-align:left"></td><td></td><td></td><td>(2.135)</td><td></td></tr>
    ## <tr><td style="text-align:left"></td><td></td><td></td><td></td><td></td></tr>
    ## <tr><td style="text-align:left">Five forward gears</td><td></td><td></td><td>3.761<sup>*</sup></td><td></td></tr>
    ## <tr><td style="text-align:left"></td><td></td><td></td><td>(2.161)</td><td></td></tr>
    ## <tr><td style="text-align:left"></td><td></td><td></td><td></td><td></td></tr>
    ## <tr><td style="text-align:left">Type of transmission (manual=1)</td><td></td><td></td><td></td><td>11.743</td></tr>
    ## <tr><td style="text-align:left"></td><td></td><td></td><td></td><td>(359.486)</td></tr>
    ## <tr><td style="text-align:left"></td><td></td><td></td><td></td><td></td></tr>
    ## <tr><td style="text-align:left">Constant</td><td>30.099<sup>***</sup></td><td>10.790<sup>**</sup></td><td>16.306<sup>**</sup></td><td>29.882</td></tr>
    ## <tr><td style="text-align:left"></td><td>(1.634)</td><td>(5.078)</td><td>(6.429)</td><td>(85.238)</td></tr>
    ## <tr><td style="text-align:left"></td><td></td><td></td><td></td><td></td></tr>
    ## <tr><td colspan="5" style="border-bottom: 1px solid black"></td></tr><tr><td style="text-align:left">Observations</td><td>32</td><td>32</td><td>32</td><td>32</td></tr>
    ## <tr><td style="text-align:left">R<sup>2</sup></td><td>0.602</td><td>0.741</td><td>0.782</td><td></td></tr>
    ## <tr><td style="text-align:left">Adjusted R<sup>2</sup></td><td>0.589</td><td>0.723</td><td>0.749</td><td></td></tr>
    ## <tr><td style="text-align:left">Log Likelihood</td><td></td><td></td><td></td><td>-1.953</td></tr>
    ## <tr><td style="text-align:left">Akaike Inf. Crit.</td><td></td><td></td><td></td><td>11.906</td></tr>
    ## <tr><td style="text-align:left">Residual Std. Error</td><td>3.863 (df = 30)</td><td>3.170 (df = 29)</td><td>3.017 (df = 27)</td><td></td></tr>
    ## <tr><td style="text-align:left">F Statistic</td><td>45.460<sup>***</sup> (df = 1; 30)</td><td>41.522<sup>***</sup> (df = 2; 29)</td><td>24.179<sup>***</sup> (df = 4; 27)</td><td></td></tr>
    ## <tr><td colspan="5" style="border-bottom: 1px solid black"></td></tr><tr><td style="text-align:left"><em>Note:</em></td><td colspan="4" style="text-align:right"><sup>*</sup>p<0.1; <sup>**</sup>p<0.05; <sup>***</sup>p<0.01</td></tr>
    ## </table>

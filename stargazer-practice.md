Stargazer Overview
==================

Here’s a link to the stargazer [package
description](https://cran.r-project.org/web/packages/stargazer/stargazer.pdf)
and [vingette on
CRAN](https://cran.r-project.org/web/packages/stargazer/vignettes/stargazer.pdf).
[This recent reddit
thread](https://www.reddit.com/r/rstats/comments/8qn43z/what_is_the_best_package_for_displaying_tables_in/)
discusses the ‘best’ packages for displaying tables in R, including
kabeExtra, pander, DT, Huxtable, and stargazer. Some users report that
stargazer is fast and works easily with a set of regression model
objects to produce near-publication quality tables, and can make it
pretty simple to compare multiple models side-by-side. Other users,
however, have reported challenges related to [hard coding, API, and
layout](https://www.reddit.com/r/rstats/comments/6o9v9h/whats_your_favorite_relatively_obscure_r_package/dkgw9q1/).
Here’s a [stargazer cheat
sheet](https://github.com/JakeRuss/cheatsheets/blob/master/stargazer.md)
for formatting options.

    library(pacman)

    ## Warning: package 'pacman' was built under R version 3.6.2

    p_load(stargazer)

Exercise with iris dataset
==========================

Step 1: Display table summary of iris dataset
---------------------------------------------

    summary(iris)

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

### PDF

**1. Stargazer with default settings**

    stargazer(iris)

    ## 
    ## % Table created by stargazer v.5.2.2 by Marek Hlavac, Harvard University. E-mail: hlavac at fas.harvard.edu
    ## % Date and time: Mon, Jan 27, 2020 - 12:55:09 PM
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

**2. Hard-coded (copy and paste from above chunk) works for pdf (but not
html)**

**3. Adding results=‘asis’**

    stargazer(iris)

% Table created by stargazer v.5.2.2 by Marek Hlavac, Harvard
University. E-mail: hlavac at fas.harvard.edu % Date and time: Mon, Jan
27, 2020 - 12:55:09 PM
### HTML

**4. Changing to type = html**

    stargazer(iris, type = "html")

    ## 
    ## <table style="text-align:center"><tr><td colspan="8" style="border-bottom: 1px solid black"></td></tr><tr><td style="text-align:left">Statistic</td><td>N</td><td>Mean</td><td>St. Dev.</td><td>Min</td><td>Pctl(25)</td><td>Pctl(75)</td><td>Max</td></tr>
    ## <tr><td colspan="8" style="border-bottom: 1px solid black"></td></tr><tr><td style="text-align:left">Sepal.Length</td><td>150</td><td>5.843</td><td>0.828</td><td>4.300</td><td>5.100</td><td>6.400</td><td>7.900</td></tr>
    ## <tr><td style="text-align:left">Sepal.Width</td><td>150</td><td>3.057</td><td>0.436</td><td>2.000</td><td>2.800</td><td>3.300</td><td>4.400</td></tr>
    ## <tr><td style="text-align:left">Petal.Length</td><td>150</td><td>3.758</td><td>1.765</td><td>1.000</td><td>1.600</td><td>5.100</td><td>6.900</td></tr>
    ## <tr><td style="text-align:left">Petal.Width</td><td>150</td><td>1.199</td><td>0.762</td><td>0.100</td><td>0.300</td><td>1.800</td><td>2.500</td></tr>
    ## <tr><td colspan="8" style="border-bottom: 1px solid black"></td></tr></table>

**5. Hard-coded (copy and paste from above chunk) works for html (but
not pdf)**

<table style="text-align:center">
<tr>
<td colspan="8" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
Statistic
</td>
<td>
N
</td>
<td>
Mean
</td>
<td>
St. Dev.
</td>
<td>
Min
</td>
<td>
Pctl(25)
</td>
<td>
Pctl(75)
</td>
<td>
Max
</td>
</tr>
<tr>
<td colspan="8" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
Sepal.Length
</td>
<td>
150
</td>
<td>
5.843
</td>
<td>
0.828
</td>
<td>
4.300
</td>
<td>
5.100
</td>
<td>
6.400
</td>
<td>
7.900
</td>
</tr>
<tr>
<td style="text-align:left">
Sepal.Width
</td>
<td>
150
</td>
<td>
3.057
</td>
<td>
0.436
</td>
<td>
2.000
</td>
<td>
2.800
</td>
<td>
3.300
</td>
<td>
4.400
</td>
</tr>
<tr>
<td style="text-align:left">
Petal.Length
</td>
<td>
150
</td>
<td>
3.758
</td>
<td>
1.765
</td>
<td>
1.000
</td>
<td>
1.600
</td>
<td>
5.100
</td>
<td>
6.900
</td>
</tr>
<tr>
<td style="text-align:left">
Petal.Width
</td>
<td>
150
</td>
<td>
1.199
</td>
<td>
0.762
</td>
<td>
0.100
</td>
<td>
0.300
</td>
<td>
1.800
</td>
<td>
2.500
</td>
</tr>
<tr>
<td colspan="8" style="border-bottom: 1px solid black">
</td>
</tr>
</table>

**6. Adding results=‘asis’**

    stargazer(iris, type = "html")

<table style="text-align:center">
<tr>
<td colspan="8" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
Statistic
</td>
<td>
N
</td>
<td>
Mean
</td>
<td>
St. Dev.
</td>
<td>
Min
</td>
<td>
Pctl(25)
</td>
<td>
Pctl(75)
</td>
<td>
Max
</td>
</tr>
<tr>
<td colspan="8" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
Sepal.Length
</td>
<td>
150
</td>
<td>
5.843
</td>
<td>
0.828
</td>
<td>
4.300
</td>
<td>
5.100
</td>
<td>
6.400
</td>
<td>
7.900
</td>
</tr>
<tr>
<td style="text-align:left">
Sepal.Width
</td>
<td>
150
</td>
<td>
3.057
</td>
<td>
0.436
</td>
<td>
2.000
</td>
<td>
2.800
</td>
<td>
3.300
</td>
<td>
4.400
</td>
</tr>
<tr>
<td style="text-align:left">
Petal.Length
</td>
<td>
150
</td>
<td>
3.758
</td>
<td>
1.765
</td>
<td>
1.000
</td>
<td>
1.600
</td>
<td>
5.100
</td>
<td>
6.900
</td>
</tr>
<tr>
<td style="text-align:left">
Petal.Width
</td>
<td>
150
</td>
<td>
1.199
</td>
<td>
0.762
</td>
<td>
0.100
</td>
<td>
0.300
</td>
<td>
1.800
</td>
<td>
2.500
</td>
</tr>
<tr>
<td colspan="8" style="border-bottom: 1px solid black">
</td>
</tr>
</table>

### DOC

**7. Creating single table in word**

    stargazer(iris, type = "html", out="iris-table-summary.doc")

<table style="text-align:center">
<tr>
<td colspan="8" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
Statistic
</td>
<td>
N
</td>
<td>
Mean
</td>
<td>
St. Dev.
</td>
<td>
Min
</td>
<td>
Pctl(25)
</td>
<td>
Pctl(75)
</td>
<td>
Max
</td>
</tr>
<tr>
<td colspan="8" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
Sepal.Length
</td>
<td>
150
</td>
<td>
5.843
</td>
<td>
0.828
</td>
<td>
4.300
</td>
<td>
5.100
</td>
<td>
6.400
</td>
<td>
7.900
</td>
</tr>
<tr>
<td style="text-align:left">
Sepal.Width
</td>
<td>
150
</td>
<td>
3.057
</td>
<td>
0.436
</td>
<td>
2.000
</td>
<td>
2.800
</td>
<td>
3.300
</td>
<td>
4.400
</td>
</tr>
<tr>
<td style="text-align:left">
Petal.Length
</td>
<td>
150
</td>
<td>
3.758
</td>
<td>
1.765
</td>
<td>
1.000
</td>
<td>
1.600
</td>
<td>
5.100
</td>
<td>
6.900
</td>
</tr>
<tr>
<td style="text-align:left">
Petal.Width
</td>
<td>
150
</td>
<td>
1.199
</td>
<td>
0.762
</td>
<td>
0.100
</td>
<td>
0.300
</td>
<td>
1.800
</td>
<td>
2.500
</td>
</tr>
<tr>
<td colspan="8" style="border-bottom: 1px solid black">
</td>
</tr>
</table>

> “To include stargazer tables in Microsoft Word documents (e.g., .doc
> or .docx), please follow the following procedure: Use the out argument
> to save output into an .htm or .html file. Open the resulting file in
> your web browser. Copy and paste the table from the web browser to
> your Microsoft Word document.” -[Using stargazer in
> Word](https://cran.r-project.org/web/packages/stargazer/stargazer.pdf)

Step 2: Display table models of iris dataset
--------------------------------------------

**8. Creating single model in html**

    mtcars$fast <- as.numeric((mtcars$mpg > 20.1)) #Creating a dummy variable 1 = fast car
    m1 <- lm(Sepal.Length ~ Sepal.Width, data=iris)

    stargazer(m1, type="html")

<table style="text-align:center">
<tr>
<td colspan="2" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
<em>Dependent variable:</em>
</td>
</tr>
<tr>
<td>
</td>
<td colspan="1" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
Sepal.Length
</td>
</tr>
<tr>
<td colspan="2" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
Sepal.Width
</td>
<td>
-0.223
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
(0.155)
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
</td>
</tr>
<tr>
<td style="text-align:left">
Constant
</td>
<td>
6.526<sup>\*\*\*</sup>
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
(0.479)
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
</td>
</tr>
<tr>
<td colspan="2" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
Observations
</td>
<td>
150
</td>
</tr>
<tr>
<td style="text-align:left">
R<sup>2</sup>
</td>
<td>
0.014
</td>
</tr>
<tr>
<td style="text-align:left">
Adjusted R<sup>2</sup>
</td>
<td>
0.007
</td>
</tr>
<tr>
<td style="text-align:left">
Residual Std. Error
</td>
<td>
0.825 (df = 148)
</td>
</tr>
<tr>
<td style="text-align:left">
F Statistic
</td>
<td>
2.074 (df = 1; 148)
</td>
</tr>
<tr>
<td colspan="2" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
<em>Note:</em>
</td>
<td style="text-align:right">
<sup>*</sup>p&lt;0.1; <sup>**</sup>p&lt;0.05; <sup>***</sup>p&lt;0.01
</td>
</tr>
</table>

**9. Comparing three models in html**

    mtcars$fast <- as.numeric((mtcars$mpg > 20.1)) #Creating a dummy variable 1 = fast car
    m1 <- lm(Sepal.Length ~ Sepal.Width, data=iris)
    m2 <- lm(Petal.Length ~ Petal.Width, data=iris)
    m3 <- lm(Sepal.Length ~ Sepal.Width + Petal.Width + factor(Species), data=iris)

    stargazer(m1, m2, m3, type="html")

<table style="text-align:center">
<tr>
<td colspan="4" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td colspan="3">
<em>Dependent variable:</em>
</td>
</tr>
<tr>
<td>
</td>
<td colspan="3" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
Sepal.Length
</td>
<td>
Petal.Length
</td>
<td>
Sepal.Length
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
(1)
</td>
<td>
(2)
</td>
<td>
(3)
</td>
</tr>
<tr>
<td colspan="4" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
Sepal.Width
</td>
<td>
-0.223
</td>
<td>
</td>
<td>
0.698<sup>\*\*\*</sup>
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
(0.155)
</td>
<td>
</td>
<td>
(0.119)
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td style="text-align:left">
Petal.Width
</td>
<td>
</td>
<td>
2.230<sup>\*\*\*</sup>
</td>
<td>
0.372<sup>\*</sup>
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
</td>
<td>
(0.051)
</td>
<td>
(0.198)
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td style="text-align:left">
factor(Species)versicolor
</td>
<td>
</td>
<td>
</td>
<td>
0.988<sup>\*\*\*</sup>
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
</td>
<td>
</td>
<td>
(0.275)
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td style="text-align:left">
factor(Species)virginica
</td>
<td>
</td>
<td>
</td>
<td>
1.238<sup>\*\*\*</sup>
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
</td>
<td>
</td>
<td>
(0.391)
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td style="text-align:left">
Constant
</td>
<td>
6.526<sup>\*\*\*</sup>
</td>
<td>
1.084<sup>\*\*\*</sup>
</td>
<td>
2.521<sup>\*\*\*</sup>
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
(0.479)
</td>
<td>
(0.073)
</td>
<td>
(0.394)
</td>
</tr>
<tr>
<td style="text-align:left">
</td>
<td>
</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td colspan="4" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
Observations
</td>
<td>
150
</td>
<td>
150
</td>
<td>
150
</td>
</tr>
<tr>
<td style="text-align:left">
R<sup>2</sup>
</td>
<td>
0.014
</td>
<td>
0.927
</td>
<td>
0.732
</td>
</tr>
<tr>
<td style="text-align:left">
Adjusted R<sup>2</sup>
</td>
<td>
0.007
</td>
<td>
0.927
</td>
<td>
0.725
</td>
</tr>
<tr>
<td style="text-align:left">
Residual Std. Error
</td>
<td>
0.825 (df = 148)
</td>
<td>
0.478 (df = 148)
</td>
<td>
0.434 (df = 145)
</td>
</tr>
<tr>
<td style="text-align:left">
F Statistic
</td>
<td>
2.074 (df = 1; 148)
</td>
<td>
1,882.452<sup>\*\*\*</sup> (df = 1; 148)
</td>
<td>
99.206<sup>\*\*\*</sup> (df = 4; 145)
</td>
</tr>
<tr>
<td colspan="4" style="border-bottom: 1px solid black">
</td>
</tr>
<tr>
<td style="text-align:left">
<em>Note:</em>
</td>
<td colspan="3" style="text-align:right">
<sup>*</sup>p&lt;0.1; <sup>**</sup>p&lt;0.05; <sup>***</sup>p&lt;0.01
</td>
</tr>
</table>

Exercise with mtcars dataset
============================

<!--Source: https://www.princeton.edu/~otorres/NiceOutputR.pdf-->

    summary(mtcars)


    mtcars$fast <- as.numeric((mtcars$mpg > 20.1)) #Creating a dummy variable 1 = fast car
    m1 <- lm(mpg ~ hp, data=mtcars)
    m2 <- lm(mpg ~ hp + drat, data=mtcars)
    m3 <- lm(mpg ~ hp + drat + factor(gear), data=mtcars)
    m4 <- glm(fast ~ hp + drat + am, family=binomial(link="logit"), data=mtcars)
    stargazer(m1, m2, m3, m4, type="html",
     dep.var.labels=c("Miles/(US) gallon","Fast car (=1)"),
     covariate.labels=c("Gross horsepower","Rear axle ratio","Four foward gears",
     "Five forward gears","Type of transmission (manual=1)"), out="models.htm")

R_auto_store_selection
================
SYsherley
2023-11-10

## Selection of electric vehicle store locations

``` r
# library
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.1     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.2     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.1     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(languageR)
library(readxl)
library(ez)
library(lme4)
```

    ## Loading required package: Matrix
    ## 
    ## Attaching package: 'Matrix'
    ## 
    ## The following objects are masked from 'package:tidyr':
    ## 
    ##     expand, pack, unpack

``` r
library(QuantPsyc)
```

    ## Loading required package: boot
    ## Loading required package: MASS
    ## 
    ## Attaching package: 'MASS'
    ## 
    ## The following object is masked from 'package:dplyr':
    ## 
    ##     select
    ## 
    ## 
    ## Attaching package: 'QuantPsyc'
    ## 
    ## The following object is masked from 'package:Matrix':
    ## 
    ##     norm
    ## 
    ## The following object is masked from 'package:base':
    ## 
    ##     norm

``` r
library(Hmisc)
```

    ## 
    ## Attaching package: 'Hmisc'
    ## 
    ## The following objects are masked from 'package:dplyr':
    ## 
    ##     src, summarize
    ## 
    ## The following objects are masked from 'package:base':
    ## 
    ##     format.pval, units

``` r
library(ggplot2)
library(ggpubr)
library(permutes)
library(kableExtra)
```

    ## 
    ## Attaching package: 'kableExtra'
    ## 
    ## The following object is masked from 'package:dplyr':
    ## 
    ##     group_rows

``` r
library(tibble) # rownames_to_column
library(lmPerm)
library(scales)
```

    ## 
    ## Attaching package: 'scales'
    ## 
    ## The following object is masked from 'package:purrr':
    ## 
    ##     discard
    ## 
    ## The following object is masked from 'package:readr':
    ## 
    ##     col_factor

``` r
library(plotly)
```

    ## 
    ## Attaching package: 'plotly'
    ## 
    ## The following object is masked from 'package:Hmisc':
    ## 
    ##     subplot
    ## 
    ## The following object is masked from 'package:MASS':
    ## 
    ##     select
    ## 
    ## The following object is masked from 'package:ggplot2':
    ## 
    ##     last_plot
    ## 
    ## The following object is masked from 'package:stats':
    ## 
    ##     filter
    ## 
    ## The following object is masked from 'package:graphics':
    ## 
    ##     layout

``` r
library(doParallel)
```

    ## Loading required package: foreach
    ## 
    ## Attaching package: 'foreach'
    ## 
    ## The following objects are masked from 'package:purrr':
    ## 
    ##     accumulate, when
    ## 
    ## Loading required package: iterators
    ## Loading required package: parallel

``` r
library(lpSolve)
library(irr)
library(report)
library(sjPlot)
library(sjmisc)
```

    ## 
    ## Attaching package: 'sjmisc'
    ## 
    ## The following object is masked from 'package:Hmisc':
    ## 
    ##     %nin%
    ## 
    ## The following object is masked from 'package:purrr':
    ## 
    ##     is_empty
    ## 
    ## The following object is masked from 'package:tidyr':
    ## 
    ##     replace_na
    ## 
    ## The following object is masked from 'package:tibble':
    ## 
    ##     add_case

``` r
library(data.table)
```

    ## 
    ## Attaching package: 'data.table'
    ## 
    ## The following objects are masked from 'package:lubridate':
    ## 
    ##     hour, isoweek, mday, minute, month, quarter, second, wday, week,
    ##     yday, year
    ## 
    ## The following objects are masked from 'package:dplyr':
    ## 
    ##     between, first, last
    ## 
    ## The following object is masked from 'package:purrr':
    ## 
    ##     transpose

``` r
library(devtools)
```

    ## Loading required package: usethis

``` r
library(dplyr)
library(sjlabelled)
```

    ## 
    ## Attaching package: 'sjlabelled'
    ## 
    ## The following object is masked from 'package:usethis':
    ## 
    ##     tidy_labels
    ## 
    ## The following object is masked from 'package:forcats':
    ## 
    ##     as_factor
    ## 
    ## The following object is masked from 'package:dplyr':
    ## 
    ##     as_label
    ## 
    ## The following object is masked from 'package:ggplot2':
    ## 
    ##     as_label

``` r
library(haven)
```

    ## 
    ## Attaching package: 'haven'
    ## 
    ## The following objects are masked from 'package:sjlabelled':
    ## 
    ##     as_factor, read_sas, read_spss, read_stata, write_sas, zap_labels

``` r
require(parameters)
```

    ## Loading required package: parameters

``` r
library(epiDisplay)
```

    ## Loading required package: foreign
    ## Loading required package: survival
    ## 
    ## Attaching package: 'survival'
    ## 
    ## The following object is masked from 'package:boot':
    ## 
    ##     aml
    ## 
    ## Loading required package: nnet
    ## 
    ## Attaching package: 'epiDisplay'
    ## 
    ## The following object is masked from 'package:parameters':
    ## 
    ##     ci
    ## 
    ## The following object is masked from 'package:scales':
    ## 
    ##     alpha
    ## 
    ## The following object is masked from 'package:ggplot2':
    ## 
    ##     alpha

``` r
library(olsrr)
```

    ## 
    ## Attaching package: 'olsrr'
    ## 
    ## The following object is masked from 'package:MASS':
    ## 
    ##     cement
    ## 
    ## The following object is masked from 'package:datasets':
    ## 
    ##     rivers

``` r
library(ggsignif)
library(palmerpenguins)
#install.packages("epiDisplay")
#install.packages("olsrr")
#install.packages("geosphere")
#install.packages("ggmap")
library(ggmap) 
```

    ## ℹ Google's Terms of Service: <https://mapsplatform.google.com>
    ## ℹ Please cite ggmap if you use it! Use `citation("ggmap")` for details.
    ## 
    ## Attaching package: 'ggmap'
    ## 
    ## 
    ## The following object is masked from 'package:plotly':
    ## 
    ##     wind

``` r
library(geosphere) # calculate geographic distance
library(gplots)    # heatmap
```

    ## 
    ## Attaching package: 'gplots'
    ## 
    ## The following object is masked from 'package:stats':
    ## 
    ##     lowess

### import dataset

``` r
car_stores<-read_excel("Dresden_car_stores.xlsx",
                       sheet = "Sheet1")
names(car_stores)
```

    ## [1] "Nr"                "plz"               "note"             
    ## [4] "residents"         "percetage of male" "qkm"              
    ## [7] "lat"               "lon"

``` r
## change column name
names(car_stores)[names(car_stores) == "percetage of male"] <-"percentage_male"
```

``` r
summary(car_stores)
```

    ##        Nr             plz           note             residents    
    ##  Min.   : 1.00   Min.   :1067   Length:28          Min.   : 5876  
    ##  1st Qu.: 7.75   1st Qu.:1128   Class :character   1st Qu.:14201  
    ##  Median :14.50   Median :1188   Mode  :character   Median :17528  
    ##  Mean   :14.50   Mean   :1198                      Mean   :18169  
    ##  3rd Qu.:21.25   3rd Qu.:1264                      3rd Qu.:20987  
    ##  Max.   :28.00   Max.   :1328                      Max.   :32890  
    ##  percentage_male       qkm              lat             lon       
    ##  Min.   :0.3200   Min.   : 3.216   Min.   :51.00   Min.   :13.62  
    ##  1st Qu.:0.4125   1st Qu.: 4.865   1st Qu.:51.03   1st Qu.:13.71  
    ##  Median :0.4850   Median : 5.900   Median :51.04   Median :13.76  
    ##  Mean   :0.4932   Mean   :11.298   Mean   :51.05   Mean   :13.76  
    ##  3rd Qu.:0.5850   3rd Qu.: 8.921   3rd Qu.:51.07   3rd Qu.:13.80  
    ##  Max.   :0.6700   Max.   :58.506   Max.   :51.15   Max.   :13.90

### Customer Coverage Analysis

``` r
car_stores$customer<-car_stores$residents * car_stores$percentage_male
```

``` r
# bar plot_number of people 
# reorder in descending order
car_stores <- car_stores[order(-car_stores$customer), ]

# the top 3 highest potential customers
top_3_indices <- 1:3

# Create a vector of colors
bar_colors <- rep("lightblue", nrow(car_stores))  # Set a default color for all bars
bar_colors[top_3_indices] <- "blue"  # Highlight the top 3 highest bars in red


# re-define y-axis labels
new_y_labels <- seq(0, ceiling(max(car_stores$customer) / 5000) * 5000, by = 5000)

# determine the y-axis limits based on the custom labels
y_limits <- range(new_y_labels)

# Create a bar chart with custom colors
barplot(car_stores$customer, 
        names.arg = car_stores$plz,
        xlab = "Dresden", 
        ylab = "Potential Customers", 
        col = bar_colors,
        main = "Potential Customers in Dresden", 
        beside = TRUE, 
        ylim = y_limits,las = 2)# 
```

![](R_auto_store_selection_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

## Including Plots

You can also embed plots, for example:

![](R_auto_store_selection_files/figure-gfm/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.

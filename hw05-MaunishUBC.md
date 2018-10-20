hw05-MaunishUBC
================

### Install necessary packages

``` r
library('gapminder')
library('kableExtra')
library('RColorBrewer')
library('plotly')
```

    ## Loading required package: ggplot2

    ## 
    ## Attaching package: 'plotly'

    ## The following object is masked from 'package:ggplot2':
    ## 
    ##     last_plot

    ## The following object is masked from 'package:stats':
    ## 
    ##     filter

    ## The following object is masked from 'package:graphics':
    ## 
    ##     layout

``` r
library('dplyr')
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library('forcats')
library('readr')
```

### Factor management

What are the continent's in gapminder

``` r
unique(gapminder$continent)
```

    ## [1] Asia     Europe   Africa   Americas Oceania 
    ## Levels: Africa Americas Asia Europe Oceania

Oceania isn't a continent! Let's drop it!!

``` r
gapminder_no_oceania <- gapminder %>% 
  filter(continent != "Oceania")
```

Also let's see what countries are there in Oceania

``` r
gapminder %>% 
  filter(continent == "Oceania") %>% 
  kable() %>%
  kable_styling()
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
country
</th>
<th style="text-align:left;">
continent
</th>
<th style="text-align:right;">
year
</th>
<th style="text-align:right;">
lifeExp
</th>
<th style="text-align:right;">
pop
</th>
<th style="text-align:right;">
gdpPercap
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
69.120
</td>
<td style="text-align:right;">
8691212
</td>
<td style="text-align:right;">
10039.60
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
70.330
</td>
<td style="text-align:right;">
9712569
</td>
<td style="text-align:right;">
10949.65
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
70.930
</td>
<td style="text-align:right;">
10794968
</td>
<td style="text-align:right;">
12217.23
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.100
</td>
<td style="text-align:right;">
11872264
</td>
<td style="text-align:right;">
14526.12
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.930
</td>
<td style="text-align:right;">
13177000
</td>
<td style="text-align:right;">
16788.63
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.490
</td>
<td style="text-align:right;">
14074100
</td>
<td style="text-align:right;">
18334.20
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.740
</td>
<td style="text-align:right;">
15184200
</td>
<td style="text-align:right;">
19477.01
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
76.320
</td>
<td style="text-align:right;">
16257249
</td>
<td style="text-align:right;">
21888.89
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.560
</td>
<td style="text-align:right;">
17481977
</td>
<td style="text-align:right;">
23424.77
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.830
</td>
<td style="text-align:right;">
18565243
</td>
<td style="text-align:right;">
26997.94
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
80.370
</td>
<td style="text-align:right;">
19546792
</td>
<td style="text-align:right;">
30687.75
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
81.235
</td>
<td style="text-align:right;">
20434176
</td>
<td style="text-align:right;">
34435.37
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
69.390
</td>
<td style="text-align:right;">
1994794
</td>
<td style="text-align:right;">
10556.58
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
70.260
</td>
<td style="text-align:right;">
2229407
</td>
<td style="text-align:right;">
12247.40
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
71.240
</td>
<td style="text-align:right;">
2488550
</td>
<td style="text-align:right;">
13175.68
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.520
</td>
<td style="text-align:right;">
2728150
</td>
<td style="text-align:right;">
14463.92
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.890
</td>
<td style="text-align:right;">
2929100
</td>
<td style="text-align:right;">
16046.04
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
72.220
</td>
<td style="text-align:right;">
3164900
</td>
<td style="text-align:right;">
16233.72
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
73.840
</td>
<td style="text-align:right;">
3210650
</td>
<td style="text-align:right;">
17632.41
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.320
</td>
<td style="text-align:right;">
3317166
</td>
<td style="text-align:right;">
19007.19
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
76.330
</td>
<td style="text-align:right;">
3437674
</td>
<td style="text-align:right;">
18363.32
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.550
</td>
<td style="text-align:right;">
3676187
</td>
<td style="text-align:right;">
21050.41
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
79.110
</td>
<td style="text-align:right;">
3908037
</td>
<td style="text-align:right;">
23189.80
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
80.204
</td>
<td style="text-align:right;">
4115771
</td>
<td style="text-align:right;">
25185.01
</td>
</tr>
</tbody>
</table>
So, Oceania has two countries, Australia and New Zealand.

``` r
gapminder %>% 
  str()
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    1704 obs. of  6 variables:
    ##  $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
    ##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
    ##  $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
    ##  $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
    ##  $ gdpPercap: num  779 821 853 836 740 ...

So, gapminder has 142 levels for countires and 5 levels for continent

Let's see what happens after removing Oceania

``` r
gapminder_no_oceania <- gapminder_no_oceania %>% 
  droplevels()

gapminder_no_oceania %>% 
  str()
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    1680 obs. of  6 variables:
    ##  $ country  : Factor w/ 140 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ continent: Factor w/ 4 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
    ##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
    ##  $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
    ##  $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
    ##  $ gdpPercap: num  779 821 853 836 740 ...

There are 140 countries and 4 continents.

The 4 continents make sense but why 140 countries? Where did 2 countries go?

Let's look at the differnce between gapminder\_no\_oceania and gapminder:

``` r
anti_join(gapminder, gapminder_no_oceania, by = "country") %>% 
  kable() %>% 
  kable_styling()
```

    ## Warning: Column `country` joining factors with different levels, coercing
    ## to character vector

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
country
</th>
<th style="text-align:left;">
continent
</th>
<th style="text-align:right;">
year
</th>
<th style="text-align:right;">
lifeExp
</th>
<th style="text-align:right;">
pop
</th>
<th style="text-align:right;">
gdpPercap
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
69.120
</td>
<td style="text-align:right;">
8691212
</td>
<td style="text-align:right;">
10039.60
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
70.330
</td>
<td style="text-align:right;">
9712569
</td>
<td style="text-align:right;">
10949.65
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
70.930
</td>
<td style="text-align:right;">
10794968
</td>
<td style="text-align:right;">
12217.23
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.100
</td>
<td style="text-align:right;">
11872264
</td>
<td style="text-align:right;">
14526.12
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.930
</td>
<td style="text-align:right;">
13177000
</td>
<td style="text-align:right;">
16788.63
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.490
</td>
<td style="text-align:right;">
14074100
</td>
<td style="text-align:right;">
18334.20
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.740
</td>
<td style="text-align:right;">
15184200
</td>
<td style="text-align:right;">
19477.01
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
76.320
</td>
<td style="text-align:right;">
16257249
</td>
<td style="text-align:right;">
21888.89
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.560
</td>
<td style="text-align:right;">
17481977
</td>
<td style="text-align:right;">
23424.77
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.830
</td>
<td style="text-align:right;">
18565243
</td>
<td style="text-align:right;">
26997.94
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
80.370
</td>
<td style="text-align:right;">
19546792
</td>
<td style="text-align:right;">
30687.75
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
81.235
</td>
<td style="text-align:right;">
20434176
</td>
<td style="text-align:right;">
34435.37
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
69.390
</td>
<td style="text-align:right;">
1994794
</td>
<td style="text-align:right;">
10556.58
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
70.260
</td>
<td style="text-align:right;">
2229407
</td>
<td style="text-align:right;">
12247.40
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
71.240
</td>
<td style="text-align:right;">
2488550
</td>
<td style="text-align:right;">
13175.68
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.520
</td>
<td style="text-align:right;">
2728150
</td>
<td style="text-align:right;">
14463.92
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.890
</td>
<td style="text-align:right;">
2929100
</td>
<td style="text-align:right;">
16046.04
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
72.220
</td>
<td style="text-align:right;">
3164900
</td>
<td style="text-align:right;">
16233.72
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
73.840
</td>
<td style="text-align:right;">
3210650
</td>
<td style="text-align:right;">
17632.41
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.320
</td>
<td style="text-align:right;">
3317166
</td>
<td style="text-align:right;">
19007.19
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
76.330
</td>
<td style="text-align:right;">
3437674
</td>
<td style="text-align:right;">
18363.32
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.550
</td>
<td style="text-align:right;">
3676187
</td>
<td style="text-align:right;">
21050.41
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
79.110
</td>
<td style="text-align:right;">
3908037
</td>
<td style="text-align:right;">
23189.80
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
80.204
</td>
<td style="text-align:right;">
4115771
</td>
<td style="text-align:right;">
25185.01
</td>
</tr>
</tbody>
</table>
So, I'd like to reorder the countries in gapminder\_no\_oceania based on a modified metric which includes lifeeExp and gdpPercap

So, *ideal* will be the new varialbe = lifeExp/max(lifeExp)\*log(gdpPercap)/max(log(gdpPercap))

``` r
gapminder_ideal <- gapminder_no_oceania %>% 
  mutate(ideal = lifeExp/max(lifeExp)*log(gdpPercap)/max(log(gdpPercap))) %>% 
  arrange(desc(ideal))

gapminder_ideal %>% 
  kable() %>% 
  kable_styling()
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
country
</th>
<th style="text-align:left;">
continent
</th>
<th style="text-align:right;">
year
</th>
<th style="text-align:right;">
lifeExp
</th>
<th style="text-align:right;">
pop
</th>
<th style="text-align:right;">
gdpPercap
</th>
<th style="text-align:right;">
ideal
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
82.20800
</td>
<td style="text-align:right;">
6980412
</td>
<td style="text-align:right;">
39724.9787
</td>
<td style="text-align:right;">
0.9054392
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
80.19600
</td>
<td style="text-align:right;">
4627926
</td>
<td style="text-align:right;">
49357.1902
</td>
<td style="text-align:right;">
0.9013874
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
79.97200
</td>
<td style="text-align:right;">
4553009
</td>
<td style="text-align:right;">
47143.1796
</td>
<td style="text-align:right;">
0.8950523
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
81.70100
</td>
<td style="text-align:right;">
7554661
</td>
<td style="text-align:right;">
37506.4191
</td>
<td style="text-align:right;">
0.8949718
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
81.75700
</td>
<td style="text-align:right;">
301931
</td>
<td style="text-align:right;">
36180.7892
</td>
<td style="text-align:right;">
0.8925254
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
82.60300
</td>
<td style="text-align:right;">
127467972
</td>
<td style="text-align:right;">
31656.0681
</td>
<td style="text-align:right;">
0.8902833
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
80.65300
</td>
<td style="text-align:right;">
33390141
</td>
<td style="text-align:right;">
36319.2350
</td>
<td style="text-align:right;">
0.8807936
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
79.05000
</td>
<td style="text-align:right;">
4535591
</td>
<td style="text-align:right;">
44683.9753
</td>
<td style="text-align:right;">
0.8803285
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
80.88400
</td>
<td style="text-align:right;">
9031088
</td>
<td style="text-align:right;">
33859.7484
</td>
<td style="text-align:right;">
0.8774175
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
80.62000
</td>
<td style="text-align:right;">
7361757
</td>
<td style="text-align:right;">
34480.9577
</td>
<td style="text-align:right;">
0.8760780
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
82.00000
</td>
<td style="text-align:right;">
127065841
</td>
<td style="text-align:right;">
28604.5919
</td>
<td style="text-align:right;">
0.8751395
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
81.49500
</td>
<td style="text-align:right;">
6762476
</td>
<td style="text-align:right;">
30209.0152
</td>
<td style="text-align:right;">
0.8743755
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
79.76200
</td>
<td style="text-align:right;">
16570613
</td>
<td style="text-align:right;">
36797.9333
</td>
<td style="text-align:right;">
0.8721495
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
79.82900
</td>
<td style="text-align:right;">
8199783
</td>
<td style="text-align:right;">
36126.4927
</td>
<td style="text-align:right;">
0.8713531
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
78.88500
</td>
<td style="text-align:right;">
4109086
</td>
<td style="text-align:right;">
40675.9964
</td>
<td style="text-align:right;">
0.8707807
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
77.58800
</td>
<td style="text-align:right;">
2505559
</td>
<td style="text-align:right;">
47306.9898
</td>
<td style="text-align:right;">
0.8686504
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
78.24200
</td>
<td style="text-align:right;">
301139947
</td>
<td style="text-align:right;">
42951.6531
</td>
<td style="text-align:right;">
0.8681127
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
80.50000
</td>
<td style="text-align:right;">
288030
</td>
<td style="text-align:right;">
31163.2020
</td>
<td style="text-align:right;">
0.8663036
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
80.65700
</td>
<td style="text-align:right;">
61083916
</td>
<td style="text-align:right;">
30470.0167
</td>
<td style="text-align:right;">
0.8661061
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.32000
</td>
<td style="text-align:right;">
4405672
</td>
<td style="text-align:right;">
41283.1643
</td>
<td style="text-align:right;">
0.8657508
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
80.94100
</td>
<td style="text-align:right;">
40448191
</td>
<td style="text-align:right;">
28821.0637
</td>
<td style="text-align:right;">
0.8644721
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
79.77000
</td>
<td style="text-align:right;">
31902268
</td>
<td style="text-align:right;">
33328.9651
</td>
<td style="text-align:right;">
0.8640221
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
80.69000
</td>
<td style="text-align:right;">
125956499
</td>
<td style="text-align:right;">
28816.5850
</td>
<td style="text-align:right;">
0.8617783
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
79.44100
</td>
<td style="text-align:right;">
10392226
</td>
<td style="text-align:right;">
33692.6051
</td>
<td style="text-align:right;">
0.8613551
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
79.42500
</td>
<td style="text-align:right;">
60776238
</td>
<td style="text-align:right;">
33203.2613
</td>
<td style="text-align:right;">
0.8599731
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
78.77000
</td>
<td style="text-align:right;">
4197776
</td>
<td style="text-align:right;">
36023.1054
</td>
<td style="text-align:right;">
0.8595591
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
80.54600
</td>
<td style="text-align:right;">
58147733
</td>
<td style="text-align:right;">
28569.7197
</td>
<td style="text-align:right;">
0.8595196
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
79.31300
</td>
<td style="text-align:right;">
5238460
</td>
<td style="text-align:right;">
33207.0844
</td>
<td style="text-align:right;">
0.8587699
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
79.40600
</td>
<td style="text-align:right;">
82400996
</td>
<td style="text-align:right;">
32170.3744
</td>
<td style="text-align:right;">
0.8571574
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
79.37000
</td>
<td style="text-align:right;">
7193761
</td>
<td style="text-align:right;">
32135.3230
</td>
<td style="text-align:right;">
0.8566788
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
80.04000
</td>
<td style="text-align:right;">
8954175
</td>
<td style="text-align:right;">
29341.6309
</td>
<td style="text-align:right;">
0.8563393
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
80.24000
</td>
<td style="text-align:right;">
57926999
</td>
<td style="text-align:right;">
27968.0982
</td>
<td style="text-align:right;">
0.8544780
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
78.98000
</td>
<td style="text-align:right;">
8148312
</td>
<td style="text-align:right;">
32417.6077
</td>
<td style="text-align:right;">
0.8531878
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
80.00000
</td>
<td style="text-align:right;">
6495918
</td>
<td style="text-align:right;">
28377.6322
</td>
<td style="text-align:right;">
0.8531318
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
78.33200
</td>
<td style="text-align:right;">
5468120
</td>
<td style="text-align:right;">
35278.4187
</td>
<td style="text-align:right;">
0.8530777
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
80.74500
</td>
<td style="text-align:right;">
6426679
</td>
<td style="text-align:right;">
25523.2771
</td>
<td style="text-align:right;">
0.8521738
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
78.53000
</td>
<td style="text-align:right;">
16122830
</td>
<td style="text-align:right;">
33724.7578
</td>
<td style="text-align:right;">
0.8515553
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
79.59000
</td>
<td style="text-align:right;">
59925035
</td>
<td style="text-align:right;">
28926.0323
</td>
<td style="text-align:right;">
0.8503439
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
77.31000
</td>
<td style="text-align:right;">
287675526
</td>
<td style="text-align:right;">
39097.0995
</td>
<td style="text-align:right;">
0.8502115
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
79.48300
</td>
<td style="text-align:right;">
10706290
</td>
<td style="text-align:right;">
27538.4119
</td>
<td style="text-align:right;">
0.8451368
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
77.78300
</td>
<td style="text-align:right;">
3879155
</td>
<td style="text-align:right;">
34077.0494
</td>
<td style="text-align:right;">
0.8442958
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
78.67000
</td>
<td style="text-align:right;">
82350671
</td>
<td style="text-align:right;">
30035.8020
</td>
<td style="text-align:right;">
0.8435950
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
79.36000
</td>
<td style="text-align:right;">
124329269
</td>
<td style="text-align:right;">
26824.8951
</td>
<td style="text-align:right;">
0.8416622
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
78.03000
</td>
<td style="text-align:right;">
6995447
</td>
<td style="text-align:right;">
31871.5303
</td>
<td style="text-align:right;">
0.8415466
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
78.32000
</td>
<td style="text-align:right;">
10311970
</td>
<td style="text-align:right;">
30485.8838
</td>
<td style="text-align:right;">
0.8410535
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.95000
</td>
<td style="text-align:right;">
271192
</td>
<td style="text-align:right;">
28061.0997
</td>
<td style="text-align:right;">
0.8410134
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.61000
</td>
<td style="text-align:right;">
30305843
</td>
<td style="text-align:right;">
28954.9259
</td>
<td style="text-align:right;">
0.8399552
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
78.47100
</td>
<td style="text-align:right;">
59912431
</td>
<td style="text-align:right;">
29478.9992
</td>
<td style="text-align:right;">
0.8399340
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
76.15600
</td>
<td style="text-align:right;">
1765345
</td>
<td style="text-align:right;">
40300.6200
</td>
<td style="text-align:right;">
0.8399219
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
79.78000
</td>
<td style="text-align:right;">
40152517
</td>
<td style="text-align:right;">
24835.4717
</td>
<td style="text-align:right;">
0.8397226
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.32000
</td>
<td style="text-align:right;">
4286357
</td>
<td style="text-align:right;">
33965.6611
</td>
<td style="text-align:right;">
0.8390069
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
76.81000
</td>
<td style="text-align:right;">
272911760
</td>
<td style="text-align:right;">
35767.4330
</td>
<td style="text-align:right;">
0.8376020
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.03000
</td>
<td style="text-align:right;">
15604464
</td>
<td style="text-align:right;">
30246.1306
</td>
<td style="text-align:right;">
0.8372985
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
76.90400
</td>
<td style="text-align:right;">
2111561
</td>
<td style="text-align:right;">
35110.1057
</td>
<td style="text-align:right;">
0.8371434
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
78.40000
</td>
<td style="text-align:right;">
23174294
</td>
<td style="text-align:right;">
28718.2768
</td>
<td style="text-align:right;">
0.8370421
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
79.39000
</td>
<td style="text-align:right;">
8897619
</td>
<td style="text-align:right;">
25266.5950
</td>
<td style="text-align:right;">
0.8370387
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.15800
</td>
<td style="text-align:right;">
3802309
</td>
<td style="text-align:right;">
33519.4766
</td>
<td style="text-align:right;">
0.8361878
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
78.37000
</td>
<td style="text-align:right;">
5193039
</td>
<td style="text-align:right;">
28204.5906
</td>
<td style="text-align:right;">
0.8352507
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
77.18000
</td>
<td style="text-align:right;">
5374693
</td>
<td style="text-align:right;">
32166.5001
</td>
<td style="text-align:right;">
0.8331189
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.64000
</td>
<td style="text-align:right;">
58623428
</td>
<td style="text-align:right;">
25889.7849
</td>
<td style="text-align:right;">
0.8311240
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
77.41000
</td>
<td style="text-align:right;">
6649942
</td>
<td style="text-align:right;">
30281.7046
</td>
<td style="text-align:right;">
0.8307403
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
78.77000
</td>
<td style="text-align:right;">
259012
</td>
<td style="text-align:right;">
25144.3920
</td>
<td style="text-align:right;">
0.8301046
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.82000
</td>
<td style="text-align:right;">
57479469
</td>
<td style="text-align:right;">
24675.0245
</td>
<td style="text-align:right;">
0.8290868
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.51000
</td>
<td style="text-align:right;">
8069876
</td>
<td style="text-align:right;">
29095.9207
</td>
<td style="text-align:right;">
0.8285932
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
79.69600
</td>
<td style="text-align:right;">
6029529
</td>
<td style="text-align:right;">
21905.5951
</td>
<td style="text-align:right;">
0.8284333
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.95000
</td>
<td style="text-align:right;">
28523502
</td>
<td style="text-align:right;">
26342.8843
</td>
<td style="text-align:right;">
0.8252382
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.53000
</td>
<td style="text-align:right;">
10199787
</td>
<td style="text-align:right;">
27561.1966
</td>
<td style="text-align:right;">
0.8244374
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
77.92600
</td>
<td style="text-align:right;">
2009245
</td>
<td style="text-align:right;">
25768.2576
</td>
<td style="text-align:right;">
0.8231966
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.34000
</td>
<td style="text-align:right;">
82011073
</td>
<td style="text-align:right;">
27788.8842
</td>
<td style="text-align:right;">
0.8230788
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
78.62300
</td>
<td style="text-align:right;">
49044790
</td>
<td style="text-align:right;">
23348.1397
</td>
<td style="text-align:right;">
0.8224947
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.42000
</td>
<td style="text-align:right;">
15174244
</td>
<td style="text-align:right;">
26790.9496
</td>
<td style="text-align:right;">
0.8209853
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
76.09000
</td>
<td style="text-align:right;">
256894189
</td>
<td style="text-align:right;">
32003.9322
</td>
<td style="text-align:right;">
0.8209520
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
78.67000
</td>
<td style="text-align:right;">
122091325
</td>
<td style="text-align:right;">
22375.9419
</td>
<td style="text-align:right;">
0.8195064
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
78.16000
</td>
<td style="text-align:right;">
8718867
</td>
<td style="text-align:right;">
23880.0168
</td>
<td style="text-align:right;">
0.8194822
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
77.23000
</td>
<td style="text-align:right;">
244676
</td>
<td style="text-align:right;">
26923.2063
</td>
<td style="text-align:right;">
0.8193660
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
75.19000
</td>
<td style="text-align:right;">
1418095
</td>
<td style="text-align:right;">
34932.9196
</td>
<td style="text-align:right;">
0.8180899
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
75.89000
</td>
<td style="text-align:right;">
4186147
</td>
<td style="text-align:right;">
31540.9748
</td>
<td style="text-align:right;">
0.8176440
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
67.71200
</td>
<td style="text-align:right;">
841934
</td>
<td style="text-align:right;">
109347.8670
</td>
<td style="text-align:right;">
0.8170891
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.21800
</td>
<td style="text-align:right;">
58808266
</td>
<td style="text-align:right;">
26074.5314
</td>
<td style="text-align:right;">
0.8166664
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.60100
</td>
<td style="text-align:right;">
5829696
</td>
<td style="text-align:right;">
24757.6030
</td>
<td style="text-align:right;">
0.8165341
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
78.25600
</td>
<td style="text-align:right;">
10603863
</td>
<td style="text-align:right;">
22514.2548
</td>
<td style="text-align:right;">
0.8156953
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
76.11000
</td>
<td style="text-align:right;">
5283663
</td>
<td style="text-align:right;">
29804.3457
</td>
<td style="text-align:right;">
0.8155313
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.46000
</td>
<td style="text-align:right;">
57374179
</td>
<td style="text-align:right;">
24703.7961
</td>
<td style="text-align:right;">
0.8148752
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
76.86000
</td>
<td style="text-align:right;">
26549700
</td>
<td style="text-align:right;">
26626.5150
</td>
<td style="text-align:right;">
0.8145547
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.77000
</td>
<td style="text-align:right;">
39855442
</td>
<td style="text-align:right;">
20445.2990
</td>
<td style="text-align:right;">
0.8131556
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
76.21000
</td>
<td style="text-align:right;">
6468126
</td>
<td style="text-align:right;">
28397.7151
</td>
<td style="text-align:right;">
0.8127708
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
75.63500
</td>
<td style="text-align:right;">
708573
</td>
<td style="text-align:right;">
29796.0483
</td>
<td style="text-align:right;">
0.8104197
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.26900
</td>
<td style="text-align:right;">
5531387
</td>
<td style="text-align:right;">
20896.6092
</td>
<td style="text-align:right;">
0.8097611
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
77.19000
</td>
<td style="text-align:right;">
8421403
</td>
<td style="text-align:right;">
23586.9293
</td>
<td style="text-align:right;">
0.8083206
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
78.74600
</td>
<td style="text-align:right;">
3942491
</td>
<td style="text-align:right;">
19328.7090
</td>
<td style="text-align:right;">
0.8083082
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.13000
</td>
<td style="text-align:right;">
5134406
</td>
<td style="text-align:right;">
23723.9502
</td>
<td style="text-align:right;">
0.8081570
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
76.46000
</td>
<td style="text-align:right;">
10045622
</td>
<td style="text-align:right;">
25575.5707
</td>
<td style="text-align:right;">
0.8071132
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
76.04000
</td>
<td style="text-align:right;">
7914969
</td>
<td style="text-align:right;">
27042.0187
</td>
<td style="text-align:right;">
0.8070891
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
78.09800
</td>
<td style="text-align:right;">
10642836
</td>
<td style="text-align:right;">
20509.6478
</td>
<td style="text-align:right;">
0.8064737
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
76.07000
</td>
<td style="text-align:right;">
80597764
</td>
<td style="text-align:right;">
26505.3032
</td>
<td style="text-align:right;">
0.8058214
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.44000
</td>
<td style="text-align:right;">
56840847
</td>
<td style="text-align:right;">
22013.6449
</td>
<td style="text-align:right;">
0.8053787
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
76.99000
</td>
<td style="text-align:right;">
233997
</td>
<td style="text-align:right;">
23269.6075
</td>
<td style="text-align:right;">
0.8051417
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
76.99000
</td>
<td style="text-align:right;">
22454239
</td>
<td style="text-align:right;">
23235.4233
</td>
<td style="text-align:right;">
0.8050240
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
76.83000
</td>
<td style="text-align:right;">
14665278
</td>
<td style="text-align:right;">
23651.3236
</td>
<td style="text-align:right;">
0.8047686
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
75.97000
</td>
<td style="text-align:right;">
4114787
</td>
<td style="text-align:right;">
26298.6353
</td>
<td style="text-align:right;">
0.8041436
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
75.02000
</td>
<td style="text-align:right;">
242803533
</td>
<td style="text-align:right;">
29884.3504
</td>
<td style="text-align:right;">
0.8040609
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
76.12200
</td>
<td style="text-align:right;">
3667233
</td>
<td style="text-align:right;">
24521.9471
</td>
<td style="text-align:right;">
0.8002146
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
75.39000
</td>
<td style="text-align:right;">
6316424
</td>
<td style="text-align:right;">
26982.2905
</td>
<td style="text-align:right;">
0.8000166
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
76.48600
</td>
<td style="text-align:right;">
10228744
</td>
<td style="text-align:right;">
22833.3085
</td>
<td style="text-align:right;">
0.7983653
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
75.33000
</td>
<td style="text-align:right;">
5171393
</td>
<td style="text-align:right;">
26406.7399
</td>
<td style="text-align:right;">
0.7976906
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
75.78800
</td>
<td style="text-align:right;">
3235865
</td>
<td style="text-align:right;">
24769.8912
</td>
<td style="text-align:right;">
0.7974965
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
76.42000
</td>
<td style="text-align:right;">
57866349
</td>
<td style="text-align:right;">
22705.0925
</td>
<td style="text-align:right;">
0.7972288
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.86900
</td>
<td style="text-align:right;">
10502372
</td>
<td style="text-align:right;">
18747.6981
</td>
<td style="text-align:right;">
0.7968342
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
77.77800
</td>
<td style="text-align:right;">
3859606
</td>
<td style="text-align:right;">
18855.6062
</td>
<td style="text-align:right;">
0.7963673
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
77.29000
</td>
<td style="text-align:right;">
10433867
</td>
<td style="text-align:right;">
19970.9079
</td>
<td style="text-align:right;">
0.7959902
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
76.34000
</td>
<td style="text-align:right;">
55630100
</td>
<td style="text-align:right;">
22066.4421
</td>
<td style="text-align:right;">
0.7941289
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.57000
</td>
<td style="text-align:right;">
39549438
</td>
<td style="text-align:right;">
18603.0645
</td>
<td style="text-align:right;">
0.7931497
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
69.34300
</td>
<td style="text-align:right;">
1140357
</td>
<td style="text-align:right;">
59265.4771
</td>
<td style="text-align:right;">
0.7925959
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
76.66000
</td>
<td style="text-align:right;">
2011497
</td>
<td style="text-align:right;">
20660.0194
</td>
<td style="text-align:right;">
0.7922068
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
77.11000
</td>
<td style="text-align:right;">
118454974
</td>
<td style="text-align:right;">
19384.1057
</td>
<td style="text-align:right;">
0.7917446
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
75.76000
</td>
<td style="text-align:right;">
25201900
</td>
<td style="text-align:right;">
22898.7921
</td>
<td style="text-align:right;">
0.7910129
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
77.04500
</td>
<td style="text-align:right;">
47969150
</td>
<td style="text-align:right;">
19233.9882
</td>
<td style="text-align:right;">
0.7904542
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.17400
</td>
<td style="text-align:right;">
1891487
</td>
<td style="text-align:right;">
28118.4300
</td>
<td style="text-align:right;">
0.7902946
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
76.42000
</td>
<td style="text-align:right;">
8325260
</td>
<td style="text-align:right;">
20667.3812
</td>
<td style="text-align:right;">
0.7897549
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
76.05000
</td>
<td style="text-align:right;">
14310401
</td>
<td style="text-align:right;">
21399.4605
</td>
<td style="text-align:right;">
0.7886845
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
75.37000
</td>
<td style="text-align:right;">
4043205
</td>
<td style="text-align:right;">
23311.3494
</td>
<td style="text-align:right;">
0.7883406
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.80000
</td>
<td style="text-align:right;">
5127024
</td>
<td style="text-align:right;">
25116.1758
</td>
<td style="text-align:right;">
0.7881801
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
75.64000
</td>
<td style="text-align:right;">
3204897
</td>
<td style="text-align:right;">
22316.1929
</td>
<td style="text-align:right;">
0.7877325
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.84700
</td>
<td style="text-align:right;">
77718298
</td>
<td style="text-align:right;">
24639.1857
</td>
<td style="text-align:right;">
0.7871827
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.65000
</td>
<td style="text-align:right;">
232187835
</td>
<td style="text-align:right;">
25009.5591
</td>
<td style="text-align:right;">
0.7862692
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
75.35000
</td>
<td style="text-align:right;">
9870200
</td>
<td style="text-align:right;">
22525.5631
</td>
<td style="text-align:right;">
0.7854442
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.94000
</td>
<td style="text-align:right;">
7578903
</td>
<td style="text-align:right;">
23687.8261
</td>
<td style="text-align:right;">
0.7850917
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
76.20000
</td>
<td style="text-align:right;">
5584510
</td>
<td style="text-align:right;">
20038.4727
</td>
<td style="text-align:right;">
0.7850322
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
76.93000
</td>
<td style="text-align:right;">
4936550
</td>
<td style="text-align:right;">
18051.5225
</td>
<td style="text-align:right;">
0.7841977
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
76.42000
</td>
<td style="text-align:right;">
56729703
</td>
<td style="text-align:right;">
19207.2348
</td>
<td style="text-align:right;">
0.7839313
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
73.78000
</td>
<td style="text-align:right;">
6401400
</td>
<td style="text-align:right;">
27195.1130
</td>
<td style="text-align:right;">
0.7835346
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.03000
</td>
<td style="text-align:right;">
10325429
</td>
<td style="text-align:right;">
17541.4963
</td>
<td style="text-align:right;">
0.7829209
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
74.79500
</td>
<td style="text-align:right;">
656397
</td>
<td style="text-align:right;">
23403.5593
</td>
<td style="text-align:right;">
0.7826334
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
76.11000
</td>
<td style="text-align:right;">
221823
</td>
<td style="text-align:right;">
19654.9625
</td>
<td style="text-align:right;">
0.7825753
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
75.70000
</td>
<td style="text-align:right;">
5041039
</td>
<td style="text-align:right;">
20647.1650
</td>
<td style="text-align:right;">
0.7822371
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
75.24000
</td>
<td style="text-align:right;">
13852989
</td>
<td style="text-align:right;">
21209.0592
</td>
<td style="text-align:right;">
0.7795849
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
75.00700
</td>
<td style="text-align:right;">
56981620
</td>
<td style="text-align:right;">
21664.7877
</td>
<td style="text-align:right;">
0.7788292
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
75.25000
</td>
<td style="text-align:right;">
21628605
</td>
<td style="text-align:right;">
20206.8210
</td>
<td style="text-align:right;">
0.7758998
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.83000
</td>
<td style="text-align:right;">
4931729
</td>
<td style="text-align:right;">
21141.0122
</td>
<td style="text-align:right;">
0.7750867
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.63000
</td>
<td style="text-align:right;">
5117810
</td>
<td style="text-align:right;">
21688.0405
</td>
<td style="text-align:right;">
0.7749979
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
78.55300
</td>
<td style="text-align:right;">
16284741
</td>
<td style="text-align:right;">
13171.6388
</td>
<td style="text-align:right;">
0.7749930
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
76.90000
</td>
<td style="text-align:right;">
38880702
</td>
<td style="text-align:right;">
15764.9831
</td>
<td style="text-align:right;">
0.7730593
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
75.97000
</td>
<td style="text-align:right;">
10156415
</td>
<td style="text-align:right;">
17641.0316
</td>
<td style="text-align:right;">
0.7725943
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
76.67000
</td>
<td style="text-align:right;">
9974490
</td>
<td style="text-align:right;">
16120.5284
</td>
<td style="text-align:right;">
0.7725256
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.89000
</td>
<td style="text-align:right;">
54433565
</td>
<td style="text-align:right;">
20293.8975
</td>
<td style="text-align:right;">
0.7725228
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
75.44000
</td>
<td style="text-align:right;">
8251648
</td>
<td style="text-align:right;">
18855.7252
</td>
<td style="text-align:right;">
0.7724290
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
74.21000
</td>
<td style="text-align:right;">
23796400
</td>
<td style="text-align:right;">
22090.8831
</td>
<td style="text-align:right;">
0.7720569
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
74.69000
</td>
<td style="text-align:right;">
5088419
</td>
<td style="text-align:right;">
20422.9015
</td>
<td style="text-align:right;">
0.7709520
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.38000
</td>
<td style="text-align:right;">
220239000
</td>
<td style="text-align:right;">
24072.6321
</td>
<td style="text-align:right;">
0.7699786
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
71.30900
</td>
<td style="text-align:right;">
1497494
</td>
<td style="text-align:right;">
31354.0357
</td>
<td style="text-align:right;">
0.7678471
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
75.51000
</td>
<td style="text-align:right;">
10256295
</td>
<td style="text-align:right;">
17596.2102
</td>
<td style="text-align:right;">
0.7677164
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
73.80000
</td>
<td style="text-align:right;">
78335266
</td>
<td style="text-align:right;">
22031.5327
</td>
<td style="text-align:right;">
0.7675849
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
75.46700
</td>
<td style="text-align:right;">
3557761
</td>
<td style="text-align:right;">
17558.8155
</td>
<td style="text-align:right;">
0.7671122
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
75.60000
</td>
<td style="text-align:right;">
4203148
</td>
<td style="text-align:right;">
17122.4799
</td>
<td style="text-align:right;">
0.7664855
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
73.93000
</td>
<td style="text-align:right;">
9856303
</td>
<td style="text-align:right;">
20979.8459
</td>
<td style="text-align:right;">
0.7651761
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
74.66300
</td>
<td style="text-align:right;">
5447502
</td>
<td style="text-align:right;">
18678.3144
</td>
<td style="text-align:right;">
0.7637393
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
74.19300
</td>
<td style="text-align:right;">
2713462
</td>
<td style="text-align:right;">
19774.8369
</td>
<td style="text-align:right;">
0.7633336
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
73.92500
</td>
<td style="text-align:right;">
598561
</td>
<td style="text-align:right;">
20292.0168
</td>
<td style="text-align:right;">
0.7625613
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.55000
</td>
<td style="text-align:right;">
4826933
</td>
<td style="text-align:right;">
18533.1576
</td>
<td style="text-align:right;">
0.7619784
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
75.13000
</td>
<td style="text-align:right;">
2011612
</td>
<td style="text-align:right;">
17161.1073
</td>
<td style="text-align:right;">
0.7618964
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
75.38000
</td>
<td style="text-align:right;">
113872473
</td>
<td style="text-align:right;">
16610.3770
</td>
<td style="text-align:right;">
0.7618744
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
74.34000
</td>
<td style="text-align:right;">
3933004
</td>
<td style="text-align:right;">
18965.0555
</td>
<td style="text-align:right;">
0.7616132
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
74.72000
</td>
<td style="text-align:right;">
8122293
</td>
<td style="text-align:right;">
17832.0246
</td>
<td style="text-align:right;">
0.7607190
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
72.77000
</td>
<td style="text-align:right;">
6063000
</td>
<td style="text-align:right;">
22966.1443
</td>
<td style="text-align:right;">
0.7600165
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
73.18000
</td>
<td style="text-align:right;">
7574613
</td>
<td style="text-align:right;">
21597.0836
</td>
<td style="text-align:right;">
0.7596205
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
64.62400
</td>
<td style="text-align:right;">
575003
</td>
<td style="text-align:right;">
80894.8833
</td>
<td style="text-align:right;">
0.7595689
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
74.91700
</td>
<td style="text-align:right;">
3759430
</td>
<td style="text-align:right;">
16999.4333
</td>
<td style="text-align:right;">
0.7589989
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
75.56300
</td>
<td style="text-align:right;">
38518241
</td>
<td style="text-align:right;">
15389.9247
</td>
<td style="text-align:right;">
0.7577265
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.98000
</td>
<td style="text-align:right;">
56535636
</td>
<td style="text-align:right;">
16537.4835
</td>
<td style="text-align:right;">
0.7574886
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
76.30000
</td>
<td style="text-align:right;">
37983310
</td>
<td style="text-align:right;">
13926.1700
</td>
<td style="text-align:right;">
0.7571857
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.77700
</td>
<td style="text-align:right;">
27601038
</td>
<td style="text-align:right;">
21654.8319
</td>
<td style="text-align:right;">
0.7556394
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
75.74800
</td>
<td style="text-align:right;">
4493312
</td>
<td style="text-align:right;">
14619.2227
</td>
<td style="text-align:right;">
0.7555341
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.04000
</td>
<td style="text-align:right;">
56339704
</td>
<td style="text-align:right;">
18232.4245
</td>
<td style="text-align:right;">
0.7555059
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
73.75000
</td>
<td style="text-align:right;">
13329874
</td>
<td style="text-align:right;">
18794.7457
</td>
<td style="text-align:right;">
0.7548767
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
74.86000
</td>
<td style="text-align:right;">
9927680
</td>
<td style="text-align:right;">
16207.2666
</td>
<td style="text-align:right;">
0.7547059
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
75.24000
</td>
<td style="text-align:right;">
9786480
</td>
<td style="text-align:right;">
15268.4209
</td>
<td style="text-align:right;">
0.7538672
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.83000
</td>
<td style="text-align:right;">
53165019
</td>
<td style="text-align:right;">
18292.6351
</td>
<td style="text-align:right;">
0.7536162
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
73.56000
</td>
<td style="text-align:right;">
2794552
</td>
<td style="text-align:right;">
18861.5308
</td>
<td style="text-align:right;">
0.7532033
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
73.47000
</td>
<td style="text-align:right;">
4991596
</td>
<td style="text-align:right;">
18866.2072
</td>
<td style="text-align:right;">
0.7523007
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
75.45000
</td>
<td style="text-align:right;">
5264500
</td>
<td style="text-align:right;">
14560.5305
</td>
<td style="text-align:right;">
0.7522460
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
77.86000
</td>
<td style="text-align:right;">
15497046
</td>
<td style="text-align:right;">
10778.7838
</td>
<td style="text-align:right;">
0.7519207
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
78.78200
</td>
<td style="text-align:right;">
4133884
</td>
<td style="text-align:right;">
9645.0614
</td>
<td style="text-align:right;">
0.7517187
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
74.64700
</td>
<td style="text-align:right;">
46173816
</td>
<td style="text-align:right;">
15993.5280
</td>
<td style="text-align:right;">
0.7515279
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
74.46000
</td>
<td style="text-align:right;">
209275
</td>
<td style="text-align:right;">
15798.0636
</td>
<td style="text-align:right;">
0.7486929
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
72.50000
</td>
<td style="text-align:right;">
78160773
</td>
<td style="text-align:right;">
20512.9212
</td>
<td style="text-align:right;">
0.7486784
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
74.08000
</td>
<td style="text-align:right;">
3786019
</td>
<td style="text-align:right;">
16361.8765
</td>
<td style="text-align:right;">
0.7475738
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
73.33800
</td>
<td style="text-align:right;">
9956108
</td>
<td style="text-align:right;">
18008.9444
</td>
<td style="text-align:right;">
0.7474020
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
72.88000
</td>
<td style="text-align:right;">
22284500
</td>
<td style="text-align:right;">
18970.5709
</td>
<td style="text-align:right;">
0.7466775
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.45000
</td>
<td style="text-align:right;">
3858421
</td>
<td style="text-align:right;">
15367.0292
</td>
<td style="text-align:right;">
0.7464503
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
72.80000
</td>
<td style="text-align:right;">
9821800
</td>
<td style="text-align:right;">
19117.9745
</td>
<td style="text-align:right;">
0.7464440
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
72.49900
</td>
<td style="text-align:right;">
2283635
</td>
<td style="text-align:right;">
19702.0558
</td>
<td style="text-align:right;">
0.7456269
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
74.01000
</td>
<td style="text-align:right;">
10300707
</td>
<td style="text-align:right;">
16048.5142
</td>
<td style="text-align:right;">
0.7453789
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
76.19500
</td>
<td style="text-align:right;">
108700891
</td>
<td style="text-align:right;">
11977.5750
</td>
<td style="text-align:right;">
0.7441984
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
72.60100
</td>
<td style="text-align:right;">
529491
</td>
<td style="text-align:right;">
19035.5792
</td>
<td style="text-align:right;">
0.7440774
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
74.26000
</td>
<td style="text-align:right;">
20686918
</td>
<td style="text-align:right;">
15215.6579
</td>
<td style="text-align:right;">
0.7437808
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
74.16000
</td>
<td style="text-align:right;">
7867931
</td>
<td style="text-align:right;">
15258.2970
</td>
<td style="text-align:right;">
0.7429950
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
72.17000
</td>
<td style="text-align:right;">
7568430
</td>
<td style="text-align:right;">
19749.4223
</td>
<td style="text-align:right;">
0.7424235
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.34000
</td>
<td style="text-align:right;">
209896000
</td>
<td style="text-align:right;">
21806.0359
</td>
<td style="text-align:right;">
0.7412354
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
78.27300
</td>
<td style="text-align:right;">
11416987
</td>
<td style="text-align:right;">
8948.1029
</td>
<td style="text-align:right;">
0.7407559
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
75.32000
</td>
<td style="text-align:right;">
40301927
</td>
<td style="text-align:right;">
12779.3796
</td>
<td style="text-align:right;">
0.7407283
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
73.82000
</td>
<td style="text-align:right;">
12596822
</td>
<td style="text-align:right;">
15363.2514
</td>
<td style="text-align:right;">
0.7401149
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
72.25000
</td>
<td style="text-align:right;">
1945870
</td>
<td style="text-align:right;">
18678.5349
</td>
<td style="text-align:right;">
0.7390572
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
72.76000
</td>
<td style="text-align:right;">
56179000
</td>
<td style="text-align:right;">
17428.7485
</td>
<td style="text-align:right;">
0.7390333
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.36000
</td>
<td style="text-align:right;">
3539900
</td>
<td style="text-align:right;">
13872.8665
</td>
<td style="text-align:right;">
0.7376370
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
73.91100
</td>
<td style="text-align:right;">
3585176
</td>
<td style="text-align:right;">
14641.5871
</td>
<td style="text-align:right;">
0.7373288
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
76.38400
</td>
<td style="text-align:right;">
3447496
</td>
<td style="text-align:right;">
10611.4630
</td>
<td style="text-align:right;">
0.7364236
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
71.32000
</td>
<td style="text-align:right;">
5666000
</td>
<td style="text-align:right;">
20431.0927
</td>
<td style="text-align:right;">
0.7361965
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
74.39000
</td>
<td style="text-align:right;">
36439000
</td>
<td style="text-align:right;">
13236.9212
</td>
<td style="text-align:right;">
0.7343040
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
72.96000
</td>
<td style="text-align:right;">
4838800
</td>
<td style="text-align:right;">
15937.2112
</td>
<td style="text-align:right;">
0.7342759
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
71.62600
</td>
<td style="text-align:right;">
24501530
</td>
<td style="text-align:right;">
19014.5412
</td>
<td style="text-align:right;">
0.7340024
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
73.42000
</td>
<td style="text-align:right;">
107188273
</td>
<td style="text-align:right;">
14778.7864
</td>
<td style="text-align:right;">
0.7331428
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.68000
</td>
<td style="text-align:right;">
9308479
</td>
<td style="text-align:right;">
14195.5243
</td>
<td style="text-align:right;">
0.7326534
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
73.64000
</td>
<td style="text-align:right;">
1999210
</td>
<td style="text-align:right;">
14214.7168
</td>
<td style="text-align:right;">
0.7323591
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.48000
</td>
<td style="text-align:right;">
56059245
</td>
<td style="text-align:right;">
14255.9847
</td>
<td style="text-align:right;">
0.7309895
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.63000
</td>
<td style="text-align:right;">
3444468
</td>
<td style="text-align:right;">
12281.3419
</td>
<td style="text-align:right;">
0.7308570
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
73.80000
</td>
<td style="text-align:right;">
5410052
</td>
<td style="text-align:right;">
13638.7784
</td>
<td style="text-align:right;">
0.7307756
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.06000
</td>
<td style="text-align:right;">
9915289
</td>
<td style="text-align:right;">
13039.3088
</td>
<td style="text-align:right;">
0.7298879
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.86500
</td>
<td style="text-align:right;">
569473
</td>
<td style="text-align:right;">
11732.5102
</td>
<td style="text-align:right;">
0.7295986
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
74.67000
</td>
<td style="text-align:right;">
38625976
</td>
<td style="text-align:right;">
12002.2391
</td>
<td style="text-align:right;">
0.7294635
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
72.38000
</td>
<td style="text-align:right;">
51732000
</td>
<td style="text-align:right;">
16107.1917
</td>
<td style="text-align:right;">
0.7292374
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
74.87600
</td>
<td style="text-align:right;">
4481020
</td>
<td style="text-align:right;">
11628.3890
</td>
<td style="text-align:right;">
0.7290116
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
70.53300
</td>
<td style="text-align:right;">
21229759
</td>
<td style="text-align:right;">
20586.6902
</td>
<td style="text-align:right;">
0.7286293
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
73.73000
</td>
<td style="text-align:right;">
198676
</td>
<td style="text-align:right;">
13319.8957
</td>
<td style="text-align:right;">
0.7282683
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
72.52000
</td>
<td style="text-align:right;">
4738902
</td>
<td style="text-align:right;">
15605.4228
</td>
<td style="text-align:right;">
0.7282609
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
74.24100
</td>
<td style="text-align:right;">
24821286
</td>
<td style="text-align:right;">
12451.6558
</td>
<td style="text-align:right;">
0.7281110
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
71.19700
</td>
<td style="text-align:right;">
1915208
</td>
<td style="text-align:right;">
18616.7069
</td>
<td style="text-align:right;">
0.7280404
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
78.12300
</td>
<td style="text-align:right;">
3834934
</td>
<td style="text-align:right;">
7723.4472
</td>
<td style="text-align:right;">
0.7273775
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
75.81600
</td>
<td style="text-align:right;">
14599929
</td>
<td style="text-align:right;">
10118.0532
</td>
<td style="text-align:right;">
0.7271930
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
70.76000
</td>
<td style="text-align:right;">
198712000
</td>
<td style="text-align:right;">
19530.3656
</td>
<td style="text-align:right;">
0.7270977
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
72.13000
</td>
<td style="text-align:right;">
20819767
</td>
<td style="text-align:right;">
16076.5880
</td>
<td style="text-align:right;">
0.7265759
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
73.47000
</td>
<td style="text-align:right;">
3638919
</td>
<td style="text-align:right;">
13450.4015
</td>
<td style="text-align:right;">
0.7264452
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
72.59000
</td>
<td style="text-align:right;">
10083313
</td>
<td style="text-align:right;">
14843.9356
</td>
<td style="text-align:right;">
0.7251869
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
72.01000
</td>
<td style="text-align:right;">
56079000
</td>
<td style="text-align:right;">
15895.1164
</td>
<td style="text-align:right;">
0.7245169
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
68.76800
</td>
<td style="text-align:right;">
16945857
</td>
<td style="text-align:right;">
24841.6178
</td>
<td style="text-align:right;">
0.7238337
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
71.06300
</td>
<td style="text-align:right;">
1861252
</td>
<td style="text-align:right;">
17866.7218
</td>
<td style="text-align:right;">
0.7236310
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.00000
</td>
<td style="text-align:right;">
78717088
</td>
<td style="text-align:right;">
18016.1803
</td>
<td style="text-align:right;">
0.7236046
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
70.75000
</td>
<td style="text-align:right;">
454612
</td>
<td style="text-align:right;">
18524.0241
</td>
<td style="text-align:right;">
0.7231022
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
74.90200
</td>
<td style="text-align:right;">
102479927
</td>
<td style="text-align:right;">
10742.4405
</td>
<td style="text-align:right;">
0.7230912
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
73.95200
</td>
<td style="text-align:right;">
6036914
</td>
<td style="text-align:right;">
12057.4993
</td>
<td style="text-align:right;">
0.7228025
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.44000
</td>
<td style="text-align:right;">
9709100
</td>
<td style="text-align:right;">
16672.1436
</td>
<td style="text-align:right;">
0.7223282
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
71.58000
</td>
<td style="text-align:right;">
10311597
</td>
<td style="text-align:right;">
16310.4434
</td>
<td style="text-align:right;">
0.7221108
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
75.53700
</td>
<td style="text-align:right;">
3242173
</td>
<td style="text-align:right;">
9809.1856
</td>
<td style="text-align:right;">
0.7220813
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.06000
</td>
<td style="text-align:right;">
3495918
</td>
<td style="text-align:right;">
13306.6192
</td>
<td style="text-align:right;">
0.7215746
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
60.47000
</td>
<td style="text-align:right;">
358266
</td>
<td style="text-align:right;">
95458.1118
</td>
<td style="text-align:right;">
0.7211552
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
72.40000
</td>
<td style="text-align:right;">
10315702
</td>
<td style="text-align:right;">
14297.0212
</td>
<td style="text-align:right;">
0.7204619
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
73.23000
</td>
<td style="text-align:right;">
11805689
</td>
<td style="text-align:right;">
12790.8496
</td>
<td style="text-align:right;">
0.7202427
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
73.37000
</td>
<td style="text-align:right;">
7561588
</td>
<td style="text-align:right;">
12329.4419
</td>
<td style="text-align:right;">
0.7188160
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.10100
</td>
<td style="text-align:right;">
562548
</td>
<td style="text-align:right;">
11222.5876
</td>
<td style="text-align:right;">
0.7187285
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
70.56000
</td>
<td style="text-align:right;">
5126000
</td>
<td style="text-align:right;">
17909.4897
</td>
<td style="text-align:right;">
0.7186844
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
71.76000
</td>
<td style="text-align:right;">
2651869
</td>
<td style="text-align:right;">
15169.1611
</td>
<td style="text-align:right;">
0.7185126
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
73.10000
</td>
<td style="text-align:right;">
3480000
</td>
<td style="text-align:right;">
12618.3214
</td>
<td style="text-align:right;">
0.7179316
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
73.74700
</td>
<td style="text-align:right;">
26084662
</td>
<td style="text-align:right;">
11415.8057
</td>
<td style="text-align:right;">
0.7166042
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
71.21800
</td>
<td style="text-align:right;">
9230783
</td>
<td style="text-align:right;">
15870.8785
</td>
<td style="text-align:right;">
0.7164353
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
72.35000
</td>
<td style="text-align:right;">
4646899
</td>
<td style="text-align:right;">
13583.3135
</td>
<td style="text-align:right;">
0.7161109
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
73.44000
</td>
<td style="text-align:right;">
3491938
</td>
<td style="text-align:right;">
11653.9730
</td>
<td style="text-align:right;">
0.7151982
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
70.63000
</td>
<td style="text-align:right;">
7544201
</td>
<td style="text-align:right;">
16661.6256
</td>
<td style="text-align:right;">
0.7140919
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.60000
</td>
<td style="text-align:right;">
4583700
</td>
<td style="text-align:right;">
11186.1413
</td>
<td style="text-align:right;">
0.7136201
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
69.81900
</td>
<td style="text-align:right;">
1056608
</td>
<td style="text-align:right;">
18008.5092
</td>
<td style="text-align:right;">
0.7115374
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
70.96000
</td>
<td style="text-align:right;">
10303704
</td>
<td style="text-align:right;">
15377.2285
</td>
<td style="text-align:right;">
0.7115078
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
76.44200
</td>
<td style="text-align:right;">
798094
</td>
<td style="text-align:right;">
7670.1226
</td>
<td style="text-align:right;">
0.7111754
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.97000
</td>
<td style="text-align:right;">
1746919
</td>
<td style="text-align:right;">
15277.0302
</td>
<td style="text-align:right;">
0.7111256
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
72.34000
</td>
<td style="text-align:right;">
8888628
</td>
<td style="text-align:right;">
12724.8296
</td>
<td style="text-align:right;">
0.7110999
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
72.71000
</td>
<td style="text-align:right;">
5383010
</td>
<td style="text-align:right;">
12126.2306
</td>
<td style="text-align:right;">
0.7110931
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
73.40000
</td>
<td style="text-align:right;">
19757799
</td>
<td style="text-align:right;">
11054.5618
</td>
<td style="text-align:right;">
0.7107776
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
72.77000
</td>
<td style="text-align:right;">
9859650
</td>
<td style="text-align:right;">
11753.8429
</td>
<td style="text-align:right;">
0.7093193
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.36000
</td>
<td style="text-align:right;">
54959000
</td>
<td style="text-align:right;">
14142.8509
</td>
<td style="text-align:right;">
0.7093081
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
71.52000
</td>
<td style="text-align:right;">
4484310
</td>
<td style="text-align:right;">
13822.5839
</td>
<td style="text-align:right;">
0.7091946
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
73.75000
</td>
<td style="text-align:right;">
3279001
</td>
<td style="text-align:right;">
10330.9891
</td>
<td style="text-align:right;">
0.7089743
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
73.27500
</td>
<td style="text-align:right;">
36203463
</td>
<td style="text-align:right;">
10967.2820
</td>
<td style="text-align:right;">
0.7089631
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
73.68000
</td>
<td style="text-align:right;">
182053
</td>
<td style="text-align:right;">
10350.1591
</td>
<td style="text-align:right;">
0.7084435
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
69.05200
</td>
<td style="text-align:right;">
377967
</td>
<td style="text-align:right;">
19211.1473
</td>
<td style="text-align:right;">
0.7083636
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
72.99000
</td>
<td style="text-align:right;">
11026383
</td>
<td style="text-align:right;">
11276.1934
</td>
<td style="text-align:right;">
0.7083143
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
74.54300
</td>
<td style="text-align:right;">
684736
</td>
<td style="text-align:right;">
9253.8961
</td>
<td style="text-align:right;">
0.7080614
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
70.21000
</td>
<td style="text-align:right;">
186538000
</td>
<td style="text-align:right;">
16173.1459
</td>
<td style="text-align:right;">
0.7076727
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.26000
</td>
<td style="text-align:right;">
3518107
</td>
<td style="text-align:right;">
6677.0453
</td>
<td style="text-align:right;">
0.7076438
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
74.00200
</td>
<td style="text-align:right;">
10150265
</td>
<td style="text-align:right;">
9786.5347
</td>
<td style="text-align:right;">
0.7072298
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
72.19000
</td>
<td style="text-align:right;">
54365564
</td>
<td style="text-align:right;">
12269.2738
</td>
<td style="text-align:right;">
0.7068881
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
70.80000
</td>
<td style="text-align:right;">
76368453
</td>
<td style="text-align:right;">
14745.6256
</td>
<td style="text-align:right;">
0.7068151
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
72.24400
</td>
<td style="text-align:right;">
43805450
</td>
<td style="text-align:right;">
12104.2787
</td>
<td style="text-align:right;">
0.7063996
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.71000
</td>
<td style="text-align:right;">
10161915
</td>
<td style="text-align:right;">
14800.1606
</td>
<td style="text-align:right;">
0.7061881
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
70.87000
</td>
<td style="text-align:right;">
4639657
</td>
<td style="text-align:right;">
14358.8759
</td>
<td style="text-align:right;">
0.7055549
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
71.30000
</td>
<td style="text-align:right;">
18985849
</td>
<td style="text-align:right;">
13462.4855
</td>
<td style="text-align:right;">
0.7050556
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.55000
</td>
<td style="text-align:right;">
49569000
</td>
<td style="text-align:right;">
12999.9177
</td>
<td style="text-align:right;">
0.7049258
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
73.68000
</td>
<td style="text-align:right;">
4444595
</td>
<td style="text-align:right;">
9875.6045
</td>
<td style="text-align:right;">
0.7048468
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
74.22300
</td>
<td style="text-align:right;">
3262838
</td>
<td style="text-align:right;">
9230.2407
</td>
<td style="text-align:right;">
0.7048242
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
73.06000
</td>
<td style="text-align:right;">
34513161
</td>
<td style="text-align:right;">
10638.7513
</td>
<td style="text-align:right;">
0.7045718
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.63000
</td>
<td style="text-align:right;">
3095893
</td>
<td style="text-align:right;">
12786.9322
</td>
<td style="text-align:right;">
0.7044833
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
73.00500
</td>
<td style="text-align:right;">
7322858
</td>
<td style="text-align:right;">
10680.7928
</td>
<td style="text-align:right;">
0.7043409
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.80100
</td>
<td style="text-align:right;">
1250882
</td>
<td style="text-align:right;">
10956.9911
</td>
<td style="text-align:right;">
0.7043059
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
73.67000
</td>
<td style="text-align:right;">
95895146
</td>
<td style="text-align:right;">
9767.2975
</td>
<td style="text-align:right;">
0.7039062
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
70.16200
</td>
<td style="text-align:right;">
9032824
</td>
<td style="text-align:right;">
15181.0927
</td>
<td style="text-align:right;">
0.7025696
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
77.15800
</td>
<td style="text-align:right;">
11226999
</td>
<td style="text-align:right;">
6340.6467
</td>
<td style="text-align:right;">
0.7025611
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
58.03300
</td>
<td style="text-align:right;">
212846
</td>
<td style="text-align:right;">
113523.1329
</td>
<td style="text-align:right;">
0.7025532
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
74.34000
</td>
<td style="text-align:right;">
38331121
</td>
<td style="text-align:right;">
8797.6407
</td>
<td style="text-align:right;">
0.7022238
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.44000
</td>
<td style="text-align:right;">
3080828
</td>
<td style="text-align:right;">
9770.5249
</td>
<td style="text-align:right;">
0.7017338
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
73.04400
</td>
<td style="text-align:right;">
22662365
</td>
<td style="text-align:right;">
10206.9779
</td>
<td style="text-align:right;">
0.7012700
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
75.30700
</td>
<td style="text-align:right;">
3363085
</td>
<td style="text-align:right;">
7727.0020
</td>
<td style="text-align:right;">
0.7011947
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.47600
</td>
<td style="text-align:right;">
22276056
</td>
<td style="text-align:right;">
10808.4756
</td>
<td style="text-align:right;">
0.7001330
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
70.94000
</td>
<td style="text-align:right;">
9556500
</td>
<td style="text-align:right;">
13149.0412
</td>
<td style="text-align:right;">
0.6997575
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
72.03000
</td>
<td style="text-align:right;">
3271900
</td>
<td style="text-align:right;">
11150.9811
</td>
<td style="text-align:right;">
0.6981616
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
72.75000
</td>
<td style="text-align:right;">
38654957
</td>
<td style="text-align:right;">
10159.5837
</td>
<td style="text-align:right;">
0.6980952
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
73.47000
</td>
<td style="text-align:right;">
165110
</td>
<td style="text-align:right;">
9244.0014
</td>
<td style="text-align:right;">
0.6977875
</td>
</tr>
<tr>
<td style="text-align:left;">
Norway
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
72.67000
</td>
<td style="text-align:right;">
3327728
</td>
<td style="text-align:right;">
10095.4217
</td>
<td style="text-align:right;">
0.6968487
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.06600
</td>
<td style="text-align:right;">
560073
</td>
<td style="text-align:right;">
9595.9299
</td>
<td style="text-align:right;">
0.6967899
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
71.81000
</td>
<td style="text-align:right;">
4487831
</td>
<td style="text-align:right;">
11099.6593
</td>
<td style="text-align:right;">
0.6956847
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
70.46000
</td>
<td style="text-align:right;">
4413368
</td>
<td style="text-align:right;">
13221.8218
</td>
<td style="text-align:right;">
0.6954273
</td>
</tr>
<tr>
<td style="text-align:left;">
Switzerland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
69.62000
</td>
<td style="text-align:right;">
4815000
</td>
<td style="text-align:right;">
14734.2327
</td>
<td style="text-align:right;">
0.6949789
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
75.43500
</td>
<td style="text-align:right;">
621621
</td>
<td style="text-align:right;">
7003.3390
</td>
<td style="text-align:right;">
0.6946715
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
71.08000
</td>
<td style="text-align:right;">
5199318
</td>
<td style="text-align:right;">
12037.2676
</td>
<td style="text-align:right;">
0.6946076
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
69.49000
</td>
<td style="text-align:right;">
171984000
</td>
<td style="text-align:right;">
14847.1271
</td>
<td style="text-align:right;">
0.6942328
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
70.76000
</td>
<td style="text-align:right;">
53292000
</td>
<td style="text-align:right;">
12477.1771
</td>
<td style="text-align:right;">
0.6941221
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
74.85200
</td>
<td style="text-align:right;">
4552198
</td>
<td style="text-align:right;">
7446.2988
</td>
<td style="text-align:right;">
0.6940773
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
72.49000
</td>
<td style="text-align:right;">
7363802
</td>
<td style="text-align:right;">
9911.8782
</td>
<td style="text-align:right;">
0.6937393
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
72.73700
</td>
<td style="text-align:right;">
5368585
</td>
<td style="text-align:right;">
9534.6775
</td>
<td style="text-align:right;">
0.6931680
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
70.29000
</td>
<td style="text-align:right;">
9862158
</td>
<td style="text-align:right;">
13108.4536
</td>
<td style="text-align:right;">
0.6931199
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
71.99300
</td>
<td style="text-align:right;">
3921278
</td>
<td style="text-align:right;">
10461.0587
</td>
<td style="text-align:right;">
0.6930208
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.30000
</td>
<td style="text-align:right;">
8686367
</td>
<td style="text-align:right;">
12980.6696
</td>
<td style="text-align:right;">
0.6925022
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
72.14600
</td>
<td style="text-align:right;">
22374398
</td>
<td style="text-align:right;">
10165.4952
</td>
<td style="text-align:right;">
0.6923430
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
71.04000
</td>
<td style="text-align:right;">
10244684
</td>
<td style="text-align:right;">
11712.7768
</td>
<td style="text-align:right;">
0.6921976
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
70.30000
</td>
<td style="text-align:right;">
73739117
</td>
<td style="text-align:right;">
12902.4629
</td>
<td style="text-align:right;">
0.6920604
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
74.71200
</td>
<td style="text-align:right;">
2990875
</td>
<td style="text-align:right;">
7356.0319
</td>
<td style="text-align:right;">
0.6918314
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
70.96400
</td>
<td style="text-align:right;">
69453570
</td>
<td style="text-align:right;">
11605.7145
</td>
<td style="text-align:right;">
0.6907794
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
67.73400
</td>
<td style="text-align:right;">
1593882
</td>
<td style="text-align:right;">
18115.2231
</td>
<td style="text-align:right;">
0.6907050
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
76.42300
</td>
<td style="text-align:right;">
3600523
</td>
<td style="text-align:right;">
5937.0295
</td>
<td style="text-align:right;">
0.6906407
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
71.93800
</td>
<td style="text-align:right;">
20476091
</td>
<td style="text-align:right;">
10132.9096
</td>
<td style="text-align:right;">
0.6901067
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
70.14000
</td>
<td style="text-align:right;">
7376998
</td>
<td style="text-align:right;">
12834.6024
</td>
<td style="text-align:right;">
0.6901006
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
75.74400
</td>
<td style="text-align:right;">
743981
</td>
<td style="text-align:right;">
6316.1652
</td>
<td style="text-align:right;">
0.6893812
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
74.99400
</td>
<td style="text-align:right;">
13755680
</td>
<td style="text-align:right;">
6873.2623
</td>
<td style="text-align:right;">
0.6891480
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
74.12600
</td>
<td style="text-align:right;">
13572994
</td>
<td style="text-align:right;">
7596.1260
</td>
<td style="text-align:right;">
0.6888812
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.17400
</td>
<td style="text-align:right;">
10239839
</td>
<td style="text-align:right;">
7532.9248
</td>
<td style="text-align:right;">
0.6886827
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
75.44500
</td>
<td style="text-align:right;">
692651
</td>
<td style="text-align:right;">
6465.6133
</td>
<td style="text-align:right;">
0.6884949
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
70.80000
</td>
<td style="text-align:right;">
5048043
</td>
<td style="text-align:right;">
11348.5459
</td>
<td style="text-align:right;">
0.6875329
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
75.71300
</td>
<td style="text-align:right;">
3173216
</td>
<td style="text-align:right;">
6160.4163
</td>
<td style="text-align:right;">
0.6871329
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
66.29500
</td>
<td style="text-align:right;">
14619745
</td>
<td style="text-align:right;">
21198.2614
</td>
<td style="text-align:right;">
0.6868679
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
71.15000
</td>
<td style="text-align:right;">
20265563
</td>
<td style="text-align:right;">
10733.9263
</td>
<td style="text-align:right;">
0.6868114
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.79500
</td>
<td style="text-align:right;">
2325300
</td>
<td style="text-align:right;">
11210.0895
</td>
<td style="text-align:right;">
0.6865805
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
69.96000
</td>
<td style="text-align:right;">
17010154
</td>
<td style="text-align:right;">
12489.9501
</td>
<td style="text-align:right;">
0.6863489
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.39000
</td>
<td style="text-align:right;">
190010647
</td>
<td style="text-align:right;">
9065.8008
</td>
<td style="text-align:right;">
0.6860645
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.64000
</td>
<td style="text-align:right;">
4318673
</td>
<td style="text-align:right;">
11305.3852
</td>
<td style="text-align:right;">
0.6856992
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
72.76600
</td>
<td style="text-align:right;">
24287670
</td>
<td style="text-align:right;">
8605.0478
</td>
<td style="text-align:right;">
0.6856805
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
69.58000
</td>
<td style="text-align:right;">
10612740
</td>
<td style="text-align:right;">
12986.4800
</td>
<td style="text-align:right;">
0.6854421
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
72.16000
</td>
<td style="text-align:right;">
2847132
</td>
<td style="text-align:right;">
9123.0417
</td>
<td style="text-align:right;">
0.6843571
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
69.82000
</td>
<td style="text-align:right;">
1694510
</td>
<td style="text-align:right;">
12383.4862
</td>
<td style="text-align:right;">
0.6843538
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
70.38000
</td>
<td style="text-align:right;">
9835109
</td>
<td style="text-align:right;">
11399.4449
</td>
<td style="text-align:right;">
0.6837819
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
70.42000
</td>
<td style="text-align:right;">
51430000
</td>
<td style="text-align:right;">
11283.1779
</td>
<td style="text-align:right;">
0.6834197
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
63.01200
</td>
<td style="text-align:right;">
11254672
</td>
<td style="text-align:right;">
33693.1753
</td>
<td style="text-align:right;">
0.6832215
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.43000
</td>
<td style="text-align:right;">
100825279
</td>
<td style="text-align:right;">
9847.7886
</td>
<td style="text-align:right;">
0.6831130
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
71.86800
</td>
<td style="text-align:right;">
33958947
</td>
<td style="text-align:right;">
9308.4187
</td>
<td style="text-align:right;">
0.6830915
</td>
</tr>
<tr>
<td style="text-align:left;">
Netherlands
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
72.13000
</td>
<td style="text-align:right;">
10381988
</td>
<td style="text-align:right;">
8941.5719
</td>
<td style="text-align:right;">
0.6825653
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
73.71700
</td>
<td style="text-align:right;">
9789224
</td>
<td style="text-align:right;">
7316.9181
</td>
<td style="text-align:right;">
0.6822090
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
72.52700
</td>
<td style="text-align:right;">
4494013
</td>
<td style="text-align:right;">
8447.7949
</td>
<td style="text-align:right;">
0.6820371
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
73.92300
</td>
<td style="text-align:right;">
10276158
</td>
<td style="text-align:right;">
7092.9230
</td>
<td style="text-align:right;">
0.6817249
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
71.95400
</td>
<td style="text-align:right;">
1200206
</td>
<td style="text-align:right;">
9021.8159
</td>
<td style="text-align:right;">
0.6815685
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
71.55500
</td>
<td style="text-align:right;">
4759670
</td>
<td style="text-align:right;">
9467.4461
</td>
<td style="text-align:right;">
0.6813771
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
69.95000
</td>
<td style="text-align:right;">
10637171
</td>
<td style="text-align:right;">
11674.8374
</td>
<td style="text-align:right;">
0.6813409
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.45000
</td>
<td style="text-align:right;">
4827803
</td>
<td style="text-align:right;">
10922.6640
</td>
<td style="text-align:right;">
0.6813314
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
72.75200
</td>
<td style="text-align:right;">
3149262
</td>
<td style="text-align:right;">
8137.0048
</td>
<td style="text-align:right;">
0.6813167
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
71.65900
</td>
<td style="text-align:right;">
9826397
</td>
<td style="text-align:right;">
9325.0682
</td>
<td style="text-align:right;">
0.6812381
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
76.15100
</td>
<td style="text-align:right;">
10983007
</td>
<td style="text-align:right;">
5431.9904
</td>
<td style="text-align:right;">
0.6811413
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
69.39000
</td>
<td style="text-align:right;">
10705535
</td>
<td style="text-align:right;">
12545.9907
</td>
<td style="text-align:right;">
0.6810800
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.06000
</td>
<td style="text-align:right;">
52667100
</td>
<td style="text-align:right;">
10022.4013
</td>
<td style="text-align:right;">
0.6808736
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
71.45500
</td>
<td style="text-align:right;">
88111030
</td>
<td style="text-align:right;">
9472.3843
</td>
<td style="text-align:right;">
0.6804637
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
73.73800
</td>
<td style="text-align:right;">
2734531
</td>
<td style="text-align:right;">
7113.6923
</td>
<td style="text-align:right;">
0.6802431
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
71.38000
</td>
<td style="text-align:right;">
5302888
</td>
<td style="text-align:right;">
9498.4677
</td>
<td style="text-align:right;">
0.6799536
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
70.25000
</td>
<td style="text-align:right;">
9218400
</td>
<td style="text-align:right;">
10991.2068
</td>
<td style="text-align:right;">
0.6798543
</td>
</tr>
<tr>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
68.44000
</td>
<td style="text-align:right;">
157553000
</td>
<td style="text-align:right;">
13990.4821
</td>
<td style="text-align:right;">
0.6795126
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
70.51000
</td>
<td style="text-align:right;">
47124000
</td>
<td style="text-align:right;">
10560.4855
</td>
<td style="text-align:right;">
0.6794388
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.28000
</td>
<td style="text-align:right;">
3024400
</td>
<td style="text-align:right;">
9530.7729
</td>
<td style="text-align:right;">
0.6792527
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
74.77200
</td>
<td style="text-align:right;">
684810
</td>
<td style="text-align:right;">
6071.9414
</td>
<td style="text-align:right;">
0.6774679
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
73.21300
</td>
<td style="text-align:right;">
10111559
</td>
<td style="text-align:right;">
7236.0753
</td>
<td style="text-align:right;">
0.6766987
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
71.86000
</td>
<td style="text-align:right;">
7124673
</td>
<td style="text-align:right;">
8527.8447
</td>
<td style="text-align:right;">
0.6764696
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
73.98100
</td>
<td style="text-align:right;">
720230
</td>
<td style="text-align:right;">
6557.1943
</td>
<td style="text-align:right;">
0.6762169
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
72.00000
</td>
<td style="text-align:right;">
4115700
</td>
<td style="text-align:right;">
8315.9281
</td>
<td style="text-align:right;">
0.6759031
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.41000
</td>
<td style="text-align:right;">
9662600
</td>
<td style="text-align:right;">
10172.4857
</td>
<td style="text-align:right;">
0.6757340
</td>
</tr>
<tr>
<td style="text-align:left;">
Denmark
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
70.78000
</td>
<td style="text-align:right;">
4334000
</td>
<td style="text-align:right;">
9692.3852
</td>
<td style="text-align:right;">
0.6757259
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
69.83000
</td>
<td style="text-align:right;">
4605744
</td>
<td style="text-align:right;">
10921.6363
</td>
<td style="text-align:right;">
0.6753285
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
71.02800
</td>
<td style="text-align:right;">
3677780
</td>
<td style="text-align:right;">
9313.9388
</td>
<td style="text-align:right;">
0.6751512
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
71.77700
</td>
<td style="text-align:right;">
71158647
</td>
<td style="text-align:right;">
8458.2764
</td>
<td style="text-align:right;">
0.6750767
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
72.23200
</td>
<td style="text-align:right;">
10336594
</td>
<td style="text-align:right;">
7914.3203
</td>
<td style="text-align:right;">
0.6743624
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
65.59300
</td>
<td style="text-align:right;">
297410
</td>
<td style="text-align:right;">
19340.1020
</td>
<td style="text-align:right;">
0.6733361
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.67000
</td>
<td style="text-align:right;">
34621254
</td>
<td style="text-align:right;">
9508.1415
</td>
<td style="text-align:right;">
0.6732651
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
70.98000
</td>
<td style="text-align:right;">
37740710
</td>
<td style="text-align:right;">
9082.3512
</td>
<td style="text-align:right;">
0.6728361
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.56700
</td>
<td style="text-align:right;">
2780132
</td>
<td style="text-align:right;">
7320.8803
</td>
<td style="text-align:right;">
0.6716072
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
70.19000
</td>
<td style="text-align:right;">
17910182
</td>
<td style="text-align:right;">
9883.5846
</td>
<td style="text-align:right;">
0.6715193
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
70.35000
</td>
<td style="text-align:right;">
4593433
</td>
<td style="text-align:right;">
9674.1676
</td>
<td style="text-align:right;">
0.6714831
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
72.14000
</td>
<td style="text-align:right;">
7661799
</td>
<td style="text-align:right;">
7696.7777
</td>
<td style="text-align:right;">
0.6714122
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.75200
</td>
<td style="text-align:right;">
2799811
</td>
<td style="text-align:right;">
5629.9153
</td>
<td style="text-align:right;">
0.6714103
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
69.54000
</td>
<td style="text-align:right;">
7129864
</td>
<td style="text-align:right;">
10750.7211
</td>
<td style="text-align:right;">
0.6713831
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
70.77400
</td>
<td style="text-align:right;">
31620918
</td>
<td style="text-align:right;">
9139.6714
</td>
<td style="text-align:right;">
0.6713465
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.88900
</td>
<td style="text-align:right;">
44227550
</td>
<td style="text-align:right;">
7006.5804
</td>
<td style="text-align:right;">
0.6712608
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
71.32000
</td>
<td style="text-align:right;">
36227381
</td>
<td style="text-align:right;">
8451.5310
</td>
<td style="text-align:right;">
0.6707194
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
74.09000
</td>
<td style="text-align:right;">
4165416
</td>
<td style="text-align:right;">
6018.9752
</td>
<td style="text-align:right;">
0.6706135
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
69.90000
</td>
<td style="text-align:right;">
9620282
</td>
<td style="text-align:right;">
10136.8671
</td>
<td style="text-align:right;">
0.6705844
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
68.97600
</td>
<td style="text-align:right;">
1101832
</td>
<td style="text-align:right;">
11460.6002
</td>
<td style="text-align:right;">
0.6705251
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
72.31200
</td>
<td style="text-align:right;">
11911819
</td>
<td style="text-align:right;">
7429.4559
</td>
<td style="text-align:right;">
0.6703544
</td>
</tr>
<tr>
<td style="text-align:left;">
Iceland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
72.49000
</td>
<td style="text-align:right;">
147962
</td>
<td style="text-align:right;">
7267.6884
</td>
<td style="text-align:right;">
0.6703448
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
55.56500
</td>
<td style="text-align:right;">
160000
</td>
<td style="text-align:right;">
108382.3529
</td>
<td style="text-align:right;">
0.6699972
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
69.76000
</td>
<td style="text-align:right;">
10394091
</td>
<td style="text-align:right;">
10168.6561
</td>
<td style="text-align:right;">
0.6694685
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
71.34000
</td>
<td style="text-align:right;">
8971958
</td>
<td style="text-align:right;">
8239.8548
</td>
<td style="text-align:right;">
0.6690254
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
72.16000
</td>
<td style="text-align:right;">
18501390
</td>
<td style="text-align:right;">
7426.3548
</td>
<td style="text-align:right;">
0.6689140
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.00000
</td>
<td style="text-align:right;">
8716441
</td>
<td style="text-align:right;">
8513.0970
</td>
<td style="text-align:right;">
0.6682460
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
74.17300
</td>
<td style="text-align:right;">
12921234
</td>
<td style="text-align:right;">
5773.0445
</td>
<td style="text-align:right;">
0.6681465
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
74.41400
</td>
<td style="text-align:right;">
10723260
</td>
<td style="text-align:right;">
5592.8440
</td>
<td style="text-align:right;">
0.6678631
</td>
</tr>
<tr>
<td style="text-align:left;">
Canada
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
68.75000
</td>
<td style="text-align:right;">
14785584
</td>
<td style="text-align:right;">
11367.1611
</td>
<td style="text-align:right;">
0.6677427
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.44000
</td>
<td style="text-align:right;">
32850275
</td>
<td style="text-align:right;">
7993.5123
</td>
<td style="text-align:right;">
0.6677080
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
73.61500
</td>
<td style="text-align:right;">
622191
</td>
<td style="text-align:right;">
6101.2558
</td>
<td style="text-align:right;">
0.6673537
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
70.98000
</td>
<td style="text-align:right;">
4442238
</td>
<td style="text-align:right;">
8412.9024
</td>
<td style="text-align:right;">
0.6671837
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
71.91800
</td>
<td style="text-align:right;">
3045153
</td>
<td style="text-align:right;">
7452.3990
</td>
<td style="text-align:right;">
0.6669326
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
72.26200
</td>
<td style="text-align:right;">
2531311
</td>
<td style="text-align:right;">
7121.9247
</td>
<td style="text-align:right;">
0.6667137
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
71.08000
</td>
<td style="text-align:right;">
8892098
</td>
<td style="text-align:right;">
8224.1916
</td>
<td style="text-align:right;">
0.6664465
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
69.17000
</td>
<td style="text-align:right;">
10348684
</td>
<td style="text-align:right;">
10535.6285
</td>
<td style="text-align:right;">
0.6663569
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
71.32200
</td>
<td style="text-align:right;">
22404337
</td>
<td style="text-align:right;">
7885.3601
</td>
<td style="text-align:right;">
0.6655946
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
67.45600
</td>
<td style="text-align:right;">
13503563
</td>
<td style="text-align:right;">
13143.9510
</td>
<td style="text-align:right;">
0.6653639
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
71.76600
</td>
<td style="text-align:right;">
2378618
</td>
<td style="text-align:right;">
7404.9237
</td>
<td style="text-align:right;">
0.6650460
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
71.00600
</td>
<td style="text-align:right;">
179914212
</td>
<td style="text-align:right;">
8131.2128
</td>
<td style="text-align:right;">
0.6649130
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
70.75000
</td>
<td style="text-align:right;">
2693585
</td>
<td style="text-align:right;">
8393.7414
</td>
<td style="text-align:right;">
0.6648540
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
68.55700
</td>
<td style="text-align:right;">
15620766
</td>
<td style="text-align:right;">
11152.4101
</td>
<td style="text-align:right;">
0.6645082
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
69.66000
</td>
<td style="text-align:right;">
22356726
</td>
<td style="text-align:right;">
9605.3141
</td>
<td style="text-align:right;">
0.6643796
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
69.53000
</td>
<td style="text-align:right;">
22686371
</td>
<td style="text-align:right;">
9696.2733
</td>
<td style="text-align:right;">
0.6638213
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
75.65100
</td>
<td style="text-align:right;">
3508512
</td>
<td style="text-align:right;">
4604.2117
</td>
<td style="text-align:right;">
0.6636602
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
72.04700
</td>
<td style="text-align:right;">
2664659
</td>
<td style="text-align:right;">
6994.7749
</td>
<td style="text-align:right;">
0.6633801
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
70.26500
</td>
<td style="text-align:right;">
3430388
</td>
<td style="text-align:right;">
8754.9639
</td>
<td style="text-align:right;">
0.6633756
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
69.10000
</td>
<td style="text-align:right;">
71019069
</td>
<td style="text-align:right;">
10187.8267
</td>
<td style="text-align:right;">
0.6632700
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
72.46200
</td>
<td style="text-align:right;">
2484997
</td>
<td style="text-align:right;">
6618.7431
</td>
<td style="text-align:right;">
0.6630368
</td>
</tr>
<tr>
<td style="text-align:left;">
United Kingdom
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
69.18000
</td>
<td style="text-align:right;">
50430000
</td>
<td style="text-align:right;">
9979.5085
</td>
<td style="text-align:right;">
0.6625514
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
69.94200
</td>
<td style="text-align:right;">
29341374
</td>
<td style="text-align:right;">
8997.8974
</td>
<td style="text-align:right;">
0.6623171
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
70.85000
</td>
<td style="text-align:right;">
33039545
</td>
<td style="text-align:right;">
8006.5070
</td>
<td style="text-align:right;">
0.6623133
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
72.64900
</td>
<td style="text-align:right;">
9537988
</td>
<td style="text-align:right;">
6380.4950
</td>
<td style="text-align:right;">
0.6619778
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
71.42100
</td>
<td style="text-align:right;">
28674757
</td>
<td style="text-align:right;">
7408.9056
</td>
<td style="text-align:right;">
0.6618888
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
68.70000
</td>
<td style="text-align:right;">
8313288
</td>
<td style="text-align:right;">
10522.0675
</td>
<td style="text-align:right;">
0.6617371
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
69.24000
</td>
<td style="text-align:right;">
8989111
</td>
<td style="text-align:right;">
9714.9606
</td>
<td style="text-align:right;">
0.6611913
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.08000
</td>
<td style="text-align:right;">
2900100
</td>
<td style="text-align:right;">
7655.5690
</td>
<td style="text-align:right;">
0.6611498
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
70.99000
</td>
<td style="text-align:right;">
38370697
</td>
<td style="text-align:right;">
7738.8812
</td>
<td style="text-align:right;">
0.6611119
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
69.50000
</td>
<td style="text-align:right;">
10223422
</td>
<td style="text-align:right;">
9326.6447
</td>
<td style="text-align:right;">
0.6607255
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
69.46000
</td>
<td style="text-align:right;">
21658597
</td>
<td style="text-align:right;">
9356.3972
</td>
<td style="text-align:right;">
0.6605753
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
69.61000
</td>
<td style="text-align:right;">
4225310
</td>
<td style="text-align:right;">
9164.0901
</td>
<td style="text-align:right;">
0.6604982
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
69.45100
</td>
<td style="text-align:right;">
66907826
</td>
<td style="text-align:right;">
9240.7620
</td>
<td style="text-align:right;">
0.6595914
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
71.52300
</td>
<td style="text-align:right;">
2253639
</td>
<td style="text-align:right;">
7034.7792
</td>
<td style="text-align:right;">
0.6589796
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
69.18000
</td>
<td style="text-align:right;">
1646912
</td>
<td style="text-align:right;">
9405.4894
</td>
<td style="text-align:right;">
0.6582890
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.81000
</td>
<td style="text-align:right;">
8797022
</td>
<td style="text-align:right;">
7612.2404
</td>
<td style="text-align:right;">
0.6582204
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
70.63600
</td>
<td style="text-align:right;">
527678
</td>
<td style="text-align:right;">
7778.4140
</td>
<td style="text-align:right;">
0.6581895
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
73.04200
</td>
<td style="text-align:right;">
9770575
</td>
<td style="text-align:right;">
5722.8957
</td>
<td style="text-align:right;">
0.6572957
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
69.81000
</td>
<td style="text-align:right;">
41622000
</td>
<td style="text-align:right;">
8533.0888
</td>
<td style="text-align:right;">
0.6572161
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.30100
</td>
<td style="text-align:right;">
33333216
</td>
<td style="text-align:right;">
6223.3675
</td>
<td style="text-align:right;">
0.6569318
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
68.48100
</td>
<td style="text-align:right;">
26983828
</td>
<td style="text-align:right;">
10079.0267
</td>
<td style="text-align:right;">
0.6565637
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
69.46500
</td>
<td style="text-align:right;">
1138101
</td>
<td style="text-align:right;">
8792.5731
</td>
<td style="text-align:right;">
0.6561324
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
69.26000
</td>
<td style="text-align:right;">
8970450
</td>
<td style="text-align:right;">
9022.2474
</td>
<td style="text-align:right;">
0.6560536
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
68.75500
</td>
<td style="text-align:right;">
4364501
</td>
<td style="text-align:right;">
9640.1385
</td>
<td style="text-align:right;">
0.6560070
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
71.09600
</td>
<td style="text-align:right;">
2826046
</td>
<td style="text-align:right;">
7110.6676
</td>
<td style="text-align:right;">
0.6558388
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
70.73600
</td>
<td style="text-align:right;">
1149818
</td>
<td style="text-align:right;">
7425.7053
</td>
<td style="text-align:right;">
0.6557073
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
69.49800
</td>
<td style="text-align:right;">
80122492
</td>
<td style="text-align:right;">
8688.1560
</td>
<td style="text-align:right;">
0.6555806
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
69.52100
</td>
<td style="text-align:right;">
2152400
</td>
<td style="text-align:right;">
8597.7562
</td>
<td style="text-align:right;">
0.6550413
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
70.61600
</td>
<td style="text-align:right;">
65068149
</td>
<td style="text-align:right;">
7458.3963
</td>
<td style="text-align:right;">
0.6549175
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
73.45000
</td>
<td style="text-align:right;">
2424367
</td>
<td style="text-align:right;">
5262.7348
</td>
<td style="text-align:right;">
0.6545637
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.10000
</td>
<td style="text-align:right;">
2648961
</td>
<td style="text-align:right;">
6929.2777
</td>
<td style="text-align:right;">
0.6539648
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
68.75000
</td>
<td style="text-align:right;">
4491443
</td>
<td style="text-align:right;">
9371.8426
</td>
<td style="text-align:right;">
0.6539410
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.23500
</td>
<td style="text-align:right;">
9319622
</td>
<td style="text-align:right;">
6025.3748
</td>
<td style="text-align:right;">
0.6539031
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
70.69300
</td>
<td style="text-align:right;">
18319502
</td>
<td style="text-align:right;">
7277.9128
</td>
<td style="text-align:right;">
0.6538306
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
71.77000
</td>
<td style="text-align:right;">
2326606
</td>
<td style="text-align:right;">
6351.2375
</td>
<td style="text-align:right;">
0.6536253
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
68.83200
</td>
<td style="text-align:right;">
1116479
</td>
<td style="text-align:right;">
9119.5286
</td>
<td style="text-align:right;">
0.6527672
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
70.33000
</td>
<td style="text-align:right;">
4237384
</td>
<td style="text-align:right;">
7481.1076
</td>
<td style="text-align:right;">
0.6524875
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
70.80500
</td>
<td style="text-align:right;">
2953997
</td>
<td style="text-align:right;">
6920.2231
</td>
<td style="text-align:right;">
0.6511552
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
68.93000
</td>
<td style="text-align:right;">
44310863
</td>
<td style="text-align:right;">
8662.8349
</td>
<td style="text-align:right;">
0.6500133
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
72.49200
</td>
<td style="text-align:right;">
12463354
</td>
<td style="text-align:right;">
5547.0638
</td>
<td style="text-align:right;">
0.6499935
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
69.24000
</td>
<td style="text-align:right;">
50843200
</td>
<td style="text-align:right;">
8243.5823
</td>
<td style="text-align:right;">
0.6493643
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
70.47200
</td>
<td style="text-align:right;">
2036305
</td>
<td style="text-align:right;">
7009.6016
</td>
<td style="text-align:right;">
0.6490334
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
70.90000
</td>
<td style="text-align:right;">
8576200
</td>
<td style="text-align:right;">
6597.4944
</td>
<td style="text-align:right;">
0.6485071
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
69.38800
</td>
<td style="text-align:right;">
168546719
</td>
<td style="text-align:right;">
7957.9808
</td>
<td style="text-align:right;">
0.6482076
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
71.19000
</td>
<td style="text-align:right;">
8658506
</td>
<td style="text-align:right;">
6302.6234
</td>
<td style="text-align:right;">
0.6477742
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
69.03000
</td>
<td style="text-align:right;">
9513758
</td>
<td style="text-align:right;">
8256.3439
</td>
<td style="text-align:right;">
0.6475058
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
69.86200
</td>
<td style="text-align:right;">
1183669
</td>
<td style="text-align:right;">
7370.9909
</td>
<td style="text-align:right;">
0.6470681
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
69.21000
</td>
<td style="text-align:right;">
20662648
</td>
<td style="text-align:right;">
8011.4144
</td>
<td style="text-align:right;">
0.6470265
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
70.84500
</td>
<td style="text-align:right;">
67308928
</td>
<td style="text-align:right;">
6508.0857
</td>
<td style="text-align:right;">
0.6469987
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
71.87800
</td>
<td style="text-align:right;">
6939688
</td>
<td style="text-align:right;">
5728.3535
</td>
<td style="text-align:right;">
0.6468923
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
63.30000
</td>
<td style="text-align:right;">
230800
</td>
<td style="text-align:right;">
18268.6584
</td>
<td style="text-align:right;">
0.6460454
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
66.23400
</td>
<td style="text-align:right;">
3799845
</td>
<td style="text-align:right;">
11770.5898
</td>
<td style="text-align:right;">
0.6457082
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.96100
</td>
<td style="text-align:right;">
1318683096
</td>
<td style="text-align:right;">
4959.1149
</td>
<td style="text-align:right;">
0.6456966
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
69.72000
</td>
<td style="text-align:right;">
22562458
</td>
<td style="text-align:right;">
7346.5476
</td>
<td style="text-align:right;">
0.6455121
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
71.68200
</td>
<td style="text-align:right;">
41008227
</td>
<td style="text-align:right;">
5755.2600
</td>
<td style="text-align:right;">
0.6454777
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
73.24400
</td>
<td style="text-align:right;">
3607000
</td>
<td style="text-align:right;">
4766.3559
</td>
<td style="text-align:right;">
0.6451810
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
71.21000
</td>
<td style="text-align:right;">
2298309
</td>
<td style="text-align:right;">
6068.0513
</td>
<td style="text-align:right;">
0.6451471
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
69.58200
</td>
<td style="text-align:right;">
1191336
</td>
<td style="text-align:right;">
7388.5978
</td>
<td style="text-align:right;">
0.6446474
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
70.29000
</td>
<td style="text-align:right;">
2830000
</td>
<td style="text-align:right;">
6631.5973
</td>
<td style="text-align:right;">
0.6433045
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
74.14300
</td>
<td style="text-align:right;">
19314747
</td>
<td style="text-align:right;">
4184.5481
</td>
<td style="text-align:right;">
0.6430611
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
67.40500
</td>
<td style="text-align:right;">
71640904
</td>
<td style="text-align:right;">
9611.1475
</td>
<td style="text-align:right;">
0.6429152
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
69.61300
</td>
<td style="text-align:right;">
10748394
</td>
<td style="text-align:right;">
7103.7026
</td>
<td style="text-align:right;">
0.6420876
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.11000
</td>
<td style="text-align:right;">
2156814
</td>
<td style="text-align:right;">
6650.1956
</td>
<td style="text-align:right;">
0.6418614
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
71.91300
</td>
<td style="text-align:right;">
562035
</td>
<td style="text-align:right;">
5303.3775
</td>
<td style="text-align:right;">
0.6414418
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
69.15000
</td>
<td style="text-align:right;">
1582962
</td>
<td style="text-align:right;">
7402.3034
</td>
<td style="text-align:right;">
0.6407784
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
71.33800
</td>
<td style="text-align:right;">
80264543
</td>
<td style="text-align:right;">
5581.1810
</td>
<td style="text-align:right;">
0.6401012
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
69.39000
</td>
<td style="text-align:right;">
2310904
</td>
<td style="text-align:right;">
7105.6307
</td>
<td style="text-align:right;">
0.6400503
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
69.00000
</td>
<td style="text-align:right;">
1997616
</td>
<td style="text-align:right;">
7433.8893
</td>
<td style="text-align:right;">
0.6396940
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.75000
</td>
<td style="text-align:right;">
2108457
</td>
<td style="text-align:right;">
5926.8770
</td>
<td style="text-align:right;">
0.6392474
</td>
</tr>
<tr>
<td style="text-align:left;">
Belgium
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
68.00000
</td>
<td style="text-align:right;">
8730405
</td>
<td style="text-align:right;">
8343.1051
</td>
<td style="text-align:right;">
0.6385837
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
67.06500
</td>
<td style="text-align:right;">
24779799
</td>
<td style="text-align:right;">
9443.0385
</td>
<td style="text-align:right;">
0.6384414
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
68.04200
</td>
<td style="text-align:right;">
63327987
</td>
<td style="text-align:right;">
8263.5903
</td>
<td style="text-align:right;">
0.6383004
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
67.48000
</td>
<td style="text-align:right;">
6965860
</td>
<td style="text-align:right;">
8842.5980
</td>
<td style="text-align:right;">
0.6377812
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
70.31300
</td>
<td style="text-align:right;">
37657830
</td>
<td style="text-align:right;">
6117.3617
</td>
<td style="text-align:right;">
0.6376123
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
68.30000
</td>
<td style="text-align:right;">
1039009
</td>
<td style="text-align:right;">
7899.5542
</td>
<td style="text-align:right;">
0.6375203
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
58.69000
</td>
<td style="text-align:right;">
8128505
</td>
<td style="text-align:right;">
34167.7626
</td>
<td style="text-align:right;">
0.6372131
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
69.29200
</td>
<td style="text-align:right;">
3219994
</td>
<td style="text-align:right;">
6890.8069
</td>
<td style="text-align:right;">
0.6369339
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
69.61000
</td>
<td style="text-align:right;">
31785378
</td>
<td style="text-align:right;">
6557.1528
</td>
<td style="text-align:right;">
0.6362637
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
70.32000
</td>
<td style="text-align:right;">
8066057
</td>
<td style="text-align:right;">
5970.3888
</td>
<td style="text-align:right;">
0.6358972
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
70.00000
</td>
<td style="text-align:right;">
3722800
</td>
<td style="text-align:right;">
6197.9628
</td>
<td style="text-align:right;">
0.6357270
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
71.97300
</td>
<td style="text-align:right;">
9231669
</td>
<td style="text-align:right;">
4876.7986
</td>
<td style="text-align:right;">
0.6356999
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.53500
</td>
<td style="text-align:right;">
6053193
</td>
<td style="text-align:right;">
4519.4612
</td>
<td style="text-align:right;">
0.6349230
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
69.48100
</td>
<td style="text-align:right;">
2873520
</td>
<td style="text-align:right;">
6504.3397
</td>
<td style="text-align:right;">
0.6345002
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
69.36000
</td>
<td style="text-align:right;">
22797027
</td>
<td style="text-align:right;">
6598.4099
</td>
<td style="text-align:right;">
0.6344311
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
70.59000
</td>
<td style="text-align:right;">
16785196
</td>
<td style="text-align:right;">
5596.5198
</td>
<td style="text-align:right;">
0.6335911
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
72.37000
</td>
<td style="text-align:right;">
3389578
</td>
<td style="text-align:right;">
4515.4876
</td>
<td style="text-align:right;">
0.6334125
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
65.04400
</td>
<td style="text-align:right;">
16543189
</td>
<td style="text-align:right;">
11643.5727
</td>
<td style="text-align:right;">
0.6333731
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
70.99400
</td>
<td style="text-align:right;">
31287142
</td>
<td style="text-align:right;">
5288.0404
</td>
<td style="text-align:right;">
0.6330308
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
65.71200
</td>
<td style="text-align:right;">
11515649
</td>
<td style="text-align:right;">
10505.2597
</td>
<td style="text-align:right;">
0.6328466
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
73.05300
</td>
<td style="text-align:right;">
17155814
</td>
<td style="text-align:right;">
4090.9253
</td>
<td style="text-align:right;">
0.6318880
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
70.42000
</td>
<td style="text-align:right;">
8310226
</td>
<td style="text-align:right;">
5577.0028
</td>
<td style="text-align:right;">
0.6318093
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
69.74500
</td>
<td style="text-align:right;">
1096202
</td>
<td style="text-align:right;">
6058.2538
</td>
<td style="text-align:right;">
0.6317573
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
70.73400
</td>
<td style="text-align:right;">
6353681
</td>
<td style="text-align:right;">
5351.5687
</td>
<td style="text-align:right;">
0.6315910
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
69.90600
</td>
<td style="text-align:right;">
26769436
</td>
<td style="text-align:right;">
5909.0201
</td>
<td style="text-align:right;">
0.6314022
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
67.96000
</td>
<td style="text-align:right;">
10063000
</td>
<td style="text-align:right;">
7550.3599
</td>
<td style="text-align:right;">
0.6311511
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
62.15500
</td>
<td style="text-align:right;">
3344074
</td>
<td style="text-align:right;">
17364.2754
</td>
<td style="text-align:right;">
0.6310773
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
69.71800
</td>
<td style="text-align:right;">
2104779
</td>
<td style="text-align:right;">
6017.6548
</td>
<td style="text-align:right;">
0.6310252
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
70.72300
</td>
<td style="text-align:right;">
8831348
</td>
<td style="text-align:right;">
5305.4453
</td>
<td style="text-align:right;">
0.6308561
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
68.50000
</td>
<td style="text-align:right;">
4174366
</td>
<td style="text-align:right;">
6960.2979
</td>
<td style="text-align:right;">
0.6303687
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
68.83500
</td>
<td style="text-align:right;">
63047647
</td>
<td style="text-align:right;">
6601.4299
</td>
<td style="text-align:right;">
0.6296617
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
69.51000
</td>
<td style="text-align:right;">
8448233
</td>
<td style="text-align:right;">
6017.1907
</td>
<td style="text-align:right;">
0.6291370
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
68.73000
</td>
<td style="text-align:right;">
95831757
</td>
<td style="text-align:right;">
6576.6495
</td>
<td style="text-align:right;">
0.6284324
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
69.69000
</td>
<td style="text-align:right;">
31158061
</td>
<td style="text-align:right;">
5693.8439
</td>
<td style="text-align:right;">
0.6267626
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
67.49000
</td>
<td style="text-align:right;">
4324000
</td>
<td style="text-align:right;">
7545.4154
</td>
<td style="text-align:right;">
0.6267402
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
70.56500
</td>
<td style="text-align:right;">
11487112
</td>
<td style="text-align:right;">
5095.6657
</td>
<td style="text-align:right;">
0.6264858
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
66.91400
</td>
<td style="text-align:right;">
7971222
</td>
<td style="text-align:right;">
7991.7071
</td>
<td style="text-align:right;">
0.6253904
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
70.25900
</td>
<td style="text-align:right;">
12572928
</td>
<td style="text-align:right;">
5186.0500
</td>
<td style="text-align:right;">
0.6250539
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.39600
</td>
<td style="text-align:right;">
20378239
</td>
<td style="text-align:right;">
3970.0954
</td>
<td style="text-align:right;">
0.6239477
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
66.09900
</td>
<td style="text-align:right;">
3115787
</td>
<td style="text-align:right;">
8659.6968
</td>
<td style="text-align:right;">
0.6232920
</td>
</tr>
<tr>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
67.50000
</td>
<td style="text-align:right;">
69145952
</td>
<td style="text-align:right;">
7144.1144
</td>
<td style="text-align:right;">
0.6229963
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
66.98300
</td>
<td style="text-align:right;">
3086876
</td>
<td style="text-align:right;">
7640.5195
</td>
<td style="text-align:right;">
0.6229045
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
69.88500
</td>
<td style="text-align:right;">
517810
</td>
<td style="text-align:right;">
5267.2194
</td>
<td style="text-align:right;">
0.6228554
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
71.75200
</td>
<td style="text-align:right;">
6667147
</td>
<td style="text-align:right;">
4172.8385
</td>
<td style="text-align:right;">
0.6221142
</td>
</tr>
<tr>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
67.41000
</td>
<td style="text-align:right;">
42459667
</td>
<td style="text-align:right;">
7029.8093
</td>
<td style="text-align:right;">
0.6210348
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
70.84700
</td>
<td style="text-align:right;">
8650322
</td>
<td style="text-align:right;">
4563.8082
</td>
<td style="text-align:right;">
0.6208669
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
68.56400
</td>
<td style="text-align:right;">
62806748
</td>
<td style="text-align:right;">
5913.1875
</td>
<td style="text-align:right;">
0.6193314
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
71.14000
</td>
<td style="text-align:right;">
4338977
</td>
<td style="text-align:right;">
4314.1148
</td>
<td style="text-align:right;">
0.6192715
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
69.50000
</td>
<td style="text-align:right;">
16331785
</td>
<td style="text-align:right;">
5249.8027
</td>
<td style="text-align:right;">
0.6191847
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
68.90000
</td>
<td style="text-align:right;">
2878220
</td>
<td style="text-align:right;">
5599.0779
</td>
<td style="text-align:right;">
0.6184550
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
62.03800
</td>
<td style="text-align:right;">
14173318
</td>
<td style="text-align:right;">
14517.9071
</td>
<td style="text-align:right;">
0.6183375
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
69.62000
</td>
<td style="text-align:right;">
2448046
</td>
<td style="text-align:right;">
5108.3446
</td>
<td style="text-align:right;">
0.6182759
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
69.53500
</td>
<td style="text-align:right;">
5783439
</td>
<td style="text-align:right;">
5154.8255
</td>
<td style="text-align:right;">
0.6181761
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
62.72800
</td>
<td style="text-align:right;">
1301048
</td>
<td style="text-align:right;">
12954.7910
</td>
<td style="text-align:right;">
0.6177827
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
68.67300
</td>
<td style="text-align:right;">
2829526
</td>
<td style="text-align:right;">
5703.4089
</td>
<td style="text-align:right;">
0.6177360
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
71.52700
</td>
<td style="text-align:right;">
15081016
</td>
<td style="text-align:right;">
4014.2390
</td>
<td style="text-align:right;">
0.6172808
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
67.05700
</td>
<td style="text-align:right;">
155975974
</td>
<td style="text-align:right;">
6950.2830
</td>
<td style="text-align:right;">
0.6169892
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
68.38600
</td>
<td style="text-align:right;">
24748122
</td>
<td style="text-align:right;">
5838.3477
</td>
<td style="text-align:right;">
0.6168176
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
67.81000
</td>
<td style="text-align:right;">
49182000
</td>
<td style="text-align:right;">
6248.6562
</td>
<td style="text-align:right;">
0.6164123
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
72.00000
</td>
<td style="text-align:right;">
3075321
</td>
<td style="text-align:right;">
3738.9327
</td>
<td style="text-align:right;">
0.6160424
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
69.80600
</td>
<td style="text-align:right;">
73312559
</td>
<td style="text-align:right;">
4754.6044
</td>
<td style="text-align:right;">
0.6147176
</td>
</tr>
<tr>
<td style="text-align:left;">
Czech Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
66.87000
</td>
<td style="text-align:right;">
9125183
</td>
<td style="text-align:right;">
6876.1403
</td>
<td style="text-align:right;">
0.6145227
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
68.29000
</td>
<td style="text-align:right;">
8139332
</td>
<td style="text-align:right;">
5690.2680
</td>
<td style="text-align:right;">
0.6141270
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
65.63400
</td>
<td style="text-align:right;">
22934225
</td>
<td style="text-align:right;">
8052.9530
</td>
<td style="text-align:right;">
0.6139484
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
67.23100
</td>
<td style="text-align:right;">
9545158
</td>
<td style="text-align:right;">
6481.7770
</td>
<td style="text-align:right;">
0.6137103
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
68.68100
</td>
<td style="text-align:right;">
1839782
</td>
<td style="text-align:right;">
5351.9121
</td>
<td style="text-align:right;">
0.6132641
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
68.25300
</td>
<td style="text-align:right;">
2598466
</td>
<td style="text-align:right;">
5603.3577
</td>
<td style="text-align:right;">
0.6127016
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
68.46800
</td>
<td style="text-align:right;">
2748579
</td>
<td style="text-align:right;">
5444.6196
</td>
<td style="text-align:right;">
0.6125852
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
67.51000
</td>
<td style="text-align:right;">
1861096
</td>
<td style="text-align:right;">
6124.7035
</td>
<td style="text-align:right;">
0.6122784
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
67.85000
</td>
<td style="text-align:right;">
1533070
</td>
<td style="text-align:right;">
5862.2766
</td>
<td style="text-align:right;">
0.6122717
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
72.95000
</td>
<td style="text-align:right;">
3428038
</td>
<td style="text-align:right;">
3193.0546
</td>
<td style="text-align:right;">
0.6121964
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
68.42100
</td>
<td style="text-align:right;">
34202721
</td>
<td style="text-align:right;">
5444.6486
</td>
<td style="text-align:right;">
0.6121651
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
70.69000
</td>
<td style="text-align:right;">
4172693
</td>
<td style="text-align:right;">
4126.6132
</td>
<td style="text-align:right;">
0.6120873
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
73.42200
</td>
<td style="text-align:right;">
4018332
</td>
<td style="text-align:right;">
3025.3498
</td>
<td style="text-align:right;">
0.6120375
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
71.26300
</td>
<td style="text-align:right;">
5307470
</td>
<td style="text-align:right;">
3844.9172
</td>
<td style="text-align:right;">
0.6118083
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
67.45000
</td>
<td style="text-align:right;">
3844277
</td>
<td style="text-align:right;">
6093.2630
</td>
<td style="text-align:right;">
0.6113732
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
70.64700
</td>
<td style="text-align:right;">
19067554
</td>
<td style="text-align:right;">
4106.4923
</td>
<td style="text-align:right;">
0.6113558
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
71.16400
</td>
<td style="text-align:right;">
33757175
</td>
<td style="text-align:right;">
3820.1752
</td>
<td style="text-align:right;">
0.6104805
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
70.00100
</td>
<td style="text-align:right;">
8523077
</td>
<td style="text-align:right;">
4332.7202
</td>
<td style="text-align:right;">
0.6096699
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
66.80000
</td>
<td style="text-align:right;">
19284814
</td>
<td style="text-align:right;">
6470.8665
</td>
<td style="text-align:right;">
0.6096589
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
69.15200
</td>
<td style="text-align:right;">
29072015
</td>
<td style="text-align:right;">
4797.2951
</td>
<td style="text-align:right;">
0.6096013
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
67.52100
</td>
<td style="text-align:right;">
60216677
</td>
<td style="text-align:right;">
5852.6255
</td>
<td style="text-align:right;">
0.6091871
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
68.97800
</td>
<td style="text-align:right;">
11178650
</td>
<td style="text-align:right;">
4858.3475
</td>
<td style="text-align:right;">
0.6089747
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
67.04400
</td>
<td style="text-align:right;">
2424959
</td>
<td style="text-align:right;">
6150.7730
</td>
<td style="text-align:right;">
0.6083482
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
65.20500
</td>
<td style="text-align:right;">
142938076
</td>
<td style="text-align:right;">
7807.0958
</td>
<td style="text-align:right;">
0.6078328
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
65.74200
</td>
<td style="text-align:right;">
60397973
</td>
<td style="text-align:right;">
7235.6532
</td>
<td style="text-align:right;">
0.6076412
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
61.36600
</td>
<td style="text-align:right;">
985739
</td>
<td style="text-align:right;">
13522.1575
</td>
<td style="text-align:right;">
0.6071047
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
65.42100
</td>
<td style="text-align:right;">
2680018
</td>
<td style="text-align:right;">
7486.3843
</td>
<td style="text-align:right;">
0.6069921
</td>
</tr>
<tr>
<td style="text-align:left;">
Finland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
66.55000
</td>
<td style="text-align:right;">
4090500
</td>
<td style="text-align:right;">
6424.5191
</td>
<td style="text-align:right;">
0.6068797
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
67.92600
</td>
<td style="text-align:right;">
3089353
</td>
<td style="text-align:right;">
5377.0913
</td>
<td style="text-align:right;">
0.6068542
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
67.17800
</td>
<td style="text-align:right;">
501035
</td>
<td style="text-align:right;">
5907.8509
</td>
<td style="text-align:right;">
0.6067487
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
66.60000
</td>
<td style="text-align:right;">
9103000
</td>
<td style="text-align:right;">
6361.5180
</td>
<td style="text-align:right;">
0.6066530
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
70.75500
</td>
<td style="text-align:right;">
5884491
</td>
<td style="text-align:right;">
3783.6742
</td>
<td style="text-align:right;">
0.6062654
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
67.84000
</td>
<td style="text-align:right;">
1944401
</td>
<td style="text-align:right;">
5385.2785
</td>
<td style="text-align:right;">
0.6061932
</td>
</tr>
<tr>
<td style="text-align:left;">
Austria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
66.80000
</td>
<td style="text-align:right;">
6927772
</td>
<td style="text-align:right;">
6137.0765
</td>
<td style="text-align:right;">
0.6059793
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
68.74000
</td>
<td style="text-align:right;">
1042663
</td>
<td style="text-align:right;">
4783.5869
</td>
<td style="text-align:right;">
0.6057648
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
65.03200
</td>
<td style="text-align:right;">
63759976
</td>
<td style="text-align:right;">
7674.9291
</td>
<td style="text-align:right;">
0.6050653
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
63.47900
</td>
<td style="text-align:right;">
9709552
</td>
<td style="text-align:right;">
9541.4742
</td>
<td style="text-align:right;">
0.6049883
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
69.51000
</td>
<td style="text-align:right;">
8012946
</td>
<td style="text-align:right;">
4254.3378
</td>
<td style="text-align:right;">
0.6040737
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
67.64000
</td>
<td style="text-align:right;">
30329617
</td>
<td style="text-align:right;">
5338.7521
</td>
<td style="text-align:right;">
0.6037957
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
60.46100
</td>
<td style="text-align:right;">
1126189
</td>
<td style="text-align:right;">
14722.8419
</td>
<td style="text-align:right;">
0.6035009
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
65.90000
</td>
<td style="text-align:right;">
975199
</td>
<td style="text-align:right;">
6619.5514
</td>
<td style="text-align:right;">
0.6030020
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
69.40000
</td>
<td style="text-align:right;">
5154123
</td>
<td style="text-align:right;">
4247.4003
</td>
<td style="text-align:right;">
0.6029999
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
60.41300
</td>
<td style="text-align:right;">
11882916
</td>
<td style="text-align:right;">
14688.2351
</td>
<td style="text-align:right;">
0.6028739
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
67.12300
</td>
<td style="text-align:right;">
39326000
</td>
<td style="text-align:right;">
5622.9425
</td>
<td style="text-align:right;">
0.6028013
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
72.02800
</td>
<td style="text-align:right;">
1280400000
</td>
<td style="text-align:right;">
3119.2809
</td>
<td style="text-align:right;">
0.6027078
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
67.84900
</td>
<td style="text-align:right;">
1834796
</td>
<td style="text-align:right;">
5118.1469
</td>
<td style="text-align:right;">
0.6026834
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
74.24900
</td>
<td style="text-align:right;">
85262356
</td>
<td style="text-align:right;">
2441.5764
</td>
<td style="text-align:right;">
0.6023758
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
67.94600
</td>
<td style="text-align:right;">
1977600
</td>
<td style="text-align:right;">
4977.4185
</td>
<td style="text-align:right;">
0.6015748
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
71.68800
</td>
<td style="text-align:right;">
91077287
</td>
<td style="text-align:right;">
3190.4810
</td>
<td style="text-align:right;">
0.6015455
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
66.41000
</td>
<td style="text-align:right;">
9839000
</td>
<td style="text-align:right;">
6040.1800
</td>
<td style="text-align:right;">
0.6013422
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
68.00000
</td>
<td style="text-align:right;">
14441916
</td>
<td style="text-align:right;">
4920.3560
</td>
<td style="text-align:right;">
0.6012374
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
65.14200
</td>
<td style="text-align:right;">
21283783
</td>
<td style="text-align:right;">
7133.1660
</td>
<td style="text-align:right;">
0.6011290
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
67.13000
</td>
<td style="text-align:right;">
4076557
</td>
<td style="text-align:right;">
5477.8900
</td>
<td style="text-align:right;">
0.6010394
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
70.65000
</td>
<td style="text-align:right;">
223547000
</td>
<td style="text-align:right;">
3540.6516
</td>
<td style="text-align:right;">
0.6004877
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
67.74400
</td>
<td style="text-align:right;">
26298373
</td>
<td style="text-align:right;">
5023.2166
</td>
<td style="text-align:right;">
0.6004316
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
72.89900
</td>
<td style="text-align:right;">
5675356
</td>
<td style="text-align:right;">
2749.3210
</td>
<td style="text-align:right;">
0.6004239
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
70.42000
</td>
<td style="text-align:right;">
2780097
</td>
<td style="text-align:right;">
3630.8807
</td>
<td style="text-align:right;">
0.6003759
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
67.86000
</td>
<td style="text-align:right;">
8096218
</td>
<td style="text-align:right;">
4916.2999
</td>
<td style="text-align:right;">
0.5999413
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
69.39000
</td>
<td style="text-align:right;">
15226039
</td>
<td style="text-align:right;">
4062.5239
</td>
<td style="text-align:right;">
0.5997013
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
67.76800
</td>
<td style="text-align:right;">
30964245
</td>
<td style="text-align:right;">
4903.2191
</td>
<td style="text-align:right;">
0.5989402
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
69.97800
</td>
<td style="text-align:right;">
20711375
</td>
<td style="text-align:right;">
3726.0635
</td>
<td style="text-align:right;">
0.5984909
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
59.92300
</td>
<td style="text-align:right;">
202182
</td>
<td style="text-align:right;">
14804.6727
</td>
<td style="text-align:right;">
0.5984762
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
69.10000
</td>
<td style="text-align:right;">
17647518
</td>
<td style="text-align:right;">
4106.5253
</td>
<td style="text-align:right;">
0.5979692
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
57.44200
</td>
<td style="text-align:right;">
2721783
</td>
<td style="text-align:right;">
21951.2118
</td>
<td style="text-align:right;">
0.5972291
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
70.19800
</td>
<td style="text-align:right;">
7483763
</td>
<td style="text-align:right;">
3548.3308
</td>
<td style="text-align:right;">
0.5968041
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
69.95700
</td>
<td style="text-align:right;">
7992357
</td>
<td style="text-align:right;">
3614.1013
</td>
<td style="text-align:right;">
0.5960915
</td>
</tr>
<tr>
<td style="text-align:left;">
Ireland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
66.91000
</td>
<td style="text-align:right;">
2952156
</td>
<td style="text-align:right;">
5210.2803
</td>
<td style="text-align:right;">
0.5955842
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
67.04600
</td>
<td style="text-align:right;">
1691210
</td>
<td style="text-align:right;">
5107.1974
</td>
<td style="text-align:right;">
0.5954013
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
69.77200
</td>
<td style="text-align:right;">
4526235
</td>
<td style="text-align:right;">
3645.3796
</td>
<td style="text-align:right;">
0.5951405
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
67.65000
</td>
<td style="text-align:right;">
3305200
</td>
<td style="text-align:right;">
4692.6483
</td>
<td style="text-align:right;">
0.5948088
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
66.14600
</td>
<td style="text-align:right;">
58179144
</td>
<td style="text-align:right;">
5678.3483
</td>
<td style="text-align:right;">
0.5947019
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
64.34200
</td>
<td style="text-align:right;">
8365850
</td>
<td style="text-align:right;">
7213.7913
</td>
<td style="text-align:right;">
0.5944988
</td>
</tr>
<tr>
<td style="text-align:left;">
Uruguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
66.07100
</td>
<td style="text-align:right;">
2252965
</td>
<td style="text-align:right;">
5716.7667
</td>
<td style="text-align:right;">
0.5944909
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
69.86000
</td>
<td style="text-align:right;">
4086000
</td>
<td style="text-align:right;">
3528.4813
</td>
<td style="text-align:right;">
0.5935229
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
68.22500
</td>
<td style="text-align:right;">
4483945
</td>
<td style="text-align:right;">
4196.4111
</td>
<td style="text-align:right;">
0.5919336
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
64.39900
</td>
<td style="text-align:right;">
19610538
</td>
<td style="text-align:right;">
6856.8562
</td>
<td style="text-align:right;">
0.5916265
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
65.79900
</td>
<td style="text-align:right;">
23254956
</td>
<td style="text-align:right;">
5681.3585
</td>
<td style="text-align:right;">
0.5916184
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
66.21600
</td>
<td style="text-align:right;">
1616384
</td>
<td style="text-align:right;">
5364.2497
</td>
<td style="text-align:right;">
0.5914123
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
67.29800
</td>
<td style="text-align:right;">
56667095
</td>
<td style="text-align:right;">
4616.8965
</td>
<td style="text-align:right;">
0.5905748
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
67.05200
</td>
<td style="text-align:right;">
10599793
</td>
<td style="text-align:right;">
4756.7638
</td>
<td style="text-align:right;">
0.5904973
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
70.81500
</td>
<td style="text-align:right;">
19576783
</td>
<td style="text-align:right;">
3015.3788
</td>
<td style="text-align:right;">
0.5900627
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
68.54000
</td>
<td style="text-align:right;">
2260000
</td>
<td style="text-align:right;">
3907.1562
</td>
<td style="text-align:right;">
0.5895754
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
72.17800
</td>
<td style="text-align:right;">
4256013
</td>
<td style="text-align:right;">
2546.7814
</td>
<td style="text-align:right;">
0.5887409
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
66.80000
</td>
<td style="text-align:right;">
18680721
</td>
<td style="text-align:right;">
4734.9976
</td>
<td style="text-align:right;">
0.5879594
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
65.40000
</td>
<td style="text-align:right;">
960155
</td>
<td style="text-align:right;">
5621.3685
</td>
<td style="text-align:right;">
0.5873088
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
60.19000
</td>
<td style="text-align:right;">
880397
</td>
<td style="text-align:right;">
11864.4084
</td>
<td style="text-align:right;">
0.5872829
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
64.53100
</td>
<td style="text-align:right;">
7616060
</td>
<td style="text-align:right;">
6289.6292
</td>
<td style="text-align:right;">
0.5870439
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
62.74500
</td>
<td style="text-align:right;">
1342614
</td>
<td style="text-align:right;">
7954.1116
</td>
<td style="text-align:right;">
0.5861184
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
68.93000
</td>
<td style="text-align:right;">
2509048
</td>
<td style="text-align:right;">
3533.0039
</td>
<td style="text-align:right;">
0.5857136
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
69.61500
</td>
<td style="text-align:right;">
31167783
</td>
<td style="text-align:right;">
3258.4956
</td>
<td style="text-align:right;">
0.5856779
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
65.61000
</td>
<td style="text-align:right;">
1665128
</td>
<td style="text-align:right;">
5246.1075
</td>
<td style="text-align:right;">
0.5844801
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
69.24900
</td>
<td style="text-align:right;">
13219062
</td>
<td style="text-align:right;">
3340.5428
</td>
<td style="text-align:right;">
0.5843898
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
66.66000
</td>
<td style="text-align:right;">
29841614
</td>
<td style="text-align:right;">
4564.8024
</td>
<td style="text-align:right;">
0.5841893
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
64.13400
</td>
<td style="text-align:right;">
20195924
</td>
<td style="text-align:right;">
6360.9434
</td>
<td style="text-align:right;">
0.5841844
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
67.06400
</td>
<td style="text-align:right;">
492095
</td>
<td style="text-align:right;">
4319.8041
</td>
<td style="text-align:right;">
0.5838820
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
66.79800
</td>
<td style="text-align:right;">
5274649
</td>
<td style="text-align:right;">
4444.2317
</td>
<td style="text-align:right;">
0.5835390
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
63.33600
</td>
<td style="text-align:right;">
128962939
</td>
<td style="text-align:right;">
7030.8359
</td>
<td style="text-align:right;">
0.5835114
</td>
</tr>
<tr>
<td style="text-align:left;">
Italy
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
65.94000
</td>
<td style="text-align:right;">
47666000
</td>
<td style="text-align:right;">
4931.4042
</td>
<td style="text-align:right;">
0.5831772
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
66.32200
</td>
<td style="text-align:right;">
9803875
</td>
<td style="text-align:right;">
4684.3138
</td>
<td style="text-align:right;">
0.5830098
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
67.21700
</td>
<td style="text-align:right;">
66134291
</td>
<td style="text-align:right;">
4173.1818
</td>
<td style="text-align:right;">
0.5828000
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
71.58100
</td>
<td style="text-align:right;">
3326498
</td>
<td style="text-align:right;">
2497.4379
</td>
<td style="text-align:right;">
0.5824147
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
66.65300
</td>
<td style="text-align:right;">
27764644
</td>
<td style="text-align:right;">
4397.5757
</td>
<td style="text-align:right;">
0.5815406
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
66.87400
</td>
<td style="text-align:right;">
3366439
</td>
<td style="text-align:right;">
4258.5036
</td>
<td style="text-align:right;">
0.5812337
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
67.37800
</td>
<td style="text-align:right;">
3886512
</td>
<td style="text-align:right;">
3998.8757
</td>
<td style="text-align:right;">
0.5812060
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
67.15900
</td>
<td style="text-align:right;">
16325320
</td>
<td style="text-align:right;">
4106.3012
</td>
<td style="text-align:right;">
0.5811686
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
66.45800
</td>
<td style="text-align:right;">
22430449
</td>
<td style="text-align:right;">
4446.3809
</td>
<td style="text-align:right;">
0.5806022
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
65.24600
</td>
<td style="text-align:right;">
7254373
</td>
<td style="text-align:right;">
5180.7559
</td>
<td style="text-align:right;">
0.5803868
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
65.77000
</td>
<td style="text-align:right;">
28235346
</td>
<td style="text-align:right;">
4734.2530
</td>
<td style="text-align:right;">
0.5788828
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
70.45700
</td>
<td style="text-align:right;">
18698655
</td>
<td style="text-align:right;">
2664.4773
</td>
<td style="text-align:right;">
0.5780136
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
63.87000
</td>
<td style="text-align:right;">
2186894
</td>
<td style="text-align:right;">
6006.9830
</td>
<td style="text-align:right;">
0.5779764
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
63.62200
</td>
<td style="text-align:right;">
1151184
</td>
<td style="text-align:right;">
6205.8839
</td>
<td style="text-align:right;">
0.5778877
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
63.04000
</td>
<td style="text-align:right;">
51889696
</td>
<td style="text-align:right;">
6642.8814
</td>
<td style="text-align:right;">
0.5770629
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
70.30300
</td>
<td style="text-align:right;">
82995088
</td>
<td style="text-align:right;">
2650.9211
</td>
<td style="text-align:right;">
0.5763773
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
68.01500
</td>
<td style="text-align:right;">
3867409
</td>
<td style="text-align:right;">
3431.5936
</td>
<td style="text-align:right;">
0.5758784
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
70.83600
</td>
<td style="text-align:right;">
5146848
</td>
<td style="text-align:right;">
2474.5488
</td>
<td style="text-align:right;">
0.5756747
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
65.86900
</td>
<td style="text-align:right;">
2820042
</td>
<td style="text-align:right;">
4448.6799
</td>
<td style="text-align:right;">
0.5754919
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
64.90000
</td>
<td style="text-align:right;">
887498
</td>
<td style="text-align:right;">
4997.5240
</td>
<td style="text-align:right;">
0.5748784
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
66.89400
</td>
<td style="text-align:right;">
7724976
</td>
<td style="text-align:right;">
3810.4193
</td>
<td style="text-align:right;">
0.5736724
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
68.56500
</td>
<td style="text-align:right;">
6677328
</td>
<td style="text-align:right;">
3099.7287
</td>
<td style="text-align:right;">
0.5732821
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
62.36100
</td>
<td style="text-align:right;">
55984294
</td>
<td style="text-align:right;">
6809.4067
</td>
<td style="text-align:right;">
0.5724533
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
61.88800
</td>
<td style="text-align:right;">
39964159
</td>
<td style="text-align:right;">
7225.0693
</td>
<td style="text-align:right;">
0.5719252
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
60.77000
</td>
<td style="text-align:right;">
8143375
</td>
<td style="text-align:right;">
8422.9742
</td>
<td style="text-align:right;">
0.5712894
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovak Republic
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
64.36000
</td>
<td style="text-align:right;">
3558137
</td>
<td style="text-align:right;">
5074.6591
</td>
<td style="text-align:right;">
0.5711204
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
68.45700
</td>
<td style="text-align:right;">
7351181
</td>
<td style="text-align:right;">
3044.2142
</td>
<td style="text-align:right;">
0.5710924
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
67.69000
</td>
<td style="text-align:right;">
2263554
</td>
<td style="text-align:right;">
3313.4222
</td>
<td style="text-align:right;">
0.5706596
</td>
</tr>
<tr>
<td style="text-align:left;">
Hungary
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
64.03000
</td>
<td style="text-align:right;">
9504000
</td>
<td style="text-align:right;">
5263.6738
</td>
<td style="text-align:right;">
0.5706275
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
65.50000
</td>
<td style="text-align:right;">
91563009
</td>
<td style="text-align:right;">
4317.6944
</td>
<td style="text-align:right;">
0.5702320
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
64.27400
</td>
<td style="text-align:right;">
461633
</td>
<td style="text-align:right;">
5047.6586
</td>
<td style="text-align:right;">
0.5700007
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
66.71100
</td>
<td style="text-align:right;">
992040
</td>
<td style="text-align:right;">
3688.0377
</td>
<td style="text-align:right;">
0.5698380
</td>
</tr>
<tr>
<td style="text-align:left;">
Slovenia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
65.57000
</td>
<td style="text-align:right;">
1489518
</td>
<td style="text-align:right;">
4215.0417
</td>
<td style="text-align:right;">
0.5692004
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
64.76600
</td>
<td style="text-align:right;">
36436000
</td>
<td style="text-align:right;">
4657.2210
</td>
<td style="text-align:right;">
0.5689409
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
63.44100
</td>
<td style="text-align:right;">
9717524
</td>
<td style="text-align:right;">
5494.0244
</td>
<td style="text-align:right;">
0.5682045
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
68.58800
</td>
<td style="text-align:right;">
211060000
</td>
<td style="text-align:right;">
2873.9129
</td>
<td style="text-align:right;">
0.5680785
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
73.01700
</td>
<td style="text-align:right;">
80908147
</td>
<td style="text-align:right;">
1764.4567
</td>
<td style="text-align:right;">
0.5677145
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
60.83400
</td>
<td style="text-align:right;">
35933379
</td>
<td style="text-align:right;">
7825.8234
</td>
<td style="text-align:right;">
0.5672385
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
53.88600
</td>
<td style="text-align:right;">
6472756
</td>
<td style="text-align:right;">
24837.4287
</td>
<td style="text-align:right;">
0.5671803
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
67.65900
</td>
<td style="text-align:right;">
5867957
</td>
<td style="text-align:right;">
3160.4549
</td>
<td style="text-align:right;">
0.5670721
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
65.42400
</td>
<td style="text-align:right;">
1588717
</td>
<td style="text-align:right;">
4161.7278
</td>
<td style="text-align:right;">
0.5670669
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
64.39000
</td>
<td style="text-align:right;">
9019800
</td>
<td style="text-align:right;">
4727.9549
</td>
<td style="text-align:right;">
0.5666474
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
70.42600
</td>
<td style="text-align:right;">
1230075000
</td>
<td style="text-align:right;">
2289.2341
</td>
<td style="text-align:right;">
0.5666410
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
56.56400
</td>
<td style="text-align:right;">
753874
</td>
<td style="text-align:right;">
15113.3619
</td>
<td style="text-align:right;">
0.5661425
</td>
</tr>
<tr>
<td style="text-align:left;">
Israel
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
65.39000
</td>
<td style="text-align:right;">
1620914
</td>
<td style="text-align:right;">
4086.5221
</td>
<td style="text-align:right;">
0.5655320
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
62.32500
</td>
<td style="text-align:right;">
6640752
</td>
<td style="text-align:right;">
6092.1744
</td>
<td style="text-align:right;">
0.5649081
</td>
</tr>
<tr>
<td style="text-align:left;">
Argentina
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
62.48500
</td>
<td style="text-align:right;">
17876956
</td>
<td style="text-align:right;">
5911.3151
</td>
<td style="text-align:right;">
0.5643998
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
64.77000
</td>
<td style="text-align:right;">
3991242
</td>
<td style="text-align:right;">
4338.2316
</td>
<td style="text-align:right;">
0.5641964
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
57.70200
</td>
<td style="text-align:right;">
35480679
</td>
<td style="text-align:right;">
11888.5951
</td>
<td style="text-align:right;">
0.5631293
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
61.48900
</td>
<td style="text-align:right;">
114313951
</td>
<td style="text-align:right;">
6660.1187
</td>
<td style="text-align:right;">
0.5630309
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
67.66000
</td>
<td style="text-align:right;">
28529501
</td>
<td style="text-align:right;">
2982.1019
</td>
<td style="text-align:right;">
0.5629929
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
65.55400
</td>
<td style="text-align:right;">
9119152
</td>
<td style="text-align:right;">
3822.1371
</td>
<td style="text-align:right;">
0.5623901
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
70.37900
</td>
<td style="text-align:right;">
17587060
</td>
<td style="text-align:right;">
2153.7392
</td>
<td style="text-align:right;">
0.5617969
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
65.79800
</td>
<td style="text-align:right;">
1750200
</td>
<td style="text-align:right;">
3674.7356
</td>
<td style="text-align:right;">
0.5617920
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
61.31000
</td>
<td style="text-align:right;">
7278866
</td>
<td style="text-align:right;">
6679.6233
</td>
<td style="text-align:right;">
0.5615784
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
64.40600
</td>
<td style="text-align:right;">
1425876
</td>
<td style="text-align:right;">
4336.0321
</td>
<td style="text-align:right;">
0.5609917
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
66.97400
</td>
<td style="text-align:right;">
11242847
</td>
<td style="text-align:right;">
3116.7743
</td>
<td style="text-align:right;">
0.5603615
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
63.10800
</td>
<td style="text-align:right;">
52881328
</td>
<td style="text-align:right;">
5089.0437
</td>
<td style="text-align:right;">
0.5601962
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
61.40600
</td>
<td style="text-align:right;">
18125129
</td>
<td style="text-align:right;">
6434.5018
</td>
<td style="text-align:right;">
0.5600699
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
65.25600
</td>
<td style="text-align:right;">
12845381
</td>
<td style="text-align:right;">
3827.9216
</td>
<td style="text-align:right;">
0.5599362
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
56.73500
</td>
<td style="text-align:right;">
1454867
</td>
<td style="text-align:right;">
13206.4845
</td>
<td style="text-align:right;">
0.5598956
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
63.72800
</td>
<td style="text-align:right;">
474528
</td>
<td style="text-align:right;">
4649.5938
</td>
<td style="text-align:right;">
0.5597139
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
56.92300
</td>
<td style="text-align:right;">
171863
</td>
<td style="text-align:right;">
12753.2751
</td>
<td style="text-align:right;">
0.5596835
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
57.36700
</td>
<td style="text-align:right;">
1004533
</td>
<td style="text-align:right;">
11848.3439
</td>
<td style="text-align:right;">
0.5596576
</td>
</tr>
<tr>
<td style="text-align:left;">
Greece
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
65.86000
</td>
<td style="text-align:right;">
7733250
</td>
<td style="text-align:right;">
3530.6901
</td>
<td style="text-align:right;">
0.5595822
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
64.07100
</td>
<td style="text-align:right;">
1405486
</td>
<td style="text-align:right;">
4421.0091
</td>
<td style="text-align:right;">
0.5593671
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
68.56400
</td>
<td style="text-align:right;">
75012988
</td>
<td style="text-align:right;">
2536.5349
</td>
<td style="text-align:right;">
0.5589748
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
60.23600
</td>
<td style="text-align:right;">
42835005
</td>
<td style="text-align:right;">
7479.1882
</td>
<td style="text-align:right;">
0.5588242
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
62.09400
</td>
<td style="text-align:right;">
1886848
</td>
<td style="text-align:right;">
5714.5606
</td>
<td style="text-align:right;">
0.5586819
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
66.80300
</td>
<td style="text-align:right;">
2874127
</td>
<td style="text-align:right;">
3095.7723
</td>
<td style="text-align:right;">
0.5584610
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
67.45000
</td>
<td style="text-align:right;">
3819000
</td>
<td style="text-align:right;">
2860.1698
</td>
<td style="text-align:right;">
0.5583168
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
66.35300
</td>
<td style="text-align:right;">
2984494
</td>
<td style="text-align:right;">
3248.3733
</td>
<td style="text-align:right;">
0.5580197
</td>
</tr>
<tr>
<td style="text-align:left;">
Spain
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
64.94000
</td>
<td style="text-align:right;">
28549870
</td>
<td style="text-align:right;">
3834.0347
</td>
<td style="text-align:right;">
0.5573325
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
56.76100
</td>
<td style="text-align:right;">
1299304
</td>
<td style="text-align:right;">
12521.7139
</td>
<td style="text-align:right;">
0.5570089
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
64.93000
</td>
<td style="text-align:right;">
913025
</td>
<td style="text-align:right;">
3710.9830
</td>
<td style="text-align:right;">
0.5550438
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
66.61000
</td>
<td style="text-align:right;">
7651254
</td>
<td style="text-align:right;">
3008.6707
</td>
<td style="text-align:right;">
0.5548704
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
66.39900
</td>
<td style="text-align:right;">
5077347
</td>
<td style="text-align:right;">
3081.6946
</td>
<td style="text-align:right;">
0.5547689
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
59.62000
</td>
<td style="text-align:right;">
43072751
</td>
<td style="text-align:right;">
7608.3346
</td>
<td style="text-align:right;">
0.5541710
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
63.37300
</td>
<td style="text-align:right;">
8486949
</td>
<td style="text-align:right;">
4439.4508
</td>
<td style="text-align:right;">
0.5535476
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
57.90700
</td>
<td style="text-align:right;">
6702668
</td>
<td style="text-align:right;">
9802.4665
</td>
<td style="text-align:right;">
0.5535095
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
67.50000
</td>
<td style="text-align:right;">
13648692
</td>
<td style="text-align:right;">
2643.8587
</td>
<td style="text-align:right;">
0.5532097
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
64.59000
</td>
<td style="text-align:right;">
9410494
</td>
<td style="text-align:right;">
3761.8377
</td>
<td style="text-align:right;">
0.5530517
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
66.04100
</td>
<td style="text-align:right;">
199278000
</td>
<td style="text-align:right;">
3119.3356
</td>
<td style="text-align:right;">
0.5526116
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
61.36800
</td>
<td style="text-align:right;">
20033753
</td>
<td style="text-align:right;">
5745.1602
</td>
<td style="text-align:right;">
0.5524907
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
63.73900
</td>
<td style="text-align:right;">
2347031
</td>
<td style="text-align:right;">
4161.4160
</td>
<td style="text-align:right;">
0.5524571
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
64.75000
</td>
<td style="text-align:right;">
2736300
</td>
<td style="text-align:right;">
3629.0765
</td>
<td style="text-align:right;">
0.5520020
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
64.10000
</td>
<td style="text-align:right;">
17829327
</td>
<td style="text-align:right;">
3943.3702
</td>
<td style="text-align:right;">
0.5519980
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
62.61000
</td>
<td style="text-align:right;">
1535090
</td>
<td style="text-align:right;">
4756.5258
</td>
<td style="text-align:right;">
0.5513753
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
66.08400
</td>
<td style="text-align:right;">
52910342
</td>
<td style="text-align:right;">
2982.6538
</td>
<td style="text-align:right;">
0.5498918
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
68.42600
</td>
<td style="text-align:right;">
4609572
</td>
<td style="text-align:right;">
2253.0230
</td>
<td style="text-align:right;">
0.5494145
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
52.79000
</td>
<td style="text-align:right;">
706367
</td>
<td style="text-align:right;">
21745.5733
</td>
<td style="text-align:right;">
0.5483451
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
58.16100
</td>
<td style="text-align:right;">
31140029
</td>
<td style="text-align:right;">
8568.2662
</td>
<td style="text-align:right;">
0.5477971
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
66.04600
</td>
<td style="text-align:right;">
6655297
</td>
<td style="text-align:right;">
2899.8422
</td>
<td style="text-align:right;">
0.5476415
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
63.83700
</td>
<td style="text-align:right;">
25094412
</td>
<td style="text-align:right;">
3815.8079
</td>
<td style="text-align:right;">
0.5475499
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
63.15400
</td>
<td style="text-align:right;">
4842194
</td>
<td style="text-align:right;">
4140.4421
</td>
<td style="text-align:right;">
0.5470547
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
63.98300
</td>
<td style="text-align:right;">
14781241
</td>
<td style="text-align:right;">
3701.6215
</td>
<td style="text-align:right;">
0.5467804
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
52.77300
</td>
<td style="text-align:right;">
2183877
</td>
<td style="text-align:right;">
21011.4972
</td>
<td style="text-align:right;">
0.5462837
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
61.68500
</td>
<td style="text-align:right;">
7271135
</td>
<td style="text-align:right;">
4981.0909
</td>
<td style="text-align:right;">
0.5461889
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
63.67400
</td>
<td style="text-align:right;">
59402198
</td>
<td style="text-align:right;">
3794.7552
</td>
<td style="text-align:right;">
0.5457854
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
66.22000
</td>
<td style="text-align:right;">
1984060
</td>
<td style="text-align:right;">
2760.1969
</td>
<td style="text-align:right;">
0.5456851
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
64.04800
</td>
<td style="text-align:right;">
6734098
</td>
<td style="text-align:right;">
3560.2332
</td>
<td style="text-align:right;">
0.5447416
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
65.39300
</td>
<td style="text-align:right;">
25798239
</td>
<td style="text-align:right;">
2948.0473
</td>
<td style="text-align:right;">
0.5433482
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
56.95000
</td>
<td style="text-align:right;">
10061506
</td>
<td style="text-align:right;">
9576.0376
</td>
<td style="text-align:right;">
0.5429776
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
60.11000
</td>
<td style="text-align:right;">
47995559
</td>
<td style="text-align:right;">
5754.7339
</td>
<td style="text-align:right;">
0.5412691
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
69.01100
</td>
<td style="text-align:right;">
16495304
</td>
<td style="text-align:right;">
1876.7668
</td>
<td style="text-align:right;">
0.5409966
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
63.88300
</td>
<td style="text-align:right;">
8445134
</td>
<td style="text-align:right;">
3413.2627
</td>
<td style="text-align:right;">
0.5405372
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
59.48900
</td>
<td style="text-align:right;">
1647412
</td>
<td style="text-align:right;">
6089.7869
</td>
<td style="text-align:right;">
0.5391786
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
61.48400
</td>
<td style="text-align:right;">
970347
</td>
<td style="text-align:right;">
4551.1421
</td>
<td style="text-align:right;">
0.5386366
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
64.49200
</td>
<td style="text-align:right;">
4372203
</td>
<td style="text-align:right;">
3023.0967
</td>
<td style="text-align:right;">
0.5375480
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
60.52300
</td>
<td style="text-align:right;">
8858908
</td>
<td style="text-align:right;">
5106.6543
</td>
<td style="text-align:right;">
0.5374672
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
64.28000
</td>
<td style="text-align:right;">
2227000
</td>
<td style="text-align:right;">
3081.9598
</td>
<td style="text-align:right;">
0.5370702
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
65.81500
</td>
<td style="text-align:right;">
2614104
</td>
<td style="text-align:right;">
2523.3380
</td>
<td style="text-align:right;">
0.5362062
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
65.48300
</td>
<td style="text-align:right;">
169270617
</td>
<td style="text-align:right;">
2605.9476
</td>
<td style="text-align:right;">
0.5356953
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
61.80000
</td>
<td style="text-align:right;">
764900
</td>
<td style="text-align:right;">
4100.3934
</td>
<td style="text-align:right;">
0.5347013
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
66.45800
</td>
<td style="text-align:right;">
67185766
</td>
<td style="text-align:right;">
2279.3240
</td>
<td style="text-align:right;">
0.5344150
</td>
</tr>
<tr>
<td style="text-align:left;">
Cuba
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
59.42100
</td>
<td style="text-align:right;">
6007797
</td>
<td style="text-align:right;">
5586.5388
</td>
<td style="text-align:right;">
0.5332317
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
62.84200
</td>
<td style="text-align:right;">
1345187
</td>
<td style="text-align:right;">
3460.9370
</td>
<td style="text-align:right;">
0.5326355
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
70.67200
</td>
<td style="text-align:right;">
76048996
</td>
<td style="text-align:right;">
1385.8968
</td>
<td style="text-align:right;">
0.5317312
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
58.44700
</td>
<td style="text-align:right;">
15990099
</td>
<td style="text-align:right;">
6281.2909
</td>
<td style="text-align:right;">
0.5316166
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
61.99900
</td>
<td style="text-align:right;">
1554253
</td>
<td style="text-align:right;">
3804.5380
</td>
<td style="text-align:right;">
0.5315940
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
61.03600
</td>
<td style="text-align:right;">
47328791
</td>
<td style="text-align:right;">
4241.3563
</td>
<td style="text-align:right;">
0.5302368
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
68.75700
</td>
<td style="text-align:right;">
15410151
</td>
<td style="text-align:right;">
1648.0798
</td>
<td style="text-align:right;">
0.5297132
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
68.69000
</td>
<td style="text-align:right;">
1164970000
</td>
<td style="text-align:right;">
1655.7842
</td>
<td style="text-align:right;">
0.5295302
</td>
</tr>
<tr>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
63.03000
</td>
<td style="text-align:right;">
86459025
</td>
<td style="text-align:right;">
3216.9563
</td>
<td style="text-align:right;">
0.5294366
</td>
</tr>
<tr>
<td style="text-align:left;">
Poland
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
61.31000
</td>
<td style="text-align:right;">
25730551
</td>
<td style="text-align:right;">
4029.3297
</td>
<td style="text-align:right;">
0.5293469
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
60.78200
</td>
<td style="text-align:right;">
7326406
</td>
<td style="text-align:right;">
4246.4860
</td>
<td style="text-align:right;">
0.5281066
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
63.72700
</td>
<td style="text-align:right;">
5968349
</td>
<td style="text-align:right;">
2861.0924
</td>
<td style="text-align:right;">
0.5275211
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
59.50400
</td>
<td style="text-align:right;">
100840058
</td>
<td style="text-align:right;">
4985.7115
</td>
<td style="text-align:right;">
0.5269347
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
61.51000
</td>
<td style="text-align:right;">
8817650
</td>
<td style="text-align:right;">
3774.5717
</td>
<td style="text-align:right;">
0.5268954
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
55.23400
</td>
<td style="text-align:right;">
30614000
</td>
<td style="text-align:right;">
9613.8186
</td>
<td style="text-align:right;">
0.5268430
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
65.84300
</td>
<td style="text-align:right;">
4017939
</td>
<td style="text-align:right;">
2170.1517
</td>
<td style="text-align:right;">
0.5261084
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
61.81700
</td>
<td style="text-align:right;">
1215725
</td>
<td style="text-align:right;">
3536.5403
</td>
<td style="text-align:right;">
0.5253372
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
64.69800
</td>
<td style="text-align:right;">
1110396331
</td>
<td style="text-align:right;">
2452.2104
</td>
<td style="text-align:right;">
0.5251818
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
61.44800
</td>
<td style="text-align:right;">
442829
</td>
<td style="text-align:right;">
3682.2599
</td>
<td style="text-align:right;">
0.5247818
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
58.79600
</td>
<td style="text-align:right;">
6298651
</td>
<td style="text-align:right;">
5280.9947
</td>
<td style="text-align:right;">
0.5241836
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
53.83200
</td>
<td style="text-align:right;">
138655
</td>
<td style="text-align:right;">
11635.7995
</td>
<td style="text-align:right;">
0.5241576
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
67.72700
</td>
<td style="text-align:right;">
21585105
</td>
<td style="text-align:right;">
1690.7568
</td>
<td style="text-align:right;">
0.5235788
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
62.05000
</td>
<td style="text-align:right;">
7693188
</td>
<td style="text-align:right;">
3326.1432
</td>
<td style="text-align:right;">
0.5233589
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
64.95100
</td>
<td style="text-align:right;">
2287985
</td>
<td style="text-align:right;">
2299.3763
</td>
<td style="text-align:right;">
0.5228883
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
64.59700
</td>
<td style="text-align:right;">
48827160
</td>
<td style="text-align:right;">
2393.2198
</td>
<td style="text-align:right;">
0.5227260
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
60.54200
</td>
<td style="text-align:right;">
414024
</td>
<td style="text-align:right;">
4021.1757
</td>
<td style="text-align:right;">
0.5225885
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
63.17900
</td>
<td style="text-align:right;">
1445929
</td>
<td style="text-align:right;">
2843.1044
</td>
<td style="text-align:right;">
0.5225704
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
64.82000
</td>
<td style="text-align:right;">
1728137
</td>
<td style="text-align:right;">
2312.8890
</td>
<td style="text-align:right;">
0.5222287
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
62.61200
</td>
<td style="text-align:right;">
33505000
</td>
<td style="text-align:right;">
3030.8767
</td>
<td style="text-align:right;">
0.5220454
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
63.01000
</td>
<td style="text-align:right;">
11441462
</td>
<td style="text-align:right;">
2849.0948
</td>
<td style="text-align:right;">
0.5213105
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
59.54500
</td>
<td style="text-align:right;">
27499638
</td>
<td style="text-align:right;">
4471.0619
</td>
<td style="text-align:right;">
0.5205504
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
60.83500
</td>
<td style="text-align:right;">
1278184
</td>
<td style="text-align:right;">
3693.7313
</td>
<td style="text-align:right;">
0.5197435
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
55.52700
</td>
<td style="text-align:right;">
27129932
</td>
<td style="text-align:right;">
8028.6514
</td>
<td style="text-align:right;">
0.5192318
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
60.76500
</td>
<td style="text-align:right;">
1261091
</td>
<td style="text-align:right;">
3682.8315
</td>
<td style="text-align:right;">
0.5189587
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
65.03300
</td>
<td style="text-align:right;">
2674234
</td>
<td style="text-align:right;">
2140.7393
</td>
<td style="text-align:right;">
0.5187132
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
61.62300
</td>
<td style="text-align:right;">
22542890
</td>
<td style="text-align:right;">
3264.6600
</td>
<td style="text-align:right;">
0.5185616
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
64.79000
</td>
<td style="text-align:right;">
3585000
</td>
<td style="text-align:right;">
2172.3524
</td>
<td style="text-align:right;">
0.5177628
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
59.50700
</td>
<td style="text-align:right;">
42404033
</td>
<td style="text-align:right;">
4269.1223
</td>
<td style="text-align:right;">
0.5173578
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
62.67700
</td>
<td style="text-align:right;">
22987397
</td>
<td style="text-align:right;">
2755.0470
</td>
<td style="text-align:right;">
0.5163673
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
67.29700
</td>
<td style="text-align:right;">
23301725
</td>
<td style="text-align:right;">
1593.0655
</td>
<td style="text-align:right;">
0.5160889
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
62.00800
</td>
<td style="text-align:right;">
3344353
</td>
<td style="text-align:right;">
2955.9844
</td>
<td style="text-align:right;">
0.5153958
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
54.45900
</td>
<td style="text-align:right;">
8519282
</td>
<td style="text-align:right;">
8931.4598
</td>
<td style="text-align:right;">
0.5152808
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
57.47000
</td>
<td style="text-align:right;">
2554598
</td>
<td style="text-align:right;">
5486.3711
</td>
<td style="text-align:right;">
0.5146424
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
62.94400
</td>
<td style="text-align:right;">
851334
</td>
<td style="text-align:right;">
2575.4842
</td>
<td style="text-align:right;">
0.5141548
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
50.22700
</td>
<td style="text-align:right;">
1759224
</td>
<td style="text-align:right;">
18772.7517
</td>
<td style="text-align:right;">
0.5140431
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
59.79700
</td>
<td style="text-align:right;">
52799062
</td>
<td style="text-align:right;">
3885.4607
</td>
<td style="text-align:right;">
0.5140225
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
61.19500
</td>
<td style="text-align:right;">
7932503
</td>
<td style="text-align:right;">
3195.4846
</td>
<td style="text-align:right;">
0.5135968
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
64.36100
</td>
<td style="text-align:right;">
2009813
</td>
<td style="text-align:right;">
2148.0271
</td>
<td style="text-align:right;">
0.5135807
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
66.66200
</td>
<td style="text-align:right;">
22215365
</td>
<td style="text-align:right;">
1646.7582
</td>
<td style="text-align:right;">
0.5135174
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
64.15100
</td>
<td style="text-align:right;">
60017788
</td>
<td style="text-align:right;">
2189.6350
</td>
<td style="text-align:right;">
0.5131851
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
58.01400
</td>
<td style="text-align:right;">
17152804
</td>
<td style="text-align:right;">
4910.4168
</td>
<td style="text-align:right;">
0.5128219
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
58.13700
</td>
<td style="text-align:right;">
6395630
</td>
<td style="text-align:right;">
4820.4948
</td>
<td style="text-align:right;">
0.5127916
</td>
</tr>
<tr>
<td style="text-align:left;">
Venezuela
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
55.08800
</td>
<td style="text-align:right;">
5439568
</td>
<td style="text-align:right;">
7689.7998
</td>
<td style="text-align:right;">
0.5126560
</td>
</tr>
<tr>
<td style="text-align:left;">
Croatia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
61.21000
</td>
<td style="text-align:right;">
3882229
</td>
<td style="text-align:right;">
3119.2365
</td>
<td style="text-align:right;">
0.5121852
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
58.96800
</td>
<td style="text-align:right;">
1099010
</td>
<td style="text-align:right;">
4191.1005
</td>
<td style="text-align:right;">
0.5115404
</td>
</tr>
<tr>
<td style="text-align:left;">
Romania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
61.05000
</td>
<td style="text-align:right;">
16630000
</td>
<td style="text-align:right;">
3144.6132
</td>
<td style="text-align:right;">
0.5113609
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
58.29900
</td>
<td style="text-align:right;">
41121485
</td>
<td style="text-align:right;">
4581.6094
</td>
<td style="text-align:right;">
0.5111387
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
60.90900
</td>
<td style="text-align:right;">
3669448
</td>
<td style="text-align:right;">
3121.7608
</td>
<td style="text-align:right;">
0.5097178
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
58.20700
</td>
<td style="text-align:right;">
3790903
</td>
<td style="text-align:right;">
4520.2460
</td>
<td style="text-align:right;">
0.5095158
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
65.20000
</td>
<td style="text-align:right;">
11918938
</td>
<td style="text-align:right;">
1822.8790
</td>
<td style="text-align:right;">
0.5091455
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
59.46100
</td>
<td style="text-align:right;">
17861905
</td>
<td style="text-align:right;">
3745.6407
</td>
<td style="text-align:right;">
0.5088678
</td>
</tr>
<tr>
<td style="text-align:left;">
Hong Kong, China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
60.96000
</td>
<td style="text-align:right;">
2125900
</td>
<td style="text-align:right;">
3054.4212
</td>
<td style="text-align:right;">
0.5087620
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
62.08200
</td>
<td style="text-align:right;">
53456774
</td>
<td style="text-align:right;">
2603.2738
</td>
<td style="text-align:right;">
0.5078065
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
61.78800
</td>
<td style="text-align:right;">
5302800
</td>
<td style="text-align:right;">
2681.9889
</td>
<td style="text-align:right;">
0.5073161
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
57.92400
</td>
<td style="text-align:right;">
7961258
</td>
<td style="text-align:right;">
4519.0943
</td>
<td style="text-align:right;">
0.5070232
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
62.68100
</td>
<td style="text-align:right;">
184816000
</td>
<td style="text-align:right;">
2383.1409
</td>
<td style="text-align:right;">
0.5069464
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
58.90900
</td>
<td style="text-align:right;">
1774766
</td>
<td style="text-align:right;">
3899.5243
</td>
<td style="text-align:right;">
0.5066106
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
61.13400
</td>
<td style="text-align:right;">
1937652
</td>
<td style="text-align:right;">
2852.3516
</td>
<td style="text-align:right;">
0.5058621
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
63.61000
</td>
<td style="text-align:right;">
153403524
</td>
<td style="text-align:right;">
2092.7124
</td>
<td style="text-align:right;">
0.5058620
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
67.27400
</td>
<td style="text-align:right;">
1084035000
</td>
<td style="text-align:right;">
1378.9040
</td>
<td style="text-align:right;">
0.5058109
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
49.90100
</td>
<td style="text-align:right;">
5618198
</td>
<td style="text-align:right;">
16903.0489
</td>
<td style="text-align:right;">
0.5052617
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
51.57900
</td>
<td style="text-align:right;">
551201
</td>
<td style="text-align:right;">
12154.0897
</td>
<td style="text-align:right;">
0.5045582
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
62.69800
</td>
<td style="text-align:right;">
22211743
</td>
<td style="text-align:right;">
2280.7699
</td>
<td style="text-align:right;">
0.5042207
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
56.69600
</td>
<td style="text-align:right;">
4282586
</td>
<td style="text-align:right;">
5138.9224
</td>
<td style="text-align:right;">
0.5038534
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
59.29800
</td>
<td style="text-align:right;">
2979423
</td>
<td style="text-align:right;">
3470.3382
</td>
<td style="text-align:right;">
0.5027646
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
65.52800
</td>
<td style="text-align:right;">
199579
</td>
<td style="text-align:right;">
1598.4351
</td>
<td style="text-align:right;">
0.5027520
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
52.14300
</td>
<td style="text-align:right;">
829050
</td>
<td style="text-align:right;">
10618.0385
</td>
<td style="text-align:right;">
0.5027480
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
55.44800
</td>
<td style="text-align:right;">
13954700
</td>
<td style="text-align:right;">
5937.8273
</td>
<td style="text-align:right;">
0.5010957
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
63.19600
</td>
<td style="text-align:right;">
1770902
</td>
<td style="text-align:right;">
2046.1547
</td>
<td style="text-align:right;">
0.5010908
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
56.69500
</td>
<td style="text-align:right;">
1774735
</td>
<td style="text-align:right;">
4879.5075
</td>
<td style="text-align:right;">
0.5007901
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
59.83700
</td>
<td style="text-align:right;">
6005061
</td>
<td style="text-align:right;">
3120.8768
</td>
<td style="text-align:right;">
0.5007291
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
64.16400
</td>
<td style="text-align:right;">
3270065
</td>
<td style="text-align:right;">
1803.1515
</td>
<td style="text-align:right;">
0.5003293
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
61.55700
</td>
<td style="text-align:right;">
789309
</td>
<td style="text-align:right;">
2475.3876
</td>
<td style="text-align:right;">
0.5002872
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
53.69600
</td>
<td style="text-align:right;">
23935810
</td>
<td style="text-align:right;">
7765.9626
</td>
<td style="text-align:right;">
0.5002523
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
63.62500
</td>
<td style="text-align:right;">
2494803
</td>
<td style="text-align:right;">
1902.2521
</td>
<td style="text-align:right;">
0.4996668
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
60.02600
</td>
<td style="text-align:right;">
1112300
</td>
<td style="text-align:right;">
2990.0108
</td>
<td style="text-align:right;">
0.4996364
</td>
</tr>
<tr>
<td style="text-align:left;">
Portugal
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
59.82000
</td>
<td style="text-align:right;">
8526050
</td>
<td style="text-align:right;">
3068.3199
</td>
<td style="text-align:right;">
0.4995302
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
57.47000
</td>
<td style="text-align:right;">
2064095
</td>
<td style="text-align:right;">
4201.1949
</td>
<td style="text-align:right;">
0.4986892
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
59.95700
</td>
<td style="text-align:right;">
6893451
</td>
<td style="text-align:right;">
2961.6997
</td>
<td style="text-align:right;">
0.4984688
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
59.31900
</td>
<td style="text-align:right;">
781472
</td>
<td style="text-align:right;">
3214.8578
</td>
<td style="text-align:right;">
0.4982249
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
50.72800
</td>
<td style="text-align:right;">
1639131
</td>
<td style="text-align:right;">
12569.8518
</td>
<td style="text-align:right;">
0.4980081
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
57.04600
</td>
<td style="text-align:right;">
24001816
</td>
<td style="text-align:right;">
4390.7173
</td>
<td style="text-align:right;">
0.4976279
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
57.67800
</td>
<td style="text-align:right;">
779348
</td>
<td style="text-align:right;">
3984.8398
</td>
<td style="text-align:right;">
0.4973224
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
58.47400
</td>
<td style="text-align:right;">
962344
</td>
<td style="text-align:right;">
3553.0224
</td>
<td style="text-align:right;">
0.4972102
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
56.67800
</td>
<td style="text-align:right;">
5432424
</td>
<td style="text-align:right;">
4579.0742
</td>
<td style="text-align:right;">
0.4968939
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
53.36500
</td>
<td style="text-align:right;">
44433622
</td>
<td style="text-align:right;">
7710.9464
</td>
<td style="text-align:right;">
0.4967740
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
52.55600
</td>
<td style="text-align:right;">
1536536
</td>
<td style="text-align:right;">
8647.1423
</td>
<td style="text-align:right;">
0.4955066
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
56.02900
</td>
<td style="text-align:right;">
5703430
</td>
<td style="text-align:right;">
4879.9927
</td>
<td style="text-align:right;">
0.4949131
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
65.94900
</td>
<td style="text-align:right;">
14116836
</td>
<td style="text-align:right;">
1348.7757
</td>
<td style="text-align:right;">
0.4943334
</td>
</tr>
<tr>
<td style="text-align:left;">
Paraguay
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
62.64900
</td>
<td style="text-align:right;">
1555876
</td>
<td style="text-align:right;">
1952.3087
</td>
<td style="text-align:right;">
0.4936944
</td>
</tr>
<tr>
<td style="text-align:left;">
Serbia
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
57.99600
</td>
<td style="text-align:right;">
6860147
</td>
<td style="text-align:right;">
3581.4594
</td>
<td style="text-align:right;">
0.4936266
</td>
</tr>
<tr>
<td style="text-align:left;">
Lebanon
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
55.92800
</td>
<td style="text-align:right;">
1439529
</td>
<td style="text-align:right;">
4834.8041
</td>
<td style="text-align:right;">
0.4934798
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
62.49400
</td>
<td style="text-align:right;">
44148285
</td>
<td style="text-align:right;">
1961.2246
</td>
<td style="text-align:right;">
0.4927691
</td>
</tr>
<tr>
<td style="text-align:left;">
Trinidad and Tobago
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
59.10000
</td>
<td style="text-align:right;">
662850
</td>
<td style="text-align:right;">
3023.2719
</td>
<td style="text-align:right;">
0.4926087
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
59.96300
</td>
<td style="text-align:right;">
19764027
</td>
<td style="text-align:right;">
2678.7298
</td>
<td style="text-align:right;">
0.4922559
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
59.20100
</td>
<td style="text-align:right;">
1063506
</td>
<td style="text-align:right;">
2961.8009
</td>
<td style="text-align:right;">
0.4921857
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
58.81100
</td>
<td style="text-align:right;">
20775703
</td>
<td style="text-align:right;">
3076.2398
</td>
<td style="text-align:right;">
0.4912622
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
60.24600
</td>
<td style="text-align:right;">
701016
</td>
<td style="text-align:right;">
2529.0675
</td>
<td style="text-align:right;">
0.4909767
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
61.81800
</td>
<td style="text-align:right;">
135564834
</td>
<td style="text-align:right;">
2049.3505
</td>
<td style="text-align:right;">
0.4902648
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
59.65000
</td>
<td style="text-align:right;">
20198730
</td>
<td style="text-align:right;">
2702.6204
</td>
<td style="text-align:right;">
0.4902372
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
56.60400
</td>
<td style="text-align:right;">
4474873
</td>
<td style="text-align:right;">
4098.3442
</td>
<td style="text-align:right;">
0.4897154
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
63.06200
</td>
<td style="text-align:right;">
12267493
</td>
<td style="text-align:right;">
1712.4721
</td>
<td style="text-align:right;">
0.4883520
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
62.87900
</td>
<td style="text-align:right;">
1034172547
</td>
<td style="text-align:right;">
1746.7695
</td>
<td style="text-align:right;">
0.4882317
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
56.07400
</td>
<td style="text-align:right;">
7048426
</td>
<td style="text-align:right;">
4315.6227
</td>
<td style="text-align:right;">
0.4881428
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
57.63200
</td>
<td style="text-align:right;">
88049823
</td>
<td style="text-align:right;">
3429.8644
</td>
<td style="text-align:right;">
0.4879360
</td>
</tr>
<tr>
<td style="text-align:left;">
Bahrain
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
50.93900
</td>
<td style="text-align:right;">
120447
</td>
<td style="text-align:right;">
9867.0848
</td>
<td style="text-align:right;">
0.4872533
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
56.43300
</td>
<td style="text-align:right;">
2409073
</td>
<td style="text-align:right;">
4016.2395
</td>
<td style="text-align:right;">
0.4870482
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
55.85500
</td>
<td style="text-align:right;">
3232927
</td>
<td style="text-align:right;">
4358.5954
</td>
<td style="text-align:right;">
0.4868120
</td>
</tr>
<tr>
<td style="text-align:left;">
Singapore
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
60.39600
</td>
<td style="text-align:right;">
1127000
</td>
<td style="text-align:right;">
2315.1382
</td>
<td style="text-align:right;">
0.4866474
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
60.22200
</td>
<td style="text-align:right;">
2015133
</td>
<td style="text-align:right;">
2338.0083
</td>
<td style="text-align:right;">
0.4858611
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
60.06000
</td>
<td style="text-align:right;">
46850962
</td>
<td style="text-align:right;">
2373.2043
</td>
<td style="text-align:right;">
0.4854874
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
67.66200
</td>
<td style="text-align:right;">
69940728
</td>
<td style="text-align:right;">
989.0231
</td>
<td style="text-align:right;">
0.4853414
</td>
</tr>
<tr>
<td style="text-align:left;">
Jamaica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
58.53000
</td>
<td style="text-align:right;">
1426095
</td>
<td style="text-align:right;">
2898.5309
</td>
<td style="text-align:right;">
0.4852926
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
56.43700
</td>
<td style="text-align:right;">
977026
</td>
<td style="text-align:right;">
3876.4860
</td>
<td style="text-align:right;">
0.4850038
</td>
</tr>
<tr>
<td style="text-align:left;">
Montenegro
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
59.16400
</td>
<td style="text-align:right;">
413834
</td>
<td style="text-align:right;">
2647.5856
</td>
<td style="text-align:right;">
0.4849770
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
55.15100
</td>
<td style="text-align:right;">
2182908
</td>
<td style="text-align:right;">
4688.5933
</td>
<td style="text-align:right;">
0.4848625
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
60.30800
</td>
<td style="text-align:right;">
18701257
</td>
<td style="text-align:right;">
2234.8208
</td>
<td style="text-align:right;">
0.4837236
</td>
</tr>
<tr>
<td style="text-align:left;">
Bulgaria
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
59.60000
</td>
<td style="text-align:right;">
7274900
</td>
<td style="text-align:right;">
2444.2866
</td>
<td style="text-align:right;">
0.4835985
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
57.66600
</td>
<td style="text-align:right;">
358900
</td>
<td style="text-align:right;">
3173.7233
</td>
<td style="text-align:right;">
0.4835688
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
51.45700
</td>
<td style="text-align:right;">
7240260
</td>
<td style="text-align:right;">
8341.7378
</td>
<td style="text-align:right;">
0.4832207
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
57.00500
</td>
<td style="text-align:right;">
37492953
</td>
<td style="text-align:right;">
3450.6964
</td>
<td style="text-align:right;">
0.4829866
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
64.33700
</td>
<td style="text-align:right;">
170372
</td>
<td style="text-align:right;">
1353.0924
</td>
<td style="text-align:right;">
0.4824642
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
64.06200
</td>
<td style="text-align:right;">
150448339
</td>
<td style="text-align:right;">
1391.2538
</td>
<td style="text-align:right;">
0.4822551
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
57.40200
</td>
<td style="text-align:right;">
3055235
</td>
<td style="text-align:right;">
3203.2081
</td>
<td style="text-align:right;">
0.4819071
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
65.04200
</td>
<td style="text-align:right;">
13016733
</td>
<td style="text-align:right;">
1213.3955
</td>
<td style="text-align:right;">
0.4803794
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
60.83800
</td>
<td style="text-align:right;">
120065004
</td>
<td style="text-align:right;">
1971.8295
</td>
<td style="text-align:right;">
0.4800527
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
61.93000
</td>
<td style="text-align:right;">
3349000
</td>
<td style="text-align:right;">
1709.6837
</td>
<td style="text-align:right;">
0.4794808
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
51.92700
</td>
<td style="text-align:right;">
20997321
</td>
<td style="text-align:right;">
7114.4780
</td>
<td style="text-align:right;">
0.4790396
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
58.55600
</td>
<td style="text-align:right;">
42292929
</td>
<td style="text-align:right;">
2602.3950
</td>
<td style="text-align:right;">
0.4789447
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
59.94200
</td>
<td style="text-align:right;">
12617009
</td>
<td style="text-align:right;">
2143.5406
</td>
<td style="text-align:right;">
0.4781881
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
55.19000
</td>
<td style="text-align:right;">
35015548
</td>
<td style="text-align:right;">
4131.5466
</td>
<td style="text-align:right;">
0.4779452
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
55.56100
</td>
<td style="text-align:right;">
649901
</td>
<td style="text-align:right;">
3895.3840
</td>
<td style="text-align:right;">
0.4777568
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
59.37100
</td>
<td style="text-align:right;">
10154878
</td>
<td style="text-align:right;">
2277.7424
</td>
<td style="text-align:right;">
0.4773828
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
61.27100
</td>
<td style="text-align:right;">
2312802
</td>
<td style="text-align:right;">
1785.4020
</td>
<td style="text-align:right;">
0.4771402
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
59.63100
</td>
<td style="text-align:right;">
4671329
</td>
<td style="text-align:right;">
2189.8745
</td>
<td style="text-align:right;">
0.4770335
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
62.24700
</td>
<td style="text-align:right;">
2828858
</td>
<td style="text-align:right;">
1579.0195
</td>
<td style="text-align:right;">
0.4767880
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
56.00600
</td>
<td style="text-align:right;">
45681811
</td>
<td style="text-align:right;">
3503.7296
</td>
<td style="text-align:right;">
0.4754108
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
62.40000
</td>
<td style="text-align:right;">
10164215
</td>
<td style="text-align:right;">
1507.8613
</td>
<td style="text-align:right;">
0.4749672
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
62.74200
</td>
<td style="text-align:right;">
125911
</td>
<td style="text-align:right;">
1428.7778
</td>
<td style="text-align:right;">
0.4740549
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
63.30600
</td>
<td style="text-align:right;">
145608
</td>
<td style="text-align:right;">
1339.0760
</td>
<td style="text-align:right;">
0.4740471
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
52.46900
</td>
<td style="text-align:right;">
26538000
</td>
<td style="text-align:right;">
5906.7318
</td>
<td style="text-align:right;">
0.4738873
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
60.35100
</td>
<td style="text-align:right;">
98593
</td>
<td style="text-align:right;">
1890.2181
</td>
<td style="text-align:right;">
0.4735567
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
56.53200
</td>
<td style="text-align:right;">
1089572
</td>
<td style="text-align:right;">
3133.4093
</td>
<td style="text-align:right;">
0.4733078
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
48.69000
</td>
<td style="text-align:right;">
537977
</td>
<td style="text-align:right;">
11401.9484
</td>
<td style="text-align:right;">
0.4730623
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
54.51800
</td>
<td style="text-align:right;">
14760787
</td>
<td style="text-align:right;">
4182.6638
</td>
<td style="text-align:right;">
0.4728229
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
54.64000
</td>
<td style="text-align:right;">
4681707
</td>
<td style="text-align:right;">
4086.1141
</td>
<td style="text-align:right;">
0.4725538
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
55.32200
</td>
<td style="text-align:right;">
3800610
</td>
<td style="text-align:right;">
3632.5578
</td>
<td style="text-align:right;">
0.4716823
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
57.25100
</td>
<td style="text-align:right;">
6156369
</td>
<td style="text-align:right;">
2753.6915
</td>
<td style="text-align:right;">
0.4716356
</td>
</tr>
<tr>
<td style="text-align:left;">
Chile
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
54.74500
</td>
<td style="text-align:right;">
6377619
</td>
<td style="text-align:right;">
3939.9788
</td>
<td style="text-align:right;">
0.4713883
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
57.86300
</td>
<td style="text-align:right;">
17009885
</td>
<td style="text-align:right;">
2492.3511
</td>
<td style="text-align:right;">
0.4706763
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
61.72800
</td>
<td style="text-align:right;">
110812
</td>
<td style="text-align:right;">
1516.5255
</td>
<td style="text-align:right;">
0.4702200
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
64.26600
</td>
<td style="text-align:right;">
11737396
</td>
<td style="text-align:right;">
1135.5143
</td>
<td style="text-align:right;">
0.4702141
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
55.66500
</td>
<td style="text-align:right;">
76039390
</td>
<td style="text-align:right;">
3336.5858
</td>
<td style="text-align:right;">
0.4696863
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
61.60000
</td>
<td style="text-align:right;">
10870037
</td>
<td style="text-align:right;">
1519.6353
</td>
<td style="text-align:right;">
0.4693762
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
49.33900
</td>
<td style="text-align:right;">
43997828
</td>
<td style="text-align:right;">
9269.6578
</td>
<td style="text-align:right;">
0.4687435
</td>
</tr>
<tr>
<td style="text-align:left;">
Costa Rica
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
57.20600
</td>
<td style="text-align:right;">
926317
</td>
<td style="text-align:right;">
2627.0095
</td>
<td style="text-align:right;">
0.4684628
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
65.52500
</td>
<td style="text-align:right;">
1000281000
</td>
<td style="text-align:right;">
962.4214
</td>
<td style="text-align:right;">
0.4681545
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
61.76500
</td>
<td style="text-align:right;">
959000000
</td>
<td style="text-align:right;">
1458.8174
</td>
<td style="text-align:right;">
0.4680097
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
55.62500
</td>
<td style="text-align:right;">
1536769
</td>
<td style="text-align:right;">
3259.1790
</td>
<td style="text-align:right;">
0.4679908
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
57.29600
</td>
<td style="text-align:right;">
6701172
</td>
<td style="text-align:right;">
2571.4230
</td>
<td style="text-align:right;">
0.4679253
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
65.15200
</td>
<td style="text-align:right;">
710960
</td>
<td style="text-align:right;">
986.1479
</td>
<td style="text-align:right;">
0.4671398
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
60.13700
</td>
<td style="text-align:right;">
169276000
</td>
<td style="text-align:right;">
1748.3570
</td>
<td style="text-align:right;">
0.4669979
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
59.28000
</td>
<td style="text-align:right;">
1476505
</td>
<td style="text-align:right;">
1942.2842
</td>
<td style="text-align:right;">
0.4668282
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
54.28900
</td>
<td style="text-align:right;">
1054486
</td>
<td style="text-align:right;">
3876.7685
</td>
<td style="text-align:right;">
0.4665486
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
52.90600
</td>
<td style="text-align:right;">
2055080
</td>
<td style="text-align:right;">
4811.0604
</td>
<td style="text-align:right;">
0.4665443
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
63.78500
</td>
<td style="text-align:right;">
28901790
</td>
<td style="text-align:right;">
1091.3598
</td>
<td style="text-align:right;">
0.4640636
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
53.73800
</td>
<td style="text-align:right;">
5149581
</td>
<td style="text-align:right;">
4031.4083
</td>
<td style="text-align:right;">
0.4639996
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
51.44500
</td>
<td style="text-align:right;">
12132200
</td>
<td style="text-align:right;">
5788.0933
</td>
<td style="text-align:right;">
0.4635532
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
59.72300
</td>
<td style="text-align:right;">
14131858
</td>
<td style="text-align:right;">
1713.7787
</td>
<td style="text-align:right;">
0.4625422
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
58.02000
</td>
<td style="text-align:right;">
15826497
</td>
<td style="text-align:right;">
2117.4845
</td>
<td style="text-align:right;">
0.4621173
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
54.90700
</td>
<td style="text-align:right;">
1340458
</td>
<td style="text-align:right;">
3213.1527
</td>
<td style="text-align:right;">
0.4611378
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
53.86700
</td>
<td style="text-align:right;">
821782
</td>
<td style="text-align:right;">
3746.0809
</td>
<td style="text-align:right;">
0.4610008
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
60.40500
</td>
<td style="text-align:right;">
39276153
</td>
<td style="text-align:right;">
1524.3589
</td>
<td style="text-align:right;">
0.4604656
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
58.08900
</td>
<td style="text-align:right;">
609816
</td>
<td style="text-align:right;">
2034.0380
</td>
<td style="text-align:right;">
0.4602378
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
49.34800
</td>
<td style="text-align:right;">
495627
</td>
<td style="text-align:right;">
7703.4959
</td>
<td style="text-align:right;">
0.4593302
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
60.43000
</td>
<td style="text-align:right;">
2444741
</td>
<td style="text-align:right;">
1483.1361
</td>
<td style="text-align:right;">
0.4589331
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
58.06500
</td>
<td style="text-align:right;">
40850141
</td>
<td style="text-align:right;">
1989.3741
</td>
<td style="text-align:right;">
0.4587068
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
55.60200
</td>
<td style="text-align:right;">
5303507
</td>
<td style="text-align:right;">
2753.2860
</td>
<td style="text-align:right;">
0.4580426
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
62.97400
</td>
<td style="text-align:right;">
614382
</td>
<td style="text-align:right;">
1075.8116
</td>
<td style="text-align:right;">
0.4572234
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
57.71600
</td>
<td style="text-align:right;">
30131000
</td>
<td style="text-align:right;">
2029.2281
</td>
<td style="text-align:right;">
0.4571404
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
51.88400
</td>
<td style="text-align:right;">
1865490
</td>
<td style="text-align:right;">
4643.3935
</td>
<td style="text-align:right;">
0.4556178
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
57.48900
</td>
<td style="text-align:right;">
1756032
</td>
<td style="text-align:right;">
2000.6031
</td>
<td style="text-align:right;">
0.4544930
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
58.55000
</td>
<td style="text-align:right;">
86796
</td>
<td style="text-align:right;">
1737.5617
</td>
<td style="text-align:right;">
0.4542968
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
55.09000
</td>
<td style="text-align:right;">
308700
</td>
<td style="text-align:right;">
2769.4518
</td>
<td style="text-align:right;">
0.4541602
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
62.01300
</td>
<td style="text-align:right;">
135656790
</td>
<td style="text-align:right;">
1136.3904
</td>
<td style="text-align:right;">
0.4537793
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
60.18700
</td>
<td style="text-align:right;">
9535314
</td>
<td style="text-align:right;">
1392.3683
</td>
<td style="text-align:right;">
0.4531344
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
62.19200
</td>
<td style="text-align:right;">
10421936
</td>
<td style="text-align:right;">
1074.4720
</td>
<td style="text-align:right;">
0.4514651
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
46.63400
</td>
<td style="text-align:right;">
1630347
</td>
<td style="text-align:right;">
11003.6051
</td>
<td style="text-align:right;">
0.4513618
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
53.85900
</td>
<td style="text-align:right;">
5642224
</td>
<td style="text-align:right;">
3156.5105
</td>
<td style="text-align:right;">
0.4513399
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
58.24500
</td>
<td style="text-align:right;">
105186881
</td>
<td style="text-align:right;">
1704.6866
</td>
<td style="text-align:right;">
0.4507731
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
55.73000
</td>
<td style="text-align:right;">
18396941
</td>
<td style="text-align:right;">
2370.6200
</td>
<td style="text-align:right;">
0.4504233
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
52.53700
</td>
<td style="text-align:right;">
551425
</td>
<td style="text-align:right;">
3781.4106
</td>
<td style="text-align:right;">
0.4501315
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
56.02400
</td>
<td style="text-align:right;">
619351
</td>
<td style="text-align:right;">
2263.6111
</td>
<td style="text-align:right;">
0.4501080
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
56.52800
</td>
<td style="text-align:right;">
1613551
</td>
<td style="text-align:right;">
2110.8563
</td>
<td style="text-align:right;">
0.4500495
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
49.95100
</td>
<td style="text-align:right;">
18356657
</td>
<td style="text-align:right;">
5768.7297
</td>
<td style="text-align:right;">
0.4499172
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
54.98500
</td>
<td style="text-align:right;">
10780667
</td>
<td style="text-align:right;">
2602.6642
</td>
<td style="text-align:right;">
0.4497424
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
52.97000
</td>
<td style="text-align:right;">
3328795
</td>
<td style="text-align:right;">
3484.0620
</td>
<td style="text-align:right;">
0.4493294
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
60.91600
</td>
<td style="text-align:right;">
8502814
</td>
<td style="text-align:right;">
1201.6372
</td>
<td style="text-align:right;">
0.4492891
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
52.96200
</td>
<td style="text-align:right;">
2800947
</td>
<td style="text-align:right;">
3484.1644
</td>
<td style="text-align:right;">
0.4492632
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
54.33600
</td>
<td style="text-align:right;">
33411317
</td>
<td style="text-align:right;">
2826.3564
</td>
<td style="text-align:right;">
0.4490937
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
60.02200
</td>
<td style="text-align:right;">
22873338
</td>
<td style="text-align:right;">
1327.6089
</td>
<td style="text-align:right;">
0.4489190
</td>
</tr>
<tr>
<td style="text-align:left;">
Panama
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
55.19100
</td>
<td style="text-align:right;">
940080
</td>
<td style="text-align:right;">
2480.3803
</td>
<td style="text-align:right;">
0.4486650
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
52.30700
</td>
<td style="text-align:right;">
2747687
</td>
<td style="text-align:right;">
3776.8036
</td>
<td style="text-align:right;">
0.4480945
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
45.91400
</td>
<td style="text-align:right;">
4943029
</td>
<td style="text-align:right;">
11626.4197
</td>
<td style="text-align:right;">
0.4470222
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
61.45600
</td>
<td style="text-align:right;">
9128546
</td>
<td style="text-align:right;">
1072.5466
</td>
<td style="text-align:right;">
0.4460077
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
60.66000
</td>
<td style="text-align:right;">
527982
</td>
<td style="text-align:right;">
1173.6182
</td>
<td style="text-align:right;">
0.4459125
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
56.36900
</td>
<td style="text-align:right;">
37090298
</td>
<td style="text-align:right;">
1993.3983
</td>
<td style="text-align:right;">
0.4454271
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
59.33900
</td>
<td style="text-align:right;">
21198082
</td>
<td style="text-align:right;">
1361.9369
</td>
<td style="text-align:right;">
0.4453862
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
51.47900
</td>
<td style="text-align:right;">
1972153
</td>
<td style="text-align:right;">
4072.3248
</td>
<td style="text-align:right;">
0.4450349
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
55.11800
</td>
<td style="text-align:right;">
14485993
</td>
<td style="text-align:right;">
2323.8056
</td>
<td style="text-align:right;">
0.4443336
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
61.34000
</td>
<td style="text-align:right;">
25873917
</td>
<td style="text-align:right;">
1057.2063
</td>
<td style="text-align:right;">
0.4442468
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
59.28500
</td>
<td style="text-align:right;">
25020539
</td>
<td style="text-align:right;">
1341.9217
</td>
<td style="text-align:right;">
0.4440680
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
62.06900
</td>
<td style="text-align:right;">
47761980
</td>
<td style="text-align:right;">
944.0000
</td>
<td style="text-align:right;">
0.4422149
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
60.22300
</td>
<td style="text-align:right;">
872000000
</td>
<td style="text-align:right;">
1164.4068
</td>
<td style="text-align:right;">
0.4422065
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
55.73700
</td>
<td style="text-align:right;">
8906385
</td>
<td style="text-align:right;">
2036.8849
</td>
<td style="text-align:right;">
0.4416841
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
53.98300
</td>
<td style="text-align:right;">
9025951
</td>
<td style="text-align:right;">
2602.7102
</td>
<td style="text-align:right;">
0.4415477
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
58.76600
</td>
<td style="text-align:right;">
17661452
</td>
<td style="text-align:right;">
1348.2258
</td>
<td style="text-align:right;">
0.4404669
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
48.43700
</td>
<td style="text-align:right;">
6248643
</td>
<td style="text-align:right;">
6229.3336
</td>
<td style="text-align:right;">
0.4401502
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
56.39300
</td>
<td style="text-align:right;">
35356600
</td>
<td style="text-align:right;">
1814.1274
</td>
<td style="text-align:right;">
0.4400896
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
51.35600
</td>
<td style="text-align:right;">
4058385
</td>
<td style="text-align:right;">
3780.5467
</td>
<td style="text-align:right;">
0.4400006
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
53.31900
</td>
<td style="text-align:right;">
38783863
</td>
<td style="text-align:right;">
2785.4936
</td>
<td style="text-align:right;">
0.4398804
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
63.96736
</td>
<td style="text-align:right;">
943455000
</td>
<td style="text-align:right;">
741.2375
</td>
<td style="text-align:right;">
0.4396526
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
53.88400
</td>
<td style="text-align:right;">
2965146
</td>
<td style="text-align:right;">
2529.8423
</td>
<td style="text-align:right;">
0.4391465
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
51.15900
</td>
<td style="text-align:right;">
706640
</td>
<td style="text-align:right;">
3793.6948
</td>
<td style="text-align:right;">
0.4384975
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
47.80800
</td>
<td style="text-align:right;">
1441863
</td>
<td style="text-align:right;">
6757.0308
</td>
<td style="text-align:right;">
0.4384776
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
62.82000
</td>
<td style="text-align:right;">
62826491
</td>
<td style="text-align:right;">
820.7994
</td>
<td style="text-align:right;">
0.4384283
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
58.45000
</td>
<td style="text-align:right;">
3076000
</td>
<td style="text-align:right;">
1353.9892
</td>
<td style="text-align:right;">
0.4383577
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
58.33300
</td>
<td style="text-align:right;">
2119465
</td>
<td style="text-align:right;">
1361.3698
</td>
<td style="text-align:right;">
0.4378101
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
56.75100
</td>
<td style="text-align:right;">
4049146
</td>
<td style="text-align:right;">
1653.7230
</td>
<td style="text-align:right;">
0.4374191
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
58.19600
</td>
<td style="text-align:right;">
8307920
</td>
<td style="text-align:right;">
1367.8994
</td>
<td style="text-align:right;">
0.4370715
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
54.65500
</td>
<td style="text-align:right;">
10761098
</td>
<td style="text-align:right;">
2156.9561
</td>
<td style="text-align:right;">
0.4363657
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
55.59900
</td>
<td style="text-align:right;">
13367997
</td>
<td style="text-align:right;">
1879.4967
</td>
<td style="text-align:right;">
0.4359402
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
56.65600
</td>
<td style="text-align:right;">
10917494
</td>
<td style="text-align:right;">
1621.6936
</td>
<td style="text-align:right;">
0.4355344
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
54.79100
</td>
<td style="text-align:right;">
496374
</td>
<td style="text-align:right;">
2082.4816
</td>
<td style="text-align:right;">
0.4354491
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
49.09600
</td>
<td style="text-align:right;">
10516500
</td>
<td style="text-align:right;">
4957.0380
</td>
<td style="text-align:right;">
0.4344727
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
58.28500
</td>
<td style="text-align:right;">
34024249
</td>
<td style="text-align:right;">
1295.4607
</td>
<td style="text-align:right;">
0.4344416
</td>
</tr>
<tr>
<td style="text-align:left;">
Reunion
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
52.72400
</td>
<td style="text-align:right;">
257700
</td>
<td style="text-align:right;">
2718.8853
</td>
<td style="text-align:right;">
0.4336445
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
53.28500
</td>
<td style="text-align:right;">
65551171
</td>
<td style="text-align:right;">
2487.3660
</td>
<td style="text-align:right;">
0.4333264
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
51.40700
</td>
<td style="text-align:right;">
12760499
</td>
<td style="text-align:right;">
3246.9918
</td>
<td style="text-align:right;">
0.4323031
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
58.13700
</td>
<td style="text-align:right;">
7607651
</td>
<td style="text-align:right;">
1270.3649
</td>
<td style="text-align:right;">
0.4321556
</td>
</tr>
<tr>
<td style="text-align:left;">
Taiwan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
58.50000
</td>
<td style="text-align:right;">
8550362
</td>
<td style="text-align:right;">
1206.9479
</td>
<td style="text-align:right;">
0.4317381
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
56.48000
</td>
<td style="text-align:right;">
76595
</td>
<td style="text-align:right;">
1532.9853
</td>
<td style="text-align:right;">
0.4308769
</td>
</tr>
<tr>
<td style="text-align:left;">
Mexico
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
50.78900
</td>
<td style="text-align:right;">
30144317
</td>
<td style="text-align:right;">
3478.1255
</td>
<td style="text-align:right;">
0.4307385
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
59.44300
</td>
<td style="text-align:right;">
19167654
</td>
<td style="text-align:right;">
1044.7701
</td>
<td style="text-align:right;">
0.4297764
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
47.98500
</td>
<td style="text-align:right;">
16151549
</td>
<td style="text-align:right;">
5487.1042
</td>
<td style="text-align:right;">
0.4297111
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
57.93900
</td>
<td style="text-align:right;">
454429
</td>
<td style="text-align:right;">
1246.9074
</td>
<td style="text-align:right;">
0.4295606
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
56.72800
</td>
<td style="text-align:right;">
8078314
</td>
<td style="text-align:right;">
1441.2849
</td>
<td style="text-align:right;">
0.4291296
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
52.96100
</td>
<td style="text-align:right;">
9250831
</td>
<td style="text-align:right;">
2367.9833
</td>
<td style="text-align:right;">
0.4279823
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
63.11888
</td>
<td style="text-align:right;">
862030000
</td>
<td style="text-align:right;">
676.9001
</td>
<td style="text-align:right;">
0.4278603
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
49.32500
</td>
<td style="text-align:right;">
22874000
</td>
<td style="text-align:right;">
4187.3298
</td>
<td style="text-align:right;">
0.4278424
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
56.15900
</td>
<td style="text-align:right;">
153343000
</td>
<td style="text-align:right;">
1516.8730
</td>
<td style="text-align:right;">
0.4278109
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
59.42600
</td>
<td style="text-align:right;">
23001113
</td>
<td style="text-align:right;">
1010.8921
</td>
<td style="text-align:right;">
0.4276161
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
55.49100
</td>
<td style="text-align:right;">
1528000
</td>
<td style="text-align:right;">
1647.5117
</td>
<td style="text-align:right;">
0.4274903
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
59.68500
</td>
<td style="text-align:right;">
1803195
</td>
<td style="text-align:right;">
977.4863
</td>
<td style="text-align:right;">
0.4273938
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
52.04000
</td>
<td style="text-align:right;">
1179760
</td>
<td style="text-align:right;">
2677.9396
</td>
<td style="text-align:right;">
0.4271974
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
52.37400
</td>
<td style="text-align:right;">
7459574
</td>
<td style="text-align:right;">
2517.7365
</td>
<td style="text-align:right;">
0.4265790
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
58.45300
</td>
<td style="text-align:right;">
20550751
</td>
<td style="text-align:right;">
1111.9846
</td>
<td style="text-align:right;">
0.4264092
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
55.37300
</td>
<td style="text-align:right;">
32160729
</td>
<td style="text-align:right;">
1632.2108
</td>
<td style="text-align:right;">
0.4260439
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
62.35100
</td>
<td style="text-align:right;">
9216418
</td>
<td style="text-align:right;">
706.1573
</td>
<td style="text-align:right;">
0.4253992
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
50.02300
</td>
<td style="text-align:right;">
5079716
</td>
<td style="text-align:right;">
3548.0978
</td>
<td style="text-align:right;">
0.4252784
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
59.41200
</td>
<td style="text-align:right;">
123315288
</td>
<td style="text-align:right;">
972.7700
</td>
<td style="text-align:right;">
0.4251400
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
51.62900
</td>
<td style="text-align:right;">
1255058
</td>
<td style="text-align:right;">
2741.7963
</td>
<td style="text-align:right;">
0.4250889
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
56.15800
</td>
<td style="text-align:right;">
91462088
</td>
<td style="text-align:right;">
1443.4298
</td>
<td style="text-align:right;">
0.4249046
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
56.67100
</td>
<td style="text-align:right;">
6913545
</td>
<td style="text-align:right;">
1341.7269
</td>
<td style="text-align:right;">
0.4244795
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
56.14500
</td>
<td style="text-align:right;">
1841240
</td>
<td style="text-align:right;">
1421.6036
</td>
<td style="text-align:right;">
0.4239165
</td>
</tr>
<tr>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
55.23000
</td>
<td style="text-align:right;">
1282697
</td>
<td style="text-align:right;">
1601.0561
</td>
<td style="text-align:right;">
0.4238366
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
51.63100
</td>
<td style="text-align:right;">
1142636
</td>
<td style="text-align:right;">
2649.7150
</td>
<td style="text-align:right;">
0.4232710
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
54.31400
</td>
<td style="text-align:right;">
12467171
</td>
<td style="text-align:right;">
1793.1633
</td>
<td style="text-align:right;">
0.4232085
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
55.29200
</td>
<td style="text-align:right;">
26420307
</td>
<td style="text-align:right;">
1536.3444
</td>
<td style="text-align:right;">
0.4219397
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
54.75700
</td>
<td style="text-align:right;">
30325264
</td>
<td style="text-align:right;">
1649.5522
</td>
<td style="text-align:right;">
0.4219062
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
55.76900
</td>
<td style="text-align:right;">
7171347
</td>
<td style="text-align:right;">
1441.7207
</td>
<td style="text-align:right;">
0.4218926
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
58.55600
</td>
<td style="text-align:right;">
18418288
</td>
<td style="text-align:right;">
1005.2458
</td>
<td style="text-align:right;">
0.4210147
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
53.65500
</td>
<td style="text-align:right;">
5680812
</td>
<td style="text-align:right;">
1881.9236
</td>
<td style="text-align:right;">
0.4207697
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
50.01600
</td>
<td style="text-align:right;">
4690773
</td>
<td style="text-align:right;">
3242.5311
</td>
<td style="text-align:right;">
0.4205341
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
56.94100
</td>
<td style="text-align:right;">
3154264
</td>
<td style="text-align:right;">
1202.2014
</td>
<td style="text-align:right;">
0.4199991
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
52.09800
</td>
<td style="text-align:right;">
29788695
</td>
<td style="text-align:right;">
2322.8699
</td>
<td style="text-align:right;">
0.4199660
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
53.37300
</td>
<td style="text-align:right;">
447416
</td>
<td style="text-align:right;">
1908.2609
</td>
<td style="text-align:right;">
0.4193297
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
58.55300
</td>
<td style="text-align:right;">
788000000
</td>
<td style="text-align:right;">
976.5127
</td>
<td style="text-align:right;">
0.4192271
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
58.06100
</td>
<td style="text-align:right;">
3747553
</td>
<td style="text-align:right;">
1034.2989
</td>
<td style="text-align:right;">
0.4191762
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
44.59800
</td>
<td style="text-align:right;">
489004
</td>
<td style="text-align:right;">
8358.7620
</td>
<td style="text-align:right;">
0.4189040
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
53.63600
</td>
<td style="text-align:right;">
5756203
</td>
<td style="text-align:right;">
1823.0160
</td>
<td style="text-align:right;">
0.4188467
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
60.36300
</td>
<td style="text-align:right;">
7636524
</td>
<td style="text-align:right;">
788.8550
</td>
<td style="text-align:right;">
0.4187884
</td>
</tr>
<tr>
<td style="text-align:left;">
Sri Lanka
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
57.59300
</td>
<td style="text-align:right;">
7982342
</td>
<td style="text-align:right;">
1083.5320
</td>
<td style="text-align:right;">
0.4185829
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
49.55200
</td>
<td style="text-align:right;">
480105
</td>
<td style="text-align:right;">
3364.8366
</td>
<td style="text-align:right;">
0.4185410
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
58.39000
</td>
<td style="text-align:right;">
4320890
</td>
<td style="text-align:right;">
982.2869
</td>
<td style="text-align:right;">
0.4184181
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
52.92200
</td>
<td style="text-align:right;">
11219340
</td>
<td style="text-align:right;">
1971.7415
</td>
<td style="text-align:right;">
0.4175877
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
55.08900
</td>
<td style="text-align:right;">
6326682
</td>
<td style="text-align:right;">
1456.3095
</td>
<td style="text-align:right;">
0.4173253
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
56.15500
</td>
<td style="text-align:right;">
14500404
</td>
<td style="text-align:right;">
1267.6132
</td>
<td style="text-align:right;">
0.4172959
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
53.15700
</td>
<td style="text-align:right;">
417908
</td>
<td style="text-align:right;">
1895.0170
</td>
<td style="text-align:right;">
0.4172477
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
51.60400
</td>
<td style="text-align:right;">
384156
</td>
<td style="text-align:right;">
2377.1562
</td>
<td style="text-align:right;">
0.4172237
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
52.86200
</td>
<td style="text-align:right;">
16660670
</td>
<td style="text-align:right;">
1930.1950
</td>
<td style="text-align:right;">
0.4159434
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
55.47100
</td>
<td style="text-align:right;">
2644765
</td>
<td style="text-align:right;">
1344.5780
</td>
<td style="text-align:right;">
0.4156137
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
50.92400
</td>
<td style="text-align:right;">
2500689
</td>
<td style="text-align:right;">
2538.2694
</td>
<td style="text-align:right;">
0.4151991
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
48.63200
</td>
<td style="text-align:right;">
1590597
</td>
<td style="text-align:right;">
3634.3644
</td>
<td style="text-align:right;">
0.4146677
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
50.04000
</td>
<td style="text-align:right;">
311025
</td>
<td style="text-align:right;">
2880.1026
</td>
<td style="text-align:right;">
0.4145671
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
54.08100
</td>
<td style="text-align:right;">
9411381
</td>
<td style="text-align:right;">
1571.1347
</td>
<td style="text-align:right;">
0.4139580
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
46.98800
</td>
<td style="text-align:right;">
714775
</td>
<td style="text-align:right;">
4720.9427
</td>
<td style="text-align:right;">
0.4134331
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
53.45900
</td>
<td style="text-align:right;">
3453434
</td>
<td style="text-align:right;">
1662.1374
</td>
<td style="text-align:right;">
0.4123276
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
58.42000
</td>
<td style="text-align:right;">
5701579
</td>
<td style="text-align:right;">
882.9699
</td>
<td style="text-align:right;">
0.4121564
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
48.57000
</td>
<td style="text-align:right;">
2355805
</td>
<td style="text-align:right;">
3421.5232
</td>
<td style="text-align:right;">
0.4110905
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
60.37700
</td>
<td style="text-align:right;">
10704340
</td>
<td style="text-align:right;">
693.4208
</td>
<td style="text-align:right;">
0.4107883
</td>
</tr>
<tr>
<td style="text-align:left;">
Ecuador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
48.35700
</td>
<td style="text-align:right;">
3548753
</td>
<td style="text-align:right;">
3522.1107
</td>
<td style="text-align:right;">
0.4107449
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
54.92600
</td>
<td style="text-align:right;">
395114
</td>
<td style="text-align:right;">
1315.9808
</td>
<td style="text-align:right;">
0.4103022
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
54.11000
</td>
<td style="text-align:right;">
35610177
</td>
<td style="text-align:right;">
1463.2493
</td>
<td style="text-align:right;">
0.4101764
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
52.05300
</td>
<td style="text-align:right;">
4786986
</td>
<td style="text-align:right;">
1932.3602
</td>
<td style="text-align:right;">
0.4096385
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
59.44800
</td>
<td style="text-align:right;">
1688359
</td>
<td style="text-align:right;">
752.7497
</td>
<td style="text-align:right;">
0.4095436
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
54.42500
</td>
<td style="text-align:right;">
70787
</td>
<td style="text-align:right;">
1384.8406
</td>
<td style="text-align:right;">
0.4094467
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
55.55800
</td>
<td style="text-align:right;">
1982823
</td>
<td style="text-align:right;">
1186.1480
</td>
<td style="text-align:right;">
0.4090212
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
54.40600
</td>
<td style="text-align:right;">
7026113
</td>
<td style="text-align:right;">
1372.8779
</td>
<td style="text-align:right;">
0.4088129
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
57.50100
</td>
<td style="text-align:right;">
16278738
</td>
<td style="text-align:right;">
925.0602
</td>
<td style="text-align:right;">
0.4084578
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
54.40700
</td>
<td style="text-align:right;">
28263827
</td>
<td style="text-align:right;">
1360.4850
</td>
<td style="text-align:right;">
0.4083073
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
51.46100
</td>
<td style="text-align:right;">
5198399
</td>
<td style="text-align:right;">
2011.1595
</td>
<td style="text-align:right;">
0.4071189
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
53.55600
</td>
<td style="text-align:right;">
28227588
</td>
<td style="text-align:right;">
1492.1970
</td>
<td style="text-align:right;">
0.4070681
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
53.59900
</td>
<td style="text-align:right;">
1622136
</td>
<td style="text-align:right;">
1481.1502
</td>
<td style="text-align:right;">
0.4069807
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
52.10200
</td>
<td style="text-align:right;">
7739235
</td>
<td style="text-align:right;">
1810.0670
</td>
<td style="text-align:right;">
0.4064813
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
57.56100
</td>
<td style="text-align:right;">
4977378
</td>
<td style="text-align:right;">
886.2206
</td>
<td style="text-align:right;">
0.4063161
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
53.75400
</td>
<td style="text-align:right;">
1320500
</td>
<td style="text-align:right;">
1421.7420
</td>
<td style="text-align:right;">
0.4058690
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
48.38600
</td>
<td style="text-align:right;">
621392
</td>
<td style="text-align:right;">
3173.2156
</td>
<td style="text-align:right;">
0.4057416
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
54.77700
</td>
<td style="text-align:right;">
6066080
</td>
<td style="text-align:right;">
1232.9753
</td>
<td style="text-align:right;">
0.4054774
</td>
</tr>
<tr>
<td style="text-align:left;">
Brazil
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
50.91700
</td>
<td style="text-align:right;">
56602560
</td>
<td style="text-align:right;">
2108.9444
</td>
<td style="text-align:right;">
0.4053294
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
57.28600
</td>
<td style="text-align:right;">
16473477
</td>
<td style="text-align:right;">
894.6371
</td>
<td style="text-align:right;">
0.4049381
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
51.13700
</td>
<td style="text-align:right;">
34807417
</td>
<td style="text-align:right;">
2024.0081
</td>
<td style="text-align:right;">
0.4048944
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
48.81200
</td>
<td style="text-align:right;">
305991
</td>
<td style="text-align:right;">
2879.4681
</td>
<td style="text-align:right;">
0.4043823
</td>
</tr>
<tr>
<td style="text-align:left;">
Colombia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
50.64300
</td>
<td style="text-align:right;">
12350771
</td>
<td style="text-align:right;">
2144.1151
</td>
<td style="text-align:right;">
0.4040194
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
52.19900
</td>
<td style="text-align:right;">
14195809
</td>
<td style="text-align:right;">
1694.3375
</td>
<td style="text-align:right;">
0.4036510
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
52.88700
</td>
<td style="text-align:right;">
2308582
</td>
<td style="text-align:right;">
1532.7770
</td>
<td style="text-align:right;">
0.4034590
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
56.06100
</td>
<td style="text-align:right;">
29263397
</td>
<td style="text-align:right;">
1002.1992
</td>
<td style="text-align:right;">
0.4028988
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
49.80100
</td>
<td style="text-align:right;">
6071696
</td>
<td style="text-align:right;">
2378.2011
</td>
<td style="text-align:right;">
0.4026690
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
50.30500
</td>
<td style="text-align:right;">
4834621
</td>
<td style="text-align:right;">
2193.0371
</td>
<td style="text-align:right;">
0.4025032
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritius
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
50.98600
</td>
<td style="text-align:right;">
516556
</td>
<td style="text-align:right;">
1967.9557
</td>
<td style="text-align:right;">
0.4022095
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
46.26300
</td>
<td style="text-align:right;">
9146100
</td>
<td style="text-align:right;">
4245.2567
</td>
<td style="text-align:right;">
0.4019438
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
42.86800
</td>
<td style="text-align:right;">
4419650
</td>
<td style="text-align:right;">
8157.5912
</td>
<td style="text-align:right;">
0.4015681
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
58.81600
</td>
<td style="text-align:right;">
56142181
</td>
<td style="text-align:right;">
707.2358
</td>
<td style="text-align:right;">
0.4013744
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
56.75200
</td>
<td style="text-align:right;">
12926707
</td>
<td style="text-align:right;">
896.2260
</td>
<td style="text-align:right;">
0.4012682
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
52.04400
</td>
<td style="text-align:right;">
12772596
</td>
<td style="text-align:right;">
1648.0738
</td>
<td style="text-align:right;">
0.4009538
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
52.68100
</td>
<td style="text-align:right;">
22611552
</td>
<td style="text-align:right;">
1487.5935
</td>
<td style="text-align:right;">
0.4002481
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
50.43000
</td>
<td style="text-align:right;">
17696293
</td>
<td style="text-align:right;">
2042.0952
</td>
<td style="text-align:right;">
0.3997631
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
59.90800
</td>
<td style="text-align:right;">
45598081
</td>
<td style="text-align:right;">
611.0000
</td>
<td style="text-align:right;">
0.3997129
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
52.37900
</td>
<td style="text-align:right;">
6147783
</td>
<td style="text-align:right;">
1518.4800
</td>
<td style="text-align:right;">
0.3990731
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
56.00700
</td>
<td style="text-align:right;">
9947814
</td>
<td style="text-align:right;">
942.6542
</td>
<td style="text-align:right;">
0.3989427
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
48.24500
</td>
<td style="text-align:right;">
439971
</td>
<td style="text-align:right;">
2814.4808
</td>
<td style="text-align:right;">
0.3985395
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
56.59600
</td>
<td style="text-align:right;">
708000000
</td>
<td style="text-align:right;">
855.7235
</td>
<td style="text-align:right;">
0.3974430
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
47.18100
</td>
<td style="text-align:right;">
19792000
</td>
<td style="text-align:right;">
3290.2576
</td>
<td style="text-align:right;">
0.3974145
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
54.04300
</td>
<td style="text-align:right;">
78152686
</td>
<td style="text-align:right;">
1175.9212
</td>
<td style="text-align:right;">
0.3973810
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
53.91900
</td>
<td style="text-align:right;">
4981671
</td>
<td style="text-align:right;">
1191.2077
</td>
<td style="text-align:right;">
0.3971935
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
52.70200
</td>
<td style="text-align:right;">
136725000
</td>
<td style="text-align:right;">
1382.7021
</td>
<td style="text-align:right;">
0.3963997
</td>
</tr>
<tr>
<td style="text-align:left;">
South Africa
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
45.00900
</td>
<td style="text-align:right;">
14264935
</td>
<td style="text-align:right;">
4725.2955
</td>
<td style="text-align:right;">
0.3960637
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
53.55900
</td>
<td style="text-align:right;">
12044785
</td>
<td style="text-align:right;">
1222.3600
</td>
<td style="text-align:right;">
0.3959797
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
57.18000
</td>
<td style="text-align:right;">
1599200
</td>
<td style="text-align:right;">
773.9932
</td>
<td style="text-align:right;">
0.3955742
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
50.33800
</td>
<td style="text-align:right;">
20367053
</td>
<td style="text-align:right;">
1895.5441
</td>
<td style="text-align:right;">
0.3951349
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
54.97800
</td>
<td style="text-align:right;">
14165114
</td>
<td style="text-align:right;">
986.2959
</td>
<td style="text-align:right;">
0.3942008
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
55.72700
</td>
<td style="text-align:right;">
20326209
</td>
<td style="text-align:right;">
897.7404
</td>
<td style="text-align:right;">
0.3941187
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
48.30300
</td>
<td style="text-align:right;">
11000948
</td>
<td style="text-align:right;">
2550.8169
</td>
<td style="text-align:right;">
0.3940770
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
51.38600
</td>
<td style="text-align:right;">
5216550
</td>
<td style="text-align:right;">
1588.6883
</td>
<td style="text-align:right;">
0.3939232
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
51.74400
</td>
<td style="text-align:right;">
24725960
</td>
<td style="text-align:right;">
1507.8192
</td>
<td style="text-align:right;">
0.3938559
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
53.29800
</td>
<td style="text-align:right;">
553541
</td>
<td style="text-align:right;">
1214.7093
</td>
<td style="text-align:right;">
0.3937020
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
54.46700
</td>
<td style="text-align:right;">
12031795
</td>
<td style="text-align:right;">
1042.5816
</td>
<td style="text-align:right;">
0.3936809
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
48.43500
</td>
<td style="text-align:right;">
1047924
</td>
<td style="text-align:right;">
2464.7832
</td>
<td style="text-align:right;">
0.3934256
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
52.93300
</td>
<td style="text-align:right;">
348643
</td>
<td style="text-align:right;">
1267.1001
</td>
<td style="text-align:right;">
0.3933305
</td>
</tr>
<tr>
<td style="text-align:left;">
Iraq
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
45.32000
</td>
<td style="text-align:right;">
5441766
</td>
<td style="text-align:right;">
4129.7661
</td>
<td style="text-align:right;">
0.3924507
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
49.85600
</td>
<td style="text-align:right;">
15929988
</td>
<td style="text-align:right;">
1934.0114
</td>
<td style="text-align:right;">
0.3923932
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
56.01800
</td>
<td style="text-align:right;">
113704579
</td>
<td style="text-align:right;">
837.8102
</td>
<td style="text-align:right;">
0.3921514
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
51.33400
</td>
<td style="text-align:right;">
26072194
</td>
<td style="text-align:right;">
1547.9448
</td>
<td style="text-align:right;">
0.3921374
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
50.65100
</td>
<td style="text-align:right;">
10238807
</td>
<td style="text-align:right;">
1704.0637
</td>
<td style="text-align:right;">
0.3919819
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
58.04100
</td>
<td style="text-align:right;">
1457766
</td>
<td style="text-align:right;">
660.5856
</td>
<td style="text-align:right;">
0.3919664
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
57.67400
</td>
<td style="text-align:right;">
6642107
</td>
<td style="text-align:right;">
685.5877
</td>
<td style="text-align:right;">
0.3917164
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
49.92300
</td>
<td style="text-align:right;">
4908554
</td>
<td style="text-align:right;">
1874.2989
</td>
<td style="text-align:right;">
0.3912921
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
51.82100
</td>
<td style="text-align:right;">
6100407
</td>
<td style="text-align:right;">
1408.6786
</td>
<td style="text-align:right;">
0.3907764
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
55.72900
</td>
<td style="text-align:right;">
14168101
</td>
<td style="text-align:right;">
847.0061
</td>
<td style="text-align:right;">
0.3907610
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
58.04000
</td>
<td style="text-align:right;">
4906585
</td>
<td style="text-align:right;">
641.3695
</td>
<td style="text-align:right;">
0.3901776
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
50.10700
</td>
<td style="text-align:right;">
4506497
</td>
<td style="text-align:right;">
1773.4983
</td>
<td style="text-align:right;">
0.3898533
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
50.33500
</td>
<td style="text-align:right;">
14770296
</td>
<td style="text-align:right;">
1711.0448
</td>
<td style="text-align:right;">
0.3897505
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
58.38112
</td>
<td style="text-align:right;">
754550000
</td>
<td style="text-align:right;">
612.7057
</td>
<td style="text-align:right;">
0.3896946
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
46.71400
</td>
<td style="text-align:right;">
4565872
</td>
<td style="text-align:right;">
2980.3313
</td>
<td style="text-align:right;">
0.3886742
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
46.51900
</td>
<td style="text-align:right;">
228694
</td>
<td style="text-align:right;">
3081.7610
</td>
<td style="text-align:right;">
0.3886710
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
48.12600
</td>
<td style="text-align:right;">
933559
</td>
<td style="text-align:right;">
2348.0092
</td>
<td style="text-align:right;">
0.3884862
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
56.53400
</td>
<td style="text-align:right;">
11782962
</td>
<td style="text-align:right;">
734.2852
</td>
<td style="text-align:right;">
0.3880084
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
49.11300
</td>
<td style="text-align:right;">
9657618
</td>
<td style="text-align:right;">
1977.5570
</td>
<td style="text-align:right;">
0.3876827
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
52.33700
</td>
<td style="text-align:right;">
4243788
</td>
<td style="text-align:right;">
1225.8560
</td>
<td style="text-align:right;">
0.3871005
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
55.63500
</td>
<td style="text-align:right;">
5861135
</td>
<td style="text-align:right;">
799.3622
</td>
<td style="text-align:right;">
0.3867520
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
46.95400
</td>
<td style="text-align:right;">
4208858
</td>
<td style="text-align:right;">
2750.3644
</td>
<td style="text-align:right;">
0.3867496
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
50.85200
</td>
<td style="text-align:right;">
1456688
</td>
<td style="text-align:right;">
1497.4922
</td>
<td style="text-align:right;">
0.3867029
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
48.04100
</td>
<td style="text-align:right;">
2090162
</td>
<td style="text-align:right;">
2291.1568
</td>
<td style="text-align:right;">
0.3865754
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
52.29500
</td>
<td style="text-align:right;">
14326203
</td>
<td style="text-align:right;">
1217.0330
</td>
<td style="text-align:right;">
0.3863969
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
48.94400
</td>
<td style="text-align:right;">
250027
</td>
<td style="text-align:right;">
1937.5777
</td>
<td style="text-align:right;">
0.3853090
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
48.07900
</td>
<td style="text-align:right;">
25670939
</td>
<td style="text-align:right;">
2218.7543
</td>
<td style="text-align:right;">
0.3852754
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
48.12700
</td>
<td style="text-align:right;">
1133134
</td>
<td style="text-align:right;">
2198.9563
</td>
<td style="text-align:right;">
0.3852114
</td>
</tr>
<tr>
<td style="text-align:left;">
Bosnia and Herzegovina
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
53.82000
</td>
<td style="text-align:right;">
2791000
</td>
<td style="text-align:right;">
973.5332
</td>
<td style="text-align:right;">
0.3851687
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.43200
</td>
<td style="text-align:right;">
1358828
</td>
<td style="text-align:right;">
3457.4159
</td>
<td style="text-align:right;">
0.3850239
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
49.29300
</td>
<td style="text-align:right;">
31681188
</td>
<td style="text-align:right;">
1814.8807
</td>
<td style="text-align:right;">
0.3847026
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
48.28400
</td>
<td style="text-align:right;">
4149908
</td>
<td style="text-align:right;">
2117.2349
</td>
<td style="text-align:right;">
0.3845662
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
49.35500
</td>
<td style="text-align:right;">
7959865
</td>
<td style="text-align:right;">
1783.4329
</td>
<td style="text-align:right;">
0.3842892
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.28900
</td>
<td style="text-align:right;">
1201578
</td>
<td style="text-align:right;">
3448.2844
</td>
<td style="text-align:right;">
0.3836875
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
49.75900
</td>
<td style="text-align:right;">
2056351
</td>
<td style="text-align:right;">
1649.6602
</td>
<td style="text-align:right;">
0.3833997
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
52.51700
</td>
<td style="text-align:right;">
38139640
</td>
<td style="text-align:right;">
1107.4822
</td>
<td style="text-align:right;">
0.3828850
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
55.07800
</td>
<td style="text-align:right;">
1411807
</td>
<td style="text-align:right;">
797.2631
</td>
<td style="text-align:right;">
0.3827293
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
47.80000
</td>
<td style="text-align:right;">
17104986
</td>
<td style="text-align:right;">
2202.9884
</td>
<td style="text-align:right;">
0.3826852
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
53.67600
</td>
<td style="text-align:right;">
8807818
</td>
<td style="text-align:right;">
945.5836
</td>
<td style="text-align:right;">
0.3825120
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
49.57900
</td>
<td style="text-align:right;">
4286552
</td>
<td style="text-align:right;">
1660.3032
</td>
<td style="text-align:right;">
0.3823444
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
46.63300
</td>
<td style="text-align:right;">
420690
</td>
<td style="text-align:right;">
2613.1017
</td>
<td style="text-align:right;">
0.3816225
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
55.24000
</td>
<td style="text-align:right;">
4414865
</td>
<td style="text-align:right;">
765.3500
</td>
<td style="text-align:right;">
0.3815080
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
55.76400
</td>
<td style="text-align:right;">
50533506
</td>
<td style="text-align:right;">
713.5371
</td>
<td style="text-align:right;">
0.3810613
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.68500
</td>
<td style="text-align:right;">
10270856
</td>
<td style="text-align:right;">
3013.9760
</td>
<td style="text-align:right;">
0.3806460
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
49.82800
</td>
<td style="text-align:right;">
2923186
</td>
<td style="text-align:right;">
1544.4030
</td>
<td style="text-align:right;">
0.3805144
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
56.86700
</td>
<td style="text-align:right;">
12894865
</td>
<td style="text-align:right;">
619.6769
</td>
<td style="text-align:right;">
0.3802570
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
43.86900
</td>
<td style="text-align:right;">
1130269
</td>
<td style="text-align:right;">
4128.1169
</td>
<td style="text-align:right;">
0.3798675
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
50.99200
</td>
<td style="text-align:right;">
31386842
</td>
<td style="text-align:right;">
1287.5147
</td>
<td style="text-align:right;">
0.3797551
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
51.25300
</td>
<td style="text-align:right;">
1149500
</td>
<td style="text-align:right;">
1226.0411
</td>
<td style="text-align:right;">
0.3790909
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
44.36600
</td>
<td style="text-align:right;">
178848
</td>
<td style="text-align:right;">
3694.2124
</td>
<td style="text-align:right;">
0.3790467
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
55.80300
</td>
<td style="text-align:right;">
10150094
</td>
<td style="text-align:right;">
682.3032
</td>
<td style="text-align:right;">
0.3787300
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
53.74400
</td>
<td style="text-align:right;">
11400338
</td>
<td style="text-align:right;">
876.0326
</td>
<td style="text-align:right;">
0.3787261
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
50.90400
</td>
<td style="text-align:right;">
3641603
</td>
<td style="text-align:right;">
1277.8976
</td>
<td style="text-align:right;">
0.3787028
</td>
</tr>
<tr>
<td style="text-align:left;">
Malaysia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
48.46300
</td>
<td style="text-align:right;">
6748378
</td>
<td style="text-align:right;">
1831.1329
</td>
<td style="text-align:right;">
0.3786743
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
53.37800
</td>
<td style="text-align:right;">
4058319
</td>
<td style="text-align:right;">
913.4708
</td>
<td style="text-align:right;">
0.3784702
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
60.32800
</td>
<td style="text-align:right;">
43247867
</td>
<td style="text-align:right;">
415.0000
</td>
<td style="text-align:right;">
0.3782442
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
54.20800
</td>
<td style="text-align:right;">
634000000
</td>
<td style="text-align:right;">
813.3373
</td>
<td style="text-align:right;">
0.3778092
</td>
</tr>
<tr>
<td style="text-align:left;">
El Salvador
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
45.26200
</td>
<td style="text-align:right;">
2042865
</td>
<td style="text-align:right;">
3048.3029
</td>
<td style="text-align:right;">
0.3776547
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
52.21400
</td>
<td style="text-align:right;">
12210395
</td>
<td style="text-align:right;">
1040.6762
</td>
<td style="text-align:right;">
0.3772971
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
42.73100
</td>
<td style="text-align:right;">
12420476
</td>
<td style="text-align:right;">
4797.2313
</td>
<td style="text-align:right;">
0.3766895
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
55.86100
</td>
<td style="text-align:right;">
1235767
</td>
<td style="text-align:right;">
653.7302
</td>
<td style="text-align:right;">
0.3766382
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
51.89300
</td>
<td style="text-align:right;">
65345
</td>
<td style="text-align:right;">
1071.5511
</td>
<td style="text-align:right;">
0.3765555
</td>
</tr>
<tr>
<td style="text-align:left;">
Peru
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
43.90200
</td>
<td style="text-align:right;">
8025700
</td>
<td style="text-align:right;">
3758.5234
</td>
<td style="text-align:right;">
0.3758705
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
51.92900
</td>
<td style="text-align:right;">
69325921
</td>
<td style="text-align:right;">
1049.9390
</td>
<td style="text-align:right;">
0.3757163
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
47.35000
</td>
<td style="text-align:right;">
4744870
</td>
<td style="text-align:right;">
2052.0505
</td>
<td style="text-align:right;">
0.3755872
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
50.82100
</td>
<td style="text-align:right;">
7272406
</td>
<td style="text-align:right;">
1213.3151
</td>
<td style="text-align:right;">
0.3753441
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
51.72400
</td>
<td style="text-align:right;">
6429417
</td>
<td style="text-align:right;">
1058.0643
</td>
<td style="text-align:right;">
0.3746478
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
50.93900
</td>
<td style="text-align:right;">
304739
</td>
<td style="text-align:right;">
1172.6030
</td>
<td style="text-align:right;">
0.3744074
</td>
</tr>
<tr>
<td style="text-align:left;">
Iran
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
44.86900
</td>
<td style="text-align:right;">
17272000
</td>
<td style="text-align:right;">
3035.3260
</td>
<td style="text-align:right;">
0.3741765
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
48.87900
</td>
<td style="text-align:right;">
5260855
</td>
<td style="text-align:right;">
1561.7691
</td>
<td style="text-align:right;">
0.3738358
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
47.99100
</td>
<td style="text-align:right;">
14625967
</td>
<td style="text-align:right;">
1786.2654
</td>
<td style="text-align:right;">
0.3737480
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
51.54200
</td>
<td style="text-align:right;">
29170398
</td>
<td style="text-align:right;">
1056.3801
</td>
<td style="text-align:right;">
0.3732441
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
53.63000
</td>
<td style="text-align:right;">
25041917
</td>
<td style="text-align:right;">
793.5774
</td>
<td style="text-align:right;">
0.3724089
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
47.76800
</td>
<td style="text-align:right;">
3900000
</td>
<td style="text-align:right;">
1777.0773
</td>
<td style="text-align:right;">
0.3717551
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
51.75600
</td>
<td style="text-align:right;">
10538093
</td>
<td style="text-align:right;">
993.2240
</td>
<td style="text-align:right;">
0.3714754
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
48.43700
</td>
<td style="text-align:right;">
1332786
</td>
<td style="text-align:right;">
1586.8518
</td>
<td style="text-align:right;">
0.3712580
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
51.57300
</td>
<td style="text-align:right;">
7562011
</td>
<td style="text-align:right;">
1004.9614
</td>
<td style="text-align:right;">
0.3707921
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
46.85900
</td>
<td style="text-align:right;">
135031164
</td>
<td style="text-align:right;">
2013.9773
</td>
<td style="text-align:right;">
0.3707797
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
50.52500
</td>
<td style="text-align:right;">
8835739
</td>
<td style="text-align:right;">
1156.1819
</td>
<td style="text-align:right;">
0.3706234
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
40.48900
</td>
<td style="text-align:right;">
455661
</td>
<td style="text-align:right;">
6631.4592
</td>
<td style="text-align:right;">
0.3705605
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
48.04200
</td>
<td style="text-align:right;">
4698301
</td>
<td style="text-align:right;">
1654.4569
</td>
<td style="text-align:right;">
0.3703150
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.22600
</td>
<td style="text-align:right;">
548080
</td>
<td style="text-align:right;">
2621.4481
</td>
<td style="text-align:right;">
0.3702583
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
51.81800
</td>
<td style="text-align:right;">
10580176
</td>
<td style="text-align:right;">
951.4098
</td>
<td style="text-align:right;">
0.3696023
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
51.52000
</td>
<td style="text-align:right;">
512764
</td>
<td style="text-align:right;">
983.6540
</td>
<td style="text-align:right;">
0.3692627
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
48.32800
</td>
<td style="text-align:right;">
18013409
</td>
<td style="text-align:right;">
1544.7501
</td>
<td style="text-align:right;">
0.3690709
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
45.03200
</td>
<td style="text-align:right;">
4040665
</td>
<td style="text-align:right;">
2586.8861
</td>
<td style="text-align:right;">
0.3680484
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
49.87500
</td>
<td style="text-align:right;">
9354120
</td>
<td style="text-align:right;">
1178.2237
</td>
<td style="text-align:right;">
0.3668349
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
50.65400
</td>
<td style="text-align:right;">
10191512
</td>
<td style="text-align:right;">
1056.7365
</td>
<td style="text-align:right;">
0.3668314
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
47.92400
</td>
<td style="text-align:right;">
13056604
</td>
<td style="text-align:right;">
1566.3535
</td>
<td style="text-align:right;">
0.3666779
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
53.91400
</td>
<td style="text-align:right;">
8371791
</td>
<td style="text-align:right;">
683.8956
</td>
<td style="text-align:right;">
0.3660402
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
50.65000
</td>
<td style="text-align:right;">
12251209
</td>
<td style="text-align:right;">
1037.6452
</td>
<td style="text-align:right;">
0.3658420
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
58.05600
</td>
<td style="text-align:right;">
34680442
</td>
<td style="text-align:right;">
424.0000
</td>
<td style="text-align:right;">
0.3652948
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
48.96900
</td>
<td style="text-align:right;">
9171477
</td>
<td style="text-align:right;">
1302.8787
</td>
<td style="text-align:right;">
0.3652933
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
47.46400
</td>
<td style="text-align:right;">
106207839
</td>
<td style="text-align:right;">
1624.9413
</td>
<td style="text-align:right;">
0.3649711
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
47.47200
</td>
<td style="text-align:right;">
93364244
</td>
<td style="text-align:right;">
1619.8482
</td>
<td style="text-align:right;">
0.3648776
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
46.47200
</td>
<td style="text-align:right;">
217378
</td>
<td style="text-align:right;">
1876.0296
</td>
<td style="text-align:right;">
0.3642881
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
51.05100
</td>
<td style="text-align:right;">
5498955
</td>
<td style="text-align:right;">
952.3861
</td>
<td style="text-align:right;">
0.3641860
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Dem. Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
50.05600
</td>
<td style="text-align:right;">
8865488
</td>
<td style="text-align:right;">
1088.2778
</td>
<td style="text-align:right;">
0.3640319
</td>
</tr>
<tr>
<td style="text-align:left;">
Saudi Arabia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
39.87500
</td>
<td style="text-align:right;">
4005677
</td>
<td style="text-align:right;">
6459.5548
</td>
<td style="text-align:right;">
0.3638518
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
51.01600
</td>
<td style="text-align:right;">
10190285
</td>
<td style="text-align:right;">
950.7359
</td>
<td style="text-align:right;">
0.3638443
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
52.81900
</td>
<td style="text-align:right;">
103764241
</td>
<td style="text-align:right;">
751.9794
</td>
<td style="text-align:right;">
0.3638195
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
52.53700
</td>
<td style="text-align:right;">
17917180
</td>
<td style="text-align:right;">
775.6325
</td>
<td style="text-align:right;">
0.3635693
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
47.04900
</td>
<td style="text-align:right;">
7021028
</td>
<td style="text-align:right;">
1684.1465
</td>
<td style="text-align:right;">
0.3635312
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
46.99200
</td>
<td style="text-align:right;">
28173309
</td>
<td style="text-align:right;">
1693.3359
</td>
<td style="text-align:right;">
0.3633567
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.05300
</td>
<td style="text-align:right;">
940458
</td>
<td style="text-align:right;">
2315.0566
</td>
<td style="text-align:right;">
0.3630178
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
54.49600
</td>
<td style="text-align:right;">
11140655
</td>
<td style="text-align:right;">
601.0745
</td>
<td style="text-align:right;">
0.3626751
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
51.45500
</td>
<td style="text-align:right;">
8048834
</td>
<td style="text-align:right;">
869.4498
</td>
<td style="text-align:right;">
0.3621922
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
49.35000
</td>
<td style="text-align:right;">
10568642
</td>
<td style="text-align:right;">
1155.4419
</td>
<td style="text-align:right;">
0.3619714
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
44.14200
</td>
<td style="text-align:right;">
3640876
</td>
<td style="text-align:right;">
2617.1560
</td>
<td style="text-align:right;">
0.3613085
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
58.33900
</td>
<td style="text-align:right;">
38028578
</td>
<td style="text-align:right;">
385.0000
</td>
<td style="text-align:right;">
0.3612208
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
59.32000
</td>
<td style="text-align:right;">
40546538
</td>
<td style="text-align:right;">
347.0000
</td>
<td style="text-align:right;">
0.3608834
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
46.83200
</td>
<td style="text-align:right;">
16252726
</td>
<td style="text-align:right;">
1648.8008
</td>
<td style="text-align:right;">
0.3608214
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
51.53500
</td>
<td style="text-align:right;">
23040630
</td>
<td style="text-align:right;">
831.8221
</td>
<td style="text-align:right;">
0.3603839
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
52.94700
</td>
<td style="text-align:right;">
76511887
</td>
<td style="text-align:right;">
690.8056
</td>
<td style="text-align:right;">
0.3600286
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
52.20800
</td>
<td style="text-align:right;">
1251524
</td>
<td style="text-align:right;">
745.3695
</td>
<td style="text-align:right;">
0.3591315
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
49.20300
</td>
<td style="text-align:right;">
121282000
</td>
<td style="text-align:right;">
1111.1079
</td>
<td style="text-align:right;">
0.3588909
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
50.32400
</td>
<td style="text-align:right;">
10352843
</td>
<td style="text-align:right;">
946.2950
</td>
<td style="text-align:right;">
0.3586639
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
43.16500
</td>
<td style="text-align:right;">
628164
</td>
<td style="text-align:right;">
2924.6381
</td>
<td style="text-align:right;">
0.3582986
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.66900
</td>
<td style="text-align:right;">
746559
</td>
<td style="text-align:right;">
1886.0806
</td>
<td style="text-align:right;">
0.3582472
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
46.60800
</td>
<td style="text-align:right;">
119901274
</td>
<td style="text-align:right;">
1615.2864
</td>
<td style="text-align:right;">
0.3581000
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
46.88100
</td>
<td style="text-align:right;">
8007166
</td>
<td style="text-align:right;">
1544.2286
</td>
<td style="text-align:right;">
0.3580040
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
44.66500
</td>
<td style="text-align:right;">
1770390
</td>
<td style="text-align:right;">
2220.4877
</td>
<td style="text-align:right;">
0.3579540
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
50.26000
</td>
<td style="text-align:right;">
8878303
</td>
<td style="text-align:right;">
931.7528
</td>
<td style="text-align:right;">
0.3573983
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.67100
</td>
<td style="text-align:right;">
1070439
</td>
<td style="text-align:right;">
1827.0677
</td>
<td style="text-align:right;">
0.3567530
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
49.91900
</td>
<td style="text-align:right;">
17129565
</td>
<td style="text-align:right;">
962.4923
</td>
<td style="text-align:right;">
0.3566586
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
50.60800
</td>
<td style="text-align:right;">
19844382
</td>
<td style="text-align:right;">
874.2426
</td>
<td style="text-align:right;">
0.3565195
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
53.99500
</td>
<td style="text-align:right;">
4995432
</td>
<td style="text-align:right;">
569.7951
</td>
<td style="text-align:right;">
0.3563397
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
52.64400
</td>
<td style="text-align:right;">
1025384
</td>
<td style="text-align:right;">
665.6244
</td>
<td style="text-align:right;">
0.3559351
</td>
</tr>
<tr>
<td style="text-align:left;">
Philippines
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
47.75200
</td>
<td style="text-align:right;">
22438691
</td>
<td style="text-align:right;">
1272.8810
</td>
<td style="text-align:right;">
0.3550580
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
46.76900
</td>
<td style="text-align:right;">
1735550
</td>
<td style="text-align:right;">
1477.5968
</td>
<td style="text-align:right;">
0.3550032
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
49.19000
</td>
<td style="text-align:right;">
3168267
</td>
<td style="text-align:right;">
1029.1613
</td>
<td style="text-align:right;">
0.3548765
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
49.80000
</td>
<td style="text-align:right;">
60641899
</td>
<td style="text-align:right;">
942.4083
</td>
<td style="text-align:right;">
0.3547162
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
47.10000
</td>
<td style="text-align:right;">
3950849
</td>
<td style="text-align:right;">
1395.2325
</td>
<td style="text-align:right;">
0.3547060
</td>
</tr>
<tr>
<td style="text-align:left;">
Nicaragua
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
42.31400
</td>
<td style="text-align:right;">
1165790
</td>
<td style="text-align:right;">
3112.3639
</td>
<td style="text-align:right;">
0.3539726
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
50.48500
</td>
<td style="text-align:right;">
2840009
</td>
<td style="text-align:right;">
844.8764
</td>
<td style="text-align:right;">
0.3538589
</td>
</tr>
<tr>
<td style="text-align:left;">
Syria
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
45.88300
</td>
<td style="text-align:right;">
3661549
</td>
<td style="text-align:right;">
1643.4854
</td>
<td style="text-align:right;">
0.3533556
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
50.35000
</td>
<td style="text-align:right;">
11457758
</td>
<td style="text-align:right;">
843.7331
</td>
<td style="text-align:right;">
0.3528418
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
46.88600
</td>
<td style="text-align:right;">
81551520
</td>
<td style="text-align:right;">
1385.0296
</td>
<td style="text-align:right;">
0.3527365
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
50.44000
</td>
<td style="text-align:right;">
26605473
</td>
<td style="text-align:right;">
825.6825
</td>
<td style="text-align:right;">
0.3523380
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
44.99200
</td>
<td style="text-align:right;">
370006
</td>
<td style="text-align:right;">
1856.1821
</td>
<td style="text-align:right;">
0.3521888
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
49.61800
</td>
<td style="text-align:right;">
474639
</td>
<td style="text-align:right;">
918.2325
</td>
<td style="text-align:right;">
0.3520787
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
45.81500
</td>
<td style="text-align:right;">
4588696
</td>
<td style="text-align:right;">
1597.7121
</td>
<td style="text-align:right;">
0.3514860
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
44.51400
</td>
<td style="text-align:right;">
62209173
</td>
<td style="text-align:right;">
1981.9518
</td>
<td style="text-align:right;">
0.3514824
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
49.55700
</td>
<td style="text-align:right;">
7586551
</td>
<td style="text-align:right;">
912.0631
</td>
<td style="text-align:right;">
0.3512984
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
48.07200
</td>
<td style="text-align:right;">
8490213
</td>
<td style="text-align:right;">
1125.6972
</td>
<td style="text-align:right;">
0.3512935
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
49.65100
</td>
<td style="text-align:right;">
34593779
</td>
<td style="text-align:right;">
899.0742
</td>
<td style="text-align:right;">
0.3512240
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
45.82600
</td>
<td style="text-align:right;">
73039376
</td>
<td style="text-align:right;">
1576.9738
</td>
<td style="text-align:right;">
0.3509477
</td>
</tr>
<tr>
<td style="text-align:left;">
Thailand
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
50.84800
</td>
<td style="text-align:right;">
21289402
</td>
<td style="text-align:right;">
757.7974
</td>
<td style="text-align:right;">
0.3506507
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
42.07400
</td>
<td style="text-align:right;">
127617
</td>
<td style="text-align:right;">
3020.0505
</td>
<td style="text-align:right;">
0.3506474
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
46.24300
</td>
<td style="text-align:right;">
4318137
</td>
<td style="text-align:right;">
1452.0577
</td>
<td style="text-align:right;">
0.3501720
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.42300
</td>
<td style="text-align:right;">
11406350
</td>
<td style="text-align:right;">
1642.0023
</td>
<td style="text-align:right;">
0.3497704
</td>
</tr>
<tr>
<td style="text-align:left;">
Algeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
43.07700
</td>
<td style="text-align:right;">
9279525
</td>
<td style="text-align:right;">
2449.0082
</td>
<td style="text-align:right;">
0.3496162
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
46.28900
</td>
<td style="text-align:right;">
1230542
</td>
<td style="text-align:right;">
1421.1452
</td>
<td style="text-align:right;">
0.3494844
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
48.25100
</td>
<td style="text-align:right;">
1010280
</td>
<td style="text-align:right;">
1056.3540
</td>
<td style="text-align:right;">
0.3494110
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
46.02300
</td>
<td style="text-align:right;">
3421000
</td>
<td style="text-align:right;">
1452.7258
</td>
<td style="text-align:right;">
0.3485281
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
44.93000
</td>
<td style="text-align:right;">
3832408
</td>
<td style="text-align:right;">
1728.8694
</td>
<td style="text-align:right;">
0.3483831
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
44.85100
</td>
<td style="text-align:right;">
7082430
</td>
<td style="text-align:right;">
1748.5630
</td>
<td style="text-align:right;">
0.3482990
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
47.54500
</td>
<td style="text-align:right;">
387838
</td>
<td style="text-align:right;">
1132.0550
</td>
<td style="text-align:right;">
0.3477209
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
45.08300
</td>
<td style="text-align:right;">
14597019
</td>
<td style="text-align:right;">
1659.6528
</td>
<td style="text-align:right;">
0.3476536
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
43.42800
</td>
<td style="text-align:right;">
3593918
</td>
<td style="text-align:right;">
2180.9725
</td>
<td style="text-align:right;">
0.3472294
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
50.65100
</td>
<td style="text-align:right;">
567000000
</td>
<td style="text-align:right;">
724.0325
</td>
<td style="text-align:right;">
0.3468910
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
39.61300
</td>
<td style="text-align:right;">
1133066
</td>
<td style="text-align:right;">
4513.4806
</td>
<td style="text-align:right;">
0.3466912
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
47.38300
</td>
<td style="text-align:right;">
4388260
</td>
<td style="text-align:right;">
1133.9850
</td>
<td style="text-align:right;">
0.3466201
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
49.90300
</td>
<td style="text-align:right;">
9384984
</td>
<td style="text-align:right;">
790.2580
</td>
<td style="text-align:right;">
0.3463109
</td>
</tr>
<tr>
<td style="text-align:left;">
Dominican Republic
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
45.92800
</td>
<td style="text-align:right;">
2491346
</td>
<td style="text-align:right;">
1397.7171
</td>
<td style="text-align:right;">
0.3459647
</td>
</tr>
<tr>
<td style="text-align:left;">
Libya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
42.72300
</td>
<td style="text-align:right;">
1019729
</td>
<td style="text-align:right;">
2387.5481
</td>
<td style="text-align:right;">
0.3456137
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
38.99900
</td>
<td style="text-align:right;">
434904
</td>
<td style="text-align:right;">
4976.1981
</td>
<td style="text-align:right;">
0.3452762
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
44.17500
</td>
<td style="text-align:right;">
8403990
</td>
<td style="text-align:right;">
1829.7652
</td>
<td style="text-align:right;">
0.3451349
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
56.05900
</td>
<td style="text-align:right;">
31528087
</td>
<td style="text-align:right;">
371.0000
</td>
<td style="text-align:right;">
0.3449439
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
48.29500
</td>
<td style="text-align:right;">
2476971
</td>
<td style="text-align:right;">
956.7530
</td>
<td style="text-align:right;">
0.3447551
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
51.50900
</td>
<td style="text-align:right;">
15283050
</td>
<td style="text-align:right;">
617.7244
</td>
<td style="text-align:right;">
0.3442602
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
49.51700
</td>
<td style="text-align:right;">
4875118
</td>
<td style="text-align:right;">
797.9081
</td>
<td style="text-align:right;">
0.3441283
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
48.94500
</td>
<td style="text-align:right;">
61325
</td>
<td style="text-align:right;">
860.7369
</td>
<td style="text-align:right;">
0.3440116
</td>
</tr>
<tr>
<td style="text-align:left;">
Turkey
</td>
<td style="text-align:left;">
Europe
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
43.58500
</td>
<td style="text-align:right;">
22235677
</td>
<td style="text-align:right;">
1969.1010
</td>
<td style="text-align:right;">
0.3438522
</td>
</tr>
<tr>
<td style="text-align:left;">
Korea, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
47.45300
</td>
<td style="text-align:right;">
20947571
</td>
<td style="text-align:right;">
1030.5922
</td>
<td style="text-align:right;">
0.3424137
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
50.25400
</td>
<td style="text-align:right;">
44655014
</td>
<td style="text-align:right;">
699.5016
</td>
<td style="text-align:right;">
0.3423706
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
48.15900
</td>
<td style="text-align:right;">
9118773
</td>
<td style="text-align:right;">
926.1411
</td>
<td style="text-align:right;">
0.3421555
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
46.45200
</td>
<td style="text-align:right;">
7355248
</td>
<td style="text-align:right;">
1190.0411
</td>
<td style="text-align:right;">
0.3421406
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
47.01400
</td>
<td style="text-align:right;">
2761407
</td>
<td style="text-align:right;">
1085.7969
</td>
<td style="text-align:right;">
0.3417974
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
52.35800
</td>
<td style="text-align:right;">
4277736
</td>
<td style="text-align:right;">
527.2722
</td>
<td style="text-align:right;">
0.3413127
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
50.95700
</td>
<td style="text-align:right;">
7272485
</td>
<td style="text-align:right;">
624.4755
</td>
<td style="text-align:right;">
0.3411470
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
46.77500
</td>
<td style="text-align:right;">
2167533
</td>
<td style="text-align:right;">
1109.3743
</td>
<td style="text-align:right;">
0.3411049
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
44.79900
</td>
<td style="text-align:right;">
6335506
</td>
<td style="text-align:right;">
1508.4531
</td>
<td style="text-align:right;">
0.3410128
</td>
</tr>
<tr>
<td style="text-align:left;">
Guatemala
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
42.02300
</td>
<td style="text-align:right;">
3146381
</td>
<td style="text-align:right;">
2428.2378
</td>
<td style="text-align:right;">
0.3406896
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
48.05100
</td>
<td style="text-align:right;">
8900294
</td>
<td style="text-align:right;">
908.9185
</td>
<td style="text-align:right;">
0.3404501
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
46.10000
</td>
<td style="text-align:right;">
8381163
</td>
<td style="text-align:right;">
1210.8846
</td>
<td style="text-align:right;">
0.3403805
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
49.39600
</td>
<td style="text-align:right;">
3265124
</td>
<td style="text-align:right;">
747.9055
</td>
<td style="text-align:right;">
0.3399626
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
47.81300
</td>
<td style="text-align:right;">
24739869
</td>
<td style="text-align:right;">
927.7210
</td>
<td style="text-align:right;">
0.3397820
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
43.59000
</td>
<td style="text-align:right;">
3880130
</td>
<td style="text-align:right;">
1796.5890
</td>
<td style="text-align:right;">
0.3397348
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
51.31300
</td>
<td style="text-align:right;">
9666252
</td>
<td style="text-align:right;">
580.3052
</td>
<td style="text-align:right;">
0.3396153
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
37.92800
</td>
<td style="text-align:right;">
5894858
</td>
<td style="text-align:right;">
5473.2880
</td>
<td style="text-align:right;">
0.3395501
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
49.59400
</td>
<td style="text-align:right;">
15796314
</td>
<td style="text-align:right;">
718.3731
</td>
<td style="text-align:right;">
0.3392473
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
47.94900
</td>
<td style="text-align:right;">
8678557
</td>
<td style="text-align:right;">
896.9664
</td>
<td style="text-align:right;">
0.3390673
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
50.00900
</td>
<td style="text-align:right;">
93074406
</td>
<td style="text-align:right;">
676.9819
</td>
<td style="text-align:right;">
0.3389994
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
49.84900
</td>
<td style="text-align:right;">
12939400
</td>
<td style="text-align:right;">
682.2662
</td>
<td style="text-align:right;">
0.3383179
</td>
</tr>
<tr>
<td style="text-align:left;">
Tunisia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
44.60000
</td>
<td style="text-align:right;">
3647735
</td>
<td style="text-align:right;">
1468.4756
</td>
<td style="text-align:right;">
0.3382520
</td>
</tr>
<tr>
<td style="text-align:left;">
Namibia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
41.72500
</td>
<td style="text-align:right;">
485831
</td>
<td style="text-align:right;">
2423.7804
</td>
<td style="text-align:right;">
0.3381939
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
41.00300
</td>
<td style="text-align:right;">
10866106
</td>
<td style="text-align:right;">
2773.2873
</td>
<td style="text-align:right;">
0.3380865
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
47.62000
</td>
<td style="text-align:right;">
14706593
</td>
<td style="text-align:right;">
915.9851
</td>
<td style="text-align:right;">
0.3377799
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
48.57600
</td>
<td style="text-align:right;">
6990574
</td>
<td style="text-align:right;">
794.3484
</td>
<td style="text-align:right;">
0.3373628
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
44.44400
</td>
<td style="text-align:right;">
25009741
</td>
<td style="text-align:right;">
1458.9153
</td>
<td style="text-align:right;">
0.3367670
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
48.46600
</td>
<td style="text-align:right;">
30686889
</td>
<td style="text-align:right;">
789.1862
</td>
<td style="text-align:right;">
0.3362702
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
42.11100
</td>
<td style="text-align:right;">
854885
</td>
<td style="text-align:right;">
2125.6214
</td>
<td style="text-align:right;">
0.3355734
</td>
</tr>
<tr>
<td style="text-align:left;">
Honduras
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
41.91200
</td>
<td style="text-align:right;">
1517453
</td>
<td style="text-align:right;">
2194.9262
</td>
<td style="text-align:right;">
0.3353862
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
44.46700
</td>
<td style="text-align:right;">
191689
</td>
<td style="text-align:right;">
1406.6483
</td>
<td style="text-align:right;">
0.3352540
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
48.12200
</td>
<td style="text-align:right;">
6634596
</td>
<td style="text-align:right;">
807.1986
</td>
<td style="text-align:right;">
0.3350129
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
43.56300
</td>
<td style="text-align:right;">
3965841
</td>
<td style="text-align:right;">
1612.4046
</td>
<td style="text-align:right;">
0.3346237
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
50.54896
</td>
<td style="text-align:right;">
637408000
</td>
<td style="text-align:right;">
575.9870
</td>
<td style="text-align:right;">
0.3341658
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
47.62200
</td>
<td style="text-align:right;">
442308
</td>
<td style="text-align:right;">
851.2411
</td>
<td style="text-align:right;">
0.3341634
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
41.89000
</td>
<td style="text-align:right;">
3211738
</td>
<td style="text-align:right;">
2127.6863
</td>
<td style="text-align:right;">
0.3338546
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
48.30300
</td>
<td style="text-align:right;">
13327079
</td>
<td style="text-align:right;">
759.3499
</td>
<td style="text-align:right;">
0.3332031
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
40.64700
</td>
<td style="text-align:right;">
8735988
</td>
<td style="text-align:right;">
2627.8457
</td>
<td style="text-align:right;">
0.3328738
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
48.38800
</td>
<td style="text-align:right;">
8416215
</td>
<td style="text-align:right;">
739.0144
</td>
<td style="text-align:right;">
0.3324233
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
47.80400
</td>
<td style="text-align:right;">
26480870
</td>
<td style="text-align:right;">
795.7573
</td>
<td style="text-align:right;">
0.3320893
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
45.56900
</td>
<td style="text-align:right;">
3899068
</td>
<td style="text-align:right;">
1104.1040
</td>
<td style="text-align:right;">
0.3320845
</td>
</tr>
<tr>
<td style="text-align:left;">
Bolivia
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
40.41400
</td>
<td style="text-align:right;">
2883315
</td>
<td style="text-align:right;">
2677.3263
</td>
<td style="text-align:right;">
0.3317497
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
44.59300
</td>
<td style="text-align:right;">
2046772
</td>
<td style="text-align:right;">
1275.1846
</td>
<td style="text-align:right;">
0.3316532
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
47.67000
</td>
<td style="text-align:right;">
53100671
</td>
<td style="text-align:right;">
803.3427
</td>
<td style="text-align:right;">
0.3316288
</td>
</tr>
<tr>
<td style="text-align:left;">
Morocco
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
42.87300
</td>
<td style="text-align:right;">
9939217
</td>
<td style="text-align:right;">
1688.2036
</td>
<td style="text-align:right;">
0.3313720
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
42.85800
</td>
<td style="text-align:right;">
12716129
</td>
<td style="text-align:right;">
1687.9976
</td>
<td style="text-align:right;">
0.3312506
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
42.82100
</td>
<td style="text-align:right;">
53740085
</td>
<td style="text-align:right;">
1698.3888
</td>
<td style="text-align:right;">
0.3312380
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
49.99100
</td>
<td style="text-align:right;">
3668440
</td>
<td style="text-align:right;">
582.8585
</td>
<td style="text-align:right;">
0.3310939
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
50.72500
</td>
<td style="text-align:right;">
67946797
</td>
<td style="text-align:right;">
530.0535
</td>
<td style="text-align:right;">
0.3309451
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
39.69300
</td>
<td style="text-align:right;">
89898
</td>
<td style="text-align:right;">
3020.9893
</td>
<td style="text-align:right;">
0.3308168
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
42.88100
</td>
<td style="text-align:right;">
6334556
</td>
<td style="text-align:right;">
1634.0473
</td>
<td style="text-align:right;">
0.3299797
</td>
</tr>
<tr>
<td style="text-align:left;">
Jordan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
43.15800
</td>
<td style="text-align:right;">
607914
</td>
<td style="text-align:right;">
1546.9078
</td>
<td style="text-align:right;">
0.3296513
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
40.96300
</td>
<td style="text-align:right;">
9875024
</td>
<td style="text-align:right;">
2277.1409
</td>
<td style="text-align:right;">
0.3293588
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
44.07700
</td>
<td style="text-align:right;">
3016000
</td>
<td style="text-align:right;">
1311.9568
</td>
<td style="text-align:right;">
0.3291188
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
39.94200
</td>
<td style="text-align:right;">
7016384
</td>
<td style="text-align:right;">
2756.9537
</td>
<td style="text-align:right;">
0.3290927
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
39.48300
</td>
<td style="text-align:right;">
6162675
</td>
<td style="text-align:right;">
3008.6474
</td>
<td style="text-align:right;">
0.3288985
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
49.26500
</td>
<td style="text-align:right;">
848406
</td>
<td style="text-align:right;">
611.6589
</td>
<td style="text-align:right;">
0.3287568
</td>
</tr>
<tr>
<td style="text-align:left;">
West Bank and Gaza
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
43.16000
</td>
<td style="text-align:right;">
1030585
</td>
<td style="text-align:right;">
1515.5923
</td>
<td style="text-align:right;">
0.3287486
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
48.82500
</td>
<td style="text-align:right;">
18252190
</td>
<td style="text-align:right;">
644.1708
</td>
<td style="text-align:right;">
0.3284505
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
50.46900
</td>
<td style="text-align:right;">
3646340
</td>
<td style="text-align:right;">
518.7643
</td>
<td style="text-align:right;">
0.3281448
</td>
</tr>
<tr>
<td style="text-align:left;">
Sao Tome and Principe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
46.47100
</td>
<td style="text-align:right;">
60011
</td>
<td style="text-align:right;">
879.5836
</td>
<td style="text-align:right;">
0.3276698
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
45.66400
</td>
<td style="text-align:right;">
341244
</td>
<td style="text-align:right;">
966.8968
</td>
<td style="text-align:right;">
0.3264746
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
46.21800
</td>
<td style="text-align:right;">
5507565
</td>
<td style="text-align:right;">
881.5706
</td>
<td style="text-align:right;">
0.3259944
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
42.59200
</td>
<td style="text-align:right;">
2012649
</td>
<td style="text-align:right;">
1569.3314
</td>
<td style="text-align:right;">
0.3259656
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
45.98900
</td>
<td style="text-align:right;">
23007669
</td>
<td style="text-align:right;">
904.8961
</td>
<td style="text-align:right;">
0.3256283
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
49.42000
</td>
<td style="text-align:right;">
10014249
</td>
<td style="text-align:right;">
563.2000
</td>
<td style="text-align:right;">
0.3255486
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
46.24200
</td>
<td style="text-align:right;">
8860588
</td>
<td style="text-align:right;">
863.0885
</td>
<td style="text-align:right;">
0.3251447
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
46.80900
</td>
<td style="text-align:right;">
11404948
</td>
<td style="text-align:right;">
792.4500
</td>
<td style="text-align:right;">
0.3249744
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
53.07000
</td>
<td style="text-align:right;">
28466390
</td>
<td style="text-align:right;">
357.0000
</td>
<td style="text-align:right;">
0.3244287
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
44.88500
</td>
<td style="text-align:right;">
2427334
</td>
<td style="text-align:right;">
1035.8314
</td>
<td style="text-align:right;">
0.3241201
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
45.93600
</td>
<td style="text-align:right;">
7753310
</td>
<td style="text-align:right;">
882.0818
</td>
<td style="text-align:right;">
0.3240330
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
44.50100
</td>
<td style="text-align:right;">
6921858
</td>
<td style="text-align:right;">
1093.2450
</td>
<td style="text-align:right;">
0.3238440
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
44.77900
</td>
<td style="text-align:right;">
6391288
</td>
<td style="text-align:right;">
1043.5615
</td>
<td style="text-align:right;">
0.3237009
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
47.78400
</td>
<td style="text-align:right;">
30646495
</td>
<td style="text-align:right;">
673.7478
</td>
<td style="text-align:right;">
0.3236786
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
39.90600
</td>
<td style="text-align:right;">
7874230
</td>
<td style="text-align:right;">
2430.2083
</td>
<td style="text-align:right;">
0.3235603
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
47.49500
</td>
<td style="text-align:right;">
10419991
</td>
<td style="text-align:right;">
692.2758
</td>
<td style="text-align:right;">
0.3230611
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
42.46900
</td>
<td style="text-align:right;">
3300000
</td>
<td style="text-align:right;">
1500.8959
</td>
<td style="text-align:right;">
0.3230548
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
48.21100
</td>
<td style="text-align:right;">
5126023
</td>
<td style="text-align:right;">
621.8188
</td>
<td style="text-align:right;">
0.3225493
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
35.98500
</td>
<td style="text-align:right;">
5247469
</td>
<td style="text-align:right;">
5522.7764
</td>
<td style="text-align:right;">
0.3224923
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
40.87000
</td>
<td style="text-align:right;">
11183227
</td>
<td style="text-align:right;">
1959.5938
</td>
<td style="text-align:right;">
0.3222272
</td>
</tr>
<tr>
<td style="text-align:left;">
Gabon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
37.00300
</td>
<td style="text-align:right;">
420702
</td>
<td style="text-align:right;">
4293.4765
</td>
<td style="text-align:right;">
0.3219254
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
43.42400
</td>
<td style="text-align:right;">
326741
</td>
<td style="text-align:right;">
1244.7084
</td>
<td style="text-align:right;">
0.3218665
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
40.08000
</td>
<td style="text-align:right;">
561977
</td>
<td style="text-align:right;">
2242.7466
</td>
<td style="text-align:right;">
0.3216247
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
47.19300
</td>
<td style="text-align:right;">
506000000
</td>
<td style="text-align:right;">
700.7706
</td>
<td style="text-align:right;">
0.3216055
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
43.60100
</td>
<td style="text-align:right;">
3495967
</td>
<td style="text-align:right;">
1196.8106
</td>
<td style="text-align:right;">
0.3213989
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
49.76700
</td>
<td style="text-align:right;">
1116779
</td>
<td style="text-align:right;">
496.5816
</td>
<td style="text-align:right;">
0.3213184
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
42.64300
</td>
<td style="text-align:right;">
5793633
</td>
<td style="text-align:right;">
1399.6074
</td>
<td style="text-align:right;">
0.3212796
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
47.83800
</td>
<td style="text-align:right;">
39463910
</td>
<td style="text-align:right;">
637.1233
</td>
<td style="text-align:right;">
0.3212635
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
47.41200
</td>
<td style="text-align:right;">
35481645
</td>
<td style="text-align:right;">
672.7748
</td>
<td style="text-align:right;">
0.3210875
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
49.40200
</td>
<td style="text-align:right;">
59861301
</td>
<td style="text-align:right;">
515.8894
</td>
<td style="text-align:right;">
0.3209217
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
45.75700
</td>
<td style="text-align:right;">
12607312
</td>
<td style="text-align:right;">
848.2187
</td>
<td style="text-align:right;">
0.3209074
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.24800
</td>
<td style="text-align:right;">
882134
</td>
<td style="text-align:right;">
912.6626
</td>
<td style="text-align:right;">
0.3207838
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
44.24800
</td>
<td style="text-align:right;">
1146757
</td>
<td style="text-align:right;">
1055.8960
</td>
<td style="text-align:right;">
0.3204032
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
41.45400
</td>
<td style="text-align:right;">
3430243
</td>
<td style="text-align:right;">
1654.9887
</td>
<td style="text-align:right;">
0.3195476
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
45.58000
</td>
<td style="text-align:right;">
715523
</td>
<td style="text-align:right;">
835.8096
</td>
<td style="text-align:right;">
0.3189674
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
47.45700
</td>
<td style="text-align:right;">
7824747
</td>
<td style="text-align:right;">
635.5174
</td>
<td style="text-align:right;">
0.3185803
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
43.92200
</td>
<td style="text-align:right;">
1528098
</td>
<td style="text-align:right;">
1067.5348
</td>
<td style="text-align:right;">
0.3185433
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
44.68600
</td>
<td style="text-align:right;">
7454779
</td>
<td style="text-align:right;">
944.4383
</td>
<td style="text-align:right;">
0.3183901
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
46.74800
</td>
<td style="text-align:right;">
13933198
</td>
<td style="text-align:right;">
694.1124
</td>
<td style="text-align:right;">
0.3181088
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
41.97400
</td>
<td style="text-align:right;">
4353666
</td>
<td style="text-align:right;">
1450.9925
</td>
<td style="text-align:right;">
0.3178133
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
45.96400
</td>
<td style="text-align:right;">
109343000
</td>
<td style="text-align:right;">
762.4318
</td>
<td style="text-align:right;">
0.3172618
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
46.13700
</td>
<td style="text-align:right;">
5889574
</td>
<td style="text-align:right;">
743.3870
</td>
<td style="text-align:right;">
0.3172421
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
45.55200
</td>
<td style="text-align:right;">
5650262
</td>
<td style="text-align:right;">
805.5725
</td>
<td style="text-align:right;">
0.3170257
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
46.92300
</td>
<td style="text-align:right;">
80428306
</td>
<td style="text-align:right;">
659.8772
</td>
<td style="text-align:right;">
0.3168312
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
46.06600
</td>
<td style="text-align:right;">
3696513
</td>
<td style="text-align:right;">
740.5063
</td>
<td style="text-align:right;">
0.3165679
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
41.89300
</td>
<td style="text-align:right;">
22223309
</td>
<td style="text-align:right;">
1418.8224
</td>
<td style="text-align:right;">
0.3162231
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
42.95500
</td>
<td style="text-align:right;">
5828892
</td>
<td style="text-align:right;">
1176.8070
</td>
<td style="text-align:right;">
0.3158840
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
40.69600
</td>
<td style="text-align:right;">
3507701
</td>
<td style="text-align:right;">
1726.8879
</td>
<td style="text-align:right;">
0.3155046
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
43.45700
</td>
<td style="text-align:right;">
1927260
</td>
<td style="text-align:right;">
1070.0133
</td>
<td style="text-align:right;">
0.3152758
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
42.38400
</td>
<td style="text-align:right;">
11746035
</td>
<td style="text-align:right;">
1271.2116
</td>
<td style="text-align:right;">
0.3150866
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
46.36400
</td>
<td style="text-align:right;">
7634008
</td>
<td style="text-align:right;">
684.1716
</td>
<td style="text-align:right;">
0.3148002
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
40.84800
</td>
<td style="text-align:right;">
5703324
</td>
<td style="text-align:right;">
1643.3871
</td>
<td style="text-align:right;">
0.3145774
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
41.71600
</td>
<td style="text-align:right;">
3150417
</td>
<td style="text-align:right;">
1389.8176
</td>
<td style="text-align:right;">
0.3139908
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
47.39100
</td>
<td style="text-align:right;">
8392818
</td>
<td style="text-align:right;">
581.1827
</td>
<td style="text-align:right;">
0.3137320
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
43.82800
</td>
<td style="text-align:right;">
31889923
</td>
<td style="text-align:right;">
974.5803
</td>
<td style="text-align:right;">
0.3137089
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
45.36300
</td>
<td style="text-align:right;">
33796140
</td>
<td style="text-align:right;">
772.0492
</td>
<td style="text-align:right;">
0.3137049
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
42.46000
</td>
<td style="text-align:right;">
170928
</td>
<td style="text-align:right;">
1211.1485
</td>
<td style="text-align:right;">
0.3135141
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.55700
</td>
<td style="text-align:right;">
46679944
</td>
<td style="text-align:right;">
747.0835
</td>
<td style="text-align:right;">
0.3134890
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
48.49200
</td>
<td style="text-align:right;">
996380
</td>
<td style="text-align:right;">
498.6390
</td>
<td style="text-align:right;">
0.3132950
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
45.34400
</td>
<td style="text-align:right;">
7688797
</td>
<td style="text-align:right;">
767.2717
</td>
<td style="text-align:right;">
0.3132808
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
49.58000
</td>
<td style="text-align:right;">
8390505
</td>
<td style="text-align:right;">
430.0707
</td>
<td style="text-align:right;">
0.3126959
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
47.47100
</td>
<td style="text-align:right;">
4580410
</td>
<td style="text-align:right;">
559.6032
</td>
<td style="text-align:right;">
0.3123935
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
44.87300
</td>
<td style="text-align:right;">
1193708
</td>
<td style="text-align:right;">
796.6645
</td>
<td style="text-align:right;">
0.3117811
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
43.79500
</td>
<td style="text-align:right;">
6633514
</td>
<td style="text-align:right;">
930.5964
</td>
<td style="text-align:right;">
0.3113692
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
44.57800
</td>
<td style="text-align:right;">
21210254
</td>
<td style="text-align:right;">
816.5591
</td>
<td style="text-align:right;">
0.3108751
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
43.66200
</td>
<td style="text-align:right;">
285483
</td>
<td style="text-align:right;">
927.8253
</td>
<td style="text-align:right;">
0.3102881
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
44.05600
</td>
<td style="text-align:right;">
19941073
</td>
<td style="text-align:right;">
861.5932
</td>
<td style="text-align:right;">
0.3096946
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
37.32800
</td>
<td style="text-align:right;">
71851
</td>
<td style="text-align:right;">
2864.9691
</td>
<td style="text-align:right;">
0.3090473
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
44.02000
</td>
<td style="text-align:right;">
6349365
</td>
<td style="text-align:right;">
847.9912
</td>
<td style="text-align:right;">
0.3087130
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
46.68400
</td>
<td style="text-align:right;">
42999530
</td>
<td style="text-align:right;">
573.7413
</td>
<td style="text-align:right;">
0.3084259
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
39.62400
</td>
<td style="text-align:right;">
9753392
</td>
<td style="text-align:right;">
1770.3371
</td>
<td style="text-align:right;">
0.3082177
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
42.03800
</td>
<td style="text-align:right;">
2672000
</td>
<td style="text-align:right;">
1147.3888
</td>
<td style="text-align:right;">
0.3080337
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
46.38800
</td>
<td style="text-align:right;">
1472041
</td>
<td style="text-align:right;">
579.2317
</td>
<td style="text-align:right;">
0.3069298
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
45.64200
</td>
<td style="text-align:right;">
6502825
</td>
<td style="text-align:right;">
632.8039
</td>
<td style="text-align:right;">
0.3061930
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
43.59100
</td>
<td style="text-align:right;">
5433886
</td>
<td style="text-align:right;">
854.7360
</td>
<td style="text-align:right;">
0.3060636
</td>
</tr>
<tr>
<td style="text-align:left;">
Ghana
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
43.14900
</td>
<td style="text-align:right;">
5581001
</td>
<td style="text-align:right;">
911.2989
</td>
<td style="text-align:right;">
0.3058359
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
44.74100
</td>
<td style="text-align:right;">
4369038
</td>
<td style="text-align:right;">
706.0165
</td>
<td style="text-align:right;">
0.3052430
</td>
</tr>
<tr>
<td style="text-align:left;">
Cote d'Ivoire
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
40.47700
</td>
<td style="text-align:right;">
2977019
</td>
<td style="text-align:right;">
1388.5947
</td>
<td style="text-align:right;">
0.3046280
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
45.00000
</td>
<td style="text-align:right;">
4657072
</td>
<td style="text-align:right;">
670.0806
</td>
<td style="text-align:right;">
0.3045650
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
45.00900
</td>
<td style="text-align:right;">
11824495
</td>
<td style="text-align:right;">
665.4231
</td>
<td style="text-align:right;">
0.3042994
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
40.97300
</td>
<td style="text-align:right;">
3840161
</td>
<td style="text-align:right;">
1254.5761
</td>
<td style="text-align:right;">
0.3040357
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
42.61800
</td>
<td style="text-align:right;">
2151895
</td>
<td style="text-align:right;">
949.4991
</td>
<td style="text-align:right;">
0.3038924
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
41.47800
</td>
<td style="text-align:right;">
1733638
</td>
<td style="text-align:right;">
1136.0566
</td>
<td style="text-align:right;">
0.3035021
</td>
</tr>
<tr>
<td style="text-align:left;">
Swaziland
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
41.40700
</td>
<td style="text-align:right;">
290243
</td>
<td style="text-align:right;">
1148.3766
</td>
<td style="text-align:right;">
0.3034471
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
45.25200
</td>
<td style="text-align:right;">
70759295
</td>
<td style="text-align:right;">
630.2336
</td>
<td style="text-align:right;">
0.3033851
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
44.24600
</td>
<td style="text-align:right;">
10863958
</td>
<td style="text-align:right;">
722.0038
</td>
<td style="text-align:right;">
0.3028963
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
48.45100
</td>
<td style="text-align:right;">
3080907
</td>
<td style="text-align:right;">
406.8841
</td>
<td style="text-align:right;">
0.3027826
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
48.09100
</td>
<td style="text-align:right;">
52088559
</td>
<td style="text-align:right;">
421.3535
</td>
<td style="text-align:right;">
0.3022807
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
46.45300
</td>
<td style="text-align:right;">
2915959
</td>
<td style="text-align:right;">
521.1341
</td>
<td style="text-align:right;">
0.3022533
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
40.42800
</td>
<td style="text-align:right;">
5359923
</td>
<td style="text-align:right;">
1313.0481
</td>
<td style="text-align:right;">
0.3019070
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
42.59800
</td>
<td style="text-align:right;">
6437188
</td>
<td style="text-align:right;">
909.7221
</td>
<td style="text-align:right;">
0.3018537
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
45.91000
</td>
<td style="text-align:right;">
3834415
</td>
<td style="text-align:right;">
556.1033
</td>
<td style="text-align:right;">
0.3018214
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
44.55500
</td>
<td style="text-align:right;">
7332638
</td>
<td style="text-align:right;">
668.3000
</td>
<td style="text-align:right;">
0.3014299
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
42.89100
</td>
<td style="text-align:right;">
4710497
</td>
<td style="text-align:right;">
857.2504
</td>
<td style="text-align:right;">
0.3012798
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
43.41300
</td>
<td style="text-align:right;">
7852401
</td>
<td style="text-align:right;">
785.6538
</td>
<td style="text-align:right;">
0.3010085
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
39.32900
</td>
<td style="text-align:right;">
3054547
</td>
<td style="text-align:right;">
1567.6530
</td>
<td style="text-align:right;">
0.3009494
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
45.50400
</td>
<td style="text-align:right;">
1332459
</td>
<td style="text-align:right;">
575.7047
</td>
<td style="text-align:right;">
0.3007917
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
49.37900
</td>
<td style="text-align:right;">
25870271
</td>
<td style="text-align:right;">
349.0000
</td>
<td style="text-align:right;">
0.3007008
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
47.36000
</td>
<td style="text-align:right;">
7021078
</td>
<td style="text-align:right;">
446.4035
</td>
<td style="text-align:right;">
0.3005306
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
42.02400
</td>
<td style="text-align:right;">
192675
</td>
<td style="text-align:right;">
958.5668
</td>
<td style="text-align:right;">
0.3000722
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
44.73600
</td>
<td style="text-align:right;">
5809236
</td>
<td style="text-align:right;">
631.6999
</td>
<td style="text-align:right;">
0.3000338
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
42.56800
</td>
<td style="text-align:right;">
6144562
</td>
<td style="text-align:right;">
862.5408
</td>
<td style="text-align:right;">
0.2992833
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
47.74700
</td>
<td style="text-align:right;">
893143
</td>
<td style="text-align:right;">
411.8006
</td>
<td style="text-align:right;">
0.2989796
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
42.51800
</td>
<td style="text-align:right;">
99028000
</td>
<td style="text-align:right;">
849.2898
</td>
<td style="text-align:right;">
0.2982471
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
40.00600
</td>
<td style="text-align:right;">
3868905
</td>
<td style="text-align:right;">
1294.4478
</td>
<td style="text-align:right;">
0.2981620
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
46.02700
</td>
<td style="text-align:right;">
2269414
</td>
<td style="text-align:right;">
506.1139
</td>
<td style="text-align:right;">
0.2980815
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
38.86500
</td>
<td style="text-align:right;">
5181679
</td>
<td style="text-align:right;">
1589.2027
</td>
<td style="text-align:right;">
0.2979507
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
43.97100
</td>
<td style="text-align:right;">
12412593
</td>
<td style="text-align:right;">
674.7881
</td>
<td style="text-align:right;">
0.2979208
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
42.12200
</td>
<td style="text-align:right;">
17486434
</td>
<td style="text-align:right;">
896.3146
</td>
<td style="text-align:right;">
0.2978303
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
39.88100
</td>
<td style="text-align:right;">
2894855
</td>
<td style="text-align:right;">
1308.4956
</td>
<td style="text-align:right;">
0.2976781
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
43.26600
</td>
<td style="text-align:right;">
1050938
</td>
<td style="text-align:right;">
745.5399
</td>
<td style="text-align:right;">
0.2976310
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
43.30800
</td>
<td style="text-align:right;">
4048013
</td>
<td style="text-align:right;">
738.6906
</td>
<td style="text-align:right;">
0.2975042
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
43.45300
</td>
<td style="text-align:right;">
62821884
</td>
<td style="text-align:right;">
721.1861
</td>
<td style="text-align:right;">
0.2974164
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
44.91600
</td>
<td style="text-align:right;">
38111756
</td>
<td style="text-align:right;">
577.8607
</td>
<td style="text-align:right;">
0.2970795
</td>
</tr>
<tr>
<td style="text-align:left;">
Sudan
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
38.63500
</td>
<td style="text-align:right;">
8504667
</td>
<td style="text-align:right;">
1615.9911
</td>
<td style="text-align:right;">
0.2968592
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
42.33800
</td>
<td style="text-align:right;">
1076852
</td>
<td style="text-align:right;">
846.1203
</td>
<td style="text-align:right;">
0.2968198
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
46.34400
</td>
<td style="text-align:right;">
16603334
</td>
<td style="text-align:right;">
472.3461
</td>
<td style="text-align:right;">
0.2968062
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
42.27000
</td>
<td style="text-align:right;">
6464046
</td>
<td style="text-align:right;">
853.5409
</td>
<td style="text-align:right;">
0.2967270
</td>
</tr>
<tr>
<td style="text-align:left;">
Comoros
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
40.71500
</td>
<td style="text-align:right;">
153936
</td>
<td style="text-align:right;">
1102.9909
</td>
<td style="text-align:right;">
0.2966682
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
42.61400
</td>
<td style="text-align:right;">
1482628
</td>
<td style="text-align:right;">
803.0055
</td>
<td style="text-align:right;">
0.2964368
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
44.85200
</td>
<td style="text-align:right;">
1956875
</td>
<td style="text-align:right;">
572.1996
</td>
<td style="text-align:right;">
0.2961970
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
39.84800
</td>
<td style="text-align:right;">
7407075
</td>
<td style="text-align:right;">
1265.0470
</td>
<td style="text-align:right;">
0.2960323
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
44.60000
</td>
<td style="text-align:right;">
3992121
</td>
<td style="text-align:right;">
590.5807
</td>
<td style="text-align:right;">
0.2959995
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
43.76700
</td>
<td style="text-align:right;">
5637246
</td>
<td style="text-align:right;">
663.2237
</td>
<td style="text-align:right;">
0.2957517
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
45.41500
</td>
<td style="text-align:right;">
6960067
</td>
<td style="text-align:right;">
523.4323
</td>
<td style="text-align:right;">
0.2957073
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
34.00000
</td>
<td style="text-align:right;">
4826015
</td>
<td style="text-align:right;">
4269.2767
</td>
<td style="text-align:right;">
0.2955995
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
41.04000
</td>
<td style="text-align:right;">
47287752
</td>
<td style="text-align:right;">
1014.5141
</td>
<td style="text-align:right;">
0.2954673
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
44.02600
</td>
<td style="text-align:right;">
18473780
</td>
<td style="text-align:right;">
633.6179
</td>
<td style="text-align:right;">
0.2954108
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
41.84200
</td>
<td style="text-align:right;">
608274
</td>
<td style="text-align:right;">
884.7553
</td>
<td style="text-align:right;">
0.2952856
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
43.43600
</td>
<td style="text-align:right;">
41346560
</td>
<td style="text-align:right;">
684.5971
</td>
<td style="text-align:right;">
0.2949479
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
42.57100
</td>
<td style="text-align:right;">
6675501
</td>
<td style="text-align:right;">
774.3711
</td>
<td style="text-align:right;">
0.2945300
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
43.60500
</td>
<td style="text-align:right;">
454000000
</td>
<td style="text-align:right;">
658.3472
</td>
<td style="text-align:right;">
0.2943223
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
43.76400
</td>
<td style="text-align:right;">
1703617
</td>
<td style="text-align:right;">
640.3224
</td>
<td style="text-align:right;">
0.2941319
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
42.08200
</td>
<td style="text-align:right;">
19951656
</td>
<td style="text-align:right;">
823.6856
</td>
<td style="text-align:right;">
0.2938489
</td>
</tr>
<tr>
<td style="text-align:left;">
Haiti
</td>
<td style="text-align:left;">
Americas
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
37.57900
</td>
<td style="text-align:right;">
3201488
</td>
<td style="text-align:right;">
1840.3669
</td>
<td style="text-align:right;">
0.2938268
</td>
</tr>
<tr>
<td style="text-align:left;">
Oman
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
37.57800
</td>
<td style="text-align:right;">
507833
</td>
<td style="text-align:right;">
1828.2303
</td>
<td style="text-align:right;">
0.2935604
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
43.91600
</td>
<td style="text-align:right;">
6998256
</td>
<td style="text-align:right;">
618.0141
</td>
<td style="text-align:right;">
0.2935338
</td>
</tr>
<tr>
<td style="text-align:left;">
Mongolia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
42.24400
</td>
<td style="text-align:right;">
800663
</td>
<td style="text-align:right;">
786.5669
</td>
<td style="text-align:right;">
0.2929542
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
41.20800
</td>
<td style="text-align:right;">
1357445
</td>
<td style="text-align:right;">
925.9083
</td>
<td style="text-align:right;">
0.2927599
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
42.97400
</td>
<td style="text-align:right;">
9452826
</td>
<td style="text-align:right;">
698.5356
</td>
<td style="text-align:right;">
0.2927116
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
44.51000
</td>
<td style="text-align:right;">
34617799
</td>
<td style="text-align:right;">
556.8084
</td>
<td style="text-align:right;">
0.2926762
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
40.23800
</td>
<td style="text-align:right;">
9417789
</td>
<td style="text-align:right;">
1071.3538
</td>
<td style="text-align:right;">
0.2919747
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
38.44500
</td>
<td style="text-align:right;">
3464522
</td>
<td style="text-align:right;">
1465.0108
</td>
<td style="text-align:right;">
0.2914773
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
39.47500
</td>
<td style="text-align:right;">
1523478
</td>
<td style="text-align:right;">
1193.0688
</td>
<td style="text-align:right;">
0.2908561
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
42.88700
</td>
<td style="text-align:right;">
28998543
</td>
<td style="text-align:right;">
676.2854
</td>
<td style="text-align:right;">
0.2906751
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
40.11800
</td>
<td style="text-align:right;">
4534062
</td>
<td style="text-align:right;">
1054.3849
</td>
<td style="text-align:right;">
0.2904378
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
45.54800
</td>
<td style="text-align:right;">
41672143
</td>
<td style="text-align:right;">
457.7192
</td>
<td style="text-align:right;">
0.2902181
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
38.97700
</td>
<td style="text-align:right;">
3428839
</td>
<td style="text-align:right;">
1284.7332
</td>
<td style="text-align:right;">
0.2901875
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
45.32600
</td>
<td style="text-align:right;">
6121610
</td>
<td style="text-align:right;">
463.1151
</td>
<td style="text-align:right;">
0.2893561
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
40.54600
</td>
<td style="text-align:right;">
5060262
</td>
<td style="text-align:right;">
954.2092
</td>
<td style="text-align:right;">
0.2893264
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
42.12900
</td>
<td style="text-align:right;">
25268405
</td>
<td style="text-align:right;">
726.7341
</td>
<td style="text-align:right;">
0.2886900
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
39.36000
</td>
<td style="text-align:right;">
41871351
</td>
<td style="text-align:right;">
1150.9275
</td>
<td style="text-align:right;">
0.2885367
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
44.53500
</td>
<td style="text-align:right;">
2512642
</td>
<td style="text-align:right;">
505.7538
</td>
<td style="text-align:right;">
0.2883860
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
40.35800
</td>
<td style="text-align:right;">
1925173
</td>
<td style="text-align:right;">
959.6011
</td>
<td style="text-align:right;">
0.2882214
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
40.65200
</td>
<td style="text-align:right;">
15577932
</td>
<td style="text-align:right;">
905.8602
</td>
<td style="text-align:right;">
0.2878843
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
41.29100
</td>
<td style="text-align:right;">
5682086
</td>
<td style="text-align:right;">
808.8971
</td>
<td style="text-align:right;">
0.2875475
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
40.76200
</td>
<td style="text-align:right;">
4227026
</td>
<td style="text-align:right;">
874.6859
</td>
<td style="text-align:right;">
0.2871786
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
43.51500
</td>
<td style="text-align:right;">
30770372
</td>
<td style="text-align:right;">
566.2439
</td>
<td style="text-align:right;">
0.2868940
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
44.14200
</td>
<td style="text-align:right;">
2260187
</td>
<td style="text-align:right;">
514.3242
</td>
<td style="text-align:right;">
0.2866126
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
40.82200
</td>
<td style="text-align:right;">
13867957
</td>
<td style="text-align:right;">
852.3959
</td>
<td style="text-align:right;">
0.2865053
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
44.50136
</td>
<td style="text-align:right;">
665770000
</td>
<td style="text-align:right;">
487.6740
</td>
<td style="text-align:right;">
0.2864833
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
45.67800
</td>
<td style="text-align:right;">
3193942
</td>
<td style="text-align:right;">
414.5073
</td>
<td style="text-align:right;">
0.2863353
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
44.10000
</td>
<td style="text-align:right;">
3451079
</td>
<td style="text-align:right;">
510.9637
</td>
<td style="text-align:right;">
0.2860392
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
43.89000
</td>
<td style="text-align:right;">
2637297
</td>
<td style="text-align:right;">
524.8758
</td>
<td style="text-align:right;">
0.2859034
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
43.00000
</td>
<td style="text-align:right;">
3051242
</td>
<td style="text-align:right;">
597.4731
</td>
<td style="text-align:right;">
0.2858996
</td>
</tr>
<tr>
<td style="text-align:left;">
Djibouti
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
34.81200
</td>
<td style="text-align:right;">
63149
</td>
<td style="text-align:right;">
2669.5295
</td>
<td style="text-align:right;">
0.2856585
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
43.75300
</td>
<td style="text-align:right;">
2814651
</td>
<td style="text-align:right;">
531.4824
</td>
<td style="text-align:right;">
0.2855802
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
39.85400
</td>
<td style="text-align:right;">
12881816
</td>
<td style="text-align:right;">
978.0114
</td>
<td style="text-align:right;">
0.2854098
</td>
</tr>
<tr>
<td style="text-align:left;">
Zambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
39.19300
</td>
<td style="text-align:right;">
10595811
</td>
<td style="text-align:right;">
1071.6139
</td>
<td style="text-align:right;">
0.2844018
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
41.53600
</td>
<td style="text-align:right;">
1279406
</td>
<td style="text-align:right;">
713.6036
</td>
<td style="text-align:right;">
0.2838388
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
39.48700
</td>
<td style="text-align:right;">
4076008
</td>
<td style="text-align:right;">
997.7661
</td>
<td style="text-align:right;">
0.2836028
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
41.71400
</td>
<td style="text-align:right;">
6491649
</td>
<td style="text-align:right;">
686.3953
</td>
<td style="text-align:right;">
0.2833686
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
41.24500
</td>
<td style="text-align:right;">
927524
</td>
<td style="text-align:right;">
736.4154
</td>
<td style="text-align:right;">
0.2832001
</td>
</tr>
<tr>
<td style="text-align:left;">
Cameroon
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
38.52300
</td>
<td style="text-align:right;">
5009067
</td>
<td style="text-align:right;">
1172.6677
</td>
<td style="text-align:right;">
0.2831506
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
40.69700
</td>
<td style="text-align:right;">
5127935
</td>
<td style="text-align:right;">
794.8266
</td>
<td style="text-align:right;">
0.2826682
</td>
</tr>
<tr>
<td style="text-align:left;">
Senegal
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
37.27800
</td>
<td style="text-align:right;">
2755589
</td>
<td style="text-align:right;">
1450.3570
</td>
<td style="text-align:right;">
0.2822397
</td>
</tr>
<tr>
<td style="text-align:left;">
Tanzania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
41.21500
</td>
<td style="text-align:right;">
8322925
</td>
<td style="text-align:right;">
716.6501
</td>
<td style="text-align:right;">
0.2818279
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
39.65800
</td>
<td style="text-align:right;">
6099799
</td>
<td style="text-align:right;">
926.9603
</td>
<td style="text-align:right;">
0.2817949
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
42.22100
</td>
<td style="text-align:right;">
2200725
</td>
<td style="text-align:right;">
609.1740
</td>
<td style="text-align:right;">
0.2815718
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
44.05700
</td>
<td style="text-align:right;">
3529983
</td>
<td style="text-align:right;">
464.0995
</td>
<td style="text-align:right;">
0.2813522
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
41.47200
</td>
<td style="text-align:right;">
11261690
</td>
<td style="text-align:right;">
676.4422
</td>
<td style="text-align:right;">
0.2810947
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
41.67400
</td>
<td style="text-align:right;">
16317921
</td>
<td style="text-align:right;">
649.3414
</td>
<td style="text-align:right;">
0.2806915
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
39.91800
</td>
<td style="text-align:right;">
90124000
</td>
<td style="text-align:right;">
858.9003
</td>
<td style="text-align:right;">
0.2804763
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
41.76300
</td>
<td style="text-align:right;">
22227415
</td>
<td style="text-align:right;">
635.3414
</td>
<td style="text-align:right;">
0.2803443
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
43.41500
</td>
<td style="text-align:right;">
6083619
</td>
<td style="text-align:right;">
496.9136
</td>
<td style="text-align:right;">
0.2803372
</td>
</tr>
<tr>
<td style="text-align:left;">
Chad
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
38.09200
</td>
<td style="text-align:right;">
2682462
</td>
<td style="text-align:right;">
1178.6659
</td>
<td style="text-align:right;">
0.2801848
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
41.21600
</td>
<td style="text-align:right;">
56839289
</td>
<td style="text-align:right;">
686.3416
</td>
<td style="text-align:right;">
0.2799823
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
45.10800
</td>
<td style="text-align:right;">
23634436
</td>
<td style="text-align:right;">
388.0000
</td>
<td style="text-align:right;">
0.2796618
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
41.01200
</td>
<td style="text-align:right;">
5359092
</td>
<td style="text-align:right;">
699.4897
</td>
<td style="text-align:right;">
0.2794059
</td>
</tr>
<tr>
<td style="text-align:left;">
Mauritania
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
40.54300
</td>
<td style="text-align:right;">
1022556
</td>
<td style="text-align:right;">
743.1159
</td>
<td style="text-align:right;">
0.2787619
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
43.48700
</td>
<td style="text-align:right;">
12311143
</td>
<td style="text-align:right;">
469.7093
</td>
<td style="text-align:right;">
0.2782556
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
38.33300
</td>
<td style="text-align:right;">
4260884
</td>
<td style="text-align:right;">
1068.6963
</td>
<td style="text-align:right;">
0.2780526
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
36.98100
</td>
<td style="text-align:right;">
3080153
</td>
<td style="text-align:right;">
1369.4883
</td>
<td style="text-align:right;">
0.2777844
</td>
</tr>
<tr>
<td style="text-align:left;">
Madagascar
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
36.68100
</td>
<td style="text-align:right;">
4762912
</td>
<td style="text-align:right;">
1443.0117
</td>
<td style="text-align:right;">
0.2775260
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
44.28400
</td>
<td style="text-align:right;">
13160731
</td>
<td style="text-align:right;">
410.8968
</td>
<td style="text-align:right;">
0.2771940
</td>
</tr>
<tr>
<td style="text-align:left;">
Benin
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
38.22300
</td>
<td style="text-align:right;">
1738315
</td>
<td style="text-align:right;">
1062.7522
</td>
<td style="text-align:right;">
0.2770330
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
41.76600
</td>
<td style="text-align:right;">
4730997
</td>
<td style="text-align:right;">
584.6220
</td>
<td style="text-align:right;">
0.2767504
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
38.98700
</td>
<td style="text-align:right;">
259864
</td>
<td style="text-align:right;">
915.5960
</td>
<td style="text-align:right;">
0.2765268
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
40.32800
</td>
<td style="text-align:right;">
9809596
</td>
<td style="text-align:right;">
724.9178
</td>
<td style="text-align:right;">
0.2762437
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
37.46400
</td>
<td style="text-align:right;">
1392284
</td>
<td style="text-align:right;">
1190.8443
</td>
<td style="text-align:right;">
0.2759661
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
36.78800
</td>
<td style="text-align:right;">
3140897
</td>
<td style="text-align:right;">
1348.2852
</td>
<td style="text-align:right;">
0.2757376
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
37.80200
</td>
<td style="text-align:right;">
37173340
</td>
<td style="text-align:right;">
1100.5926
</td>
<td style="text-align:right;">
0.2753572
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
39.32700
</td>
<td style="text-align:right;">
825987
</td>
<td style="text-align:right;">
838.1240
</td>
<td style="text-align:right;">
0.2753222
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
42.49500
</td>
<td style="text-align:right;">
11127868
</td>
<td style="text-align:right;">
502.3197
</td>
<td style="text-align:right;">
0.2748749
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
31.99900
</td>
<td style="text-align:right;">
4561361
</td>
<td style="text-align:right;">
3827.9405
</td>
<td style="text-align:right;">
0.2745711
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
39.97800
</td>
<td style="text-align:right;">
5824797
</td>
<td style="text-align:right;">
734.7535
</td>
<td style="text-align:right;">
0.2744066
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
40.51600
</td>
<td style="text-align:right;">
277603
</td>
<td style="text-align:right;">
672.4123
</td>
<td style="text-align:right;">
0.2743631
</td>
</tr>
<tr>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
44.00000
</td>
<td style="text-align:right;">
556263527
</td>
<td style="text-align:right;">
400.4486
</td>
<td style="text-align:right;">
0.2742376
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
40.80200
</td>
<td style="text-align:right;">
1912974
</td>
<td style="text-align:right;">
636.6229
</td>
<td style="text-align:right;">
0.2739788
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
42.11500
</td>
<td style="text-align:right;">
27860297
</td>
<td style="text-align:right;">
516.1186
</td>
<td style="text-align:right;">
0.2736039
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
42.79500
</td>
<td style="text-align:right;">
12587223
</td>
<td style="text-align:right;">
462.2114
</td>
<td style="text-align:right;">
0.2731115
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
43.54800
</td>
<td style="text-align:right;">
3330989
</td>
<td style="text-align:right;">
412.9775
</td>
<td style="text-align:right;">
0.2728158
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
45.04700
</td>
<td style="text-align:right;">
813338
</td>
<td style="text-align:right;">
335.9971
</td>
<td style="text-align:right;">
0.2725415
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
46.46200
</td>
<td style="text-align:right;">
64606759
</td>
<td style="text-align:right;">
277.5519
</td>
<td style="text-align:right;">
0.2718681
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
40.50200
</td>
<td style="text-align:right;">
1112796
</td>
<td style="text-align:right;">
634.1952
</td>
<td style="text-align:right;">
0.2718034
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
41.50000
</td>
<td style="text-align:right;">
2822082
</td>
<td style="text-align:right;">
540.2894
</td>
<td style="text-align:right;">
0.2715840
</td>
</tr>
<tr>
<td style="text-align:left;">
Togo
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
38.59600
</td>
<td style="text-align:right;">
1219113
</td>
<td style="text-align:right;">
859.8087
</td>
<td style="text-align:right;">
0.2712300
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
39.14300
</td>
<td style="text-align:right;">
14100005
</td>
<td style="text-align:right;">
780.5423
</td>
<td style="text-align:right;">
0.2711363
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
39.98900
</td>
<td style="text-align:right;">
11926563
</td>
<td style="text-align:right;">
672.0386
</td>
<td style="text-align:right;">
0.2707713
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
38.59800
</td>
<td style="text-align:right;">
3692184
</td>
<td style="text-align:right;">
835.5234
</td>
<td style="text-align:right;">
0.2700938
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
42.18900
</td>
<td style="text-align:right;">
1820319
</td>
<td style="text-align:right;">
468.7950
</td>
<td style="text-align:right;">
0.2698647
</td>
</tr>
<tr>
<td style="text-align:left;">
Vietnam
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
40.41200
</td>
<td style="text-align:right;">
26246839
</td>
<td style="text-align:right;">
605.0665
</td>
<td style="text-align:right;">
0.2692232
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
40.24900
</td>
<td style="text-align:right;">
409000000
</td>
<td style="text-align:right;">
590.0620
</td>
<td style="text-align:right;">
0.2670861
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
38.84200
</td>
<td style="text-align:right;">
3811387
</td>
<td style="text-align:right;">
741.6662
</td>
<td style="text-align:right;">
0.2669874
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
38.43800
</td>
<td style="text-align:right;">
14880372
</td>
<td style="text-align:right;">
786.1134
</td>
<td style="text-align:right;">
0.2665372
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
42.86100
</td>
<td style="text-align:right;">
12891952
</td>
<td style="text-align:right;">
389.8762
</td>
<td style="text-align:right;">
0.2659458
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
39.34800
</td>
<td style="text-align:right;">
51365468
</td>
<td style="text-align:right;">
661.6375
</td>
<td style="text-align:right;">
0.2657927
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
39.39300
</td>
<td style="text-align:right;">
10332057
</td>
<td style="text-align:right;">
652.3969
</td>
<td style="text-align:right;">
0.2655204
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
35.40000
</td>
<td style="text-align:right;">
2879013
</td>
<td style="text-align:right;">
1353.7598
</td>
<td style="text-align:right;">
0.2654833
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
39.97700
</td>
<td style="text-align:right;">
5828158
</td>
<td style="text-align:right;">
581.3689
</td>
<td style="text-align:right;">
0.2646641
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
39.48600
</td>
<td style="text-align:right;">
975950
</td>
<td style="text-align:right;">
620.9700
</td>
<td style="text-align:right;">
0.2641197
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
38.30800
</td>
<td style="text-align:right;">
517101
</td>
<td style="text-align:right;">
756.0868
</td>
<td style="text-align:right;">
0.2640841
</td>
</tr>
<tr>
<td style="text-align:left;">
Nigeria
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
36.32400
</td>
<td style="text-align:right;">
33119096
</td>
<td style="text-align:right;">
1077.2819
</td>
<td style="text-align:right;">
0.2637824
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
39.89700
</td>
<td style="text-align:right;">
4578212
</td>
<td style="text-align:right;">
574.6482
</td>
<td style="text-align:right;">
0.2636520
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
41.36600
</td>
<td style="text-align:right;">
5322536
</td>
<td style="text-align:right;">
434.0383
</td>
<td style="text-align:right;">
0.2612862
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
36.98400
</td>
<td style="text-align:right;">
6740785
</td>
<td style="text-align:right;">
862.4421
</td>
<td style="text-align:right;">
0.2600194
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
34.97700
</td>
<td style="text-align:right;">
2780415
</td>
<td style="text-align:right;">
1258.1474
</td>
<td style="text-align:right;">
0.2596465
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
37.81400
</td>
<td style="text-align:right;">
4919632
</td>
<td style="text-align:right;">
722.5120
</td>
<td style="text-align:right;">
0.2588922
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
37.46500
</td>
<td style="text-align:right;">
745228
</td>
<td style="text-align:right;">
764.7260
</td>
<td style="text-align:right;">
0.2587154
</td>
</tr>
<tr>
<td style="text-align:left;">
Niger
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
37.44400
</td>
<td style="text-align:right;">
3379468
</td>
<td style="text-align:right;">
761.8794
</td>
<td style="text-align:right;">
0.2584252
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
40.00000
</td>
<td style="text-align:right;">
2534927
</td>
<td style="text-align:right;">
493.3239
</td>
<td style="text-align:right;">
0.2579844
</td>
</tr>
<tr>
<td style="text-align:left;">
Indonesia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
37.46800
</td>
<td style="text-align:right;">
82052000
</td>
<td style="text-align:right;">
749.6817
</td>
<td style="text-align:right;">
0.2579619
</td>
</tr>
<tr>
<td style="text-align:left;">
Central African Republic
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
35.46300
</td>
<td style="text-align:right;">
1291695
</td>
<td style="text-align:right;">
1071.3107
</td>
<td style="text-align:right;">
0.2573249
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
42.04500
</td>
<td style="text-align:right;">
2961915
</td>
<td style="text-align:right;">
355.2032
</td>
<td style="text-align:right;">
0.2568098
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
44.96600
</td>
<td style="text-align:right;">
55379852
</td>
<td style="text-align:right;">
241.1659
</td>
<td style="text-align:right;">
0.2565425
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
41.90500
</td>
<td style="text-align:right;">
21731844
</td>
<td style="text-align:right;">
350.0000
</td>
<td style="text-align:right;">
0.2553115
</td>
</tr>
<tr>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
30.01500
</td>
<td style="text-align:right;">
4232095
</td>
<td style="text-align:right;">
3520.6103
</td>
<td style="text-align:right;">
0.2549345
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
39.48700
</td>
<td style="text-align:right;">
4147252
</td>
<td style="text-align:right;">
495.5148
</td>
<td style="text-align:right;">
0.2548577
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
36.48600
</td>
<td style="text-align:right;">
625361
</td>
<td style="text-align:right;">
820.2246
</td>
<td style="text-align:right;">
0.2546136
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
37.48400
</td>
<td style="text-align:right;">
46886859
</td>
<td style="text-align:right;">
684.2442
</td>
<td style="text-align:right;">
0.2545113
</td>
</tr>
<tr>
<td style="text-align:left;">
Congo, Dem. Rep.
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
42.58700
</td>
<td style="text-align:right;">
47798986
</td>
<td style="text-align:right;">
312.1884
</td>
<td style="text-align:right;">
0.2544028
</td>
</tr>
<tr>
<td style="text-align:left;">
Liberia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
38.48000
</td>
<td style="text-align:right;">
863308
</td>
<td style="text-align:right;">
575.5730
</td>
<td style="text-align:right;">
0.2543523
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
37.19700
</td>
<td style="text-align:right;">
3451418
</td>
<td style="text-align:right;">
708.7595
</td>
<td style="text-align:right;">
0.2539245
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
40.31700
</td>
<td style="text-align:right;">
7450606
</td>
<td style="text-align:right;">
421.6240
</td>
<td style="text-align:right;">
0.2534434
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
38.48700
</td>
<td style="text-align:right;">
5212416
</td>
<td style="text-align:right;">
545.0099
</td>
<td style="text-align:right;">
0.2522145
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
34.11300
</td>
<td style="text-align:right;">
2662190
</td>
<td style="text-align:right;">
1206.0435
</td>
<td style="text-align:right;">
0.2517321
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
40.05900
</td>
<td style="text-align:right;">
25145372
</td>
<td style="text-align:right;">
419.4564
</td>
<td style="text-align:right;">
0.2516068
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
38.11300
</td>
<td style="text-align:right;">
8680909
</td>
<td style="text-align:right;">
566.6692
</td>
<td style="text-align:right;">
0.2513085
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
37.68600
</td>
<td style="text-align:right;">
9682338
</td>
<td style="text-align:right;">
597.9364
</td>
<td style="text-align:right;">
0.2505981
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
40.53300
</td>
<td style="text-align:right;">
2667518
</td>
<td style="text-align:right;">
379.5646
</td>
<td style="text-align:right;">
0.2503710
</td>
</tr>
<tr>
<td style="text-align:left;">
Lesotho
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
42.13800
</td>
<td style="text-align:right;">
748747
</td>
<td style="text-align:right;">
298.8462
</td>
<td style="text-align:right;">
0.2498063
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
37.48500
</td>
<td style="text-align:right;">
249220
</td>
<td style="text-align:right;">
582.8420
</td>
<td style="text-align:right;">
0.2482647
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
40.15800
</td>
<td style="text-align:right;">
1666618
</td>
<td style="text-align:right;">
380.9958
</td>
<td style="text-align:right;">
0.2482118
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
36.08800
</td>
<td style="text-align:right;">
13079460
</td>
<td style="text-align:right;">
739.9811
</td>
<td style="text-align:right;">
0.2479719
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
35.85700
</td>
<td style="text-align:right;">
439593
</td>
<td style="text-align:right;">
734.7829
</td>
<td style="text-align:right;">
0.2461218
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
35.18000
</td>
<td style="text-align:right;">
6120081
</td>
<td style="text-align:right;">
825.6232
</td>
<td style="text-align:right;">
0.2457398
</td>
</tr>
<tr>
<td style="text-align:left;">
India
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
37.37300
</td>
<td style="text-align:right;">
372000000
</td>
<td style="text-align:right;">
546.5657
</td>
<td style="text-align:right;">
0.2450250
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
35.75300
</td>
<td style="text-align:right;">
3140003
</td>
<td style="text-align:right;">
686.3737
</td>
<td style="text-align:right;">
0.2428736
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
35.49200
</td>
<td style="text-align:right;">
601287
</td>
<td style="text-align:right;">
715.5806
</td>
<td style="text-align:right;">
0.2426389
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
39.41700
</td>
<td style="text-align:right;">
4693836
</td>
<td style="text-align:right;">
368.4693
</td>
<td style="text-align:right;">
0.2422612
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
38.41000
</td>
<td style="text-align:right;">
3628608
</td>
<td style="text-align:right;">
427.9011
</td>
<td style="text-align:right;">
0.2420458
</td>
</tr>
<tr>
<td style="text-align:left;">
Somalia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
32.97800
</td>
<td style="text-align:right;">
2526994
</td>
<td style="text-align:right;">
1135.7498
</td>
<td style="text-align:right;">
0.2412968
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
36.08700
</td>
<td style="text-align:right;">
7212583
</td>
<td style="text-align:right;">
589.9445
</td>
<td style="text-align:right;">
0.2394603
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
32.76700
</td>
<td style="text-align:right;">
2467895
</td>
<td style="text-align:right;">
1116.6399
</td>
<td style="text-align:right;">
0.2391746
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
36.93600
</td>
<td style="text-align:right;">
4690372
</td>
<td style="text-align:right;">
496.1743
</td>
<td style="text-align:right;">
0.2384441
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
34.02000
</td>
<td style="text-align:right;">
11537966
</td>
<td style="text-align:right;">
836.1971
</td>
<td style="text-align:right;">
0.2380873
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
36.16100
</td>
<td style="text-align:right;">
7788944
</td>
<td style="text-align:right;">
556.6864
</td>
<td style="text-align:right;">
0.2377690
</td>
</tr>
<tr>
<td style="text-align:left;">
Nepal
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
36.15700
</td>
<td style="text-align:right;">
9182536
</td>
<td style="text-align:right;">
545.8657
</td>
<td style="text-align:right;">
0.2370045
</td>
</tr>
<tr>
<td style="text-align:left;">
Burundi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
39.03100
</td>
<td style="text-align:right;">
2445618
</td>
<td style="text-align:right;">
339.2965
</td>
<td style="text-align:right;">
0.2365404
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
33.97000
</td>
<td style="text-align:right;">
5498090
</td>
<td style="text-align:right;">
804.8305
</td>
<td style="text-align:right;">
0.2363865
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
37.20700
</td>
<td style="text-align:right;">
3221238
</td>
<td style="text-align:right;">
416.3698
</td>
<td style="text-align:right;">
0.2334078
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
34.90600
</td>
<td style="text-align:right;">
4713416
</td>
<td style="text-align:right;">
617.1835
</td>
<td style="text-align:right;">
0.2332623
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
38.04700
</td>
<td style="text-align:right;">
1542611
</td>
<td style="text-align:right;">
344.1619
</td>
<td style="text-align:right;">
0.2311405
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
34.55800
</td>
<td style="text-align:right;">
2876726
</td>
<td style="text-align:right;">
576.2670
</td>
<td style="text-align:right;">
0.2284713
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
35.30700
</td>
<td style="text-align:right;">
4241884
</td>
<td style="text-align:right;">
490.3822
</td>
<td style="text-align:right;">
0.2274967
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
31.57000
</td>
<td style="text-align:right;">
2295678
</td>
<td style="text-align:right;">
1004.4844
</td>
<td style="text-align:right;">
0.2269618
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
35.98300
</td>
<td style="text-align:right;">
232922
</td>
<td style="text-align:right;">
426.0964
</td>
<td style="text-align:right;">
0.2265936
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
36.66700
</td>
<td style="text-align:right;">
22815614
</td>
<td style="text-align:right;">
378.9042
</td>
<td style="text-align:right;">
0.2264244
</td>
</tr>
<tr>
<td style="text-align:left;">
Yemen, Rep.
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
32.54800
</td>
<td style="text-align:right;">
4963829
</td>
<td style="text-align:right;">
781.7176
</td>
<td style="text-align:right;">
0.2255049
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
33.89600
</td>
<td style="text-align:right;">
374020
</td>
<td style="text-align:right;">
599.6503
</td>
<td style="text-align:right;">
0.2254969
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
31.99700
</td>
<td style="text-align:right;">
10267083
</td>
<td style="text-align:right;">
853.1007
</td>
<td style="text-align:right;">
0.2245954
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
34.48800
</td>
<td style="text-align:right;">
627820
</td>
<td style="text-align:right;">
522.0344
</td>
<td style="text-align:right;">
0.2244632
</td>
</tr>
<tr>
<td style="text-align:left;">
Malawi
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
36.25600
</td>
<td style="text-align:right;">
2917802
</td>
<td style="text-align:right;">
369.1651
</td>
<td style="text-align:right;">
0.2229045
</td>
</tr>
<tr>
<td style="text-align:left;">
Myanmar
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
36.31900
</td>
<td style="text-align:right;">
20092996
</td>
<td style="text-align:right;">
331.0000
</td>
<td style="text-align:right;">
0.2191697
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
33.77900
</td>
<td style="text-align:right;">
7038035
</td>
<td style="text-align:right;">
495.5868
</td>
<td style="text-align:right;">
0.2180222
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
33.60900
</td>
<td style="text-align:right;">
2664249
</td>
<td style="text-align:right;">
510.1965
</td>
<td style="text-align:right;">
0.2179405
</td>
</tr>
<tr>
<td style="text-align:left;">
Eritrea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
35.92800
</td>
<td style="text-align:right;">
1438760
</td>
<td style="text-align:right;">
328.9406
</td>
<td style="text-align:right;">
0.2165770
</td>
</tr>
<tr>
<td style="text-align:left;">
Mali
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
33.68500
</td>
<td style="text-align:right;">
3838168
</td>
<td style="text-align:right;">
452.3370
</td>
<td style="text-align:right;">
0.2142163
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
30.33100
</td>
<td style="text-align:right;">
2143249
</td>
<td style="text-align:right;">
879.7877
</td>
<td style="text-align:right;">
0.2138730
</td>
</tr>
<tr>
<td style="text-align:left;">
Equatorial Guinea
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
34.48200
</td>
<td style="text-align:right;">
216964
</td>
<td style="text-align:right;">
375.6431
</td>
<td style="text-align:right;">
0.2126217
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
30.33200
</td>
<td style="text-align:right;">
9240934
</td>
<td style="text-align:right;">
820.8530
</td>
<td style="text-align:right;">
0.2116927
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
33.48900
</td>
<td style="text-align:right;">
601095
</td>
<td style="text-align:right;">
431.7905
</td>
<td style="text-align:right;">
0.2113506
</td>
</tr>
<tr>
<td style="text-align:left;">
Burkina Faso
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
31.97500
</td>
<td style="text-align:right;">
4469979
</td>
<td style="text-align:right;">
543.2552
</td>
<td style="text-align:right;">
0.2094326
</td>
</tr>
<tr>
<td style="text-align:left;">
Ethiopia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
34.07800
</td>
<td style="text-align:right;">
20860941
</td>
<td style="text-align:right;">
362.1463
</td>
<td style="text-align:right;">
0.2088336
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
32.06500
</td>
<td style="text-align:right;">
323150
</td>
<td style="text-align:right;">
520.9267
</td>
<td style="text-align:right;">
0.2086224
</td>
</tr>
<tr>
<td style="text-align:left;">
Cambodia
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
31.22000
</td>
<td style="text-align:right;">
6978607
</td>
<td style="text-align:right;">
524.9722
</td>
<td style="text-align:right;">
0.2033758
</td>
</tr>
<tr>
<td style="text-align:left;">
Mozambique
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
31.28600
</td>
<td style="text-align:right;">
6446316
</td>
<td style="text-align:right;">
468.5260
</td>
<td style="text-align:right;">
0.2001043
</td>
</tr>
<tr>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Asia
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
28.80100
</td>
<td style="text-align:right;">
8425333
</td>
<td style="text-align:right;">
779.4453
</td>
<td style="text-align:right;">
0.1994571
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
30.00000
</td>
<td style="text-align:right;">
284320
</td>
<td style="text-align:right;">
485.2307
</td>
<td style="text-align:right;">
0.1929722
</td>
</tr>
<tr>
<td style="text-align:left;">
Guinea-Bissau
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
32.50000
</td>
<td style="text-align:right;">
580653
</td>
<td style="text-align:right;">
299.8503
</td>
<td style="text-align:right;">
0.1927829
</td>
</tr>
<tr>
<td style="text-align:left;">
Rwanda
</td>
<td style="text-align:left;">
Africa
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
23.59900
</td>
<td style="text-align:right;">
7290203
</td>
<td style="text-align:right;">
737.0686
</td>
<td style="text-align:right;">
0.1620593
</td>
</tr>
</tbody>
</table>
Let's explore the factors in gapminder\_ideal

``` r
gapminder_ideal %>% 
  str()
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    1680 obs. of  7 variables:
    ##  $ country  : Factor w/ 140 levels "Afghanistan",..: 55 94 112 122 57 66 20 94 121 122 ...
    ##  $ continent: Factor w/ 4 levels "Africa","Americas",..: 3 4 3 4 4 3 2 4 4 4 ...
    ##  $ year     : int  2007 2007 2007 2007 2007 2007 2007 2002 2007 2002 ...
    ##  $ lifeExp  : num  82.2 80.2 80 81.7 81.8 ...
    ##  $ pop      : int  6980412 4627926 4553009 7554661 301931 127467972 33390141 4535591 9031088 7361757 ...
    ##  $ gdpPercap: num  39725 49357 47143 37506 36181 ...
    ##  $ ideal    : num  0.905 0.901 0.895 0.895 0.893 ...

So, the factor list is yet ordered alphabetically.

Let's change that based on our *ideal* metric:

``` r
gapminder_ideal <- gapminder_ideal %>% 
  mutate(country = fct_reorder(country, desc(ideal)))

gapminder_ideal %>% str()
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    1680 obs. of  7 variables:
    ##  $ country  : Factor w/ 140 levels "Switzerland",..: 21 2 26 1 3 9 6 2 7 1 ...
    ##  $ continent: Factor w/ 4 levels "Africa","Americas",..: 3 4 3 4 4 3 2 4 4 4 ...
    ##  $ year     : int  2007 2007 2007 2007 2007 2007 2007 2002 2007 2002 ...
    ##  $ lifeExp  : num  82.2 80.2 80 81.7 81.8 ...
    ##  $ pop      : int  6980412 4627926 4553009 7554661 301931 127467972 33390141 4535591 9031088 7361757 ...
    ##  $ gdpPercap: num  39725 49357 47143 37506 36181 ...
    ##  $ ideal    : num  0.905 0.901 0.895 0.895 0.893 ...

### File I/O

Let's look at Oceania Now:

``` r
gapminder_oceania <- gapminder %>% 
  filter(continent == "Oceania") %>% 
  droplevels()

gapminder_oceania %>% 
  str()
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    24 obs. of  6 variables:
    ##  $ country  : Factor w/ 2 levels "Australia","New Zealand": 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ continent: Factor w/ 1 level "Oceania": 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
    ##  $ lifeExp  : num  69.1 70.3 70.9 71.1 71.9 ...
    ##  $ pop      : int  8691212 9712569 10794968 11872264 13177000 14074100 15184200 16257249 17481977 18565243 ...
    ##  $ gdpPercap: num  10040 10950 12217 14526 16789 ...

Let's reorder it by smallest to highest lifeExp

``` r
gapminder_oceania <- gapminder_oceania %>% 
  mutate(country = fct_reorder(country, lifeExp))

gapminder_oceania %>% 
  str()
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    24 obs. of  6 variables:
    ##  $ country  : Factor w/ 2 levels "New Zealand",..: 2 2 2 2 2 2 2 2 2 2 ...
    ##  $ continent: Factor w/ 1 level "Oceania": 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
    ##  $ lifeExp  : num  69.1 70.3 70.9 71.1 71.9 ...
    ##  $ pop      : int  8691212 9712569 10794968 11872264 13177000 14074100 15184200 16257249 17481977 18565243 ...
    ##  $ gdpPercap: num  10040 10950 12217 14526 16789 ...

Let's write this as a csv

``` r
gapminder_oceania_data <- tempfile()
write_csv(gapminder_oceania, 'oceania_data.csv')
```

Let's read it back and genrate the table

``` r
read_csv('oceania_data.csv') %>% 
  kable() %>% 
  kable_styling()
```

    ## Parsed with column specification:
    ## cols(
    ##   country = col_character(),
    ##   continent = col_character(),
    ##   year = col_integer(),
    ##   lifeExp = col_double(),
    ##   pop = col_integer(),
    ##   gdpPercap = col_double()
    ## )

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
country
</th>
<th style="text-align:left;">
continent
</th>
<th style="text-align:right;">
year
</th>
<th style="text-align:right;">
lifeExp
</th>
<th style="text-align:right;">
pop
</th>
<th style="text-align:right;">
gdpPercap
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
69.120
</td>
<td style="text-align:right;">
8691212
</td>
<td style="text-align:right;">
10039.60
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
70.330
</td>
<td style="text-align:right;">
9712569
</td>
<td style="text-align:right;">
10949.65
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
70.930
</td>
<td style="text-align:right;">
10794968
</td>
<td style="text-align:right;">
12217.23
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.100
</td>
<td style="text-align:right;">
11872264
</td>
<td style="text-align:right;">
14526.12
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.930
</td>
<td style="text-align:right;">
13177000
</td>
<td style="text-align:right;">
16788.63
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
73.490
</td>
<td style="text-align:right;">
14074100
</td>
<td style="text-align:right;">
18334.20
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
74.740
</td>
<td style="text-align:right;">
15184200
</td>
<td style="text-align:right;">
19477.01
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
76.320
</td>
<td style="text-align:right;">
16257249
</td>
<td style="text-align:right;">
21888.89
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
77.560
</td>
<td style="text-align:right;">
17481977
</td>
<td style="text-align:right;">
23424.77
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
78.830
</td>
<td style="text-align:right;">
18565243
</td>
<td style="text-align:right;">
26997.94
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
80.370
</td>
<td style="text-align:right;">
19546792
</td>
<td style="text-align:right;">
30687.75
</td>
</tr>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
81.235
</td>
<td style="text-align:right;">
20434176
</td>
<td style="text-align:right;">
34435.37
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1952
</td>
<td style="text-align:right;">
69.390
</td>
<td style="text-align:right;">
1994794
</td>
<td style="text-align:right;">
10556.58
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1957
</td>
<td style="text-align:right;">
70.260
</td>
<td style="text-align:right;">
2229407
</td>
<td style="text-align:right;">
12247.40
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1962
</td>
<td style="text-align:right;">
71.240
</td>
<td style="text-align:right;">
2488550
</td>
<td style="text-align:right;">
13175.68
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1967
</td>
<td style="text-align:right;">
71.520
</td>
<td style="text-align:right;">
2728150
</td>
<td style="text-align:right;">
14463.92
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1972
</td>
<td style="text-align:right;">
71.890
</td>
<td style="text-align:right;">
2929100
</td>
<td style="text-align:right;">
16046.04
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1977
</td>
<td style="text-align:right;">
72.220
</td>
<td style="text-align:right;">
3164900
</td>
<td style="text-align:right;">
16233.72
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1982
</td>
<td style="text-align:right;">
73.840
</td>
<td style="text-align:right;">
3210650
</td>
<td style="text-align:right;">
17632.41
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1987
</td>
<td style="text-align:right;">
74.320
</td>
<td style="text-align:right;">
3317166
</td>
<td style="text-align:right;">
19007.19
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1992
</td>
<td style="text-align:right;">
76.330
</td>
<td style="text-align:right;">
3437674
</td>
<td style="text-align:right;">
18363.32
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
1997
</td>
<td style="text-align:right;">
77.550
</td>
<td style="text-align:right;">
3676187
</td>
<td style="text-align:right;">
21050.41
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2002
</td>
<td style="text-align:right;">
79.110
</td>
<td style="text-align:right;">
3908037
</td>
<td style="text-align:right;">
23189.80
</td>
</tr>
<tr>
<td style="text-align:left;">
New Zealand
</td>
<td style="text-align:left;">
Oceania
</td>
<td style="text-align:right;">
2007
</td>
<td style="text-align:right;">
80.204
</td>
<td style="text-align:right;">
4115771
</td>
<td style="text-align:right;">
25185.01
</td>
</tr>
</tbody>
</table>
### Visualization design

Let's look at the ideal scale for the continents in gapminder\_ideal for the year 2007:

``` r
gapminder_ideal %>% 
  filter(year == 2007) %>% 
  ggplot(aes(x = continent, y = ideal)) +
  geom_violin()
```

![](hw05-MaunishUBC_files/figure-markdown_github/unnamed-chunk-15-1.png)

Let's get each country on here and colour it based on it's population

``` r
ideal_plot <- gapminder_ideal %>% 
  filter(year == 2007) %>% 
  ggplot(aes(x = continent, y = ideal)) +
  geom_violin(aes(fill = continent)) + 
  geom_point(aes(colour=pop)) +
  scale_colour_continuous(trans="log10") +
  labs(title = "Ideal metric for each of the continents") + 
   theme_bw() +
    theme(axis.text = element_text(size = 16),
          strip.background = element_rect(fill = "orange"),
          panel.background = element_rect(fill = "pink"))

ideal_plot
```

![](hw05-MaunishUBC_files/figure-markdown_github/unnamed-chunk-16-1.png)

Let's make this a plotly object.

``` r
ideal_plot %>% 
    ggplotly()
```

<!--html_preserve-->

<!--/html_preserve-->
We can hover over each of the data points

### Save the figure

``` r
ggsave("gapminder_ideal_plot.png", plot = ideal_plot, width = 5 , height = 4 , scale = 1)
```

This image was stored on my computer:

![Maunish's final plot](gapminder_ideal_plot.png)
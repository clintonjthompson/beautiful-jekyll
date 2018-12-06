---
layout: post
title: Filtered Table with Pipes
subtitle: Placing a table at the end of a dplyr chain
tags: [pipes, table, filter]
---

This

You can write regular [markdown](http://markdowntutorial.com/) here and Jekyll will automatically convert it to a nice webpage.  I strongly encourage you to [take 5 minutes to learn how to write in markdown](http://markdowntutorial.com/) - it'll teach you how to transform regular text into bold/italics/headings/tables/etc.

**Here is some bold text**

And this is some code:

```r
as_tibble(mtcars)
```

`
## # A tibble: 32 x 11
##      mpg   cyl  disp    hp  drat    wt  qsec    vs    am  gear  carb
##  * <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
##  1  21       6  160    110  3.9   2.62  16.5     0     1     4     4
##  2  21       6  160    110  3.9   2.88  17.0     0     1     4     4
##  3  22.8     4  108     93  3.85  2.32  18.6     1     1     4     1
##  4  21.4     6  258    110  3.08  3.22  19.4     1     0     3     1
##  5  18.7     8  360    175  3.15  3.44  17.0     0     0     3     2
##  6  18.1     6  225    105  2.76  3.46  20.2     1     0     3     1
##  7  14.3     8  360    245  3.21  3.57  15.8     0     0     3     4
##  8  24.4     4  147.    62  3.69  3.19  20       1     0     4     2
##  9  22.8     4  141.    95  3.92  3.15  22.9     1     0     4     2
## 10  19.2     6  168.   123  3.92  3.44  18.3     1     0     4     4
## # ... with 22 more rows
`

```r
mtcars %>%
  filter(am==1) %>%
  {table("Number Cylinders" = .$cyl, "Engine Type" = .$vs)}
```

`
##                 Engine Type
## Number Cylinders 0 1
##                4 1 7
##                6 3 0
##                8 2 0
`

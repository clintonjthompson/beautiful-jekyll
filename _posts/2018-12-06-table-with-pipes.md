---
layout: post
title: Filtered Table with Pipes
subtitle: Placing a table at the end of a dplyr chain
tags: [pipes, table, filter]
---

There is no questioning the power and versatility of `tidyverse`.  One thing I couldn't figure out, though, was how to use the piping capability (`%>%`) with the `table` or `CrossTable` commands.  After much sleuthing and searching around on the interwebs, I learned that the `table` command needs to be surrounded by curly brackets and the variable name preceded by `.$`.  

Here is some example code:

```R
as_tibble(mtcars)
```

```RMarkdown
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
```

```R
mtcars %>%
  filter(am==1) %>%
  {table("Number Cylinders" = .$cyl, "Engine Type" = .$vs)}
```

```RMarkdown
##                 Engine Type
## Number Cylinders 0 1
##                4 1 7
##                6 3 0
##                8 2 0
```

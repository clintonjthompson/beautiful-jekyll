---
layout: post
title: Stack One-Way Frequencies
subtitle: Function to extract frequencies for several variables
tags: [R, function, frequencies]
---

I recently sought to embed a table in a graph with the frequency of occurence of certain characteristics.  In order to do this I needed to extract said frequencies, stack them (`rbind`), then designate as a `data.frame`.  Using the `mtcars` data as example, this is how I did it.  

```R
head(mtcars)
```

```RMarkdown
##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```

```R
get_1wayfreqs <- function(varname) {
  df <- as.data.frame(table(mtcars[[varname]]))
  df <- df %>% 
    filter(Var1=="1")
  df$Var1 <- varname
  return(df)
}
```

```R
as.data.frame(table(mtcars$vs))
```

```RMarkdown
##   Var1 Freq
## 1    0   18
## 2    1   14
```

```R
as.data.frame(table(mtcars$am))
```

```RMarkdown
##   Var1 Freq
## 1    0   19
## 2    1   13
```

```R
vs <- get_1wayfreqs("vs")
am <- get_1wayfreqs("am")
```

```R
vs
```

```RMarkdown
##   Var1 Freq
## 1   vs   14
```

```R
am
```

```RMarkdown
##   Var1 Freq
## 1   am   13
```

```R
rbind(vs, am)
```

```RMarkdown
##   Var1 Freq
## 1   vs   14
## 2   am   13
```

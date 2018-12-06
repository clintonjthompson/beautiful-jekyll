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

mtcars %>%
  filter(am==1) %>%
  {table("Number Cylinders" = .$cyl, "Engine Type" = .$vs)}
```

```
                Engine Type
Number Cylinders 0 1
               4 1 7
               6 3 0
               8 2 0
```

# Some ggplot2 things

### Make theme_bw() the default
```R
# In a session:
new_theme <- theme_bw()
theme_set(new_theme)

# Permanently by adding to .Rprofile
setHook(packageEvent("ggplot2", "onLoad"), 
        function(...) ggplot2::theme_set(ggplot2::theme_bw()))
```

### Grid lines
```R
# Remove grid lines
ggplot(df, aes(x=x, y=y)) +
    theme(panel.grid.major = element_blank(),     # all major
          panel.grid.minor = element_blank(),     # all minor
          panel.grid.major.x = element_blank(),   # x major
          panel.grid.major.y = element_blank())   # y major
```

### Add space between facet panels
```R
ggplot(df, aes(x=x, y=y)) +
    theme(panel.spacing.x = unit(4,"mm"))
```

### Change facet labels
```R
facet_labels <- c(`afactorlevel` = "Readable version", `anotherfactorlevel` = "Another readable version")
ggplot(df, aes(x=x, y=y)) +
    facet_wrap(~somefactor, labeller = as_labeller(facet_labels))
```

### Rotate axis labels:
```R
ggplot(df, aes(x=x, y=y)) +
    theme(axis.text.x = element_text(angle = 90, hjust = 1))
```

### joining
e.g. inner_join()
inner:  only rows with matching keys in both x and y
left:   all rows in x, adding matching columns from y
right:  all rows in y, adding matching columns from x
full:   all rows in x with matching columns in y, then the rows of y that don't match x.

### Point shapes
![](http://sape.inf.usi.ch/sites/default/files/ggplot2-shape-identity.png)

### Using cowplot
[cowplot documentation](https://cran.r-project.org/web/packages/cowplot/vignettes/introduction.html) 

```R
library(cowplot)

fig <- plot_grid(p1, p2, labels="auto", ncol=2, rel_widths=c(0.5, 1))

```

# HOW TO PERFORM CLUSTERING AND CREATE HEATMAPS IN R
## Clustering in R
The iris dataset which is loaded by default in R package will be used for this tutorial
```R
iris <- datasets::iris
iris2 <- iris[,-5] #Loading the values of the characteristics of the dataset
View(iris2) #To view them 
species_labels <- iris[,5]
library(colorspace) # get nice colors
species_col <- rev(rainbow_hcl(3))[as.numeric(species_labels)]
```

Plot a Scatter Plot Matrix which gives the combination of the column values
```R
pairs(iris2, col = species_col,
      lower.panel = NULL,
      cex.labels=2, pch=19, cex = 1.2)#Add a legend
```
![clustering in R](https://github.com/davidenoma/thanos-hackbio/blob/main/clustering.jpeg)

```R
par(xpd = TRUE)
legend(x = 0.05, y = 0.4, cex = 2,
   legend = as.character(levels(species_labels)),
    fill = unique(species_col))
par(xpd = NA)
```
## Heatmaps in R 
```R
heatmap(as.matrix(iris2), scale="none")
```
![Heatmap in R](https://github.com/davidenoma/thanos-hackbio/blob/main/heatmap.jpeg)

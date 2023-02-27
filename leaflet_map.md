---
always_allow_html: yes
output: github_document
---

# Top 10 Best colleges for Data Science in California, US  
Developing Data Products Week2 Assignment  

Doris Chen  
2023-02-23  
  
  
**Data Source: [EduRank](https://edurank.org/cs/data-science/california/)**  
  

### Load packages and data


```r
library(dplyr)
library(leaflet)
edu <- read.csv("eduRank.csv")
```
  
### Edit icon color  
  

```r
Icons <- makeAwesomeIcon(iconColor = 'transparent')
webshot::install_phantomjs(force=TRUE)
```

```
## phantomjs has been installed to /Users/Doris/Library/Application Support/PhantomJS
```
  
### Create the map  
  

```r
edu %>% 
        leaflet() %>% 
        addTiles() %>% 
        addAwesomeMarkers(lat=edu$lat, lng=edu$lng, label=edu$num, 
                         labelOptions = labelOptions(permanent=TRUE, textOnly=TRUE, textsize = "15px", style=list(color="white"), direction="top"), 
                         icon=Icons,
                         popup=paste('<strong>', edu[,1],  '</strong>', edu[,2], edu[,3], edu[,4], sep = "<br/>"))
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png)
 

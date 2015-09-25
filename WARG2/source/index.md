---
title       : Interactive Data Visualisations with R
subtitle    : 2nd WARG event, Perth, Australia
author      : Andrey Kostenko, June 25, 2015
framework   : io2012       # {io2012, html5slides, shower, dzslides, deck.js,landslide, Slidy ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [bootstrap, quiz]            # {mathjax, quiz, bootstrap}
ext_widgets : {rCharts: ["libraries/highcharts", libraries/nvd3"]}
mode        : selfcontained # {selfcontained, standalone, draft}
knit        : slidify::knit2slides
license     : by-nc-sa
logo        : logo.png
github      :
  user      : andrekos
  repo      : WARG2
  html_document: 
    highlight: pygments
---






# Agenda 

* <h2>Intro</h2>

* <h2>Package htmlwidgets</h2>

* <h2>Package rCharts</h2>

* <h2>Package googleVis</h2>

* <h2>Package plotly</h2>

* <h2>Coda</h2>

---
### **R**

<div class="alert alert-info">
<h3>R is a programming language and software environment for statistical computing and graphics. R and its libraries implement a variety of statistical and graphical techniques. Dynamic and interactive graphics are available through R packages. </h3> 
</div>

### **Data Visualisation**

<div class="alert alert-info">
<h3>Data visualization is the presentation of data in a pictorial or graphical format to understand information more easily and quickly.</h3> 
</div>

### **Interactive**

<div class="alert alert-info">
<h3>Interactive charts. What does that mean?</h3> 
</div>



---
## INTERACTIVE: <a href="#" rel="tooltip" data-original-title="Hi, I'm a Tooltip. I live in the title.">tooltipable</a>, clickable, transformable

<iframe src=' assets/fig/unnamed-chunk-1-1.html ' scrolling='no' frameBorder='0' seamless class='rChart nvd3 ' id=iframe- chartb5c7af7653b ></iframe> <style>iframe.rChart{ width: 100%; height: 400px;}</style>

---
## INTERACTIVE: pan-zoomable aka zoom-panable

<iframe src="d2.html"> </iframe>

---
## INTERACTIVE: info-legends and series highlighting

<iframe src="d3.html"> </iframe>

--- #MR
## JavaScript libraries make it possible   
<script>
$('#MR').on('slideenter', function(){
  $(this).find('article')
    .append('<iframe src="http://bl.ocks.org/mbostock/raw/3231298/"></iframe>')
    
});
$('#MR').on('slideleave', function(){
  $(this).find('iframe').remove();
});
</script>


--- #D3 
## D3.js - Data-Driven Documents 
<script>
$('#D3').on('slideenter', function(){
  $(this).find('article')
    .append('<iframe src="http://bl.ocks.org/mbostock/raw/1256572/"></iframe>')
    
});
$('#D3').on('slideleave', function(){
  $(this).find('iframe').remove();
});
</script>


---
## Some of the key technologies

<div class="alert alert-danger alert-dismissible">
<button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
<h3>0. Standalone R wrappers for JS libraries</h3></div>

<div class="alert alert-success">
<h3>1. htmlwidgets framework to bridge R and JS </h3></div>

<div class="alert alert-info">
<h3>2. rCharts makes use of many JS libraries</h3></div>

<div class="alert alert-warning">
<h3>3. Google Chart API</h3></div>

<div class="alert alert-danger">
<h3>4. Plotly API </h3></div>


---
## <div class="alert alert-success">Technology 1: Htmlwidgets </div>

**htmlwidgets** is one of the latest interactive data visualisation 
technologies, developed specifically for R users and developers. It 
aims to make it easy to:

- produce a D3 graphic or Leaflet map with a few lines of R code

- use JS visualization libraries at the R console, just like plots

- embed widgets in R Markdown docs and Shiny web apps

- develop new widgets using a framework that bridges R and JS

There are already several R packages based on the htmlwidgets framework.


--- &twocol w1:40% w2:60%
## R packages based on htmlwidgets 

*** =left

> - **dygraphs** for time series plots
> - **leaflet** for geo-spatial mapping
> - **MetricsGraphics** - D3 scatterplots, line charts, and histograms
> - **networkD3** - D3 network graphs 
> - **d3heatmap** - interactive heatmaps with D3
> - **DT** - HTML tables with filtering, pagination, sorting
> - **threejs** - 3D scatterplot and 3D globe
> - **DiagrammeR** - diagrams & flowcharts using Graphviz & Mermaid
> - **sparkline** - small inline charts

More examples: http://www.htmlwidgets.org/

*** =right

<iframe src="d4.html"> </iframe>

---
## A dygraph tool in action

<iframe src="d1.html" > </iframe>

---
## R code for the previous plot

```r
fcast1 <- predict(HoltWinters(ldeaths), n.ahead = 36)
fcast2 <- predict(HoltWinters(ldeaths,alpha=0.1), n.ahead = 36)
fcast3 <- predict(HoltWinters(ldeaths,alpha=0.9), n.ahead = 36)
fcast4 <- predict(HoltWinters(ldeaths,alpha=0.1,beta=0.1), n.ahead = 36)
fcast5 <- predict(HoltWinters(ldeaths,gamma=FALSE), n.ahead = 36)
fcast6 <- forecast::forecast(forecast::auto.arima(ldeaths), h = 36)$mean
ts <- cbind(ldeaths,fcast1,fcast2,fcast3,fcast4,fcast5,fcast6)

dygraph(ts, "Deaths from Lung Disease (UK)") %>%
  dySeries("ldeaths", label = "Deaths") %>%
  dyLegend(show = "onmouseover")
```


---
## A threejs tool in action (load vs temp vs rhum)

<iframe src="d5.html" > </iframe>


---
## R code for the previous plot



```r
HUM<-round(M$HMAX,2);TEMP<-round(M$MAX,2);LOAD<-round(M$Load,2)

pal <- leaflet::colorQuantile("YlOrRd", NULL, n = 9)

scatterplot3js(x=HUM,y=TEMP,z=LOAD, color=pal(TEMP),
               labels=sprintf("HUM=%.2f, TEMP=%.2f, LOAD=%.2f, DATE=%s",
                              HUM,TEMP,LOAD,M$Date), renderer="canvas",
               size = LOAD/30,num.ticks = c(6, 6, 6),
               x.ticklabs=paste(seq(min(HUM),max(HUM),length.out=6),"%"),
                y.ticklabs=paste(seq(max(TEMP),min(TEMP),length.out=6),"C"),
                z.ticklabs=paste(seq(min(LOAD),max(LOAD),length.out=6),"MW"),
               signif = 6,bg="#fffaf0")
```


---
## A leaflet tool in action (numer of R users by suburb)

<iframe src="d6.html" > </iframe>


---
## R code for the previous plot


```r
tmp <- tempdir();file <- "walocalitypolygon.zip";unzip(file, exdir = tmp)
wa <- readOGR(dsn = tmp, layer = "WA Locality Polygon", encoding = "UTF-8")
wa@data$num<-sample.int(100L,nrow(wa@data), TRUE)

pal <- colorQuantile("YlGn", NULL, n = 10)
state_popup <- paste0("<strong>LOC_PID: </strong>", wa$LOC_PID, 
        "<br><strong>Suburb/Locality: </strong>", wa$WA_LOCAL_2,
        "<br><strong>Numer of R uses :) </strong>", wa$num)

mb_tiles <- "http://a.tiles.mapbox.com/v3/kwalkertcu.l1fc0hab/{z}/{x}/{y}.png"
mb_attribution <- 'Mapbox <a href="http://mapbox.com/about/maps" 
target="_blank">Terms &amp; Feedback</a>'

leaflet(data =wa) %>% addTiles(urlTemplate = mb_tiles,  
  attribution = mb_attribution) %>% addPolygons(fillColor = ~pal(num), 
  fillOpacity = 0.8, color = "#BDBDC3", weight = 1, popup = state_popup)
```


---
## <div class="alert alert-info">Technology 2: rCharts </div> 

**rCharts** is an R package to create, customize and publish interactive 
JavaScript visualizations from R, using a familiar lattice style plotting 
interface. It aims to

- make the process of creating, customizing and sharing interactive visualizations easy
- access the power of many different JavaScript libraries, each with its own strengths
- make sensible conventions like using hPlot() function for the Highcharts library, 
mPlot() function for the Morris.js etc.
- be easily embeddable into Shiny apps, rmarkdown docs, HTML5 slides etc.


**rCharts** builds on earlier projects like  rHighcharts, rVega,  rNVD3 and 
incorporates many other names that a good web developer would  be familiar with.

--- &twocol w1:50% w2:50%
## JavaScript libraries behind R package rCharts  

*** =left

> - **jquery.dataTables.js** - Table plug-in for jQuery JavaScript library
> - **d3.js** - JavaScript library for Data-Driven Documents
> - **dimple.js** - a simple charting API for d3 data visualisations
> - **highcharts.js** - easy interactive charts for web projects
> - **leaflet.js** - for mobile-friendly interactive maps
> - **morris.js** - pretty time-series line graphs
> - **raphael.js** - simplifies work with vector graphics on the web

More details and examples: http://rcharts.io/

*** =right

> - **nv.d3.js** - re-usable charts for d3.js
> - **polychart.js** - combines data, layers, guides and interactions to create charts 
> - **rickshaw.js** - JavaScript toolkit for creating interactive real-time graphs
> - **timeline.js** - Beautifully crafted timelines that are easy and intuitive to use.
> - **uvcharts.js** - charting library based on d3.js
> - **vega.js** - interactive views using either HTML5 Canvas or SVG.
> - **xcharts.js** - xCharts is a D3-based library for building custom charts and graphs.


---
## An nvd3 tool in action 

<link rel='stylesheet' href=C:/Users/Andrey/Documents/R/win-library/3.2/rCharts/libraries/nvd3/css/nv.d3.css>
<link rel='stylesheet' href=C:/Users/Andrey/Documents/R/win-library/3.2/rCharts/libraries/nvd3/css/rNVD3.css>
<script type='text/javascript' src=C:/Users/Andrey/Documents/R/win-library/3.2/rCharts/libraries/nvd3/js/jquery-1.8.2.min.js></script>
<script type='text/javascript' src=C:/Users/Andrey/Documents/R/win-library/3.2/rCharts/libraries/nvd3/js/d3.v3.min.js></script>
<script type='text/javascript' src=C:/Users/Andrey/Documents/R/win-library/3.2/rCharts/libraries/nvd3/js/nv.d3.min-new.js></script>
<script type='text/javascript' src=C:/Users/Andrey/Documents/R/win-library/3.2/rCharts/libraries/nvd3/js/fisheye.js></script> 
 <style>
  .rChart {
    display: block;
    margin-left: auto; 
    margin-right: auto;
    width: 800px;
    height: 400px;
  }  
  </style>
<div id = 'chartb5c8f56d8c' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchartb5c8f56d8c()
    });
    function drawchartb5c8f56d8c(){  
      var opts = {
 "dom": "chartb5c8f56d8c",
"width":    800,
"height":    400,
"x": "Sepal.Width",
"y": "Sepal.Length",
"group": "Species",
"type": "scatterChart",
"id": "chartb5c8f56d8c" 
},
        data = [
 {
 "Sepal.Length":            5.1,
"Sepal.Width":            3.5,
"Petal.Length":            1.4,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.9,
"Sepal.Width":              3,
"Petal.Length":            1.4,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.7,
"Sepal.Width":            3.2,
"Petal.Length":            1.3,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.6,
"Sepal.Width":            3.1,
"Petal.Length":            1.5,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":              5,
"Sepal.Width":            3.6,
"Petal.Length":            1.4,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.4,
"Sepal.Width":            3.9,
"Petal.Length":            1.7,
"Petal.Width":            0.4,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.6,
"Sepal.Width":            3.4,
"Petal.Length":            1.4,
"Petal.Width":            0.3,
"Species": "setosa" 
},
{
 "Sepal.Length":              5,
"Sepal.Width":            3.4,
"Petal.Length":            1.5,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.4,
"Sepal.Width":            2.9,
"Petal.Length":            1.4,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.9,
"Sepal.Width":            3.1,
"Petal.Length":            1.5,
"Petal.Width":            0.1,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.4,
"Sepal.Width":            3.7,
"Petal.Length":            1.5,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.8,
"Sepal.Width":            3.4,
"Petal.Length":            1.6,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.8,
"Sepal.Width":              3,
"Petal.Length":            1.4,
"Petal.Width":            0.1,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.3,
"Sepal.Width":              3,
"Petal.Length":            1.1,
"Petal.Width":            0.1,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.8,
"Sepal.Width":              4,
"Petal.Length":            1.2,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.7,
"Sepal.Width":            4.4,
"Petal.Length":            1.5,
"Petal.Width":            0.4,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.4,
"Sepal.Width":            3.9,
"Petal.Length":            1.3,
"Petal.Width":            0.4,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.1,
"Sepal.Width":            3.5,
"Petal.Length":            1.4,
"Petal.Width":            0.3,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.7,
"Sepal.Width":            3.8,
"Petal.Length":            1.7,
"Petal.Width":            0.3,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.1,
"Sepal.Width":            3.8,
"Petal.Length":            1.5,
"Petal.Width":            0.3,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.4,
"Sepal.Width":            3.4,
"Petal.Length":            1.7,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.1,
"Sepal.Width":            3.7,
"Petal.Length":            1.5,
"Petal.Width":            0.4,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.6,
"Sepal.Width":            3.6,
"Petal.Length":              1,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.1,
"Sepal.Width":            3.3,
"Petal.Length":            1.7,
"Petal.Width":            0.5,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.8,
"Sepal.Width":            3.4,
"Petal.Length":            1.9,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":              5,
"Sepal.Width":              3,
"Petal.Length":            1.6,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":              5,
"Sepal.Width":            3.4,
"Petal.Length":            1.6,
"Petal.Width":            0.4,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.2,
"Sepal.Width":            3.5,
"Petal.Length":            1.5,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.2,
"Sepal.Width":            3.4,
"Petal.Length":            1.4,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.7,
"Sepal.Width":            3.2,
"Petal.Length":            1.6,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.8,
"Sepal.Width":            3.1,
"Petal.Length":            1.6,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.4,
"Sepal.Width":            3.4,
"Petal.Length":            1.5,
"Petal.Width":            0.4,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.2,
"Sepal.Width":            4.1,
"Petal.Length":            1.5,
"Petal.Width":            0.1,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.5,
"Sepal.Width":            4.2,
"Petal.Length":            1.4,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.9,
"Sepal.Width":            3.1,
"Petal.Length":            1.5,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":              5,
"Sepal.Width":            3.2,
"Petal.Length":            1.2,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.5,
"Sepal.Width":            3.5,
"Petal.Length":            1.3,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.9,
"Sepal.Width":            3.6,
"Petal.Length":            1.4,
"Petal.Width":            0.1,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.4,
"Sepal.Width":              3,
"Petal.Length":            1.3,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.1,
"Sepal.Width":            3.4,
"Petal.Length":            1.5,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":              5,
"Sepal.Width":            3.5,
"Petal.Length":            1.3,
"Petal.Width":            0.3,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.5,
"Sepal.Width":            2.3,
"Petal.Length":            1.3,
"Petal.Width":            0.3,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.4,
"Sepal.Width":            3.2,
"Petal.Length":            1.3,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":              5,
"Sepal.Width":            3.5,
"Petal.Length":            1.6,
"Petal.Width":            0.6,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.1,
"Sepal.Width":            3.8,
"Petal.Length":            1.9,
"Petal.Width":            0.4,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.8,
"Sepal.Width":              3,
"Petal.Length":            1.4,
"Petal.Width":            0.3,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.1,
"Sepal.Width":            3.8,
"Petal.Length":            1.6,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            4.6,
"Sepal.Width":            3.2,
"Petal.Length":            1.4,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":            5.3,
"Sepal.Width":            3.7,
"Petal.Length":            1.5,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":              5,
"Sepal.Width":            3.3,
"Petal.Length":            1.4,
"Petal.Width":            0.2,
"Species": "setosa" 
},
{
 "Sepal.Length":              7,
"Sepal.Width":            3.2,
"Petal.Length":            4.7,
"Petal.Width":            1.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.4,
"Sepal.Width":            3.2,
"Petal.Length":            4.5,
"Petal.Width":            1.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.9,
"Sepal.Width":            3.1,
"Petal.Length":            4.9,
"Petal.Width":            1.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.5,
"Sepal.Width":            2.3,
"Petal.Length":              4,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.5,
"Sepal.Width":            2.8,
"Petal.Length":            4.6,
"Petal.Width":            1.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.7,
"Sepal.Width":            2.8,
"Petal.Length":            4.5,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.3,
"Sepal.Width":            3.3,
"Petal.Length":            4.7,
"Petal.Width":            1.6,
"Species": "versicolor" 
},
{
 "Sepal.Length":            4.9,
"Sepal.Width":            2.4,
"Petal.Length":            3.3,
"Petal.Width":              1,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.6,
"Sepal.Width":            2.9,
"Petal.Length":            4.6,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.2,
"Sepal.Width":            2.7,
"Petal.Length":            3.9,
"Petal.Width":            1.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":              5,
"Sepal.Width":              2,
"Petal.Length":            3.5,
"Petal.Width":              1,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.9,
"Sepal.Width":              3,
"Petal.Length":            4.2,
"Petal.Width":            1.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":              6,
"Sepal.Width":            2.2,
"Petal.Length":              4,
"Petal.Width":              1,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.1,
"Sepal.Width":            2.9,
"Petal.Length":            4.7,
"Petal.Width":            1.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.6,
"Sepal.Width":            2.9,
"Petal.Length":            3.6,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.7,
"Sepal.Width":            3.1,
"Petal.Length":            4.4,
"Petal.Width":            1.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.6,
"Sepal.Width":              3,
"Petal.Length":            4.5,
"Petal.Width":            1.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.8,
"Sepal.Width":            2.7,
"Petal.Length":            4.1,
"Petal.Width":              1,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.2,
"Sepal.Width":            2.2,
"Petal.Length":            4.5,
"Petal.Width":            1.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.6,
"Sepal.Width":            2.5,
"Petal.Length":            3.9,
"Petal.Width":            1.1,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.9,
"Sepal.Width":            3.2,
"Petal.Length":            4.8,
"Petal.Width":            1.8,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.1,
"Sepal.Width":            2.8,
"Petal.Length":              4,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.3,
"Sepal.Width":            2.5,
"Petal.Length":            4.9,
"Petal.Width":            1.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.1,
"Sepal.Width":            2.8,
"Petal.Length":            4.7,
"Petal.Width":            1.2,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.4,
"Sepal.Width":            2.9,
"Petal.Length":            4.3,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.6,
"Sepal.Width":              3,
"Petal.Length":            4.4,
"Petal.Width":            1.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.8,
"Sepal.Width":            2.8,
"Petal.Length":            4.8,
"Petal.Width":            1.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.7,
"Sepal.Width":              3,
"Petal.Length":              5,
"Petal.Width":            1.7,
"Species": "versicolor" 
},
{
 "Sepal.Length":              6,
"Sepal.Width":            2.9,
"Petal.Length":            4.5,
"Petal.Width":            1.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.7,
"Sepal.Width":            2.6,
"Petal.Length":            3.5,
"Petal.Width":              1,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.5,
"Sepal.Width":            2.4,
"Petal.Length":            3.8,
"Petal.Width":            1.1,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.5,
"Sepal.Width":            2.4,
"Petal.Length":            3.7,
"Petal.Width":              1,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.8,
"Sepal.Width":            2.7,
"Petal.Length":            3.9,
"Petal.Width":            1.2,
"Species": "versicolor" 
},
{
 "Sepal.Length":              6,
"Sepal.Width":            2.7,
"Petal.Length":            5.1,
"Petal.Width":            1.6,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.4,
"Sepal.Width":              3,
"Petal.Length":            4.5,
"Petal.Width":            1.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":              6,
"Sepal.Width":            3.4,
"Petal.Length":            4.5,
"Petal.Width":            1.6,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.7,
"Sepal.Width":            3.1,
"Petal.Length":            4.7,
"Petal.Width":            1.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.3,
"Sepal.Width":            2.3,
"Petal.Length":            4.4,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.6,
"Sepal.Width":              3,
"Petal.Length":            4.1,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.5,
"Sepal.Width":            2.5,
"Petal.Length":              4,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.5,
"Sepal.Width":            2.6,
"Petal.Length":            4.4,
"Petal.Width":            1.2,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.1,
"Sepal.Width":              3,
"Petal.Length":            4.6,
"Petal.Width":            1.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.8,
"Sepal.Width":            2.6,
"Petal.Length":              4,
"Petal.Width":            1.2,
"Species": "versicolor" 
},
{
 "Sepal.Length":              5,
"Sepal.Width":            2.3,
"Petal.Length":            3.3,
"Petal.Width":              1,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.6,
"Sepal.Width":            2.7,
"Petal.Length":            4.2,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.7,
"Sepal.Width":              3,
"Petal.Length":            4.2,
"Petal.Width":            1.2,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.7,
"Sepal.Width":            2.9,
"Petal.Length":            4.2,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.2,
"Sepal.Width":            2.9,
"Petal.Length":            4.3,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.1,
"Sepal.Width":            2.5,
"Petal.Length":              3,
"Petal.Width":            1.1,
"Species": "versicolor" 
},
{
 "Sepal.Length":            5.7,
"Sepal.Width":            2.8,
"Petal.Length":            4.1,
"Petal.Width":            1.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":            6.3,
"Sepal.Width":            3.3,
"Petal.Length":              6,
"Petal.Width":            2.5,
"Species": "virginica" 
},
{
 "Sepal.Length":            5.8,
"Sepal.Width":            2.7,
"Petal.Length":            5.1,
"Petal.Width":            1.9,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.1,
"Sepal.Width":              3,
"Petal.Length":            5.9,
"Petal.Width":            2.1,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.3,
"Sepal.Width":            2.9,
"Petal.Length":            5.6,
"Petal.Width":            1.8,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.5,
"Sepal.Width":              3,
"Petal.Length":            5.8,
"Petal.Width":            2.2,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.6,
"Sepal.Width":              3,
"Petal.Length":            6.6,
"Petal.Width":            2.1,
"Species": "virginica" 
},
{
 "Sepal.Length":            4.9,
"Sepal.Width":            2.5,
"Petal.Length":            4.5,
"Petal.Width":            1.7,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.3,
"Sepal.Width":            2.9,
"Petal.Length":            6.3,
"Petal.Width":            1.8,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.7,
"Sepal.Width":            2.5,
"Petal.Length":            5.8,
"Petal.Width":            1.8,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.2,
"Sepal.Width":            3.6,
"Petal.Length":            6.1,
"Petal.Width":            2.5,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.5,
"Sepal.Width":            3.2,
"Petal.Length":            5.1,
"Petal.Width":              2,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.4,
"Sepal.Width":            2.7,
"Petal.Length":            5.3,
"Petal.Width":            1.9,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.8,
"Sepal.Width":              3,
"Petal.Length":            5.5,
"Petal.Width":            2.1,
"Species": "virginica" 
},
{
 "Sepal.Length":            5.7,
"Sepal.Width":            2.5,
"Petal.Length":              5,
"Petal.Width":              2,
"Species": "virginica" 
},
{
 "Sepal.Length":            5.8,
"Sepal.Width":            2.8,
"Petal.Length":            5.1,
"Petal.Width":            2.4,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.4,
"Sepal.Width":            3.2,
"Petal.Length":            5.3,
"Petal.Width":            2.3,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.5,
"Sepal.Width":              3,
"Petal.Length":            5.5,
"Petal.Width":            1.8,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.7,
"Sepal.Width":            3.8,
"Petal.Length":            6.7,
"Petal.Width":            2.2,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.7,
"Sepal.Width":            2.6,
"Petal.Length":            6.9,
"Petal.Width":            2.3,
"Species": "virginica" 
},
{
 "Sepal.Length":              6,
"Sepal.Width":            2.2,
"Petal.Length":              5,
"Petal.Width":            1.5,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.9,
"Sepal.Width":            3.2,
"Petal.Length":            5.7,
"Petal.Width":            2.3,
"Species": "virginica" 
},
{
 "Sepal.Length":            5.6,
"Sepal.Width":            2.8,
"Petal.Length":            4.9,
"Petal.Width":              2,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.7,
"Sepal.Width":            2.8,
"Petal.Length":            6.7,
"Petal.Width":              2,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.3,
"Sepal.Width":            2.7,
"Petal.Length":            4.9,
"Petal.Width":            1.8,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.7,
"Sepal.Width":            3.3,
"Petal.Length":            5.7,
"Petal.Width":            2.1,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.2,
"Sepal.Width":            3.2,
"Petal.Length":              6,
"Petal.Width":            1.8,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.2,
"Sepal.Width":            2.8,
"Petal.Length":            4.8,
"Petal.Width":            1.8,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.1,
"Sepal.Width":              3,
"Petal.Length":            4.9,
"Petal.Width":            1.8,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.4,
"Sepal.Width":            2.8,
"Petal.Length":            5.6,
"Petal.Width":            2.1,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.2,
"Sepal.Width":              3,
"Petal.Length":            5.8,
"Petal.Width":            1.6,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.4,
"Sepal.Width":            2.8,
"Petal.Length":            6.1,
"Petal.Width":            1.9,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.9,
"Sepal.Width":            3.8,
"Petal.Length":            6.4,
"Petal.Width":              2,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.4,
"Sepal.Width":            2.8,
"Petal.Length":            5.6,
"Petal.Width":            2.2,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.3,
"Sepal.Width":            2.8,
"Petal.Length":            5.1,
"Petal.Width":            1.5,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.1,
"Sepal.Width":            2.6,
"Petal.Length":            5.6,
"Petal.Width":            1.4,
"Species": "virginica" 
},
{
 "Sepal.Length":            7.7,
"Sepal.Width":              3,
"Petal.Length":            6.1,
"Petal.Width":            2.3,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.3,
"Sepal.Width":            3.4,
"Petal.Length":            5.6,
"Petal.Width":            2.4,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.4,
"Sepal.Width":            3.1,
"Petal.Length":            5.5,
"Petal.Width":            1.8,
"Species": "virginica" 
},
{
 "Sepal.Length":              6,
"Sepal.Width":              3,
"Petal.Length":            4.8,
"Petal.Width":            1.8,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.9,
"Sepal.Width":            3.1,
"Petal.Length":            5.4,
"Petal.Width":            2.1,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.7,
"Sepal.Width":            3.1,
"Petal.Length":            5.6,
"Petal.Width":            2.4,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.9,
"Sepal.Width":            3.1,
"Petal.Length":            5.1,
"Petal.Width":            2.3,
"Species": "virginica" 
},
{
 "Sepal.Length":            5.8,
"Sepal.Width":            2.7,
"Petal.Length":            5.1,
"Petal.Width":            1.9,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.8,
"Sepal.Width":            3.2,
"Petal.Length":            5.9,
"Petal.Width":            2.3,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.7,
"Sepal.Width":            3.3,
"Petal.Length":            5.7,
"Petal.Width":            2.5,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.7,
"Sepal.Width":              3,
"Petal.Length":            5.2,
"Petal.Width":            2.3,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.3,
"Sepal.Width":            2.5,
"Petal.Length":              5,
"Petal.Width":            1.9,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.5,
"Sepal.Width":              3,
"Petal.Length":            5.2,
"Petal.Width":              2,
"Species": "virginica" 
},
{
 "Sepal.Length":            6.2,
"Sepal.Width":            3.4,
"Petal.Length":            5.4,
"Petal.Width":            2.3,
"Species": "virginica" 
},
{
 "Sepal.Length":            5.9,
"Sepal.Width":              3,
"Petal.Length":            5.1,
"Petal.Width":            1.8,
"Species": "virginica" 
} 
]
  
      if(!(opts.type==="pieChart" || opts.type==="sparklinePlus" || opts.type==="bulletChart")) {
        var data = d3.nest()
          .key(function(d){
            //return opts.group === undefined ? 'main' : d[opts.group]
            //instead of main would think a better default is opts.x
            return opts.group === undefined ? opts.y : d[opts.group];
          })
          .entries(data);
      }
      
      if (opts.disabled != undefined){
        data.map(function(d, i){
          d.disabled = opts.disabled[i]
        })
      }
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .width(opts.width)
          .height(opts.height)
          
        if (opts.type != "bulletChart"){
          chart
            .x(function(d) { return d[opts.x] })
            .y(function(d) { return d[opts.y] })
        }
          
         
        
          
        

        
        
        
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>


---
## R code for the previous plot


```r
p2 <- nvd3Plot(Sepal.Length ~ Sepal.Width, group = 'Species', 
        data = iris, type = 'scatterChart')
p2$show('inline',include_assets = TRUE)
```


---
## A Highcharts tool in action

<iframe src=' assets/fig/unnamed-chunk-13-1.html ' scrolling='no' frameBorder='0' seamless class='rChart nvd3 ' id=iframe- chartb5c6e306d53 ></iframe> <style>iframe.rChart{ width: 100%; height: 400px;}</style>

---
## R code for the previous plot


```r
x <- data.frame(USPersonalExpenditure)
colnames(x) <- substr(colnames(x), 2, 5)
x$industry<-rownames(x)
xx <- reshape2::melt(x,id="industry")
nPlot(value~variable, group = 'industry', data = xx, type = 'lineChart')
```

---
## <div class="alert alert-warning">Technology 3: googleVis </div> 

R package **googleVis** is the interface to **Google Charts API** for creating interactive charts based on data frames ([see examples](https://developers.google.com/chart/interactive/docs/gallery)). Google Chart tools are powerful, simple to use, and free. Note some facts:
 - data are visualised using a large number of ready-to-use chart types, from simple line charts to complex hierarchical tree maps 
 - charts are rendered using Flash/HTML5/SVG technology to provide cross-browser compatibility and cross platform portability
 - **Flash based** (Motion Charts, Annotated Time Lines, Geo Maps) and 
  **HMTL5/SVG based** (Maps, Geo Charts, Intensity Maps, Tables, Gauges, Tree Maps, Line-, Bar-, Column-, Area- and Combo Charts, Scatter-, Bubble-,      Candlestick-, Pie- and Org Charts)
 - [five vignettes](http://cran.r-project.org/web/packages/googleVis/index.html) have been written on how to use googleVis 
 - [a Slidify presentation](http://mages.github.io/Introduction_to_googleVis/) about the details and usage of googleVis is available on GitHub


---
## gvisMotionChart() in action


```r
plot(gvisMotionChart(Fruits, "Fruit", "Year", options = list(width = 600, height = 400)))
```

<!-- MotionChart generated in R 3.2.1 by googleVis 0.5.9 package -->
<!-- Thu Jun 25 02:13:55 2015 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataMotionChartIDb5c7bd5399c () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Apples",
2008,
"West",
98,
78,
20,
"2008-12-31" 
],
[
 "Apples",
2009,
"West",
111,
79,
32,
"2009-12-31" 
],
[
 "Apples",
2010,
"West",
89,
76,
13,
"2010-12-31" 
],
[
 "Oranges",
2008,
"East",
96,
81,
15,
"2008-12-31" 
],
[
 "Bananas",
2008,
"East",
85,
76,
9,
"2008-12-31" 
],
[
 "Oranges",
2009,
"East",
93,
80,
13,
"2009-12-31" 
],
[
 "Bananas",
2009,
"East",
94,
78,
16,
"2009-12-31" 
],
[
 "Oranges",
2010,
"East",
98,
91,
7,
"2010-12-31" 
],
[
 "Bananas",
2010,
"East",
81,
71,
10,
"2010-12-31" 
] 
];
data.addColumn('string','Fruit');
data.addColumn('number','Year');
data.addColumn('string','Location');
data.addColumn('number','Sales');
data.addColumn('number','Expenses');
data.addColumn('number','Profit');
data.addColumn('string','Date');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartMotionChartIDb5c7bd5399c() {
var data = gvisDataMotionChartIDb5c7bd5399c();
var options = {};
options["width"] =    600;
options["height"] =    400;
options["state"] = "";

    var chart = new google.visualization.MotionChart(
    document.getElementById('MotionChartIDb5c7bd5399c')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "motionchart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartMotionChartIDb5c7bd5399c);
})();
function displayChartMotionChartIDb5c7bd5399c() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartMotionChartIDb5c7bd5399c"></script>
 
<!-- divChart -->
  
<div id="MotionChartIDb5c7bd5399c" 
  style="width: 600; height: 400;">
</div>

--- 
## gvisPieChart() in action

<!-- PieChart generated in R 3.2.1 by googleVis 0.5.9 package -->
<!-- Thu Jun 25 02:13:55 2015 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataPieChartIDb5c556b1d81 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "New York",
200 
],
[
 "Boston",
300 
],
[
 "Miami",
400 
],
[
 "Chicago",
500 
],
[
 "Los Angeles",
600 
],
[
 "Houston",
700 
] 
];
data.addColumn('string','City');
data.addColumn('number','Popularity');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartPieChartIDb5c556b1d81() {
var data = gvisDataPieChartIDb5c556b1d81();
var options = {};
options["allowHtml"] = true;
options["width"] =    400;
options["height"] =    400;

    chartPieChartIDb5c556b1d81 = new google.visualization.ChartWrapper({
    dataTable: data,       
    chartType: 'PieChart',
    containerId: 'PieChartIDb5c556b1d81',
    options: options
    });
    chartPieChartIDb5c556b1d81.draw();
    

}

  function openEditorPieChartIDb5c556b1d81() {
  var editor = new google.visualization.ChartEditor();
  google.visualization.events.addListener(editor, 'ok',
  function() { 
  chartPieChartIDb5c556b1d81 = editor.getChartWrapper();  
  chartPieChartIDb5c556b1d81.draw(document.getElementById('PieChartIDb5c556b1d81')); 
  }); 
  editor.openDialog(chartPieChartIDb5c556b1d81);
  }
    
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "charteditor";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartPieChartIDb5c556b1d81);
})();
function displayChartPieChartIDb5c556b1d81() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartPieChartIDb5c556b1d81"></script>
 
<!-- divChart -->
<input type='button' onclick='openEditorPieChartIDb5c556b1d81()' value='please edit me into a barchart'/>  
<div id="PieChartIDb5c556b1d81" 
  style="width: 400; height: 400;">
</div>


--- &twocol w1:40% w2:60%
## gvisGeoChart() in action

*** =left

<!-- GeoChart generated in R 3.2.1 by googleVis 0.5.9 package -->
<!-- Thu Jun 25 02:13:55 2015 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataGeoChartIDb5c11b1182 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "AU-WA",
323 
],
[
 "AU-VIC",
425 
],
[
 "AU-NT",
154 
],
[
 "AU-NSW",
486 
],
[
 "AU-SA",
201 
],
[
 "AU-QLD",
195 
],
[
 "AU-TAS",
87 
],
[
 "NZ",
123 
] 
];
data.addColumn('string','state');
data.addColumn('number','R_users');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartGeoChartIDb5c11b1182() {
var data = gvisDataGeoChartIDb5c11b1182();
var options = {};
options["width"] =    500;
options["height"] =    400;
options["region"] = "AU";
options["dataMode"] = "regions";
options["resolution"] = "provinces";

    var chart = new google.visualization.GeoChart(
    document.getElementById('GeoChartIDb5c11b1182')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "geochart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartGeoChartIDb5c11b1182);
})();
function displayChartGeoChartIDb5c11b1182() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartGeoChartIDb5c11b1182"></script>
 
<!-- divChart -->
  
<div id="GeoChartIDb5c11b1182" 
  style="width: 500; height: 400;">
</div>

*** =right


```r
df=data.frame(state=c("AU-WA","AU-VIC", 
"AU-NT", "AU-NSW", "AU-SA","AU-QLD",
"AU-TAS","NZ"), 
R_users=c(323,425,154,486,201,195,87,123))
Geo <- gvisGeoChart(df, 
locationvar="state",colorvar=c("R_users"),
options=list(region="AU",
dataMode="regions",resolution="provinces",
width=500, height=400))
plot(Geo)
```

---
## <div class="alert alert-danger">Technology 4: plotly </div>

**Plotly** is an online data visualization tool, with scientific graphing libraries available for Python, R, MATLAB, Perl, Julia and other languages. 
Plotly was built using Python and the Django framework, with a front end using JavaScript and the visualization library D3.js, HTML and CSS. 
Files are hosted on Amazon S3. 

With **plottly**,
- all plots are online and editable by you and your collaborators
- you can analyse and visualize data, together 
- you can publish your ggplot2 figures to the web with one line
- your Shiny application would have plots one can zoom, pan and more

Details and examples: https://plot.ly/r/user-guide/

---
## Too many static ggplots suggest a Shiny app

<img src="topten_sys_201506.svg" height="400" width="850" onerror="this.src='topten_sys_201506.png'">


---
## Adding some interactivity is another good idea


<center><iframe scrolling='no' seamless='seamless' style='border:none' src='https://plot.ly/~andrekos/30/800/1200' width='800' height='1200'></iframe><center>

---
## The end. Take-home messages

<div class="alert alert-info alert-dismissable">
<button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
<h3> htmlwidgets | rCharts | googleVis | plotly - all are good but the first seems best.</h3> 
</div>

<div class="alert alert-success alert-dismissable">
<button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
<h3>Start your own exploration for htmlwidgets and associated packages.</h3> 
</div>

<div class="alert alert-success alert-dismissable">
<button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
<h3>Try them in various environments, e.g. web apps, rmd docs, HTML5 presentations.</h3> 
</div>

<div class="alert alert-warning alert-dismissable">
<button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
<h3>Develop your own widget, either to learn by doing or start a really useful project.</h3> 
</div>

<div class="alert alert-warning alert-dismissable">
<button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
<h3>An R package for animated heatmaps for weather data with turf.js sounds cool. </h3> 
</div>


--- &radio

## What is the best theme for the 3rd WARG event?

I am sure you will be able to deductively conclude that the correct answer is ...

1. Dashboards in R with Shiny & plotly

2. Exploring Hadley's recent R packages (readr, readxl, rvest, etc)

3. Building R packages in the modern way (with RStudio and roxigen2)

4. _Twitter's AnomalyDetection vs. Hyndman's anomalous R packages_

5. S4 vs. S3, object.size(), gc() and other advanced topics

6. Maps and spatial data analysis using R

*** .hint 
Well, right now, I personally would like to learn more about 2, 4 and maybe 6, or even 1.


*** .explanation 
That's right! I love time series, especially if it's about [detecting anomalies]
(https://blog.twitter.com/2015/introducing-practical-and-robust-anomaly-detection-in-a-time-series).


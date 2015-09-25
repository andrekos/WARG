
 <!-- .slide: data-background-size="contain"; data-background="./images/news.jpg" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

# <span style='color:grey50'>R news &amp; tips </span> 

##  WARG meetup  <span style='color:orangered'>#3 </span>

### Andrey Kostenko

#### 29 July, 2015 

##### Perth, WA

<a href="http:\\andreykostenko.com/WARG/">andreykostenko.com/WARG/</a>


***

 <!-- .slide: data-background-size="contain"; data-background="./images/R.png" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

## R 3.2.2 is coming <span style='color:red'>in a fortnight  </span> 

<span style='color:red'> 14 Aug 2015 | R 3.2.2 | "Fire Safety" </span> <!-- .element: class="fragment" data-fragment-index="1" --> 
1. 18 Jun 2015 | R 3.2.1 | "World-Famous Astronaut" <!-- .element: class="fragment" data-fragment-index="1" --> 
2. 16 Apr 2015 | R 3.2.0 | "Full of Ingredients" <!-- .element: class="fragment" data-fragment-index="1" --> 
3. 09 Mar 2015 | R 3.1.3 | "Smooth Sidewalk" <!-- .element: class="fragment" data-fragment-index="1" --> 
4. 31 Oct 2014 | R 3.1.2 | "Pumpkin Helmet" <!-- .element: class="fragment" data-fragment-index="1"--> 


---

## What's new?  

<!-- .slide: data-background-size="contain"; data-background="./images/R.png" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

- New function <span style='color:yellow;font-weight: bold;'> strrep() </span>for repeating the elements of a character vector.

- <span style='color:yellow;font-weight: bold;'>str(x) </span>now displays "Time-Series" also for matrix (multivariate) time-series, i.e. when is.ts(x) is true.

- <span style='color:yellow;font-weight: bold;'>news() </span>now displays R and package news files within the HTML help system if it is available. 

---

## More detail?  

<!-- .slide: data-background-size="contain"; data-background="./images/R.png" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

In the usual place: <br> http://stat.ethz.ch/R-manual/R-devel/doc/html/NEWS.html


***

## R Journal <span style='color:red'>Vol 7/1, June 2015 </span> is out 

<!-- .slide: data-background-size="contain"; data-background="./images/rjournal.jpg" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.4);" -->

<br>
<span style='color:yellow;font-weight: bold;'> started with Vol 1/1, six years ago </span>
<br>
<span style='color:yellow;font-weight: bold;'> replaced R News, the Newsletter of the R Project </span>

---

##  R Journal <span style='color:red'>Vol 7/1, June 2015 </span> featuring 

<!-- .slide: data-background-size="contain"; data-background="./images/rjournal.jpg" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.4);" -->

* <span style='color:green'>fanplot:</span> Visualising Sequential Distributions

* <span style='color:green'>sparkTable:</span> Graphical Tables for Websites and Documents

* <span style='color:green'>showtext</span> Using System Fonts in R Graphics


---

##  Each issue comes with

<!-- .slide: data-background-size="contain"; data-background="./images/rjournal.jpg" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

- R Foundation News
- Changes on CRAN
  - <span style='color:orange'> New packages in CRAN task views </span>
  - <span style='color:orange'> New contributed packages </span>
  - Archived / resurrected packages
- Changes in R

***


##  <span style='color:orange'>RStudio rules! </span>

<!-- .slide: data-background-size="contain"; data-background="./images/RStudioBall.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.8);" -->

- best <span style='color:orange'>IDE</span> (better than e.g. Tinn-R) 

- excellent <span style='color:orange'>people</span> (headed by Hadley Wickham) 

- fantastic new <span style='color:orange'>packages</span> (e.g. leaflet, dygraphs)

- helpful recorded <span style='color:orange'>webinars</span> and [the blog](http://blog.rstudio.org/)

- web applications with <span style='color:orange'>Shiny</span> and [rmarkdown](https://github.com/rstudio/rmarkdown) 

---

## Latest release <br> RStudio v0.99.467 – July 13th, 2015 

<!-- .slide: data-background-size="contain"; data-background="./images/RStudioScreenshot.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.4);" -->

---

## RStudio webinars

<!-- .slide: data-background-size="contain"; data-background="./images/Webinars1.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

Latest: <span style='color:red'> Speaking Analytics: RStudio, Shiny, and RMarkdown </span>  

1. Getting your data into R
2. How to start with Shiny (3 parts)
3. Dynamic Dashboards with Shiny
4. JS data visualizations in R
5. [See the webinar archive for more ](https://www.rstudio.com/resources/webinars/archives/)


---

## RStudio webinars

<!-- .slide: data-background-size="contain"; data-background="./images/Webinars1.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

Second latest: <span style='color:red'>  Getting your data into R </span>  

- <span style='color:green'> haven </span> has fast functions to read SAS data files
- more speady functions are in  <span style='color:green'> readr </span> and <span style='color:green'> readxl </span> 
- <span style='color:green'> DBI </span> to be preferred to <span style='color:green'> RODBC </span>
- <span style='color:green'> jsonlite </span> to be preferred to <span style='color:green'> RJSON </span> or <span style='color:green'> RJSONIO </span>
- <span style='color:green'> rvest </span> for web scraping


***

## <br><br><br> A truly fantastic

<!-- .slide: data-background-size="contain"; data-background="./images/Shiny.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0);" -->

---

## In <span style='color:red'>Shiny 0.12.0 </span> released on June 16, 2015

<!-- .slide: data-background-size="contain"; data-background="./images/Shiny.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 1);" -->

- Interactive plots with base graphics and ggplot2

- In addition to the existing support for clicking and hovering on plots
  created by base graphics, added support for double-clicking and <span style='color:orange'>brushing</span>.

- Added support for clicking, hovering, double-clicking, and <span style='color:orange'>brushing</span> for
  plots created by ggplot2, including support for facets.  
  
- Read more: http://blog.rstudio.org/2015/06/16/shiny-0-12-interactive-plots-with-ggplot2/

***

## We've been noticed!

<!-- .slide: data-background-size="contain"; data-background="./images/revolutions.PNG" style="padding: 20px; display: block; background: rgba(300, 0, 0, 0.1);" -->

***

## More news, tips and reviews and the like <br> in a month's time



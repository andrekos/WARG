<!-- .slide: data-background-size="contain"; data-background="./images/news.jpg" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

# <span style='color:grey50'>R news &amp; tips </span> 

##  WARG meetup  <span style='color:orangered'>#6  </span>

### Andrey Kostenko

#### 28 January, 2016 

##### Perth, WA

<a href="http:\\andreykostenko.com/WARG/">andreykostenko.com/WARG/</a>


***

 <!-- .slide: data-background-size="contain"; data-background="./images/R.png" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

## R 3.2.3 has been released <span style='color:red'> last month </span> 

<span style='color:red'> 10 Dec 2015 | R 3.2.3 | "Wooden Christmas-Tree" </span> <!-- .element: class="fragment" data-fragment-index="1" --> 

- 15 Aug 2015 | R 3.2.2 | "Fire Safety" <!-- .element: class="fragment" data-fragment-index="1" --> 
- 18 Jun 2015 | R 3.2.1 | "World-Famous Astronaut" <!-- .element: class="fragment" data-fragment-index="1" --> 
- 16 Apr 2015 | R 3.2.0 | "Full of Ingredients" <!-- .element: class="fragment" data-fragment-index="1" --> 
- 09 Mar 2015 | R 3.1.3 | "Smooth Sidewalk" <!-- .element: class="fragment" data-fragment-index="1" --> 
- 31 Oct 2014 | R 3.1.2 | "Pumpkin Helmet" <!-- .element: class="fragment" data-fragment-index="1"--> 

<span>  All past releases since R 1.0.0 in Feb 2000: <br> https://cran.r-project.org/bin/windows/base/old/ </span> <!-- .element: class="fragment" data-fragment-index="2"--> 

  
***

---

## Mew features and bug fixes in 3.2.3  

<!-- .slide: data-background-size="contain"; data-background="./images/R.png" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

- function <span style='color:yellow;font-weight: bold;'> which.min(x) </span>  and <span style='color:yellow;font-weight: bold;'> which.max(x) </span> 
may be much faster for logical and integer x ...

- function <span style='color:yellow;font-weight: bold;'>within(df, ..) </span>  no longer drops columns whose name start with a "."

- function <span style='color:yellow;font-weight: bold;'>aperm(a, *) </span> now preserves names(dim(a))

check it all here: https://cran.r-project.org/bin/windows/base/NEWS.R-3.2.3.html

---

## MRO 3.2.3  has been released <span style='color:red'> last week </span> 

<!-- .slide: data-background-size="contain"; data-background="./images/R.png" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

- Revolution R Open is now known as Microsoft R Open

- Microsoft R Open (MRO) 3.2.3 is based on R 3.2.3

- MRO is the enhanced distribution of R from Microsoft

- Key enhancement: multi-core processing (BLAS/LAPACK)

- Supported on Mac OS X 10.11 & Red Hat / CentOS 7.1

- in  addition to versions of Windows, Ubuntu and more


---

<!-- .slide: data-background-size="contain"; data-background="./images/multi-threaded-R.jpg" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.0);" -->

---

<!-- .slide: data-background-size="contain"; data-background="./images/multi-threaded-R2.jpg" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.0);" -->

***

## R Journal <span style='color:red'>Vol 7/2, December 2015 </span> is out 

<!-- .slide: data-transition="convex"; data-background-size="contain"; data-background="./images/rjournal.jpg" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.4);" -->

<br>
<span style='color:yellow;font-weight: bold;'> started with Vol 1/1, 7 years ago </span>
<br>
<span style='color:yellow;font-weight: bold;'> replaced R News, the Newsletter of the R Project </span>

---

##  R Journal <span style='color:red'>Vol 7/2, December 2015 </span> 

<!-- .slide: data-transition="convex"; data-background-size="contain"; data-background="./images/rjournal.jpg" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

* 20 research articles,  including those on R packages

* <span style='color:yellow'>VSURF</span>  for Variable Selection Using Random Forests

* <span style='color:yellow'>hermite</span> for Generalized Hermite Distribution Modelling 

* <span style='color:yellow'>GUIProfiler </span> for R Code Profiling (with Review of Tools)

* <span style='color:yellow'>QuantifQuantile </span> for  Quantile Regression via Optimal Quantization




---

##  Each issue of the journal comes with

<!-- .slide: data-transition="convex"; data-background-size="contain"; data-background="./images/rjournal.jpg" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

- R Foundation News
- Changes on CRAN
  - <span style='color:orange'> New packages in CRAN task views </span>
  - <span style='color:orange'> New contributed packages </span>
  - Archived / resurrected packages
- Changes in R

***


##  <span style='color:orange'>RStudio Inc.</span> mostly known for

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/RStudioBall.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.8);" -->

- popular <span style='color:orange'>IDE</span> (for R users and developers)

- excellent <span style='color:orange'>people</span> (headed by Hadley Wickham) 

- fantastic new <span style='color:orange'>packages</span> (e.g. leaflet, dygraphs)

- useful recorded <span style='color:orange'>webinars</span> and [the blog](http://blog.rstudio.org/)

- beautiful and helpful [cheatsheets](https://www.rstudio.com/resources/cheatsheets/)

- web applications with <span style='color:orange'>Shiny</span> and [rmarkdown](https://github.com/rstudio/rmarkdown) 

---

## Latest release <br> RStudio v0.99.491 – December 30th, 2015 

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/RStudioScreenshot.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.4);" -->

---

## Commercial products free for 45 days  

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/RStudioScreenshot.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.8);" -->

- RStudio for the Enterprise: <span style='color:red'>RStudio Server Pro</span>   lets you access RStudio from anywhere using a web browser. 

- Shiny for the Enterprise: <span style='color:red'>Shiny Server Pro</span>   combines the computational power of R with the interactivity of the modern web. 


---

## Latest RStudio webinars

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/RStudioScreenshot.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.8);" -->

Programming: 
- Part 1 (Writing code in RStudio)
- Part 2 (Debugging code in RStudio)
- Part 3 (Package writing in RStudio)

---


## Latest RStudio webinars

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/RStudioScreenshot.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.8);" -->

Managing Change:
- Part 1 (Projects in RStudio)
- Part 2 <span style='color:red'>(Github and RStudio)</span> - latest recorded 
- Part 3 (Package version with Packrat) - next on 3rd Feb

[See the webinar archive for more ](https://www.rstudio.com/resources/webinars/archives/) in 4 groups: <br> <span style='color:yellow'> RStudio, Shiny, Data Science and Advanced Data Science</span>  


---

## In <span style='color:red'>Shiny 0.13.0 </span> (January 20, 2016)

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/RStudioScreenshot.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.8);" -->

some of the most exciting features include:

- Shiny Gadgets
- HTML templates
- Shiny modules
- Error stack traces
- Checking for missing inputs
- New JavaScript events
  
Read: http://www.r-bloggers.com/shiny-0-13-0/

***

## Other major updates include

<!-- .slide: data-transition="convex" -->

- <span style='color:yellow'>plotly</span> v.2.0 (Nov 17, 2015)

- <span style='color:yellow'>ggplot2</span> v.2.0.0 (Dec 15, 2015)


---

<!-- .slide: data-transition="convex" -->

## plotly v.2.0

- an interactive, browser-based charting library built on the open source JavaScript graphing library, plotly.js: 
click-drag to zoom, shift-click to pan, double-click to autoscale 

- works entirely locally, through the HTML widgets framework, in your RStudio viewer pane / your internet browser

- try R package <span style='color:yellow'>ggplotly</span> to turn your static ggplot2 plot (.pdf file) into an interactive one (.html file) with no changes to your original code! 

Read: https://plot.ly/r/

---

<!-- .slide: data-transition="convex" -->

## ggplot2 v.2.0.0

-  huge  release, with over 100 fixes and improvements 
-  breaks some of your (it did it to mine) existing code
-  <span style='color:yellow'>has now an official extension mechanism</span>
-  handful of new geoms, and updates to existing geoms
-  default appearance tweaked - plots should look better
-  facets have a much richer set of labelling options
-  documentation has been overhauled to be more helpful
-  older and less used features have been deprecated

Read: http://blog.rstudio.org/2015/12/21/ggplot2-2-0-0/


***

## R user conference:  <span style='color:orange'>useR! 2016</span>

http://www.R-project.org/useR-2016

- Don Knuth to speak at useR! 2016

- is scheduled for June 27-30, 2016, and will take place at the campus of Stanford University, Stanford California, USA.

- the program will consist of a day of tutorials followed by three days of invited lectures and user-contributed sessions.


***

## Other interesting reads include

- [r-coming-to-visual-studio](http://www.r-bloggers.com/r-coming-to-visual-studio/)
- [satRdays-are-coming](http://www.r-bloggers.com/satrdays-are-coming/)
- [r-trends-in-2015-based-on-cranlogs](http://www.r-bloggers.com/r-trends-in-2015-based-on-cranlogs/)
- [how-to-detect-heteroscedasticity-and-rectify-it](http://www.r-bloggers.com/how-to-detect-heteroscedasticity-and-rectify-it/)
- [regression-diagnostic-plots-using-r-and-plotly](http://www.r-bloggers.com/regression-diagnostic-plots-using-r-and-plotly/)
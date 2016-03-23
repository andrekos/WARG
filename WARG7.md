<!-- .slide: data-background-size="contain"; data-background="./images/news.jpg" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

# <span style='color:grey50'>R news &amp; tips </span> 

##  WARG meetup  <span style='color:orangered'>#7  </span>

### Andrey Kostenko

#### 24 March, 2016 

##### Perth, WA

<a href="http:\\andreykostenko.com/WARG/">andreykostenko.com/WARG/</a>


***

 <!-- .slide: data-background-size="contain"; data-background="./images/R.png" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

## R 3.2.4 has been released <span style='color:red'> this month </span> 

<span style='color:red'> 10 Mar 2016 | R 3.2.4 | "Very Secure Dishes" </span> <!-- .element: class="fragment" data-fragment-index="1" --> 

- 10 Dec 2015 | R 3.2.3 | "Wooden Christmas-Tree" <!-- .element: class="fragment" data-fragment-index="1" --> 
- 15 Aug 2015 | R 3.2.2 | "Fire Safety" <!-- .element: class="fragment" data-fragment-index="1" --> 
- 18 Jun 2015 | R 3.2.1 | "World-Famous Astronaut" <!-- .element: class="fragment" data-fragment-index="1" --> 
- 16 Apr 2015 | R 3.2.0 | "Full of Ingredients" <!-- .element: class="fragment" data-fragment-index="1" --> 
- 09 Mar 2015 | R 3.1.3 | "Smooth Sidewalk" <!-- .element: class="fragment" data-fragment-index="1" --> 

<span style='color:red'> 14 Apr 2016 | R 3.3.0 | "Supposedly Educational" </span> <!-- .element: class="fragment" data-fragment-index="2"--> 

  
***

---

## Mew features and bug fixes in 3.2.4  

<!-- .slide: data-background-size="contain"; data-background="./images/R.png" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->


- data.frame method of <span style='color:yellow;font-weight: bold;'> rbind() </span>  gains an optional argument  stringsAsFactors

- function  <span style='color:yellow;font-weight: bold;'> summary.data.frame() </span>  now displays NAs in Date columns in all cases

- function <span style='color:yellow;font-weight: bold;'>format.POSIXlt() </span> now behaves correctly


check it all here: [R-3.2.4](https://cran.r-project.org/bin/windows/base/NEWS.R-3.2.4.html) and here [R-3.2.4revised](https://cran.r-project.org/bin/windows/base/NEWS.R-3.2.4revised.html)

---

## new R logo

<!-- .slide: data-background-size="contain"; data-background="./images/newRlogo.svg" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

The R logo has been revised to be more compatible with the principles
of flat design followed by recent user interfaces like MS Windows >= 8 and Mac OS X >= 10.10   


***

## <span style='color:red'>Microsoft</span> R distribution 

<!-- .slide: data-background-size="contain"; data-background="./images/newRlogo.svg" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

- Revolution R Open is now known as Microsoft R Open

- Microsoft R Open (MRO) 3.2.3 is based on R 3.2.3

- MRO is the enhanced distribution of R from Microsoft

- Key enhancement: multi-core processing (BLAS/LAPACK)

- Supported on Mac OS X 10.11 & Red Hat / CentOS 7.1

- in  addition to versions of Windows, Ubuntu and more


***

## <span style='color:red'>Oracle</span> R distribution 

<!-- .slide: data-transition="convex"; data-background-size="contain"; data-background="./images/newRlogo.svg" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

R integration through four key technologies:

- 1 <span style='color:yellow'>Oracle R Distribution</span> is a free download from Oracle, enhanced with dynamic loading of high performance linear algebra libraries 

- 2 <span style='color:yellow'>Oracle R Enterprise</span> integrates R with Oracle Databases and makes R ready for the enterprise with scalability, performance, and ease of production deployment 


---


## <span style='color:red'>Oracle</span> R distribution

<!-- .slide: data-transition="convex"; data-background-size="contain"; data-background="./images/newRlogo.svg" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

R integration through four key technologies:

- 3 <span style='color:yellow'>Oracle R Advanced Analytics for Hadoop</span> provides high performance access to Hadoop Distributed File System and MapReduce programming framework for R users

- 4 <span style='color:yellow'>ROracle </span> is an R package maintained by Oracle and optimised to handle Oracle database connections


---

## <span style='color:red'>Oracle</span> & <span style='color:red'>Microsoft</span> 

<!-- .slide: data-transition="convex"; data-background-size="contain"; data-background="./images/newRlogo.svg" style=" padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

- recognised the need to support data scientists with a widely used and rapidly growing programming language 

- recognised R as the new de facto standard for computational statistics and advanced analytics 

- used R as the language of interaction with the database so that analytics can be written and executed in the database

***

##  R Tools for Visual Studio  

<!-- .slide: data-transition="convex"; data-background-size="contain"; data-background="./images/RTVS-1.jpg" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

[more info](https://blogs.technet.microsoft.com/machinelearning/2016/03/09/announcing-r-tools-for-visual-studio-2/)

 - supports R, Python, C++, C#, Node.js, SQL simultaneously
 
 - attractive to kagglers using R and Python simultaneously

---

##  <span style='color:red'>RTools</span> close clone to <span style='color:red'>RStudio</span> 

<!-- .slide: data-transition="convex"; data-background-size="contain"; data-background="./images/RTVS-1.jpg" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.9);" -->

- <span style='color:red'>perpetually free and open source</span>

- Editor – complete editing experience for R scripts

- IntelliSense – aka auto-completion

- Variable Explorer – drill into your data structures

- Plotting – your R plots in a Visual Studio tool window

- Debugging – breakpoints, stepping, call stacks ...

- R Markdown – rmarkdown/knitr support

- Git – source code control via Git and GitHub


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

## Latest release <br> RStudio v0.99.893 – March 18th, 2016 

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/RStudioScreenshot.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.4);" -->

---

## Commercial products free for 45 days  

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/RStudioScreenshot.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.8);" -->

- RStudio for the Enterprise: <span style='color:red'>RStudio Server Pro</span>   lets you access RStudio from anywhere using a web browser. 

- Shiny for the Enterprise: <span style='color:red'>Shiny Server Pro</span>   combines the computational power of R with the interactivity of the modern web. 


---


## RStudio webinars

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/RStudioScreenshot.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.8);" -->

- Understanding Add-Ins (latest recorded)

- Team productivity with RStudio Server Pro (just finished)

- Understanding Modules (upcoming in April)

[check them all](https://www.rstudio.com/resources/webinars/) in 4 groups: <br> <span style='color:yellow'> RStudio, Shiny, Data Science and Advanced Data Science</span>  


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

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/kdnugget.JPG" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

[New tutorials for Data Scientist at KDnuggets.com](http://www.kdnuggets.com/tutorials/index.html)

***

<!-- .slide: data-transition="concave"; data-background-size="contain"; data-background="./images/r4ds.png" style="padding: 20px; display: block; background: rgba(0, 0, 0, 0.7);" -->

Hadley's new book. Read it: http://r4ds.had.co.nz/


***

## Other interesting reads include

- [600 websites about R](http://www.datasciencecentral.com/profiles/blogs/600-websites-about-r)
- [Hadley Wickham in Melbourne (52 min video)](http://robjhyndman.com/hyndsight/wombat2016-hadley/)
- [scoring r models with Excel](http://blog.revolutionanalytics.com/2016/03/scoring-r-models-with-excel.html)
- [R tools for Visual Studio (26 min video)](https://www.youtube.com/watch?v=PFmOKELowPA)
- [building BI applications using SQL Server R services](https://www.youtube.com/watch?v=qnYaWNC_IUA)
- [in case you missed it: February 2016 roundup](http://blog.revolutionanalytics.com/2016/03/in-case-you-missed-it-february-2016-roundup.html)
- [latest Redmonk and Tiobe language rankings for R](http://blog.revolutionanalytics.com/2016/02/latest-redmonk-and-tiobe-language-rankings-for-r.html)
- [faster data manipulation 7 packages](http://www.analyticsvidhya.com/blog/2015/12/faster-data-manipulation-7-packages/)
- [using R ML script as a Power BI Desktop data source](https://www.simple-talk.com/sql/bi/using-r-machine-learning-script-as-a-power-bi-desktop-data-source/)
- [autobox for R](http://www.autobox.com/cms/index.php/news/219-autobox-for-r)
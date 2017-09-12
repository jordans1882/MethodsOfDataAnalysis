---
title: "Introduction to R"
author: "Jordan Schupbach"
output:
  revealjs::revealjs_presentation
    fig_height: 6
    fig_width: 10
    fig_crop: FALSE
    height: "960px"
    width: "720px"
    theme: "black"
    slide_level: 1
    transition: "slide"
    incremental: FALSE
    self_contained: TRUE
---

What is R?
========================================================

R is 'GNU S', a libre (free) software environment for statistical computing under
the Free Software Foudation's GNU General Public Liscense.
- R is a dynamic, lexically scoped, functional, class based object oriented 
programming (OOP) language written for statistical computation often written by 
statisticians.
- Through its base set of packages and extensive number of packages, you can
conduct nearly any statistical analyses with ease.

What is S?
-----------

- S is a statistical programming language developed by John Chambers, Rick
  Becker, and Alan Wilks at Bell Labs. It's first implementation was in 1976.
- S was superceded by S-PLUS, commercial software owned by TIBCO.

R is an implementation of S with lexical scoping.
- R was created by Ross Ihaka and Robert Gentleman at the University at Aukland, 
New Zealand.
- It's inception was in 1992, it's initial version was released in 1995 and the 
first stable version in 2000.

Why use R?
===============

- R is a programming language available, libre, as Free Software under the Free 
Software Foudation's GNU General Public Liscense 
- Maintained and supported by a large communitiy of statisticians. 
- Over 5000 packages on CRAN to extend its base functionality.
- R is written in C, Fortan, and R. It can easily be extended through Java
  and C++.
- With careful coding, R can be quite fast.
- It's easy and fun.

R Studio Tips and Tricks
========================================================

RStudio is an IDE developed specifically for programming in R (though there is
functionality for programming in other programming languages). Here's some tips 
for using RStudio.
- Keep your workspace clean (i.e., don't save your workspace at the end of a 
session and don't use attach() unless you have some really great reason to do
so).
- Open a file in Rstudio, and then set your working directory to the file
location
using Session -> Set Working Directory -> Source File Location
- Customize your RStudio IDE by changing the global options by Tools -> Global 
Options. You might:
  - Modify your color scheme
  - Modify pane layout
  - Change R startup options or editor settings (e.g. code completion)
  - Enable vim keybindings

R Studio Tips and Tricks
========================================================

- Use keybindings 
  - Ctrl + Enter to run a line of code
  - Ctrl + Shift + k to compile your rmarkdown or knitr document
  - Ctrl + 1, Ctrl + 2, ... to make certain panes in RStudio active
  - Ctrl + Shift + n to open a new R script
  - You can see all and modify keybindings using Tools -> Modify Keyboard 
  Shortcuts

So you're new to R programming (and maybe programming)?
========================================================

Fear not programming in R. It is quite easy and there is a plethora of material 
out on the internet.
- Your first step when you have an R question is to type it into a search engine.
Chances are that someone has asked this question before and someone has responded
to them on some forum site like stack exchange
  - How strong is your Google Fu?

Object Oriented Programming
===========================

- Object oriented programming is a programming paradigm based on the concept of 
"objects" which can be either data (i.e. fields) or procedures (i.e. methods).
- Class based OOP languages have the added notion of types of objects (i.e. 
class)
- R has four main object oriented paradigms for which you can create classes, 
methods and objects: S3, S4, R5, and R6
  - S3 and S4 objects are the most popular and likely all you will encounter
  - R6 is based on the R5 paradigm, which you might want to use if speed is 
  crucial.
  - There are other reasons why you might want to write in one paradigm or
  the other, such as some program more naturally falling within one paradigm or
  the other, but these details aren't important for when you just learning R
- OOP concepts are not something to worry about while you're learning R, but you
may want to know whether you are dealing with an S3 or an S4 object (i.e.,
when looking at source code or extracting objects from an object).
- The basic implication is that you should recognize that every bit of code, if 
it runs, is an object that you can inspect. Even arguments you give in a 
functionare objects. So, if you want to inspect a line of code with a function 
you don't know, you can not only inspect the help documentation, but you can 
inspect the arguments to the function as well.

Object structure
================
- R is an OOP language. Learn how to use the str() command to look at the 
structure of an object.
  - Knowing what type of object you are dealing with can help you diagnose how
  to extract what you need from it.

```r
data(iris)
str(iris)
```

```
'data.frame':	150 obs. of  5 variables:
 $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
 $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
 $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
 $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
 $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...
```
The output tells us that the object iris is of data.frame class with 150 
observations (rows) and 5 variables (e.g. Sepal.Length). If you look at the help
documentation for the function `data.frame()` (i.e. `?data.frame`), 
which creates objects of class `data.frame`, you can see examples of creating 
data.frame objects.

data.frame objects
===================

- data.frame objects are basic R objects that are the fundamental data structures 
used by most of R's modeling software. 
- Effectively, a data.frame is a list of variables of the same number rows with 
unique row names.
- To extract the component of the list named `Sepal.Length`, we can run

```r
iris$Sepal.Length
```

```
  [1] 5.1 4.9 4.7 4.6 5.0 5.4 4.6 5.0 4.4 4.9 5.4 4.8 4.8 4.3 5.8 5.7 5.4
 [18] 5.1 5.7 5.1 5.4 5.1 4.6 5.1 4.8 5.0 5.0 5.2 5.2 4.7 4.8 5.4 5.2 5.5
 [35] 4.9 5.0 5.5 4.9 4.4 5.1 5.0 4.5 4.4 5.0 5.1 4.8 5.1 4.6 5.3 5.0 7.0
 [52] 6.4 6.9 5.5 6.5 5.7 6.3 4.9 6.6 5.2 5.0 5.9 6.0 6.1 5.6 6.7 5.6 5.8
 [69] 6.2 5.6 5.9 6.1 6.3 6.1 6.4 6.6 6.8 6.7 6.0 5.7 5.5 5.5 5.8 6.0 5.4
 [86] 6.0 6.7 6.3 5.6 5.5 5.5 6.1 5.8 5.0 5.6 5.7 5.7 6.2 5.1 5.7 6.3 5.8
[103] 7.1 6.3 6.5 7.6 4.9 7.3 6.7 7.2 6.5 6.4 6.8 5.7 5.8 6.4 6.5 7.7 7.7
[120] 6.0 6.9 5.6 7.7 6.3 6.7 7.2 6.2 6.1 6.4 7.2 7.4 7.9 6.4 6.3 6.1 7.7
[137] 6.3 6.4 6.0 6.9 6.7 6.9 5.8 6.8 6.7 6.7 6.3 6.5 6.2 5.9
```
By default, R will use the `print` method on an object when you run an object by 
itself

Vector objects
===============
The object `iris$Sepal.Length` is what is called a vector. Specifically it is a 
numeric vector of length 150.

```r
str(iris$Sepal.Length)
```

```
 num [1:150] 5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
```
We can access the 28th element of the vector using square bracket notation:

```r
str(iris$Sepal.Length[28])
```

```
 num 5.2
```
For which the object is now a numeric vector of length one whose value is 5.2.

Another Object structure
========================

Let's look at a linear model object. Print the first 9 lines of the output 
of the `str()` function using the following code. 

```r
lm1 <- lm(Sepal.Length ~ Sepal.Width, data = iris)
print(gsub("\"", "", head(capture.output(str(lm1)), 9)))
```

```
[1] "List of 12"                                                                 
[2] " $ coefficients : Named num [1:2] 6.526 -0.223"                             
[3] "  ..- attr(*, names)= chr [1:2] (Intercept) Sepal.Width"                    
[4] " $ residuals    : Named num [1:150] -0.644 -0.956 -1.111 -1.234 -0.722 ..." 
[5] "  ..- attr(*, names)= chr [1:150] 1 2 3 4 ..."                              
[6] " $ effects      : Named num [1:150] -71.566 -1.188 -1.081 -1.187 -0.759 ..."
[7] "  ..- attr(*, names)= chr [1:150] (Intercept) Sepal.Width   ..."            
[8] " $ rank         : int 2"                                                    
[9] " $ fitted.values: Named num [1:150] 5.74 5.86 5.81 5.83 5.72 ..."           
```
We can see that the object `lm1` is a list object of length 12, the first 5 elements 
of which we can see are named coefficients, residuals, effects, rank and fitted.values.
We see `lm1$coefficients` is a named numeric vector of length 2, whose values are 
6.526 and -0.223. lm1 is also an S3 object, because it's slots are accessed using `$`
instead of `@` (for S4 objects).

R documentation and source code
================================
- Read the documentation of a function if you don't know exactly how it works.
- Use `?function_name` or `help(function_name)` to look at the documentation of 
a function. Make sure to look at the examples at the bottom of the help
- Check out the help documentation for plot and plot.default 
 

```r
?plot
?plot.default  
```
- We will go through the difference between `plot` and `plot.default` in a few
slides, but notice there are a larger set of graphical parameters set as arguments
by default for the plot.default method.
- Also notice the `...` argument to the function. This is used to pass arguments 
from some other function. In this case, they are passed from `par()`. Make sure
to look at the help for par to see all of the possible graphical parameters you 
can set. 

Function source code
====================
Run a line of code with only the function name in R console to see the source
code of a function, (e.g. plot or plot.default).


```r
plot
```

```
function (x, y, ...) 
UseMethod("plot")
<bytecode: 0x301a930>
<environment: namespace:graphics>
```

Seeing the call to the `UseMethod()` function tells me that this is a generic S3 function.

Function source code
====================


```r
plot.default
```

```
function (x, y = NULL, type = "p", xlim = NULL, ylim = NULL, 
    log = "", main = NULL, sub = NULL, xlab = NULL, ylab = NULL, 
    ann = par("ann"), axes = TRUE, frame.plot = axes, panel.first = NULL, 
    panel.last = NULL, asp = NA, ...) 
{
    localAxis <- function(..., col, bg, pch, cex, lty, lwd) Axis(...)
    localBox <- function(..., col, bg, pch, cex, lty, lwd) box(...)
    localWindow <- function(..., col, bg, pch, cex, lty, lwd) plot.window(...)
    localTitle <- function(..., col, bg, pch, cex, lty, lwd) title(...)
    xlabel <- if (!missing(x)) 
        deparse(substitute(x))
    ylabel <- if (!missing(y)) 
        deparse(substitute(y))
    xy <- xy.coords(x, y, xlabel, ylabel, log)
    xlab <- if (is.null(xlab)) 
        xy$xlab
    else xlab
    ylab <- if (is.null(ylab)) 
        xy$ylab
    else ylab
    xlim <- if (is.null(xlim)) 
        range(xy$x[is.finite(xy$x)])
    else xlim
    ylim <- if (is.null(ylim)) 
        range(xy$y[is.finite(xy$y)])
    else ylim
    dev.hold()
    on.exit(dev.flush())
    plot.new()
    localWindow(xlim, ylim, log, asp, ...)
    panel.first
    plot.xy(xy, type, ...)
    panel.last
    if (axes) {
        localAxis(if (is.null(y)) 
            xy$x
        else x, side = 1, ...)
        localAxis(if (is.null(y)) 
            x
        else y, side = 2, ...)
    }
    if (frame.plot) 
        localBox(...)
    if (ann) 
        localTitle(main = main, sub = sub, xlab = xlab, ylab = ylab, 
            ...)
    invisible()
}
<bytecode: 0x4f94870>
<environment: namespace:graphics>
```

plot() vs plot.default()
========================

- `plot.default` is the default method for the generic S3 function `plot()`

We can see all of the available methods for this generic plotting function using
the `methods()` function


```r
methods(plot)
```

```
 [1] plot.acf*           plot.data.frame*    plot.decomposed.ts*
 [4] plot.default        plot.dendrogram*    plot.density*      
 [7] plot.ecdf           plot.factor*        plot.formula*      
[10] plot.function       plot.hclust*        plot.histogram*    
[13] plot.HoltWinters*   plot.isoreg*        plot.lm*           
[16] plot.medpolish*     plot.mlm*           plot.ppr*          
[19] plot.prcomp*        plot.princomp*      plot.profile.nls*  
[22] plot.raster*        plot.spec*          plot.stepfun       
[25] plot.stl*           plot.table*         plot.ts            
[28] plot.tskernel*      plot.TukeyHSD*     
see '?methods' for accessing help and source code
```
Functions with an asterisk are 'non-visible', meaning the function is not exported
from the package's namespace.

Viewing source code from non-exported S3 functions
===========================================

These functions which aren't exported from their packages namespace have a 
certain way to view source code. We can vew the source for instance using the 
`:::` function


```r
gsub("\"", "", head(capture.output(graphics:::plot.table), 8))
```

```
[1] "function (x, type = h, ylim = c(0, max(x)), lwd = 2, xlab = NULL, "
[2] "    ylab = NULL, frame.plot = is.num, ...) "                       
[3] "{"                                                                 
[4] "    xnam <- deparse(substitute(x))"                                
[5] "    rnk <- length(dim(x))"                                         
[6] "    if (rnk == 0L) "                                               
[7] "        stop(invalid table 'x')"                                   
[8] "    if (rnk == 1L) {"                                              
```

S4 objects
===========

S4 objects have a slightly different storage format than S3 objects. Consider
the following S4 object.


```r
lmer1 <- lme4::lmer(Sepal.Length ~ Sepal.Width + (1|Species), data = iris)
gsub("\"", "", head(capture.output(str(lmer1)), 8))
```

```
[1] "Formal class 'lmerMod' [package lme4] with 13 slots"                  
[2] "  ..@ resp   :Reference class 'lmerResp' [package lme4] with 9 fields"
[3] "  .. ..$ Ptr    :<externalptr> "                                      
[4] "  .. ..$ mu     : num [1:150] 5.07 4.67 4.83 4.75 5.15 ..."           
[5] "  .. ..$ offset : num [1:150] 0 0 0 0 0 0 0 0 0 0 ..."                
[6] "  .. ..$ sqrtXwt: num [1:150] 1 1 1 1 1 1 1 1 1 1 ..."                
[7] "  .. ..$ sqrtrwt: num [1:150] 1 1 1 1 1 1 1 1 1 1 ..."                
[8] "  .. ..$ weights: num [1:150] 1 1 1 1 1 1 1 1 1 1 ..."                
```


Accessing S4 object slots
=========================

We can access slots of an S4 object using `@`. For instance, we can obtain the first
100 fitted values from the model using

```r
head(lmer1@resp$mu, 100)
```

```
  [1] 5.067641 4.669063 4.828494 4.748779 5.147356 5.386502 4.987925
  [8] 4.987925 4.589348 4.748779 5.227071 4.987925 4.669063 4.669063
 [15] 5.466218 5.785079 5.386502 5.067641 5.306787 5.306787 4.987925
 [22] 5.227071 5.147356 4.908210 4.987925 4.669063 4.987925 5.067641
 [29] 4.987925 4.828494 4.748779 4.987925 5.545933 5.625649 4.748779
 [36] 4.828494 5.067641 5.147356 4.669063 4.987925 5.067641 4.111055
 [43] 4.828494 5.067641 5.306787 4.669063 5.306787 4.828494 5.227071
 [50] 4.908210 6.277571 6.277571 6.197855 5.560132 5.958709 5.958709
 [57] 6.357286 5.639847 6.038424 5.878994 5.320986 6.118140 5.480416
 [64] 6.038424 6.038424 6.197855 6.118140 5.878994 5.480416 5.719563
 [71] 6.277571 5.958709 5.719563 5.958709 6.038424 6.118140 5.958709
 [78] 6.118140 6.038424 5.799278 5.639847 5.639847 5.878994 5.878994
 [85] 6.118140 6.437001 6.197855 5.560132 6.118140 5.719563 5.799278
 [92] 6.118140 5.799278 5.560132 5.878994 6.118140 6.038424 6.038424
 [99] 5.719563 5.958709
```

User defined functions
=======================

You can also define your own functions in R. If you're going to be doing some
operation in R, it's a good habbit to functionalize the process so that you can 
reuse it later and save on programming time. 
- Here's a simple example of a function you could define


```r
foo <- function(bar){
  return(list(foo = "foo", bar = bar))
}
print(foo("bar"))
```

```
$foo
[1] "foo"

$bar
[1] "bar"
```
The function `foo()` takes `bar` as an object and simply returns the object `bar`.
Not a great example of why you would want to functionalize something, but does 
show you the mechanics.

A small test
=============

What would you expect to see as output from the following?


```r
foo("bar")$foo
```

Viewing the source
==================

Now that `foo()` is a function defined in our global environment, we can access
it's source code again by writing the name of the function in console.


```r
foo
```

```
function(bar){
  return(list(foo = "foo", bar = bar))
}
<bytecode: 0x76fb658>
```

```r
methods(foo)
```

```
no methods found
```

There are no methods written for this function, as we haven't defined any.




More
=========

- Check out the methods() of a generic function (e.g. methods(plot)) and look
at the help documentation for a specific function method using ? or help()




```
Error in parse(text = x, srcfile = src) : 
  <text>:4:0: unexpected end of input
2: ?matmult
3: ?function
  ^
```

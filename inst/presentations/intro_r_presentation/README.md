Compile .Rmd File
==================

You can compile the .Rmd file by first running the following lines of code:

```r
# Set CRAN location for installing packages
r <- getOption("repos")
r["CRAN"] <- "http://cran.us.r-project.org"
options(repos = r)
rm(r)

# Helper function to install CRAN package if not installed and load
use_package <- function(p) {
if (!is.element(p, installed.packages()[,1]))
  install.packages(p, dep = TRUE)
library(p, character.only = TRUE)
}

# Install CRAN packages
use_package('devtools')
use_package('rmarkdown')
use_package('lme4')

# Helper function to install and load github packages
use_github_package <- function(r) {
p <- gsub(".*/","",r)
if (!is.element(p, installed.packages()[,1]))
  install_github(r, dep = TRUE)
library(p, character.only = TRUE)
}

# Install github packages
use_github_package('yihui/xaringan')
```

Then, change your working directory to the location of the .Rmd file and run

```r
rmarkdown::render('intro_r_presentation.rmd')
```

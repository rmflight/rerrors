## Collection of Errors, Warnings and Messages in R

When someone is first starting out in R, if they are not used to programming, the various errors, warnings and messages that R provides can be intimidating. This is meant to be a useful collection of observed types of messages that R provides, along with an explanation of what R is trying to tell them.

### Have an Error Message?

If you have an error message you need help with file an [issue](https://github.com/rmflight/rerrors/issues).

If you have an error message and explanation you want to add, [please clone the repo](https://github.com/rmflight/rerrors), add your message, and create a pull request.

## Installing packages

You don't need to do 'install.packages("tidyverse")' every time. Install is installing it on your system. You only need to do it again if you re-install R, or want a newer version. 'library()' loads it for use, and 'install.packages()' installs it to your computer.

```
instal.packages("tidyverse")
Error in instal.packages("tidyverse") :
 could not find function "instal.packages
```


This error is telling you it **can't find the function**. Most times, this is because it is spelled wrong, as it is here. Other times, it's because you haven't done "library('tidyverse')" yet and it can't find the function you want. This is a good reason to use a tab-completion enabled editor such as RStudio, it will help you make sure the spelling of functions is correct. 

## Loading packages

### Conflict Messages

```r
library("tidyverse")
-- Conflicts ------------------------------------------ tidyverse_conflicts() --
x dplyr::filter() masks stats::filter()
x dplyr::lag()    masks stats::lag()
```

This is telling you that there are packages you have loaded via 'library("tidyverse")' that have functions that are named the same as functions in the base install that are always loaded.

### Built Version Warnings

```
Warning messages:
 1: package ‘tidyverse’ was built under R version 3.5.3
```

And this is just saying that the packages on CRAN are built under the latest version of R 3.5.3 , but you have 3.5.something_else. In my experience, as long as it installs, you are OK. 

## Using packages

### Function not found

```r
ggplot(...)
Error in ggplot() : could not find function "ggplot"
```

This is telling you that you have not loaded the library that the ggplot function is in (ggplot2 in this case). To fix this you load ggplot2 first with `library(ggplot2)` .

### Lengths differ

```r
x = rnorm(100)
y = rnorm(1000)
plot(x,y)
Error in xy.coords(x, y, xlabel, ylabel, log) : 
 'x' and 'y' lengths differ
```

This is pretty clear, the number of x coordinates is different to the number of y coordinates you have given. Often caused by either a typo in x or y names, or you subsetted one and not the other. You can double check it by doing:

```r
length(x)
length(y)
```

### Length is not a multiple

```r
(1:2)*(1:3)
[1] 1 4 3
Warning message:
In (1:2) * (1:3) :
 longer object length is not a multiple of shorter object length
```

This is only a warning, but you should usually think of it as an error.  Your code is trying to do an operation on two vectors of different lengths.  R has rules that allow the operation to proceed (which is why it's only a warning) but you probably used the wrong name or subsetted one and not the other, or something similar.

###  Not subsettable

```r
df[2]
Error in df[2] : object of type 'closure' is not subsettable
```

Technically, R is telling you that you are trying to subset a function (`df` is the density function for the F distribution).  In practice, this almost always happens when you think you have a variable called `df` (eg, a data frame) but R can't find it. Most likely the variable doesn't exist, but it might exist somewhere that R can't see. 

### Unexpected String Constant

```r
data_frame[, c("column1" "column2")]
Error: unexpected string constant in data_frame[, c("column1" "column2")]
```

What happened here when I tried to get two columns of the `data_frame` is that I forgot the "," in between the two column names.

## Contributing

If you have an error message you need help with file an [issue](https://github.com/rmflight/rerrors/issues). 
If you have an error message and explanation you want to add, [please clone the repo](https://github.com/rmflight/rerrors), add your message, and create a pull request.

This project has a [Contributor Code of Conduct](https://github.com/rmflight/rerrors/blob/master/CODE_OF_CONDUCT.md), and you are asked to abide by it.



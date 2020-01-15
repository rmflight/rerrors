## Collection of Errors, Warnings and Messages in R

When someone is first starting out in R, if they are not used to programming, the various errors, warnings and messages that R provides can be intimidating. This is meant to be a useful collection of observed types of messages that R provides, along with an explanation of what R is trying to tell them.

## Installing packages

You don't need to do 'install.packages("tidyverse")' every time. Install is installing it on your system. You only need to do it again if you re-install R, or want a newer version. 'library()' loads it for use, and 'install.packages()' installs it to your computer.

> Error in instal.packages("tidyverse") :

>   could not find function "instal.packages

This error is telling you it **can't find the function**. Most times, this is because it is spelled wrong, as it is here. Other times, it's because you haven't done "library('tidyverse')" yet and it can't find the function you want. This is a good reason to use a tab-completion enabled editor such as RStudio, it will help you make sure the spelling of functions is correct. 

## Loading packages

### Conflict Messages

> library("tidyverse")
> -- Conflicts ------------------------------------------ tidyverse_conflicts() --

> x dplyr::filter() masks stats::filter()

> x dplyr::lag()    masks stats::lag()

This is telling you that there are packages you have loaded via 'library("tidyverse")' that have functions that are named the same as functions in the base install that are always loaded.

### Built Version Warnings

> Warning messages:

> 1: package ‘tidyverse’ was built under R version 3.5.3

And this is just saying that the packages on CRAN are built under the latest version of R 3.5.3 , but you have 3.5.something_else. In my experience, as long as it installs, you are OK. 

## Using packages
### Function not found

> Error in ggplot() : could not find function "ggplot"

This is telling you that you have not loaded the library that the ggplot function is in (ggplot2 in this case). To fix this you load ggplot2 first with `library(ggplot2)` .

### Lengths differ
> plot(x,y)
> Error in xy.coords(x, y, xlabel, ylabel, log) : 
>   'x' and 'y' lengths differ

This is pretty clear, the number of x coordinates is different to the number of y coordinates you have given. Often caused by either a typo in x or y names, or you subsetted one and not the other. 

## Contributing

If you have a message you don't know the meaning of, please file an issue. If you have a message you would like to see added, please file a pull request. 

This project has a Contributor Code of Conduct that you are asked to abide by.



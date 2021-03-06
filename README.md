# RAVE
R Analysis and Visualization of ECOG Data

## A. Installation

### 1. Environment Setup

In this section, you'll install R, RStudio, devtools and all other dependencies.

**R** is a functional programming language that *RAVE* uses. **Devtools** are necessary to enable advanced features. **RStudio** is an *IDE (Intergrated Development Environment)* for easy and better code management especially designed for R. If you are hosting a server in RAVE, or prefer to using command lines, RStudio is not necessary.

You need to check your operating system before installtion:

+ [Mac OS](#macos)
+ [Windows (Windows 10, with Bash enabled)](#windows)
+ Linux (Ubuntu-Like)
+ Linux (Others)


#### MacOS

1. First, go to Cran-R official website and download install the latest R:

[https://cran.r-project.org/bin/macosx/](https://cran.r-project.org/bin/macosx/)

2. After installing R, make sure that you install Xcode from the Mac App Store:

The best way is to google **How to install Xcode**. Moncef Belyamani has a great article [here](https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/).

Or if you have `AFNI` installed, you must have Xcode installed, then you need xcode command line tool. Open terminal (from Application), enter

```
xcode-select --install
```

3. RStudio

[https://www.rstudio.com/products/rstudio/download/](https://www.rstudio.com/products/rstudio/download/)

#### Windows

On Windows, RAVE is limited because *AFNI* doesn't support windows. However, most of RAVE functions should work. To install RAVE, you need to have *bash* enabled on Windows 10.

It's easy to install on Windows. 

1. First, go to Cran-R official website and download install the latest R:

[https://cran.r-project.org/bin/windows/base/](https://cran.r-project.org/bin/windows/base/)

2. After installing R, download and install *Rtools*. Please install the latest version:

[https://cran.r-project.org/bin/windows/Rtools/](https://cran.r-project.org/bin/windows/Rtools/)

3. RStudio

[https://www.rstudio.com/products/rstudio/download/](https://www.rstudio.com/products/rstudio/download/)

### 2. Install R dependencies and RAVE

**If you have installed RStudio, open it, or if you are using terminal/command line, type `R` to enter R.**

There are two ways to install RAVE. 

#### 2.1 If you want to install recommended version of RAVE (strongly recommended)

I have written a very simple and easy script for you. Open R, or RStudio, enter:

```
source('https://raw.githubusercontent.com/dipterix/instrave/master/R/hello.R')
```

If you fail, don't worry, try it several times, since there are so many packages to be installed and "turn R off and on again" is the easiest way to clean the installation environment :) However, if you try more than five times and still get errors, this might be an issue. Please report the issue on Github or contact me via my [email](mailto:dipterix.wang@gmail.com?Subject=[RAVE_Issues_Github]&Body=Hi%20Dipterix).

Then you will see that `RAVE` is installed and attached. Type 

```
init_app()
```

to enjoy :)

#### 2.2 If you want to install specific version of RAVE

Inside of R, install `devtools` and `rhdf5` by typing the following commands:

```
install.packages('devtools')
source("https://bioconductor.org/biocLite.R")
biocLite(c("rhdf5", "HDF5Array"), suppressUpdates = T, suppressAutoUpdate = T)
```

Next, install RAVE,

There are two versions of RAVE, **Alpha**, **Beta** version. To see the difference, please check [RAVE updates]()

#### Alpha version (NOT recommended now)

This version was last updated at *Dec/2017* and is no-longer supported. This version is only developed for [Beauchamp's Lab](https://openwetware.org/wiki/Beauchamp). However, you can still see the [demo here](http://34.214.213.191:8080/)

`devtools::install_github('beauchamplab/rave')`

*Please make sure that your R has packages `devtools`, `tidyverse` installed.*
*It is also recommended that other packages (`rhdf5`, `HDF5Array`) be installed.*

#### Beta Version

IMPORTANT: I'm Still maturing this version. However, it's runnable and contains more features than the alpha version. Please go to [RAVE_dev-cycle]() to see the todo-list.

To install this version of RAVE, simply enter the following command:

`devtools::install_github('beauchamplab/rave@rave-dipterix')`

or -

`devtools::install_github('beauchamplab/rave', ref = 'rave-dipterix')`

Please make sure that you have latest `yaml` package installed. Upon failure, you might want to try: `install.packages('yaml')`.
All other dependencies should be installed automatically


## B. Toy example

*Depending on the version of `RAVE` that you have installed*

### Beta version

Beta version is very easy. This version comes with some "real" data

To play with **preprocess**, type the following R command 

```
rave_pre_process()
```

In the `subject code`, type `Subject` and press `load` button

To play with **Main**, type:

```
init_app()
```

### Alpha version

If you have installed `Alpha` version, you can use the following code to launch

```
# Load packages
library(rave)
require(tidyverse)
require(magrittr)

# Re-direct ECOG data directory and module index file
rave_opts$set_options(
  data_dir = system.file('example/data', package='rave'),
  module_lookup_file = system.file('modules.csv', package='rave')
);

# Launch web service
init_app()
```

Please check `vignettes/user_guide` for details such as 
*data format*, *SUMA connection*, *Matlab options*. To know how to 
*write modules*, or *use command lines* (import subject data and perform 
quick analysis), check `vignettes/rafe-cookbook`.




# Foundational Skills {#c06}

## Chapter overview
This chapter is designed to give you the skills and knowledge necessary to _get started_ in any of the walk through chapters. 
Our goal is to get you working with R using the RStudio *I*ntegrated *D*evelopment *E*nvironment (IDE) through a series of applied examples. 
If you have not yet installed R and/or RStudio, please go through the steps outlined in Chapter 05 before beginning this chapter.    

Please note that this chapter is not intended to be a full and complete introduction to programming with R, nor for using R for data science. 
There are many excellent resources available which provide this kind of instruction, and we've listed them for you on page [AAA] in the **Resources** section [link for bookdown version].  

## Foundational Skills Framework
No two data science projects are the same, and rather than be overly prescriptive, this chapter errs on the side of creating a general framework for you to use as a home base as you work through this text. 
The four basic concepts we will use to build our framework are:  

* **Data**
* **Projects**  
* **Packages**  
* **Functions**  

You're likely using this text because you have some data that you'd like to do something with, and you'd like to try doing said thing using R. 
The framework we'll use assumes that your data exists externally from R in a `.csv` file, and needs to be brought into R so that we can work with it.  

There are a multitude of file types that data can be stored in.
We've provided additional resources for loading data from Excel, SAV, and Google Sheets at the end of this chapter.

While it is possible to connect directly to a database from within R, we do not cover those skills in this text. 
For those curious as to how to accomplish this, we recommend the following resources [AAA].  

### Data
We have **data** that we bring into a Project within RStudio. 
RStudio is the interface that we use to access and manipulate R. 
Sometimes you'll hear RStudio referred to as an IDE, or "Interactive Development Environment." 
We use an IDE - in this case RStudio, although you could use others - because it adds features that make our analytical lives a little (and sometimes a lot!) easier. 

## Projects
Within RStudio we set up a **Project**. 
This is the home for all of the files, images, reports, and code that we'll create for a single project.
While there are a myriad of ways to set up the files in your Project, the method we'll use in this text is:  

[IMAGE with src, data (sub: raw, for use), results, images] 

It's OK (and totally normal) for your initial projects to consist of only one or two files. 
As your skill set grows and develops you'll need more and more files, and laying the groundwork for a file structure now will make future you very happy.  

We use Projects because they create a self-contained folder for a given analysis in R. 
This means that if you want to share your Project with a colleague they will not have to reset file paths (or even know anything about file paths!) in order to re-run your analysis.  

And even if the only person you ever collaborate with is a future version of yourself, using a Project for each of your analyses will mean that you can move the Project folder around on your computer, or even move it to a new computer, and remain confident that the analysis will run in the future, at least in terms of file path structures. 
You may run into issues with packages being out of date and functions being deprecated - in which case you may be interested in learning more about how to set up a Project within Docker [AAA].  

### Setting up your Project

**How do I create a Project?**  
Creating a Project is one of the first steps in working on an R-based data science project in RStudio (if we were using GitHub for this we'd absolutely recommend setting up your repository first! While we do not use Git or GitHub in this text, you can read more about it at [happygitwithr.com](http://www.happygitwithr.com).) 
To create a Project you will need to be in RStudio.  

From within RStudio, follow these steps:  

1. Click on File
2. Select New Project
3. Choose New Directory
4. Click on New Project
5. Enter your Project's name in the box that says "Directory name." 
We recommend choosing a Project name that helps you to remember that this is a project that involves data science in education.
Avoid using spaces in your Project name, and instead separate words with hyphens or underscore characters.
6. Choose where to save your Project by clicking on "Browse" next to the box labeled "Create project as a subdirectory of: "
If you are just using this to learn and to test out creating a Project, consider placing it in your downloads or another temporary directory so that you remember to remove it later.
7. Click "Create Project"  

If you are looking for more resources, including information on using a git repository, whether or not you should open in a new session, etc., please see AAA and BBB resources.  

We should point out that it is not _necessary_ to create a Project for your work, although we strongly recommend it. 
If you do not create a Project, you can always check where your working directory (i.e., where your R is pointing) is by running `getwd()`. 
You can then change your working directory manually, by running `setwd()` and providing your file path name as an argument. 

More on manually setting your working directory can be found [here]().

## Packages

"Packages" are shareable collections of R code that provide functions (i.e., a command to perform a specific task), data, and documentation. Packages increase the functionality of R by providing access to additional functions to suit a variety of needs, thereby expanding on base R. 

**Importing your data**  

R comes with built in data sets, the list of which you can see by running `data()` in the Console (go ahead, try it!
You can do this by typing `data()` in the Console window and hitting Enter.) 
You may be familiar with some of the data sets, such as `mtcars` or `iris`, which often get used in vignettes and other various examples. 
Using built-in data sets are a great way to work with R code using a data set that "just works."   

Think of any data science project as consisting of data and code. 
We use code to manipulate data, which means that when we are troubleshooting we need to think about whether or not our code is the source of the error, if our data is the source of the error, or if the error comes from the interaction of the code with the data.  

For this chapter we'll be using data from the Massachusetts Public School System that was originally downloaded from Kaggle on October 23, 2019. 
You can access the data from within the `dataedu` package, or [download the data from Kaggle]().

Save your data to the `data --> raw` folder, make a copy of your data, and put the new copy into the `data --> for_use` folder. 

When working with downloaded data (in other words, data files, as opposed to pulling your data directly into R through an API, database connection, or webscraping) it's good practice to keep the initial copy of your data in a folder and to never open that data, _especially if that data is in an `.xls* or .csv` format!_ 
Excel has an overly aggressive way of trying to be helpful with your data, and when you open a file you may find that [your numeric values have been converted to dates](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-016-1044-7). 
At best you need to re-download the file, and at worst you've made a significant amount of work for yourself.    

## Code for Foundational Skills

The following code comprises all of the code that we'll use in this chapter. 
We present it here in its entirety, and then break it down into chunks in order to explain what's happening.  

This code may resemble the start of an analytical workflow, but does not walk you through a complete analysis. 
Instead, the code chosen below is used to highlight key features and foundational skills that comprise the interaction of packages and functions with data.
We recommend the text [R for Data Science]("https://r4ds.had.co.nz/") for those looking for a more in-depth look into completing an analytical workflow in R.   

We do not recommend running the following block of code all at once! 
It intentionally contains errors that will prevent it from running in its entirety. 
Instead we recommend creating a new `.R` script and adding chunks of code as we discuss them in the book, running each chunk of code as we go along in order to better see what is happening in a given line of code.   

_Note: when we talk about a script, we're referring to an `.R` file that is created using File --> New File --> R script, and **not** to code that you're running in the Console._


```r
# Installing the packages used in this walkthrough

# install.packages("tidyverse")
# install.packages("janitor")
# install.packages("skimr")
# install.packages("here")

# Setting up your environment
library(tidyverse)
library(janitor)
library(skimr)
library(here)

# Importing data
read_csv(here("zz_jesse_practice_scripts/data/for_use", 
              "MA_Public_Schools_2017.csv"))  # change path once finalized in book

read_csv(here("zz_jesse_practice_scripts/data/for_use", 
              "MA_Public_Schools_2017.csv")) -> my_data

ma_data_init <- read_csv(here("zz_jesse_practice_scripts/data/for_use", 
                              "MA_Public_Schools_2017.csv"))

# Exploring and manipulating your data
names(ma_data_init)

glimpse(ma_dat_init)  
glimpse(ma_data_init)
summary(ma_data_init)

glimpse(ma_data_init$Town)
summary(ma_data_init$Town)

glimpse(ma_data_init$`AP_Test Takers`)
glimpse(ma_data_init$`AP_Test Takers`)
summary(ma_data_init$`AP_Test Takers`)

ma_data_init %>% 
    group_by(`District Name`) %>%  
    count()

ma_data_init %>% 
    group_by(`District Name`) %>% 
    count()  
    
ma_data_init %>% 
    group_by(`District Name`) %>% 
    count() %>% 
    filter(n > 10)

# ma_data_init %>% 
#     group_by(`District Name`) %>% 
#     count() %>% 
#     filter(n > 10) %>% 
#     arrange(desc(n)

ma_data_init %>%
    group_by(`District Name`) %>%
    count() %>%
    filter(n > 10) %>%
    arrange(desc(n))

ma_data_init %>%
    group_by(`District Name`) %>%
    count() %>%
    filter(n = 10) %>%
    arrange(desc(n))

ma_data_init %>%
    group_by(`District Name`) %>%
    count() %>%
    filter(n == 10) %>%
    arrange(desc(n))

ma_data_init %>% 
    rename(district_name = `District Name`,
           grade = Grade) %>% 
    select(district_name, grade)

ma_data %>% 
    clean_names()

01_ma_data <- ma_data_init %>%  #' intentional error
    clean_names()

$_ma_data <- ma_data_init %>%  #' intentional error
    clean_names()

ma_data_01 <- ma_data_init %>% 
    clean_names()
```

## Packages and Functions

**From the outside in**  
Packages are a collection of functions, and most packages are designed for: a specific data set, a specific field, and/or a specific set of tasks. 
Functions are individual components within a package, and functions are what we use to interact with our data.  

**From the inside out**  
To put it another way, an R user might write a series of functions that they find themselves needing to use repeatedly in a variety of projects. 
Instead of re-writing (or copying and pasting) the functions each time they need to use them, an R user can collect all of these individual functions inside a package. 
The R user can then load the package any time that they want to use the functions, using a single line of code instead of tens to tens of thousands of lines of code for each function.  

If an R user feels that their package would be of benefit to a broad audience, they may choose to submit their package to [CRAN](https://cran.r-project.org/), the **C**omprehensive **R** **A**rchive **N**etwork.
Most of the packages we'll be working with in this book are available on CRAN, which means that we can install them using the `install.packages()` function, as we did above.  

The process of submitting a package and having it published through CRAN is beyond the scope of this book, and it's important to point out that you - yes, you! - can create a package that you use all for yourself, share with colleagues, or submit to CRAN. 
Packages do not need to be submit to CRAN to be used by the public, and many packages are available directly from their respective developers via GitHub.  

[image]

**The Tidyverse, a package of packages**
The `tidyverse` is a single package that contains additional packages, and within each of those individual packages are a set of functions. 
The `tidyverse` is an excellent tool that has a cohesive syntax across all functions, and the packages allow you do to the bulk of an analytical workflow. 
As of this writing, the `tidyverse` is the only known package of packages.  

[image]

## Installing and loading a package

*Installing a package*
If you read Chapter 05, you might have noticed at the very end that we both installed and loaded packages, but didn't talk too much about what we were doing. 
We'll get into more detail on installing and loading packages now!

While it is entirely possible to do all of your work in R without ever using a package, we do not recommend that approach due to the wealth of packages available that help reduce both the learning curve associated with R, as well as the amount of time spent on any given analytical project.  

In order to access the functions within a package, you must first install the package on your computer. 
If the package is on CRAN we can install it by running the following code:  


```r
# template for installing a package
install.packages("package_name")

# example of installing a package
install.packages("dplyr")
```

You can also navigate to the Packages pane, and then click "Install", which will work the same as the line of code above. 

[IMG of packages pane]

This is a way to install a package using code or part of the RStudio interface. 
Usually writing code is a bit quicker, but using the interface can be very useful and complimentary to use of code. 

*Loading a package*
Once a package is installed on your computer you do not have to re-install it in order to use the functions in the package, however you need to give R instructions telling it where to look for the functions in order to access the functions in the package.

If you know that you'll be using a package's functions multiple times in an R script (a file ending in `.R`), you can load the package into your R environment using `library()`.
Loading a package into our R enviroment signals to R that we would like to use any of the functions available to us in that package.

We load a package using the following code:  


```r
# template for loading a package
library(package_name)  

# example of loading a package
library(dplyr)
```

We only have to install a package once, but to use it, we have to load it each time we start a new R session.

> A package is a like a book, a library is like a library; you use library() to check a package out of the library.
> - Hadley Wickham, Chief Scientist, RStudio

Sometimes you'll see `require()` instead of `library()`. 
We strongly advocate for the use of `library()`, as it forces R to load the package, and if the package is not installed or there are issues with the package, will give you an error message. 
`require()` on the other hand will not give an error if the package is not available or if there are issues with the package. 
Using `library()` will help to eliminate sources of confusion later on.  

### Recognizing a function
Functions in R can be spotted by a word followed by a set of parentheses, like so: `word()`

The word (or set of words) represent the name of the function, and the parentheses are where we can provide arguments to a function, if arguments are needed for the function to run. 
Many functions in R packages do not _require_ arguments, and will use a set of default arguments unless you provide something different from the default.
You can see what the available arguments are for a given function by using the help documentation.

What are the arguments for `library()`?

### Running code in R  
In order to run code in R you need to type your code either in the Console or within an `.R` (or `.Rmd`) script. 
For the purposes of this chapter we recommend creating an `.R` script to type all of your code because you can add comments and then save your `.R` script for reference, whereas anything that you type in the Console will disappear as soon as you restart or close R.  

To run code in the Console, you type your code and hit 'Enter'.  

To run code in an R script, you can run a single line by highlighting it (or placing your cursor at the end of the line) and hitting `Ctrl` + `Enter`.  

You can also run your code by highlighting it and clicking the `Run` button.

[image]

### Run this code
Take a few minutes to type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line.  


```r
# Installing packages
install.packages("tidyverse")
install.packages("janitor")
install.packages("skimr")
install.packages("here")

# Setting up your environment
library(tidyverse)
library(janitor)
library(skimr)
library(here)
```

Based on what we've covered so far in this chapter, what did running the above lines of code accomplish?
How do you know?

### Function conflicts between packages
In your Console you may have noticed the following message: 

[IMG on tidyverse conflicts] 

This isn't error, but rather some important information that we need to consider!
When we first open R (via RStudio) we are working with base R -- that is, everything that comes with R along with a (relative) handful of pre-installed packages. 
These are packages and functions that exist in R that we have access to without needing to first load the package using `library()`. 

If you would like to see what functions are available to you in base R, you can run `library(help = "base")` in the Console.

If you would like to see the packages that came pre-installed with R, you can run `installed.packages()[ installed.packages()[,"Priority"] %in% "base", c("Package", "Priority")]` in the Console.

Additionally, if you would like to see a list of _all_ of the packages that have been installed (both pre-installed with base R as well as those that you have installed), you can run `rownames(installed.packages())` in the Console.

However because of the broad array of packages that have been created for use in R, it's not uncommon for two (or more!) packages to have functions with the same name.
What this message is telling us then is that if we use the `filter()` function, R will use the `filter()` function from the `dplyr` package (a package within the `tidyverse`) rather than the `filter()` function from within the `stats()` package (one of the packages that accompanies base R). 

How can we use the Help documentation to explore how the two functions might differ?

R will give precedence the most recently loaded package.
What happens if we want to use the `filter()` function from the `stats` package _and_ the `filter()` function from the `dplyr` package in the same R session? 
One solution would be to reload the library you want to use each time you want to change the package you're using the `filter()` function from.
But this can be tricky for several reasons: 
- It's best practice to keep your `library()` calls at the very top of your R script, so re-loading a package using `library()` throughout your script can clutter things and cause you headaches down the road
- If you scroll to the top of your script and reload the packages as you need them, it can be difficult to keep track of which one you recently loaded.

Instead there's an easier way to handle this kind of problem.
When we have conflicting function names from different packages we can tell R which package we'd like to pull a function from by using `::`.
Using the example of the `filter()` function above, coupled with the examples in the Help documentation, we can specify which package to pull the `filter()` function using `::`, as outlined below: 

_Note: we haven't covered what any of this code does yet, but see what you can learn from running the code and using the Help documentation!_


```r
# using the filter() function from the stats package
x <- 1:100
stats::filter(x, rep(1, 3))

# using the filter() function from the dplyr package
starwars %>% 
    dplyr::filter(mass > 85)
```

### How to find a package
As you begin your R learning journey, the bulk of the packages that you will need to use are either already included when you install R, or available on CRAN. 
[CRAN TaskViews](link) is one of the best resources for seeing what packages are available and might be relevant to your work.
Other great resources to learn about various R packages are through Twitter (following the #rstats hashtag) as well as through Google searches.
As R has grown in popularity, Google has gotten significantly better at returning R-related results.

### How to learn more about a package
Sometimes when you look up a package, you're able to pull the function that you need and continue on your way.
Other times you may need (or want!) to learn more about a specific package. 
Packages on CRAN all come with something called a "vignette," which is a worked example using various functions from within the package. 
You can access a package's vignette(s) on CRAN TaskViews:

[IMG]

Package authors may also publish vignettes or blog posts about their package, and other R users may _also_ publish tutorials about a specific package.
You may also find yourself on GitHub looking at information for a package - more often than not the README file will have good information for getting started with a package.

### Commenting in R
It is considered good practice to comment your code when working in an `.R` script. 
Even if you are the only person to ever work on your code, it can be helpful to write yourself notes about what you were trying to do with a specific piece of code. Comments in R are how we accomplish that!
Comments are ignored by R when running a script, so they will not affect your code or analysis. 
To comment out a line of code, you can place a pound sign (`#`) in front of the line of code.
If you think you'll be writing more than one line of code, you can do a pound sign followed by a single quotation mark (`#'`). 
This will continue to comment out lines of text or code each time you hit "Enter."
You can delete the `#'` on a new line where you want to write code for R to run.

You can also use `#` to comment out lines of code.
Be careful when doing this, especially in longer files, as it can be easy to forget where you've commented out code. 
It is often better to simply start a new section of code to tinker with until you get it working as expected, rather than commenting out lines of code.

_Note: when we refer to "commenting" we're referring to adding in actual text comments, whereas "commenting out" refers to using the pound sign in front of a line of code so that R ignores it._
_We will also use the phrase "uncomment code," which means you should delete (or omit when typing out) the `#` or `#'` sign in an example._

## Using functions to import data

### Run this code
Take a few minutes to type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line. 

_Note: although we provide all of the data sets used in this book in the `dataedu` package, we would strongly suggest [downloading the dataset from Kaggle](link) so that we can show you the true power of Projects in R._

```r
read_csv(here("data/foundational_skills/for_use", 
              "MA_Public_Schools_2017.csv"))  # change path once finalized in book

read_csv(here("data/foundational_skills/for_use", 
              "MA_Public_Schools_2017.csv")) -> my_data

ma_data_init <- read_csv(here("data/foundational_skills/for_use", 
                              "MA_Public_Schools_2017.csv"))
```

Each of the three code examples above look slightly different, but two of them do almost the exact same thing.
The first example provided loads the data into our R environment, but not in a format that's immediately useful to us.
The second and third examples read in the data and assign it to a variable,`my_data` and `ma_data_init` respectively.
In our Environment pane we can see how each of the data types has been brought into R, and even click on the table icon to get an interactive table
(The data set is rather large, so RStudio may lag as you open the table and manipulate it.)

[IMG of Environment pane]

### The assignment operator
The second and third examples in the code chunk above are how you'll most commonly see things in R being saved to a variable.
When we save something to a variable, we do so using what's called an "assignment operator," which in R is either a left- or right-facing arrow (`<-` or `->`).
Writing the name of your variable followed by a left-facing arrow is currently the most common convention used in R, but it is also perfectly acceptable to use the right-facing arrow.

Intuitively the right-facing arrow may make more sense for those of us who work predemoninantly in languages that read left to right, as what we're essentially saying is "take this entire chunk of code and save it to this variable name." 
Regardless of which option you choose, both are different means to the same end.

### The `here` package 
We've talked about what Projects are and why you should use them, but what really makes Projects in RStudio shine is the use of the `here()` function from the `here` package.
What `here()` does is eliminate the need for you to do what's called "hard-coding" your file path. 
For example, if we had loaded the data using the file path on one of our individual computers, it would be difficult for someone to open our folders on _their_ computer and re-run the analysis because they do not have the same file structure.
What `here()` does is tell R that the file structure starts at the Project-level, and so every subsequent call starts at the Project-level, and allows you to navigate throughout each of the folders and files within a given Project.

### Data types
There are different types of data within R. 
When you loaded the Massachusetts Public Schools data from 2017, you likely saw a series of messages like this:

[IMG of import message]

This message is telling you how R decided to "code" each column, as you can only have one data type per column in R.
We can see that the default is to code everything as a double (a number) where it says `.default = col_double().
Where columns were coded as something _other_ than double, we see `col_character()` (text that has at least one non-numeric character), `col_number()` (for our purposes a number, and analogous to `col_double()`), and `col_logical()` (TRUE or FALSE). 

When `read_csv()` reads through the first 1,000 rows of data, it uses what it encounters to make a best guess as to what type of data is in the column.
If R sees 990 rows of numbers, but 10 rows of numbers mixed with letters, R will _coerce_ the data in the column into character data. 
This means that `193` and `192A` are both seen as _text_.
One of the (many) implications of this is that you can no longer do mathematical operations on `193` when it's been coerced into a character string. 

Not all is lost! 
There are methods for safely coercing your data into the correct format, and we'll cover a handful throughout this text. 
If you're looking for more in-depth information on data types and coercion rules, we recommend both [Hands on Programming With R](https://rstudio-education.github.io/hopr/) and [Advanced R](https://adv-r.hadley.nz/).

## Reading code and writing functions
### Run this code
Take a few minutes to type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line.
If you'd like, practice commenting your code by noting what you see happening with each line of code that you run.

_Note: we have intentionally included errors in this chapter to help highlight concepts as well as introduce you to error messages early on!_


```r
# Exploring and manipulating your data
names(ma_data_init)

glimpse(ma_dat_init) 
glimpse(ma_data_init)
summary(ma_data_init)

glimpse(ma_data_init$Town)
summary(ma_data_init$Town)

glimpse(ma_data_init$AP_Test Takers)
glimpse(ma_data_init$`AP_Test Takers`)
summary(ma_data_init$`AP_Test Takers`)
```

What differences do you see between each line of code?
What changes in the output to the Console with each line of code that you run?

### Common errors
There were two lines of code that resulted in errors, and both were due to one of the most common sources of error in programming - typos!
The first was `glimpse(ma_dat_init)`. 
This might be a tricky error to spot, because at first glance it might seem like nothing is wrong!
However we've left off the "a" in "data," which has caused problems with R.

R will do exactly as you tell it to do.
This means if you want to run a function on a data set, R will only run the function on the data sets that are available in its environment.
Looking at our Environment pane we can see that there is no data set called `ma_dat_init`, which is what R is trying to tell us with its error message of `Error in glimpse(ma_dat_init) : object 'ma_dat_init' not found`. 

The second error was with `glimpse(ma_data_init$AP_Test Takers)`.
What do you think the error is here? 

R is unhappy with the space in the file name, and doesn't know how to read the code. 
To get around this there are a couple of things we can do.
First, we could make sure that data column names never have spaces in them.
This is unlikely to be within our control, so a second option would be to use R to convert the column names upon import, before we start doing any exploration. 
Another method for dealing with it is to leave the column names as they are, but to use single backticks `` `` to surround the column header with spaces in it.

_Note: the single backtick key is usually in the top-left of your keyboard. It's common to try and use a set of single quotation marks `' '` instead of the actual backticks `` ``!_

### The `$` operator
There are many ways to isolate and explore a single variable within your data set.
In this set of examples we used the `$` symbol.
The pattern for using the `$` symbol is `name_of_dataset$variable_in_dataset`.
It's important that the spelling, punctuation, and capitalization that you use in your code match what's in your data set, otherwise R will tell you that it can't find anything! 

## The pipe operator
The pipe operator `%>%` tends to throw R learners for a loop, until all of a sudden something clicks for them and they decide that they either love it or hate it.
We use the pipe operator throughout this text because we also heavily rely on use of the Tidyverse. 

_Note: As you progress in your R learning journey you will likely find that you need to move well beyond the Tidyverse for accomplishing your analytical goals - and that's OK!_
_We like the Tidyverse for teaching and learning because it relies on the same syntax across packages, so as you learn how to use functions within one package, you're learning the syntax for functions in other Tidyverse packages._  

It's worth taking a few moments to talk about the pipe operator and its package.
The pipe operator first appeared in the `magrittr` package, and is a play on a famous painting by the artist Magritte, who painted The Treachery of Images.
In these images he would paint an object, such as a pipe, and accompany it with the text "Ceci n'est pas une pipe," which is French for "This is not a pipe." 

[IMG of Magritte painting] 

At the risk of spoiling a joke by over-explaining it, it's common in the R programming world to name a package by choosing a word that represents what the package does (or what the package is for) and either capitalizing the letter R if it appears in the package name, or adding an R to the end of the package (`dplyr`, `tidyr`, `stringr`, and even `purrr`).

### Run this code
Take a few minutes to type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line. 

```r
ma_data_init %>% 
    group_by(District Name) %>%  
    count()

ma_data_init %>% 
    group_by(`District Name`) %>% 
    count()  
    
ma_data_init %>% 
    group_by(`District Name`) %>% 
    count() %>% 
    filter(n > 10)

# ma_data_init %>% 
#     group_by(`District Name`) %>% 
#     count() %>% 
#     filter(n > 10) %>% 
#     arrange(desc(n)
```

### Piping practices 
The `magrittr` package
`dplyr` and package dependencies 
"Correct" pipe length (careful - will need to stick to this throughout text)

### Closing your parentheses
Seeing the `+` sign in the Console
Fixing it by pressing `Esc`

## Functions and equality
### Run this code 
Take a few minutes to read through the code before typing or running anything in R.
Try to guess what is happening in each code chunk by writing out a sentence for each line of code so that you have a small paragraph for each chunk of code.
Once you've done that, type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line. 

```r
ma_data_init %>%
    group_by(`District Name`) %>%
    count() %>%
    filter(n > 10) %>%
    arrange(desc(n))

ma_data_init %>%
    group_by(`District Name`) %>%
    count() %>%
    filter(n = 10) 

ma_data_init %>%
    group_by(`District Name`) %>%
    count() %>%
    filter(n == 10) 

ma_data_init %>% 
    rename(district_name = `District Name`,
           grade = Grade) %>% 
    select(district_name, grade)
```

### "Reading" code
When you encounter new-to-you code, it's helpful to pause and read through the code to see if you can come up with a hypothesis as to what the code is trying to accomplish.
Doing this will help you not only understand code a bit better, but also help you spot errors more quickly when the code doesn't do what you thought it was going to do. 

The way that we would read the first chunk of code is:

> Take the `ma_data_init` data set _and then_ **group** it **by** `District Name` _and then_ **count** (the number of schools in a district) _and then_ **filter** for Districts with more than 10 schools _and then_ **arrange** the list of Districts and the number of schools in each District in descending order, based on the number of schools.

That's a mouthful! 
But there are a couple of consistent points to make regarding this paragraph.
Every time we see the pipe, we say "and then." 
This is because we're starting with our data set, `ma_data_init`, _and then_ doing one thing after another to it.
Because we're using the pipe operator between each function, R knows that all of our functions are being applied to the `ma_data_init` data set.
We do not need to call or refer to the `ma_data_init` data set each time.

When we link together functions using the pipe operator in this manner, we often refer to it as "chaining together functions."

### Verb-based functions
Another pattern you may have picked up on is that every function is a verb.
That is, the name of the function is telling us what the function is going to do!
This is common both within the Tidyverse as well as in other packages.

### When functions need arguments and when they don't
You also may have noticed that some of our functions needed arguments, that is, some kind of additional information provided inside the parentheses.
There are not any hard and fast rules about when a function needs an argument (or series of arguments), however if you are having trouble running your code, first check for typos, then check the help documentation to see if you can provide arguments to more clearly direct R as to what to do.

### Functions within functions
One of the (many!) cool things about R is that we can nest our functions.
When we nest our functions, R will read the functions from the innermost function to the outermost.
We saw this both in the section of code above that used `arrange(desc(n))`, as well as when we imported data using `read_csv(here())`. 

### The difference between `=` and `==` 
We talked earlier about using a left- or right-facing arrow to assign values or code to a variable, but we could also use an equals sign (`=`) to accomplish the same thing.
When R encounters an equal sign (`=`) it is almost always looking to create an object by assigning a value to a variable.
So when we saw `filter(n = 10)`, R didn't understand why we were trying to filter something we were naming, and told us so with an error message.

When we are looking to determine whether or not values are equal, we use a double equals sign (`==`), as we did in `filter(n == 10)`. 
When R sees a double equals sign (`==`) it is evaluating whether or not the value on the left is equivalent to the value on the right. 

### Writing your own functions
As you work in R more and more, you may find yourself copying and pasting the same lines of code, and then making small modifications. 
This is perfectly fine while you're learning, but eventually you're going to come across a large enough dataset that's going to take you a couple hours to type out by hand (and increase the opportunity to introduce errors!).
This is when you _know_ you need to write a function.
_(We could argue that you need functions **much** sooner! For example, a general premise in programming is DRY, or **D**on't **R**epeat **Y**ourself._
_What this translates to is the idea that once you find yourself copying and pasting code for the third time, it's time to write a function!)_

Functions are reusable pieces of code that you can write and use over and over again. 
You might write a function for a specific script, or you might find yourself using a function across multiple scripts (at which point you might want to consider creating a package!) 

We'll cover the very basics of writing a function, but would strongly suggest you check out [RESOURCE ONE](link) and [RESOURCE TWO](link) for more information and practice. 

The template for writing a function is: 


```r
name_of_function <- function(argument_1, argument_2, argument_n){
    code_that_does_something
    code_that_does_something_else
}
```

Functions can be as simple or as complex as you would like.
For example, if we wanted to create a function that adds two numbers together, we would write: 


```r
# writing our function
# we've named the function "addition"
# and asked for two arguments, "number_1" and "number_2"
addition <- function(number_1, number_2) {
    number_1 + number_2
}

# using our function
# note that we provide each argument separated by commas
addition(number_1 = 3, number_2 = 1)
```

```
## [1] 4
```

```r
addition(0.921, 12.01)
```

```
## [1] 12.931
```

```r
addition(62, 34)
```

```
## [1] 96
```

What happens if we only provide one argument?
What happens if we provide more than two arguments?

You'll encounter several (more advanced) functions that we'll write together in various walkthroughs in this book!

## Basics of names
Naming things is important! 
The more you use R the more you'll develop your own sense of how you prefer to name things, either as an organization or an individual programmer. 
But there are some hard and fast rules that R has about naming things, and we'll cover them in this section. 

### Run this code
Take a few minutes to type out and run each of the following lines of code, one by one, and notice what you see happening in the Console after you run each line. 

```r
ma_data %>% 
    clean_names()

01_ma_data <- ma_data_init %>%  
    clean_names()

$_ma_data <- ma_data_init %>%  
    clean_names()

ma_data_01 <- ma_data_init %>% 
    clean_names()
```

As you saw in the above examples, R doesn't like it when you create a name that starts with a number or symbol.
In addition, R is going to squawk when you give it a name with a space in it.

## Conclusion
It would be impossible for us to cover _everything_ you can do in a single chapter of a book, but it is our hope that this chapter gives you a strong foundation from which to explore both subsequent chapters as well as additional R resources. 
In this chapter we've covered the concepts of data, Projects, packages, and functions, and also walked through foundational ideas, concepts, and skills related to doing data science in R. 


### STILL NEED TO INCORPORATE THE FOLLOWING ###
-- import from 05A: plug in as needed

### Track Two: Welcome to the Tidyverse

The `tidyverse` is a set of packages for data manipulation, exploration, and visualization using the design philosophy of 'tidy' data. 
Tidy data has a specific structure: each variable is a column, each observation is a row, and each type of observational unit is a table.

The packages contained in the `tidyverse` provide useful functions that augment base R functionality.

You can installing and load the complete `tidyverse` with:


```r
install.packages("tidyverse")
```


```r
library(tidyverse)
```

**For more information on tidy data, check out [Hadley Wickhams's Tidy Data paper](http://vita.had.co.nz/papers/tidy-data.html).**

## Include at end of chapter!
## Loading Data from Excel, SAV, and Google Sheets

### Loading Excel Files

We will now do the same with an Excel file. 
You might be thinking that you can open the file in Excel and then save it as a `.csv`. 
This is generally a good idea. 
At the same time, sometimes you may need to directly read a file from Excel. 
Note that, when possible, we recommend the use of `.csv` files. 
They work well across platforms and software (i.e., even if you need to load the file with some other software, such as Python).

The package for loading Excel files, `readxl`, is not a part of the tidyverse, so we will have to install it first (remember, we only need to do this once), and then load it using `library(readxl)`. Note that the command to install `readxl` is grayed-out below: The `#` symbol before `install.packages("readxl")` indicates that this line should be treated as a comment and not actually run, like the lines of code that are not grayed-out. It is here just as a reminder that the package needs to be installed if it is not already.

Once we have installed readxl, we have to load it (just like tidyverse):


```r
install.packages("readxl")
```


```r
library(readxl)
```

We can then use the function `read_excel()` in the same way as `read_csv()`, where "path/to/file.xlsx" is where an Excel file you want to load is located (note that this code is not run here):


```r
my_data <-
    read_excel("path/to/file.xlsx")
```

Of course, were this run, you can replace `my_data` with a name you like. Generally, it's best to use short and easy-to-type names for data as you will be typing and using it a lot. 

Note that one easy way to find the path to a file is to use the "Import Dataset" menu. It is in the Environment window of RStudio. Click on that menu bar option, select the option corresponding to the type of file you are trying to load (e.g., "From Excel"), and then click The "Browse" button beside the File/URL field. Once you click on the, RStudio will automatically generate the file path - and the code to read the file, too - for you. You can copy this code or click Import to load the data.

### Loading SAV Files

The same factors that apply to reading Excel files apply to reading `SAV` files (from SPSS). NOte that you can also read `.csv` file directly into SPSS and so because of this and the benefits of using CSVs (they are simple files that work across platforms and software), we recommend using CSVs when possible. First, install the package `haven`, load it, and the use the function `read_sav()`:


```r
install.packages("haven")
```


```r
library(haven)
my_data <-
    read_sav("path/to/file.xlsx")
```

### Google Sheets

Finally, it can sometimes be useful to load a file directly from Google Sheets, and this can be done using the Google Sheets package.


```r
install.packages("googlesheets")
```


```r
library(googlesheets)
```

When you run the command below, a link to authenticate with your Google account will open in your browser. 


```r
my_sheets <- gs_ls()
```

You can then simply use the `gs_title()` function in conjunction with the `gs_read()` function:


```r
df <- gs_title('title')
df <- gs_read(df)
```


This section goes into depth on loading various types of data sources.

In this section, we'll load data.

You might be thinking that an Excel file is the first that we would load, but there happens to be a format which you can open and edit in Excel that is even easier to use between Excel and R as well as SPSS and other statistical software, like MPlus, and even other programming languages, like Python. That format is `.csv`, or a comma-separated-values file. 

The `.csv` file is useful because you can open it with Excel and save Excel files as `.csv` files. 
Additionally, and as its name indicates, a `.csv` file is rows of a spreadsheet with the columns separated by commas, so you can view it in a text editor, like TextEdit for Macintosh, as well. 
Not surprisingly, Google Sheets easily converts `.csv` files into a Sheet, and also easily saves Sheets as `.csv` files. 
However we would be remiss if we didn't point out that there is a package, `googlesheets`, which can be used to read a Google Sheet directly into R.

For these reasons, we start with - and emphasize - reading `.csv` files. 

### Saving a File from the Web

You'll need to copy this URL:

`https://goo.gl/bUeMhV`

Here's what it resolves to (it's a `.csv` file):

`https://raw.githubusercontent.com/data-edu/data-science-in-education/master/data/pisaUSA15/stu-quest.csv`

This next chunk of code downloads the file to your working directory. 
Run this to download it so in the next step you can read it into R. 
As a note: There are ways to read the file directory (from the web) into R. 
Also, of course, you could do what the next (two) lines of code do manually: Feel free to open the file in your browser and to save it to your computer (you should be able to 'right' or 'control' click the page to save it as a text file with a `.csv` extension).


```r
student_responses_url <-
    "https://goo.gl/bUeMhV"

student_responses_file_name <-
    paste0(getwd(), "/data/student-responses-data.csv")

download.file(
    url = student_responses_url,
    destfile = student_responses_file_name)
```

It may take a few seconds to download as it's around 20 MB.

The process above involves many core data science ideas and ideas from programming/coding. 
We will walk through them step-by-step.

1. The *character string* `"https://goo.gl/wPmujv"` is being saved to an *object* called `student_responses_url`.


```r
student_responses_url <-
    "https://goo.gl/bUeMhV"
```

2. We concatenate your working directory file path to the desired file name for the `.csv` using a *function* called `paste0`. 
This is stored in another *object* called `student_reponses_file_name`. 
This creates a file name with a *file path* in your working directory and it saves the file in the folder that you are working in. 


```r
student_responses_file_name <-
    paste0(getwd(), "/data/student-responses-data.csv")
```

3. The `student_responses_url` *object* is passed to the `url` argument of the *function* called `download.file()` along with `student_responses_file_name`, which is passed to the `destfile` argument.

In short, the `download.file()` function needs to know
- where the file is coming from (which you tell it through the `url`) argument and
- where the file will be saved (which you tell it through the `destfile` argument).


```r
download.file(
    url = student_responses_url,
    destfile = student_responses_file_name)
```

Understanding how R is working in these terms can be helpful for troubleshooting and reaching out for help. 
It also helps you to use functions that you have never used before because you are familiar with how some functions work.

Now, in RStudio, you should see the downloaded file in the Files tab. 
This should be the case if you created a project with RStudio; if not, it should be whatever your working directory is set to. 
If the file is there, great. 
If things are *not* working, consider downloading the file in the manual way and then move it into the directory that the R Project you created it. 

### Loading a `.csv` File

Okay, we're ready to go. 
The easiest way to read a `.csv` file is with the function `read_csv()` from the package `readr`, which is contained within the Tidyverse.

Let's load the tidyverse library:


```r
library(tidyverse) # so tidyverse packages can be used for analysis
```

You may have noticed the hash symbol after the code that says `library(tidyverse`)`. 
It reads `# so tidyverse packages can be used for analysis`. 
That is a comment and the code after it (but not before it) is not run (the code before it runs just like normal). 
Comments are useful for showing *why* a line of code does what it does. 

After loading the tidyverse packages, we can now load a file. 
We are going to call the data `student_responses`:


```r
# readr::write_csv(pisaUSA15::stu_quest, here::here("data", "pisaUSA15", "stu_quest.csv"))
student_responses <-
    read_csv("./data/student-responses-data.csv")
```

```
## Parsed with column specification:
## cols(
##   .default = col_double(),
##   CNT = col_character(),
##   CYC = col_character(),
##   NatCen = col_character(),
##   STRATUM = col_character(),
##   Option_Read = col_character(),
##   Option_Math = col_character(),
##   ST011D17TA = col_character(),
##   ST011D18TA = col_character(),
##   ST011D19TA = col_character(),
##   ST124Q01TA = col_logical(),
##   IC001Q01TA = col_logical(),
##   IC001Q02TA = col_logical(),
##   IC001Q03TA = col_logical(),
##   IC001Q04TA = col_logical(),
##   IC001Q05TA = col_logical(),
##   IC001Q06TA = col_logical(),
##   IC001Q07TA = col_logical(),
##   IC001Q08TA = col_logical(),
##   IC001Q09TA = col_logical(),
##   IC001Q10TA = col_logical()
##   # ... with 420 more columns
## )
```

```
## See spec(...) for full column specifications.
```

Since we loaded the data, we now want to look at it. 
We can type its name in the function `glimpse()` to print some information on the dataset (this code is not run here).


```r
glimpse(student_responses)
```

Woah, that's a big data frame (with a lot of variables with confusing names, to boot)!

Great job loading a file and printing it! 
We are now well on our way to carrying out analysis of our data.


### Saving Files

Using our data frame `student_responses`, we can save it as a `.csv` (for example) with the following function. The first argument, `student_reponses`, is the name of the object that you want to save. The second argument, `student-responses.csv`, what you want to call the saved dataset.


```r
write_csv(student_responses, "student-responses.csv")
```

That will save a `.csv` file entitled `student-responses.csv` in the working directory. If you want to save it to another directory, simply add the file path to the file, i.e. `path/to/student-responses.csv`. To save a file for SPSS, load the haven package and use `write_sav()`. There is not a function to save an Excel file, but you can save as a `.csv` and directly load it in Excel.

### Conclusion

We will detail the functions used to read every file in a folder (or, to write files to a folder).

## Processing Data

Now that we have loaded `student_responses` into an object, we can process it. This section highlights some common data processing functions. 

We're also going to introduce a powerful, unusual *operator* in R, the pipe. The pipe is this symbol: `%>%`. It lets you *compose* functions. It does this by passing the output of one function to the next. A handy shortcut for writing out `%>%` is Command + Shift + M.

Here's an example. Let's say that we want to select a few variables from the `student_responses` dataset and save those variables into a new object, `student_mot_vars`. Here's how we would do that using `dplyr::select()`.


```r
student_mot_vars <- # save object student_mot_vars by...
    student_responses %>% # using dataframe student_responses
    select(SCIEEFF, JOYSCIE, INTBRSCI, EPIST, INSTSCIE) # and selecting only these five variables
```

Note that we saved the output from the `select()` function to `student_mot_vars` but we could also save it back to `student_responses`, which would simply overwrite the original data frame (the following code is not run here):


```r
student_responses <- # save object student_responses by...
    student_responses %>% # using dataframe student_responses
    select(student_responses, SCIEEFF, JOYSCIE, INTBRSCI, EPIST, INSTSCIE) # and selecting only these five variables
```

We can also rename the variables at the same time we select them. I put these on separate lines so I could add the comment, but you could do this all in the same line, too. It does not make a difference in terms of how `select()` will work.


```r
student_mot_vars <- # save object student_mot_vars by...
    student_responses %>% # using dataframe student_responses
    select(student_efficacy = SCIEEFF, # selecting variable SCIEEFF and renaming to student_efficiency
           student_joy = JOYSCIE, # selecting variable JOYSCIE and renaming to student_joy
           student_broad_interest = INTBRSCI, # selecting variable INTBRSCI and renaming to student_broad_interest
           student_epistemic_beliefs = EPIST, # selecting variable EPIST and renaming to student_epistemic_beliefs
           student_instrumental_motivation = INSTSCIE # selecting variable INSTSCIE and renaming to student_instrumental_motivation
    )
```

[will add more on creating new variables, filtering grouping and summarizing, and joining data sets]

## Communicating / Sharing Results

R Markdown is a highly convenient way to communicate and share results. Navigate to "New File" and then "R Markdown". [add]

Then, click "Knit to PDF", "Knit to HTML", or "Knit to Word".

-- end of import



## May not need
**Grab your data**  
[Kaggle Massachusetts Public Schools Data](https://www.kaggle.com/ndalziel/massachusetts-public-schools-data/download)  

Comes as a .zip file (explain this?)

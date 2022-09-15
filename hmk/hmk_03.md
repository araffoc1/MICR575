Homework 3
================
Beatrice Caiado

Please download this template, fill it out, and submit it as homework.

# Data input/output

Use the tidyverse `read_csv()` function to read a .csv file of your own
data. If you don’t have any data of your own, make up an excel file with
fake data.

A few notes:

- In order to work with `read_csv()`, the first row of the spreadsheet
  should contain the names of the columns, and all other rows should
  contain data
- To export the data as a .csv, go to “save as” and select File Format
  “UTF-8 csv” or similar.
- Save the file in the same directory as your homework `.qmd` file.
- Quarto/knitr make a new R session when they run, and the home
  directory of that session is the directory that the file is saved in.
  So if your `.qmd` file is in `micr_595/hmk`, and you save the `.csv`
  file as `micr_595/hmk/my_data.csv`, you would load the file as
  `read_csv("my_data.csv")`.
- Sometimes R and Excel disagree on the end of a .csv file. If you get
  extra lines containing `NA`, don’t worry about it.

**We have to first assign the .csv file to an object so that the
computer knows what to name it.**

`sample_values <- read_csv("/hmk/test_dataset.csv")`

**From doing this, when we look into our global environment, we can see
that there is a sample_values data in there meaning it was created
successfully.**

# Investigating the properties of data frames

Use two different functions that both give some kind of summary or
overview of the data frame. Which one do you think is more useful?

- **You could use `summary()` or `str()` where str means structure. I
  personally think that the `summary()` function is much more
  informative. This is because the `summary()` function is more
  organized and easier to read. The `str()` function gives roughly the
  same information however it is not laid out as nice to read. It
  honestly might give a bit more information with examples, but it is
  more confusing to look at.**

# Manipulating data frames

Create a new column of your data frame by performing some kind of
arithmetic operation on an existing column.

- **I want to crate a new column that multiplies the values in a
  previous column by 100.**
- `sample_values$multiplied <- sample_values$x *100`

# Working on columns

Calculate the mean of a numeric column in your data frame.

- **I chose to calculate the mean of my y column.**
- `mean(sample_values$y)`

# Accessing elements of data frames

- [Challenge 3 from SC Data Structures
  lesson](https://swcarpentry.github.io/r-novice-gapminder/04-data-structures-part1/index.html#challenge-3):
  Show what each of the following returns, and explain what each line of
  code is doing:

  - `cats[1]` - coat 1. calico 2. black 3. tabby 4. calico - This code
    is returning listed numerically the coat colors. Using a single
    bracket with only one value tells it to select a column, in this
    case column one and it lists out the observations in column 1.

  - `cats[[1]]` - \[1\] “calico” “black” “tabby” “calico” - Double
    brackets will just give the observations in the told column, in this
    case it is column 1. Unlike using single brackets, it won’t what
    those observations are from, they don’t give element names.

  - `cats$coat` - \[1\] “calico” “black” “tabby” “calico” The dollar
    sign tells it to list out the observations in the column labeled
    coat.

  - `cats[1, 1]` - \[1\] “calico” This code gives the first observation
    of the first column which in coat the first observation is calico.

  - `cats[ , 1]` - \[1\] “calico” “black” “tabby” “calico” This code
    takes from all the rows, but only the first observation of each row
    which in this case are the coat types.

  - `cats[1, ]` - coat weight likes.string \[1\] calico 2.1 TRUE - This
    code uses all columns, but only the first observation from each
    column.

# Optional challenge

A data frame is an example of a list. I haven’t discussed how to access
elements of lists, but it is covered
[here](https://swcarpentry.github.io/r-novice-gapminder/04-data-structures-part1/index.html#lists)).

Explain in what ways accessing elements of lists are like accessing
columns of data frames, and given that, how it shows that data frames
are a type of list.

- **When you access the elements of a list, it is going to tell you
  everything in that list. When you access a column of a data frame, it
  will also read and list out the observations in that specified column.
  In a column, the observations are listed out individually like a list
  does.**

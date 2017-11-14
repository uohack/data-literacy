# Welcome

* Notes link - [bit.ly/2ms7Irp](https://github.com/uohack/data-literacy/blob/master/04-advanced-analysis/notes.md)
* Colaboratory sign up - https://colab.research.google.com
  * Open beta, takes a few hours for them to accept you
  * In the meantime you can still view example, but you can't make your own copy to play with

# Intro python

* High-level programming language
  * Easy to write/understand with some basic training
    * There are a ton of open-source tools that people have built for and in Python
    * These modules can be installed and utilized to perform nearly any task
    * Pandas is one example that we will be using today
  * [Learn more about Python](https://github.com/uohack/digital-media-boot-camp/blob/gh-pages/programming/01-programming-basics.md)
* Various ways to run python (work through each with print('this is x'))
  * Terminal (easy)
  * File (easy)
  * Jupyter Notebook (difficult) - [learn more](http://www.firstpythonnotebook.org/notebook/index.html)
  * Colaboratory (VERY easy)
    * Same as Jupyter but all hosted by Google
    * Virtual machine associated with your account
    * You use their computing power & easy to share
    * Dependent on their versioning (use Pandas 20.3 not current stable 21)
    * Of course this is on their servers so don't put anything personal in
* Using 
  * Print function - explain arguments
  * Math
  * Data types
  * Variables
  * Lists
    * Manipulating lists
  * Functions
    * print('Hello ' + name) example
  * Comments
* Pandas
  * Can read/write data in many formats
  * Good with tabular data (called Data Frames)
  * Handles missing data nicely
  * Handles datetime data nicely
  * It's FAST
  * Good [documentation](http://pandas.pydata.org/pandas-docs/stable/)
  * [Learn more](http://www.firstpythonnotebook.org/pandas/index.html)


# Example - [answer key](https://drive.google.com/file/d/1-lBJ0jjQzwos_iajen8Lstz1TNO3530y/view?usp=sharing)

* Import pandas as pd
  * This is just some developer shorthand
  * Makes it easier to call it
  * Must import or else you don't have access to it
* Import data
  * [bit.ly/2yXO5x1](https://raw.githubusercontent.com/uohack/data-literacy/master/04-advanced-analysis/citations.csv)
  * Pandas comes with handy read_csv function
  * Can also give you a quick snapshot
    * All data is an object - Pandas way to say its not a number, didn't automatically create datetime items
* Describe
  * Gives you a description of the data
  * Count tells us how many rows there are and that some are missing a time
  * Unique tells us how many unique items there are in each column
    * This is interesting because it tells us there are 429 locations (probably not super consistent) and only 15 fine amounts
  * Top gives us the most frequent in each column
    * Immediately see that the day with most tickets
    * Most common fine amount
    * Place you're most likely to get a ticket
    * Most common violation, makes sense with location
* Create new column for datetime
  *  Combine ISSUE DATE and ISSUE TIME
  * This allows us to do logic on the values
* Trim to just FY 15-16
  * `df = df.drop(df[<some boolean condition>].index)`
  * Then I chain them together to drop before and after in one line
  * Do describe() to double check
* value_counts()
  * This is what we're looking for
  * This is really the power of pandas
* You can describe the value_counts()
  * This shows us how crazy dirty this data is
* Graphing
  * Create new column for day of week
  * Create new data fram with that info with count
  * Try plotting it
  * Try bar chart
  * Just use ISSUE DATE
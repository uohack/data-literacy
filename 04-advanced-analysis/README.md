**This repo is constantly under development. Have suggestions or feedback? Please let me know! rob [at] uohack [dot] com or file a pull request!**

## Introduction

As we start every course, here is a simple work flow for basic data analysis.

* Get data
* Clean data
* Analyze data
* Present (or share) data

This course will cover advanced data analysis using Python and the Pandas data analysis library. The purpose is to show students what is possible with a little code, not to teach you how to program.

By the end of this course you should:

* Have a basic understanding of how to analyze data with Python pandas

**Note:** If you do not want to or are not able to actively participate in this course, that is totally fine. I created this course to show you want is possible, not as a step-by-step guide to learning pandas. That said, there are two ways to proceed:

1. You may follow along through the example using a notebook I created and is served by Github [here](https://github.com/uohack/data-literacy/blob/master/04-advanced-analysis/parking.ipynb). For those of you not familiar with command line and Python, this is strongly encouraged. Please do read through the whole course, but do not feel discouraged if you do not fully understand what's going on.
1. For those of you with command line experience and Python, I have placed enough information below to push you in the right direction. But I do not explain every step from zero to working in a Jupyter notebook. You will need to do some outside reading to get your computer up to speed. I would recommend you go through the tutorial once, reading the notebook via Github (option one) and then come back and try to do it yourself later.

## Background

Moving forward I am going to assume you are familiar with the command line, Python, virtualenv, Jupyter and pandas. If you want to read up on any of these topics, there are a number of resources out there. Here are a few I recommend:

* [Digital media boot camp programming basics - UO Hack (Python)](https://github.com/uohack/digital-media-boot-camp/blob/gh-pages/programming/01-programming-basics.md)
* [How to setup your Mac to develop news applications like we do - NPR (virtualenv)](http://blog.apps.npr.org/2013/06/06/how-to-setup-a-developers-environment.html)
* [Hello virtualenv - First Python Notebook](http://www.firstpythonnotebook.org/virtualenv/index.html#chapter-1-hello-virtualenv)
* [Hello Jupyter - First Python Notebook (you might pick up on a pattern here)](http://www.firstpythonnotebook.org/notebook/index.html#chapter-2-hello-jupyter)
* [Hello Pandas - First Python Notebook](http://www.firstpythonnotebook.org/pandas/index.html#chapter-3-hello-pandas)
* [10 minutes to pandas - pandas documentation](https://pandas.pydata.org/pandas-docs/stable/10min.html)

This may seem like a lot, but the learning curve is not as steep as you might think. Python is quickly becoming the language of choice for entry-level computer science classes and once you get your system set up with virtualenv, you can launch a Jupyter notebook and get working with pandas in less than five minutes. And every project after that will be quick to start as well.

The reason why we want to use tools like Jupyter is so that we can show our work and be as transparent as possible with our analysis. We want to use pandas because pandas makes that analysis really easy. It comes with hundreds of functions to analyze, manipulate and sort through data that might be difficult to work with in a spreadsheet. Virtualenv allows us to encapsulate our work so that it is easily reproducible and so that it is self-contained. And, of course, Python is the foundation on which all of that is built.

So, let's get started by jumping right into our example.

## Example

**Scenario:** You are a reporter at the student newspaper and working on a story regarding parking citations on campus. You request and receive a little more than two year's worth of citation data, some 31,000 rows worth. The data is fairly tidy and you want to run some quick analysis regarding where the most tickets are given out. Your goal is to take the parking data and see at what location (or locations) the most tickets were given out in the most recent budget year.

**Note:** Thanks to the [Daily Emerald](http://dailyemerald.com) for sharing this data with UO Hack. It was originally requested by former Emerald EIC Cooper Green in spring 2017.

Back to the scenario, we know from the University of Oregon's office of [Budget and Resource Planning](https://brp.uoregon.edu/vcontent/faqs) that the UO fiscal year runs July 1 - June 30. That means in our data set we only have one full budget year, between July 2015 - June 2016. So we'll need to trim the data once we get it into pandas to remove the excess information.

We want to keep our analysis in line with a budget year because that is the only way we can compare budget items. For instance, you could say that the x many citations were given out in budget year 2015-16 resulting in total revenue of y dollars. However, that level of analysis is beyond the scope of this example.

In addition to the budget year, we also know that we'll need to organize the data based on location in order to sort out where the most tickets were issues. Let's hope that the location information is present, accurate and consistent for all of the citations.

## Getting started

*You may skip this section if you are not setting up a Jupyter notebook on your computer.*

If you're following along, here are the basic steps to getting a Jupyter notebook running if you have all the prerequisites installed.

```
> mkvirtualenv myfirstnotebook
# virtualenv should be created, installing fresh Python and pip

(myfirstnotebook) > pip install jupyter
# Jupyter and dependencies should install

(myfirstnotebook) > pip install pandas
# pandas and dependencies should install

(myfirstnotebook) > jupyter notebook
# Jupyter server should begin and browser should launch
```

At this point your computer should open up a fresh Jupyter interface in your default browser. From there you can navigate to your project folder and create a new notebook using the New drop down on the right side.

## Into the notebook

From here on out, I will be walking you through an associated Jupyter notebook. You can view a full, pre-populated notebook [here](https://github.com/uohack/data-literacy/blob/master/04-advanced-analysis/parking.ipynb) if you are not setting up a notebook on your own computer.

First things first, we need to import pandas so that we can work on it.

Next, we want to "read" the data from the CSV into a pandas data frame. A data frame is just a fancy name for a data structure in pandas. It makes the data available to us for analysis. We'll set that data frame equal to a variable called citations.

After we import the data we want to take a look at it and see what we're working with. To get a snapshot of the data you can use the `.info()` method. This will return useful information like the number of entries in the data frame, column names and column types.

We won't do it here but you could also do the `.head()` method, which would print out the first five rows.

You can also run `.describe()` which tells us the following:

* Each column has a count of 31,086 data points, except the ISSUE TIME. This means, that not every citation has a time listed. This will be important later.
* There are 429 citation locations (that seems like a lot for an area the size of campus, could be an indication of inconsistent naming of locations)
* The day with the most tickets? Oct. 3, 2016
* The top fine amount? $20
* The location with the most citations? University Street meters, which matches the top violation: Overtime street meter

All of that information gives us a great introduction to this data set. But it certainly isn't perfect. For one, it's not the fiscal year we want and we don't know if the data is messy yet. So let's dig deeper.

### Modifying data

Remember, there is data from outside FY15-16, but we don't know the exact range of the dates. To better work with this column, let's convert the values, which are plain text, into datetime objects. We know that this column is plain text because back in `.info()` the data type was a regular old 'object'. After we convert the column to datetime, we'll be able to do all sorts of analysis based on the date.

To to this we use a pandas method called `to_datetime()` to convert that column into datetime. This may take a second, we have more than 30,000 rows after all.

When that's done we can do another `.info()` and we see that the column's new type is datetime!

Now if we do a `citations['ISSUE DATE'].describe()` pandas tells us that the first date is Jan. 4, 2015 and the last date is March 13, 2017.

Let's take the next step and remove all the unnecessary data outside FY15-16.

To do this, we are going to `drop` data from the whole data frame `citations` that does not match our criteria. In this case, that's tickets from before July 1, 2015 or after June 30, 2016.

Unsure of how exactly to do this, I did a quick Google search and found [this StackOverflow answer](https://stackoverflow.com/a/27360130) that should help us.

It looks like the basic syntax looks like this:

`df = df.drop(df[<some boolean condition>].index)`

There are a few things you need to know about this command. `df` is the typical name of data frames in pandas examples. So this line is setting the data frame variable equal to the data frame, but also dropping some rows based on some boolean condition. Inside the `drop` method we see `df[...]`. Inside the square brackets we could put an integer for a row index or a string for a column name. When you do a conditional inside there and tack on `.index` you pass the row object to the drop method.

*If any of that doesn't make sense, don't worry. Just know that we're whittling down the data to just FY15-16.*

Now, we do the boolean dropping like so:

```
citations = citations.drop(citations[citations['ISSUE DATE'] < '7-1-2015'].index).drop(citations[citations['ISSUE DATE'] > '6-30-2016'].index)
```

Now we can do a `.describe()` on the column and see that the first date is July 1, 2015 and the last date is June 30, 2016.

**Note:** You may have noticed that the time on these datetime objects is set to 00:00:00. Back when we converted the column from plain text to datetime, we probably should have also passed the time data in with the date. This would have given us more precise datetime information. But, remember, not all of the citations had ISSUE TIME values, so this might have caused additional problems that are outside the scope of this example. It also might have been better to just make them date objects, but, again, this is about exploring the data, not making the most efficient script to run time and time again.

### Checking locations

Now that the data is narrowed down to FY15-16 we can query the data for the top locations.

This is easily accomplished via a method I learned about from Ben Welsh during his class on Python for data journalists. That method is `.value_counts()` which you can read more about [here](http://www.firstpythonnotebook.org/value_counts/index.html#counting-a-column-s-values).

And voila! There are your locations where the most citations were given out.

It's obvious that University Street meters are indeed the most popular place to get a ticket. By a long shot. In fact, it's more than double the next highest location. The next highest is Lot 16A, then 15th Avenue and so on and so forth.

In scanning the counts, you should notice that 15th Avenue is listed twice in the top 30. This may be because there are two lots on 15th Avenue, but it's more likely that this is just messy data input.

If you combine those two it still isn't enough to move it up into the second spot. This gives me some confidence that even if the data is messy (it is), it isn't messy enough to skew our general findings.

At the bottom of the count it shows a length of 291 locations. That is a lot, especially given the drop off from four digits down to just two in the top 30 locations. Again, I'm guessing that this data fits a "[long tail](https://en.wikipedia.org/wiki/Long_tail)" curve, which is only to say that there are a lot of locations where only one ticket was given out. This is caused by inconsistent naming conventions and manual data input by multiple users.

We can double check this assumption by doing a `describe()` on the counts. This is made possible because pandas allows you to chain methods together. You might of noticed this earlier when we dropped data.

`citations['TICKET LOCATION STREET'].value_counts().describe()`

This returns some statistics that confirm my suspicion. The min is 1, the 25th percentile is 1, the 50th percentile is 2 and the 75th percentile is 12.

It is **very** unlikely that the bottom 200, with counts from 1 to 10, were all different spellings of the same lot. And even if that was the case, I doubt that it would allow that location to crack the top five locations we found via the value counts.

So, in only (about) five steps, we were able to calculate the most-ticketed places on campus and learn more about how citations are distributed on campus.

You can take that information and go back and ask some questions and do some more reporting. Or you could export the data using the `to_csv()` method for some manual cleaning if you wanted to do some data visualization.

In any case, you leveraged the power of pandas to do quick data analysis that would be time consuming to perform in a standard spreadsheet.

**Note:** If you're an Excel power user you may be asking why this couldn't have been done using a pivot table? Well, it certainly could have. But we were dealing with 30,000+ rows and had to do some time-based cleaning. Those two elements, in my opinion, are better handled in pandas.

## Wrap up

At this point you should have a decent understanding of what is possible using Python pandas through a Jupyter notebook.

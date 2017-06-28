This is the second course (out of four) on data literacy created for UOHack.

## Introduction

In the last course we looked at the following basic data work flow:

* Get data
* Clean data
* Analyze data
* Present (or share) data

The truth of the matter is that cleaning the data usually takes up the vast majority of your time. This time spent cleaning leads to better understanding and important insights.

In this course I'm going to go over ways to work with data in a spreadsheet and some more advanced methods of cleaning. We'll also go through an example where you have to go get data out of a PDF, do some math to check the numbers and create some basic graphs.

By the end of this course you should:

* Understand basic spreadsheet formulas
* Know the formula for percent change
* Have a decent understanding of how to transfer data from a native PDF to a spreadsheet
* Know how to add data columns to your set and populate them using spreadsheet formulas
* Begin to visualize data using Google charts

Let's get started.

## The power of spreadsheets

The great thing about digital spreadsheets is that they offer a number of powerful mathematical and programmatic functions to help you work with data. Here are a few useful formulas:

```
=SUM(A1:A5)
# Adds the numerical values of A1, A2, A3, A4 and A5

=IF(A1>A2,"One is bigger","Two is bigger")
# Conditional IF test
# For example, given:
# A1 = 5 and A2 = 7 the cell would display:
# Two is bigger

=CONCATENATION(B2,": ",B3)
# Concatenate multiple strings
# For example, given:
# B2 = "Monday" and B3 = "Weekday" would display:
# Monday: Weekday
```

You can also combine formulas like this simple example:

```
# The A column is sales this month, B1 is this month's quota
# A1 = 50
# A2 = 40
# A3 = 5
# B1 = 100
=IF(SUM(A1:A3)<B1,"Did NOT make quota","Made quota this month")
=IF((50+40+5)<100,"Did NOT make quota","Made quota this month")
=IF(95<100,"Did NOT make quota","Made quota this month")
# Did NOT make quota
```

These are simplistic examples but offer a lot of leverage when working with data. Simple things like percentages or percent change ((N-O)/O) and more complex things like concatenating street addresses or creating new data with conditionals can be easily accomplished in spreadsheets.

### Percent change

Matt Waite, a journalism instructor at the University of Nebraska, tells his students that they can't graduate until they [prove to him](https://twitter.com/ACRStriker9/status/861642695390965762) that they have memorized the formula for percent change.

[Percent change](https://www.youtube.com/watch?v=uxMr5sEjIJI) is a simple and important formula for anyone to know, especially those working with data. You (*yes, you*) should know this. Here is the formula and an example:

```
(New value - Old value) / Old value

Last month you had $132,638 in sales. This month you had $145,689 in sales. What's the percent change?

(N-O)/O
($145,689-$132,638)/$132,638
$13,051/$132,638
9.84% growth
```

I want to spend the majority of this course in an example that exemplifies many different methods of cleaning data, so let's move into that.

## Example

**Scenario:** You're a reporter looking at the proposed [City of Eugene budget](https://github.com/uohack/data-literacy/raw/master/02-cleaning-data/FY18_proposed_budget.pdf) for fiscal year 2018. On page 56/62 you find a breakdown of the budget by department, a helpful snapshot of how the city spends money. Your task it to double check their math and get a sense of the city's priorities moving into the new budget year. This includes looking at what departments get the most and least money, and what departments are getting small and large budget increases.

**Note:** This proposed budget was downloaded in June 2017 and may have changed. Any changes do not matter for the sake of this example.

Go ahead and crack that budget PDF open and find page 56/62. There is a table labeled "General Fund (All Subfunds) Operating Budget Summary by Department" that we are most interested in. First step? Get the data into a spreadsheet

### Getting data out of PDFs

There are several types of PDFs, but for the purposes of this course I'm going to oversimplify to just two types: native and scanned. Scanned PDFs are effectively flat images where text cannot be copied. There are a number of OCR programs that try to retrieve text from these images, but nothing is perfect.

Native PDFs, on the other hand, offer fairly easy copying of any text information. This means that most tables or spreadsheets are extractable. The PDF in this example is native so we should absolutely try to copy and paste the table into an empty Google Sheet.

**Pro tip:** The way that Google Chrome renders PDFs make them copy and paste easier than Apple's Preview application.

So let's give it a go. Hey, it works! Kind of...

![screen shot 2017-06-11 at 8 47 20 pm](https://user-images.githubusercontent.com/4853944/27018711-3e7774ac-4ee7-11e7-9b5d-4706bf365b8e.png)

We need to clean that up a little bit. You have two options. The first is to keep the data in the spreadsheet and do manual cleaning using copy and pasting. The threat of introducing errors is pretty low because it's a fairly small data set and it's easy to double check your work.

The second option is to copy/paste the data into a text editor and format the data in there. If you utilize [regular expressions](http://www.hongkiat.com/blog/getting-started-with-regex/) and find and replace then this can be quicker than manual data editing. Unfortunately, regular expressions have a fairly steep learning curve so this is not a great venue to teach that.

We'll continue with manual data editing in the spreadsheet.

First things first, give the Google Sheet a name so that you can find it again if you step away. Next, pull up the PDF next to the Sheet and try to replicate the table in the spreadsheet.

Start with the headers and make sure those are accurate. Then move to separating the data values one line at a time. When you're done, go through, value by value, and make sure you didn't introduce any errors.

Got it? Good.

There's a few things that I'd like to point out:

* Google sheets automatically added an additional decimal point when it formatted the percentages. You probably noticed that when double checking your numbers. This is easily fixed if you highlight that column and move the decimal point up using the "Decrease decimal places" button in the tool bar.
* The original data set was not very consistent with the dollar styles. The first and last rows have a dollar sign but the others do not. Let's format all these cells. Highlight the B and C columns and select Format > Number > Currency (rounded).
* In the final column the city has calculated percent change for us. How nice of them. We should check their math.

### Check their math

You should never trust someone else to do analysis for you. Especially when it could benefit them. If someone does some math for you, double check their work.

Let's create a new column, and using the equation for percent change, plug in the correct cells for the first row. After you have that value calculated, you can drag down on the bottom right corner of the cell and apply that math to the rest of the column.

![pc](https://user-images.githubusercontent.com/4853944/27019805-791ed8d0-4ef0-11e7-9d5a-2496187cbe50.gif)

The numbers are sightly off but that can be explained by rounding. We can match our numbers to their's by decreasing the decimal place by one.

Ok, so they did the math right, that's good! Let's move on to do some additional analysis. We can solve for the average percent change over all the departments. `=AVERAGE(A2:A7)` is 6.8%. Remember to exclude the total!

Another good metric is to see what the actual value is as a percent of the total. This gives us a better idea of how that percent change is in scale. For instance, you can have a large percent change of a very small number. Or, you could have a very small percent change on a very large number.

In a new column, let's divide the FY18 budget by the total to get a sense of scale with the percent of total. You can drag down the formula like we did before.


![pertot](https://user-images.githubusercontent.com/4853944/27020081-e9038676-4ef2-11e7-8b24-2d094736bd82.gif)

Uh oh. That's not good. What's wrong? Well, when we drag down the formula to apply it to the cells below, the cells in the formula are changed as well. You can see that the formula for F2 is C2/C8 and F3 is C3/C9, but it should be C3/C8. We need to "lock" in C8 in the formula. This can be accomplished with a dollar sign, like so: `=(C2/C$8)`.

![pertot2](https://user-images.githubusercontent.com/4853944/27020179-dd6858b8-4ef3-11e7-8f89-296b35e28c30.gif)

This adds some context, but one thing we haven't looked at is the actual dollar value change from one year to the next. Let's solve for that with simple subtraction of B from C.

![diff](https://user-images.githubusercontent.com/4853944/27020237-42eb2486-4ef4-11e7-8aae-bfe1641bcc1d.gif)

This is interesting because Police has the smallest percentage increase (4%) but it has the largest total dollar increase ($2,027,321). At the same time, the highest percent change (11%) of Planning & Development has the second smallest total dollar increase ($704,712).

So now we have a couple of different points of reference. One is percent change, which we double checked. Another is total dollar increase. And even another is FY18 amount as a percent of the total. Each gives us a different perspective on the same data

Let's take a step back and see what we've learned:

* While Planning & Development has largest increase, it's total budget is much smaller than others so that may not be the most important story
* Police has the largest increase at over $2,000,000. After that, Library, Rec & Cultural Services.
  * In the last year Douglas County shut down all of their libraries so that could be an interesting comparative story.
* One thing we haven't discussed yet is that each department is getting a budget increase and the total budget is increasing by nearly $8,000,000. Is this surprising?

Now that we have the budget analyzed, where do we go from here? Well, there are a number of story ideas above and we're still at the highest possible level of this budget proposal. You could dig deeper into any (or all) of the department budgets.

But before we get to that, let's visualize some of this data.

### Simple viz

The best way to create simple graphs in Google Sheets is to create a new sheet for each graph. Let's do that with this data.

Starting with total dollar change, let's copy that column and the far left column into a new sheet. Be sure not to copy the Total row, that will just skew the axes of the bar graph.

Uh oh. More errors. This is because you're trying to paste in formulas, not values. Right click and "Paste Values Only" instead of just pasting data in the second column.

![screen shot 2017-06-11 at 10 33 37 pm](https://user-images.githubusercontent.com/4853944/27065208-ba66acbc-4fb0-11e7-8b24-33a4647cbd08.png)

That should help a lot. You can also change to format to currency if you want to maintain consistency.

From here, select A1 and go Insert > Chart. It should create a bar chart by default.

![screen shot 2017-06-12 at 8 59 27 pm](https://user-images.githubusercontent.com/4853944/27065445-0dedf678-4fb2-11e7-9fe0-329dbb9b67dc.png)

What do we learn from this? Well, it confirms what we found about the Police budget increase being the largest by a huge margin. It also shows how small the Public Works and Planning & Development increases are.

I should note that these charts can be stylized and exported as an image or interactive embed. Designers will be disappointed, however, at the lack of options and it's tough to add any brand identity.

You can copy this method and apply it to the other values to see charts of those columns as well.

## Wrap up

At this point, you should:

* Understand basic spreadsheet formulas
* Know the formula for percent change
* Have a decent understanding of how to transfer data from a native PDF to a spreadsheet
* Know how to add data columns to your set and populate them using spreadsheet formulas
* Begin to visualize data using Google charts

Next, we'll dive deeper into sharing data and do a simple mapping example.

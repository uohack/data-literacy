*Have suggestions or feedback? Please let me know! rob [at] uohack [dot] com or file a pull request!*

* [Slides](http://uohack.com/data-literacy/02-cleaning-data/slides/)
* [Notes](https://github.com/uohack/data-literacy/blob/master/02-cleaning-data/notes.txt)

## Introduction

In the [last course](https://github.com/uohack/data-literacy/tree/master/01-getting-started) we looked at the following basic data work flow:

* Get data
* Clean data
* Analyze data
* Present (or share) data

The truth is that cleaning the data usually takes up the vast majority of your time. This time spent cleaning leads to better understanding and important insights.

In this course I'm going to go over ways to work with data in a spreadsheet and some more advanced methods of cleaning. We'll also go through an example where you have to go get data out of a PDF, do some math to check the numbers and then we'll create a simple graph.

By the end of this course you should:

* Understand basic spreadsheet formulas
* Know the formula for percent change by heart
* Have a decent understanding of how to transfer data from a native PDF to a spreadsheet
* Know how to add data columns to your set and populate them using spreadsheet formulas
* Begin to visualize data using Google charts

Let's get started.

## The power of spreadsheets

The great thing about digital spreadsheets is that they offer a number of powerful mathematical and programmatic functions to help you work with data. Here are a few useful formulas.

### Adding

Let's start simple. Say you need to add two cells together. You can do that like so:

```
=SUM(B3,C10)
# The same as: B3 + C10
```

Or you can add a series of cells like so:

```
=SUM(A2:A8)
# The same as: A2 + A3 + A4 + A5 + A6 + A7 + A8
```

### Conditional statements

A [conditional statement](https://en.wikipedia.org/wiki/Conditional_(computer_programming)) is a programming principle where you can say if something is like this, then do this, otherwise do something else. They're also called if-else statements. You can do these in spreadsheets and they can be very helpful.

For instance, say you have a monthly report and you need to figure out each month if the company has met it's projections. Each one of these values is a different cell in a spreadsheet. So you would do something like this:

```
# A1 is your monthly profit
# A2 is your projected profit
=IF(A1>A2,"You made your projections","You did not make your projections")
```
In this example, you would put this equation in another cell, like A3. Then, the A3 cell would tell you if you met your projections or not.

### Concatenation

To concatenate is to simply combine multiple things. In spreadsheets, sometimes it's helpful to concatenate multiple cells. This is common with addresses.

Say the B column in your spreadsheet contains a user's street address. The C column contains the city, D contains the state and E contains the ZIP code. You need to concatenate these to print out a legible address.

```
# B2 = "500 Example St."
# C2 = "Eugene"
# D2 = "OR"
# E2 = "97401"

=CONCATENATION(B2," ",C2,", ",D2," ",E2)

# This would combine those cells with the additional spaces and comma like so:

"500 Example St. Eugene, OR 97401"
```

### Combining formulas

If you're feeling fancy, you can get really effcient by combining formulas. But, it's important to remember order of operations. (Remember [PEMDAS](https://www.mathsisfun.com/operation-order-pemdas.html)?)

Let's say you have this month's sales figures in the A column. In cell B1 you have this month's projections. Try to solve this formula on your own.

```
# A1 = 50
# A2 = 40
# A3 = 5
# B1 = 100

=CONCATENATE(SUM(A1:A3), IF(SUM(A1:A3)<B1,": did NOT make quota",": made quota this month"))
```

<details>
<summary>Click here for the answer</summary>
This should render: `95: did NOT make quota`

Is that what you got?

You can see an example [here](https://docs.google.com/spreadsheets/d/1pVvIxBbrfv-pM3wlGgS5i-Ih76TBe7i0tIYW5VAGBkw/edit?usp=sharing).
</details>

## Percent change

Matt Waite, a journalism instructor at the University of Nebraska, tells his students that they can't graduate until they [prove to him](https://twitter.com/ACRStriker9/status/861642695390965762) that they have memorized the formula for percent change.

[Percent change](https://www.youtube.com/watch?v=uxMr5sEjIJI) is a simple and important formula for anyone to know, especially those working with data. You (*yes, you*) should know this by heart. Here is the formula and an example:

```
(New value - Old value) / Old value

# Simple example
### You had 10 apples and now you have 5, what is the percent change?
(N-O)/O
(5-10)/10
-5/10
-0.5 = -50%
### This makes since because 5 apples is 50% less than 10 apples.

# Real-world example
### Last month you had $132,638 in sales. This month you had $145,689 in sales.
### What's the percent change?
(N-O)/O
($145,689-$132,638)/$132,638
$13,051/$132,638
9.84% growth
### This makes sense because your sales increased, but not by a ton.
```

I want to spend the majority of this course in an example that shows many different methods of cleaning data, so let's move into that.

## Example

**Scenario:** You're a reporter looking at the proposed [City of Eugene budget](https://github.com/uohack/data-literacy/raw/master/02-cleaning-data/FY18_proposed_budget.pdf) for fiscal year 2018. On page 56/62 you find a breakdown of the budget by department, a helpful snapshot of how the city spends money. Your task it to double check their math and get a sense of the city's priorities moving into the new budget year. This includes looking at what departments get the most and least money, and what departments are getting small and large budget increases.

**Note:** This proposed budget was downloaded in June 2017 and may have changed. Any changes do not matter for the sake of this example.

Go ahead and crack that budget PDF open and find page 56/62. There is a table labeled "General Fund (All Subfunds) Operating Budget Summary by Department" that we are most interested in. First step? Get the data into a spreadsheet, of course!

### Getting data out of PDFs

There are several types of PDFs, but for the purposes of this course I'm going to oversimplify to just two types: native and scanned. Scanned PDFs are effectively flat images where text cannot be copied. There are a number of OCR programs that try to retrieve text from these images, but doing so is time consuming and difficult.

Native PDFs, on the other hand, have text that can be easily copy and pasted. This means that most tables or spreadsheets are extractable. The PDF in this example is native so we should try to copy and paste the table into an empty Google Sheet.

**Pro tip:** The way that Google Chrome renders PDFs make them copy and paste easier than Apple's Preview application. Other applications will have their own flavor. If something doesn't work the way you should, experiment with others.

So let's give it a go.

Hey, it works! Kind of...

![screen shot 2017-06-11 at 8 47 20 pm](https://user-images.githubusercontent.com/4853944/27018711-3e7774ac-4ee7-11e7-9b5d-4706bf365b8e.png)

*Remember, your mileage may vary, depending on the application you copied from ...*

We need to clean that up a little bit. You have two options. The first is to keep the data in the spreadsheet and do manual cleaning using copy and pasting. The threat of introducing errors is pretty low because it's a fairly small data set and it's easy to double check your work.

The second option is to copy/paste the data into a text editor and format the data in there. If you utilize [regular expressions](http://www.hongkiat.com/blog/getting-started-with-regex/), as well as find and replace, then this can be quicker than manual data editing. Unfortunately, regular expressions have a fairly steep learning curve so this is not a great venue to teach that.

We'll continue with manual data editing in the spreadsheet.

First things first, give the Google Sheet a name so that you can find it again if you step away. Next, pull up the PDF next to the Sheet and try to replicate the table in the spreadsheet.

Start with the headers and make sure those are accurate. Then move to separating the data values one line at a time. When you're done, go through, value by value, and make sure you didn't introduce any errors.

Got it? Good.

There're a few things that I'd like to point out:

* Google sheets automatically added an additional decimal point when it formatted the percentages. You probably noticed that when double checking your numbers. This is easily fixed if you highlight that column and move the decimal point up using the "Decrease decimal places" button in the tool bar.
* The original data set was not very consistent with the dollar styles. The first and last rows have a dollar sign but the others do not. Let's format all these cells. Highlight the B and C columns and select Format > Number > Currency (rounded).
* In the final column the city has calculated percent change for us. How nice of them. We should check their math.

### Check their math

You should never trust someone else to do math for you. Especially when it could benefit them. Always double check their work.

Let's create a new column with a header of "my-percent-change". Using the equation for percent change you just learned, plug in the correct cells for the first row. After you have that value calculated, you can drag down on the bottom right corner of the cell and apply that math to the rest of the column.

![pc](https://user-images.githubusercontent.com/4853944/27019805-791ed8d0-4ef0-11e7-9d5a-2496187cbe50.gif)

The numbers are sightly off but that can be explained by rounding. We can match our numbers to their's by decreasing the decimal place by one.

Ok, so they did the math right, that's good! Let's move on to do some additional analysis. We can solve for the average percent change over all the departments. `=AVERAGE(A2:A7)` is 6.8%. Remember to exclude the total!

Another good metric is to see what the actual value is as a percent of the total. This gives us a better idea of how that percent change is in scale. For instance, you can have a large percent change of a very small number. Or, you could have a very small percent change on a very large number.

In a new column, let's divide the FY18 budget by the total to get a sense of scale with the percent of total. You can drag down the formula like we did before.

![percent of total error](https://user-images.githubusercontent.com/4853944/28104867-ee0a4fa4-6691-11e7-9a83-bad342f99064.png)

Uh oh. That's not good. What's wrong? Well, when we drag down the formula to apply it to the cells below, the cells in the formula are changed as well. You can see that the formula for F2 is C2/C8 and F3 is C3/C9, but it should be C3/C8. We need to "lock" in C8 in the formula. This can be accomplished with a dollar sign, like so: `=(C2/C$8)`.

![percent of total corrected](https://user-images.githubusercontent.com/4853944/28104918-28dcd354-6692-11e7-86fa-46273546e639.png)

This adds some context, but one thing we haven't looked at is the actual dollar value change from one year to the next. Let's solve for that with simple subtraction of B from C.

![Change in dollars](https://user-images.githubusercontent.com/4853944/28104948-4e6cc4ee-6692-11e7-939f-ff36d825d267.png)

This is interesting because Police has the smallest percentage increase (4%) but it has the largest total dollar increase ($2,027,321). At the same time, the highest percent change (11%) of Planning & Development has the second smallest total dollar increase ($704,712).

So now we have a couple of different points of reference. One is percent change, which we double checked. Another is total dollar increase. And even another is FY18 amount as a percent of the total. Each gives us a different perspective on the same data

Let's take a step back and see what we've learned:

* While Planning & Development has largest increase, it's total budget is much smaller than others so that may not be the most important story
* Police has the largest increase at over $2,000,000. After that, Library, Rec & Cultural Services.
  * In the last year Douglas County shut down all of their libraries so that could be an interesting comparative story.
* One thing we haven't discussed yet is that each department is getting a budget increase and the total budget is increasing by nearly $8,000,000. Is this surprising?

Now that we have the budget analyzed, where do we go from here? Well, there are a number of story ideas above and we're still at the highest possible level of this budget proposal. You could dig deeper into any (or all) of the department budgets.

We won't go any further with the analysis. Instead, we'll turn to basic data visualization with bar graphs.

### Simple viz

The best way to create simple graphs in Google Sheets is to create a new sheet for each graph. Let's do that with this data.

Starting with total dollar change, let's copy that column and the far left column into a new sheet. Be sure not to copy the Total row, that will just skew the axes of the bar graph.

Uh oh. More errors. This is because you're trying to paste in formulas, not values. Right click and "Paste Values Only" instead of just pasting data in the second column.

![screen shot 2017-06-11 at 10 33 37 pm](https://user-images.githubusercontent.com/4853944/27065208-ba66acbc-4fb0-11e7-8b24-33a4647cbd08.png)

That should help a lot. You can also change to format to currency if you want to maintain consistency.

From here, select A1 and go Insert > Chart. It should create a bar chart by default.

![screen shot 2017-06-12 at 8 59 27 pm](https://user-images.githubusercontent.com/4853944/27065445-0dedf678-4fb2-11e7-9fe0-329dbb9b67dc.png)

What do we learn from this? Well, it confirms what we found about the Police budget increase being the largest by a huge margin. It also shows how small the Public Works and Planning & Development increases are.

I should note that these charts can be stylized and exported as an image or interactive embed. Designers will be disappointed, however, at the lack of options.

You can copy this process and apply it to the other columns to see charts of those columns as well.

## Wrap up

At this point, you should:

* Understand basic spreadsheet formulas
  * Get data
  * Clean data
  * Analyze data
  * Present (or share) data
* Know the formula for percent change
  * ((N-O)/O)
* Have a decent understanding of how to transfer data from a native PDF to a spreadsheet
* Know how to add data columns to your set and populate them using spreadsheet formulas
* Begin to visualize data using Google charts

[Next, we'll dive deeper into sharing data and do a simple mapping example.](https://github.com/uohack/data-literacy/tree/master/03-sharing-data)

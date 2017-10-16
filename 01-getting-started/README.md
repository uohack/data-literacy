*Have suggestions or feedback? Please let me know! rob [at] uohack [dot] com or file a pull request!*

## Introduction

Data literacy is the ability to create, work with and analyze data. While all data is different, there are several common ideas and tools that you can learn to help you apply to nearly any data set you may encounter.

The goal of the first section of this course is to introduce you to basic data concepts. No prior knowledge is required. After this course, you should be able to:

* Explain the basic steps of working with data
* Explain what CSV is
* Open a data set in a spreadsheet
* Use a spreadsheet to do basic cleaning

Let's get started.

### Requirements

For this course you'll need a computer with administrative privileges, a text editor and a Google account. If you don't have a text editor, that's fine, I'll discuss it below.

## Work flow

When working with data, your first job is to acquire the data, simplify it into something manageable and understandable, analyze the information and finally share it with others. It doesn't matter whether you're a journalist or business analyst, you will want to follow this basic checklist:

* Get data
* Clean data
* Analyze data
* Present (or share) data

Of course, the process of working with data is rarely that simple. At any point in that cycle you may need to stop and ask questions, request more data or cut the data down to something more manageable.

### Working with data

After acquiring data, your goal should be to get that data into a tabular format, AKA a spreadsheet. Doing so will allow you to easily edit, visualize and export the data. This may seem simple but data can take all sorts of different formats, some are unfriendly to work with.

For example, if the data is coming out of a database, the data may retain the format of that database. That might mean awkward formatting in an Excel document or files with [`.spss`](https://en.wikipedia.org/wiki/SPSS) or [`.accdb`](https://en.wikipedia.org/wiki/Microsoft_Access) extensions, which require special software to access.

Sometimes a spreadsheet is printed off to a paper file, then that piece of paper is scanned and emailed to you as an image PDF. Sure, you could manually enter the data, but that's a terrible waste of your time and the probability of making a mistake is very high.
For the purposes of these courses, all examples will be fairly easy to access. But be warned, the real world can be much crueler. **When requesting data it is important to always request the data in a digital format (rather than paper).** This gives us the best chance at success.

A lot of people will offer the data as an Excel file. That's fine, but Excel files can have very complex designs and require you to have the same version of Excel as where it was created. A CSV file is often superior because it's a simple, standard file type. Almost every database or spreadsheet program can write out the data to a CSV file.

### CSV

CSV stands for Comma-Separated Values. This is what a simple CSV file looks like:

```csv
school, mascot, conference
Oregon, Ducks, Pac-12
Colorado, Buffaloes, Pac-12
Texas, Longhorns, Big-12
```

Each column is separated by a comma and each row is separated by a line break. If you open up a CSV file in a text-editor, like [Sublime Text](https://www.sublimetext.com/) you'll see this format. But, if you open a CSV file in a spreadsheet program, it will display like any other spreadsheet. You can edit the data and save it as a CSV.

Because the files is just text, it is the lowest-common denominator for any data program. In fact, whenever you request data, you should request a CSV file. This ensures a small file size, simple data structure and the ability to directly import into a spreadsheet editor.

*Warning: Some organizations keep complex multi-sheet spreadsheets with advanced formatting. These are hard to convert into CSV without losing data. Each situation is different and sometimes that advanced formatting is beneficial, but defaulting to CSV is usually a good plan.*

### Other data formats

There are many other ways to store data in text files (or otherwise).

One of the most popular ways to pass data via API is JSON, or JavaScript Object Notation. JSON files contain a series of key-value pairs as demonstrated below.

```JavaScript
{
	"Key": "Value",
	"Parent key": {
		"Child key": "Child value",
		"Another child": "Another child value"
	}
}
```

TSVs are another popular data file type. These are very similar to CSVs but they are tab separated instead of comma separated.

## Example

**Scenario:** You're a student journalist and you've heard rumors of students ordering marijuana and having it delivered to their dorms. This, of course, is [against UO rules](https://dos.uoregon.edu/marijuana), which prohibit marijuana on campus. Your goal for this example is to figure out how many pot shops near the UO deliver as the starting point for a story.

**Note:** The data I have pulled for this example is accurate, as of May 26, 2017, and has been modified for instructional purposes. You can find current data from OLCC [here](http://www.oregon.gov/olcc/marijuana/Documents/Approved_Retail_Licenses.xlsx). Any changes do not matter for the sake of this example.

To begin this example, please download [this CSV](https://raw.githubusercontent.com/uohack/data-literacy/master/01-getting-started/lane-pot.csv) of my simplified data. If the link opens in a new tab, right click and save the file as lane-pot.csv to your Desktop or wherever is convenient on your machine.

### Text editors

You will also need a [text editor](https://www.maxmasnick.com/2015/08/12/real-text-editor/). A text editor allows you to open text files (like CSVs) in the raw text format. This is important because you know immediately if the data is corrupt and immediately learn about the data structure.

Text editors differ from word processors that you may be familiar with, in that they only deal with plain text, not formatted text. If you don't have a text editor installed, I suggest downloading [Sublime Text](https://www.sublimetext.com/).

### Back to the example

Now that you have a text editor installed and the [CSV file](https://raw.githubusercontent.com/uohack/data-literacy/master/01-getting-started/lane-pot.csv) downloaded, open it up in the text editor. You should see something like this:

```csv
TRADE NAME,POSTAL CITY,COUNTY,STREET ADDRESS,ZIP,Notes
APOTHECARIA,COTTAGE GROVE,LANE,700 ROW RIVER ROAD ,97424,Med Grade
MANDY'S SUGAR SHACK,COTTAGE GROVE,LANE,339 HWY 99 SOUTH ,97424,Med Grade
THE HOLISTIC COOP LLC,COTTAGE GROVE,LANE,1049 E MAIN ST ,97424,
THE MEDICATION STATION,COTTAGE GROVE,LANE,1041 HWY 99 NORTH ,97424,Delivery
THE PEOPLE'S WELLNESS CENTER,EUEGENE,LANE,71 CENTENNIAL LOOP SUITE B,97401,"Med Grade, Delivery"

...

```

Let's take a second to pause and learn more about this data set. First, look at the header row. Here are the column names we see:

* Trade name (looks like the business name)
* Postal city
* County
* Street address
* ZIP
* Notes

Immediately we can see that this is a list of pot shops with some basic location information and notes. If you scroll to the bottom of the file you can see that there are only 66 lines in the file which means there are 65 rows of data, since the first row contains column headers. You can also see that "Delivery" is demarcated in the Notes column.

This may not seem like a lot of information but we already know the basic structure, that the file is relatively small and that this is the data we are looking for.

Unfortunately, it's kind of hard to read the data in this format because everything is capitalized and runs together. Let's move into a spreadsheet for further analysis.

Open up Google Drive and drag the CSV file into the window. When you upload a CSV file to Drive, it defaults as a text file so double click on it and select "Open with Google Sheets". Sheets should have no problem reading it.

**A note on Google Sheets:** For the purposes of this course, Google Sheets will provide more than enough horsepower. If you're an Excel purist, go ahead and use that, almost everything will be identical. The reason I chose Google Sheets is because nearly everyone has free access to it and I use it in my work much more than Excel.

Now that you have the data open in a Sheet, feel free to explore the data. Some more details should pop out to you.

For instance, it appears nearly every shop is from Lane County, this is because I simplified the file for you. But I introduced a few errors to keep you on your toes.

At the end of the file, there is one shop from Lincoln County. Our goal is to find shops near the UO, so we can delete the Lincoln County row.

You can also see that the notes column includes a value called "Med Grade," which we don't really care about for this example. Let's simplify things and create a new column just for delivery. Go ahead and add a "Delivery" header. Now we're going to do some manual data manipulation. Go down the list and type "TRUE" in the cell if a shop has delivery. You can delete the Notes column when you're done.

Now we want to sort out just the shops that offer delivery. Let's freeze the first row (View > Freeze > 1 row). Click on the drop down arrow next to the Delivery column header and select "Sort sheet (A > Z)".

All of the shops without TRUE in the Delivery column should be grouped on top. Go ahead and delete that block of shops that does not deliver.

We're left with 24 shops. Let's cut some more. Shops in Cottage Grove, Florence and Veneta can be deleted because they're not near campus. This brings us down to 19 in Eugene and Springfield.

If you wanted to continue the example you'll need to do more research to see the delivery areas of these shops but at least you have a hard number of shops in Eugene and Springfield that deliver. To keep this example simple, we'll wrap up our research here.

How would you present this data? Well, you could map it (more on that later), but the simplest possible way is to just state the data in your story. No data visualization necessary.

## Wrap up

In our example, we got the data by downloading it, cleaned it up to narrow it down to just shops in Eugene/Springfield that deliver. You now would have to do further analysis to see which one's are nearby. And to present it you would include the data in the story.

At this point you should be familiar with:

* The basic steps of working with data
	* Get data
	* Clean data
	* Analyze data
	* Present (or share) data
* What CSV is
	* Comma-Seperated Values
* Opening a data set in a spreadsheet
* Using a spreadsheet to do basic cleaning

[Up next: More on cleaning data ...](https://github.com/uohack/data-literacy/tree/master/02-cleaning-data)

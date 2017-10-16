*Have suggestions or feedback? Please let me know! rob [at] uohack [dot] com or file a pull request!*

## Introduction

As we start every course, here is a simple workflow for basic data analysis.

* Get data
* Clean data
* Analyze data
* Present (or share) data

The majority of time doing data analysis is spent cleaning data, but just as much care should be put into sharing data. After all, your goal is to gain an understanding of the data set and provide a comprehensive and easily-understandable explanation of your findings.

You don't want a complicated visualization but you don't want to dumb down the data either. It takes a bit of tact and sometimes a good editor to help you distill thousands of data points into an easy-to-understand graphic.

All this is to say, use caution when sharing data. It's easy to inadvertently mislead your audience with a bad axis scale or lazy maps. Data visualizations are a powerful tool to share information, use care when creating them.

By the end of this course you should be familiar with:

* Why transparency is important when sharing data
* The difference between different types of data visualizations
* Be able to take basic location data and make a map

## Be open

Working with data can be fraught with pitfalls. One great way to avoid issues is to be completely transparent with your data. In addition to any visualizations or a story citing a data set, go ahead and make the whole data set public. You can also add a link to download the full CSV with your other analysis.

> “We often will embed our data onto our site in a visualization and in a form that allows for easy download of the dataset. Our readers can explore the data behind the stories through interacting in the visualization or using the data themselves in other ways. Why is this important? It increases the transparency of The Seattle Times. We are showing the readers the same data that we used to draw powerful conclusions. And who uses it? Our critics for sure, as well as those just interested in the story and all of its ramifications. By making the data available we also can enlist tips from these same critics and general readers on what we may have missed and what more we could explore — all valuable in the pursuit of journalism that matters.”
— Cheryl Phillips (The Seattle Times), taken from [The Data Journalism Handbook](http://datajournalismhandbook.org/1.0/en/delivering_data_0.html#_publishing_the_data)

In addition to sharing the original data, you can (and should) explain how you modified the data and completed your analysis. In academic studies this is typically referred to as the methodology and is slowly, but surely, [beginning to appear](https://www.washingtonpost.com/graphics/business/create-your-ideal-streaming-bundle/#methodology) more often in journalism.

This is especially important because data is so easily manipulated in spreadsheet programs and it's helpful to write out exactly what was done to that data.

Beyond simple transparency, there are [a number of additional ways](http://datavizproject.com/) to share information. Let's look at some of them now.

## Bar chart

Bar charts are great for showing comparison between different measures of the same value. For instance, a city's revenue over multiple years, or sales figures on different products.

This type of graph is the workhorse of data visualizations. More times than not, complex or fancy visualizations could be presented as a bar graph and be just as good, if not better. Remember, your goal is to analyze the data and present it to an audience so that they can understand it quickly. Bar graphs are very logical and easy to understand by almost everyone.

**Side note: Mind your scales.** Always set your y-axis scale to start at zero. Some graphing programs will change the axis so that it zooms in on the data area. This can be misleading. Remember your goal is to accurately represent the data, not provide a sensational graphic. Below are two examples of the same data. In the first, it appears as if the third value is several times as large as the first two, when, in reality, they are quite similar.

![bar chart - non-zeroed scale](https://user-images.githubusercontent.com/4853944/27066387-7d7961b6-4fb8-11e7-9cc5-a0c1325701ea.png)

![bar chart - zeroed y scale](https://user-images.githubusercontent.com/4853944/27066388-7d795748-4fb8-11e7-8f54-ebe268e5a192.png)

## Line graphs

Line graphs show how the same measure changes over a continuous period. Temperature over time is the most common use of a line graph because it is a single entity that changes throughout the day.

Like, bar graphs, they are simple and widely understood.

![line graph](https://user-images.githubusercontent.com/4853944/27620363-08edc75c-5b7e-11e7-9e0b-d656c6d4ebd3.png)


## Scatter plots

Scatter plots do a really good job of comparing two values on a spectrum and can reveal correlations between the values. Be careful though, correlation does not equal causation!

The example below depicts a comparison between years worked at a fictional company versus the employee's salary from the previous year. There's certainly a correlation, with the outlier being the new CFO. This makes sense because good workers are typically promoted over time, giving them a higher pay scale.

![scatter plot](https://user-images.githubusercontent.com/4853944/27620658-d7eddbf4-5b7f-11e7-9612-e8891a2b02b3.png)


## Pie graphs

Please don't use pie graphs. While they appear simple they often misrepresent the data. See below [tweet](https://twitter.com/MaxCRoser/status/857389434756505600) for more.

![screen shot 2017-06-12 at 9 50 35 pm](https://user-images.githubusercontent.com/4853944/27066459-384ddb84-4fb9-11e7-811f-0156171a091c.png)

## Tables

A table can show a simplified (but still accurate) version of your data. Instead of 1,000 rows and 12 columns, you can have three columns and five rows. This could include original data or data that you've generated (like percent change!).

Tables are easy to understand and allow for multiple types of data. Unlike graphs, you can mix words, currency, percents and regular numbers in one graphic.

If your data is complex and does not neatly fit into a graph, this is a great solution.

Remember, your goal is to simplify and share the data, so don't include too many data points.

## Mapping

If you have data tied to a geography, you may want to map it. This process can be much more difficult than other data visualization methods. For starters, there are a lot of different types of maps.

An example is single point maps, where you are simply plotting points based on latitude and longitude. These are far simpler to create than heat maps.

A word of caution: Maps can be deceptive. The classic example is county election maps. In fact, a [University of Michigan professor](http://www-personal.umich.edu/~mejn/election/2016/) addressed this issue after the 2012 and 2016 presidential elections. The two maps below represent the same data. If you ever want to map election data, I urge you to read his report [here](http://www-personal.umich.edu/~mejn/election/2016/).

![screen shot 2017-06-12 at 10 02 12 pm](https://user-images.githubusercontent.com/4853944/27066696-d5f39008-4fba-11e7-8363-679f61a0dacf.png)

Let's go through an example real quick of how I might make a simple map.

## Example

**Scenario:** You're an entrepreneur looking to buy up a big swath of land for a new, secretive venture. Let's just say you need a place to put a lot of servers and Lane County has agreed to give you a deal on taxes if you build here.

Because you want to water cool your servers, it would be best to build near a major river. But, you've heard recently about the potential for a massive earthquake and you're a bit paranoid that when "the big one" hits, dams could fail and your new building could be flooded.

Your goal is to go check out the U.S. Army Corps of Engineers' 2016 National Inventory of Dams and map out large dams in Lane County.

This example will show you how to query a government database, select the data you need and map it. First, we need to go get some data.

**Note:** You will once again need access to Google Drive for this example. Instead of Sheets, we're going to use an app called Fusion Tables. I'll explain how to install that below.

### Getting started

Head on over to the [U.S. Army Corps of Engineers 2016 National Inventory of Dams](http://nid.usace.army.mil/cm_apex/f?p=838:1:0::NO), which I found through a simple Google search. For the purposes of this example go ahead and select Academic. After you're granted access, go ahead and click on the Help button in the header. Before we query any data we need to figure out what data is available.

There is a lot going on on this page, but I'd say this is par for the course when it comes to government data. For now, let's focus on the NID columns. What do we want to know? Here are the columns I would be interested in:

* Dam name
* NIDID - helpful if we need to ask for more information
* Longitude - necessary for mapping
* Latitude - necessary for mapping
* County - so that we can limit our query to Lane County
* Purposes - this might be interesting
* Dam_height - this might be interesting
* NID_storage - this will tell us roughly how "big" it is
* State - so that we can limit our query to Lane County in Oregon

Okay, now that we have a sense of what data is available and what we'd like to get, go ahead and click on NID Interactive Report in the header. This will open up the dams database.

The first thing you should look for is how many rows are in this database. Right at the top it tells us that there are more than 10,000 rows. This is a federal database so that shouldn't be surprising. Before we proceed, let's try to cut this down to just Lane County, Oregon.

If you click on Actions there is a Filter option. This is what will allow us to make specific queries. When making queries it's often best to start with general information, like state, and get more precise as you go. This will help you cut the data set down quickly.

Select Actions > Filter. Select State as the column and type in "OR". We know this is how they format the state name by looking at the state column of the data available. We can safely assume that if Alabama is AL, then Oregon will be OR. Apply the filter.

This should reduce the data from more than 10,000 rows to only 869. That's great but we can simplify the data even more. Let's add another filter for County = "LANE". Again, we know that this is the format of the data by simply looking at the data.

In two queries we've gone from more than 10,000 rows down to 30. But we can simplify even more. Remember, we only care about the big dams. And there's a pretty clear distinction between the big and small ones if you look at the NID_storage column. Let's add another filter for NID Storage greater than 25,000.

**Pause:** Wait, 25,000 what?

If you go back over to the Help tab and select the question mark bubble next to NID_storage you'll see that dam storage is measured in acre-feet. That's good to know but it doesn't help me visualize how much water that is. Let's try [converting 25,000 acre-feet into gallons](https://www.google.com/search?q=25000+acre+feet+to+gallons). We find out that's 8.15x10^<sup>9</sup> gallons. That is a lot of water.

Let's take a look at what we've go now.

Back in the query table it looks like the dams I want but there's all this extra info that I don't need right now. And, more importantly, we're missing latitude and longitude, which we need for mapping. Go back to Actions > Select Columns. Feel free to drop any columns you don't need and add any that are of interest, including latitude and longitude. Apply your changes.

Now we have a data set we can do something with. But how do we export our information? There doesn't seem to be any button that says "Download CSV," although that would be nice.

It does look like it's in some sort of web table format. Let's try to just copy and paste it into an empty Google Sheet. It's so simple it just might work ...

![nid](https://user-images.githubusercontent.com/4853944/27067582-76917a02-4fc0-11e7-9c3b-3816a904674f.gif)

... and sometimes you get lucky.

There are some small problems though. The headers came through with white text on a white background and there's an empty column on the left-hand side. But those are easy to fix with some minor cleaning. Other than that, we did all the cleaning we needed to do with the queries.

That's one of the perks of getting access to the full database. You're able to get just the data you need. Nothing more and nothing less.

### Fusion Tables

Now, we're going to take the data from Google Sheets to Fusion Tables, but first you need to install Fusion Tables. In Drive select New > More > Connect More Apps and search for "fusion tables".

I know it's labeled as "experimental," but I've been using it for six years and it's always been experimental. The program is solid, don't worry about that.

After you have Fusion Tables installed, go back to Drive and select New > More > Google Fusion Tables.

Now, you can create an empty table, upload data (CSVs, other spreadsheet formats) or import data from a Google Sheet. We will be doing the latter. Select the Google Sheet where you put your NID data and click Select.

Next, Fusion Tables lets your preview your data but there shouldn't be any surprises here, click Next. Give your table a name and be sure to attribute the data to the U.S. Army Corps of Engineers 2016 National Inventory of Dams database and provide a link.

**Side note:** This is a fairly small data set but you can import up to 250MB of data. Because CSVs are such simple file formats, you can pack a ton of data into 250MB.

If you do not have Latitude and Longitude, Google can geocode addresses for you but it's not always perfect. Since we have those specific values, Fusion Tables has automatically created a Map tab for us. Click on it and you will see our nine dams plotted on a Google Map! Pretty easy right?

![basic map](https://user-images.githubusercontent.com/4853944/27621371-37c79d44-5b85-11e7-93b4-79ab688c04d5.png)

Those red dots are a little boring though. And we have some data that we could visualize with markers. Let's change those marker and have Google relate the marker colors to the dam's size.

#### Buckets

On the left-hand side of the window, select "Change feature styles..." and select the Buckets option.

In Fusion Tables buckets can access your data and apply that data to your marker. Select the radio button to divide into buckets and change two to three. Change the column to NID Storage and select the "use this range" option.

This is a nifty feature that applies the maximum and minimum values of the selected data set to our bucket marker options. These can be modified but it gives a good starting point. Then you can change the marker types and unfortunately there aren't a whole lot available. Your screen should match mine:

![screen shot 2017-06-12 at 11 08 38 pm](https://user-images.githubusercontent.com/4853944/27068281-1a41fab6-4fc4-11e7-8b2d-80d750c7630f.png)

Save that and you get a nice map where the markers correlate with some of your data.

![map with marker buckets](https://user-images.githubusercontent.com/4853944/27621458-b175ed76-5b85-11e7-800b-2eca8551e358.png)

You can also modify the windows that display information when you click on a marker.

#### Info window

To change the information given within the pop-up bubble, select Change Info Window... on the left-hand side of the screen. Here you can see the check boxes to add or remove any values to the info box. This is pretty rudimentary but would allow you to keep some data hidden from view.

If you want to get fancy with some minor HTML and CSS, click on the custom tab and experiment. Web designers will be disappointed because some HTML and CSS is automatically stripped by Google so you really have to work within their styles.

Example:

```HTML
<div class='googft-info-window'>
<b style="font-size:18px;">{Dam Name}</b><br>
<b>Storage (acre feet):</b> {NID Storage}<br>
<b>Primary Purpose:</b> {Primary Purpose}<br>
</div>
```

Result:

![custom info window](https://user-images.githubusercontent.com/4853944/27621570-907c1932-5b86-11e7-90c6-d1e6d404ad81.png)

#### Caution

In order to embed a Fusion Table map you have to make the Fusion Table public. This means that all of the data you uploaded will become public.

Do not upload any data to Fusion Tables that you do not want to become public. You should always refrain from publishing personally identifying information and use caution when deciding what data to include.

I generally follow this workflow:

* Clean/analyze full data set in Google Sheets
* When I'm ready to map, I create a new, simplified, sheet with only the data I want to publish
* Then I download that individual sheet as a CSV and double check my data
* When I'm ready, I create a new Fusion Table and upload that CSV so that my full data set in Google Sheets never touches my Fusion Table

## Wrap up

At this point you should be familiar with:

* Why transparency is important when sharing data
* The difference between different types of data visualizations
* Be able to take basic location data and make a map

In the [next course](https://github.com/uohack/data-literacy/tree/master/04-advanced-analysis) will go over advanced analysis with Python Pandas.

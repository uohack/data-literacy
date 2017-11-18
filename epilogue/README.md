# Epilogue

This week we wrapped up the data literacy workshop and I'm thrilled that more than 30 students participated in the four sessions over five weeks. We started with a blank slate and worked our way up through CSVs, spreadsheet functions, graphing, mapping and finally into Python.

This structure was set up to mimic a traditional college course and started out emphasizing concepts and best practices. As we moved forward, and I received feedback from students, the sessions incorporated more and more real-world tools.

This feedback, in the form of Google surveys, was sparse but indicated that students were happy with the workshop overall.

## Back story

I started putting this together eight months ago.

Before writing any lessons I read through the [Data Journalism Handbook](http://datajournalismhandbook.org/) and Matt Waite's [data journalism syllabus](https://github.com/mattwaite/JOUR307-Data-Journalism), both of which have since been updated. These helped me define a scope for the workshop and see ways other people are teaching data skills to those with little experience.

The most important thing I learned was that it's important to define the vocabulary around data before teaching methods.

I drafted an outline of what I wanted to teach and realized that it would take more than an hour or two to go over everything I wanted to teach. Eventually I settled on four sessions. The topics of these four sessions changed a lot during late spring and early summer but ended up being: basic process, advanced spreadsheets, data visualization, and advanced analysis.

This progression would allow me to lay out all of the concepts and slowly introduce the different methods.

Each session would include a lecture where I explained concepts and would end with an example using real data. Most of the examples centered around journalism, but would be applicable to other concentrations.

Dates were set and we did the workshop.

## What I learned

The workshop worked well in a lot of ways. As a class, with required reading and a better defined audience, it would have been more successful. Unfortunately, this workshop was not that.

There are three categories that I would improve on, if we did this workshop again. Each of which lead to one thing: simplification.

### Scope

Four sessions, listed at two hours a piece, was ambitious. (Insane might be a better word.)

I'm glad I did it, but trying to get students to show up for just one session was hard enough. Four sessions was never going to work.

Also, the third week was Halloween, so we had to extend the workshop to five weeks and take a break in the middle. Five weeks is half of a term for UO students and a huge investment.

On top of that one of those weeks was a midterm week. To be honest, I'm surprised anyone showed up. I don't think I would have.

For a workshop like this to succeed it has to be much smaller in scope. One, maybe two sessions is much more realistic.

Regardless, I was able to get students to show, and a handful were consistent too. That's amazing and a huge accomplishment in my eyes.

But, keeping their attention for more than an hour was difficult. During the first session I realized how difficult two hours would be and planned to cut down the remaining sessions to an hour and pick up the pace a bit.

Even with these changes a student fell asleep during one session. He wasn't just taking a little nap, he was full on passed out for a decent chunk of the lecture.

So … that wasn't great.

In any case, the scope of the workshop was probably intimidating to the average student with pre-existing obligations. At least two students approached me with interest but could not attend because of schedule conflicts.

Simplifying the workshop into fewer sessions might help this.

#### Flash vs. substance

In the future, if I do this again, I would create two 1-hour sessions. The first would be an introduction and free, easy tools for students to use. The second would introduce advanced tools like Python or R for students that are comfortable with spreadsheets. Each one of these sessions would consist of quick hit examples, with links to more information.

*NOTE: This is dumb. I think it's important to mention this conflict but I don't think this is the right place.*

One of my big concerns with following the plan above is that I won't provide students with a proper foundation of data literacy. It would be more flash with little substance.

Obviously, it would be much more exciting and keep their attention, but it wouldn't cover the important basics and the ethics I tried to mix in. There has to be a happy medium.

### Student interest

It seems like the content and structure (lecture, example) were well-received overall.

"It was explained well, and having the chance to mess around with actual data was very useful," one student said.

Another said: "The lecture was a little long, and I would have liked more time to interact with the example. The vocab was explained clearly."

But it was difficult to get a read on what exactly students wanted to learn, despite asking several times in different ways.

This is probably a symptom of students not fully understanding different skill sets needed for different types of data work. Maybe an overview of different types of jobs associated with different types of data sets would be helpful. This would be similar to creating [personas](https://ux.stackexchange.com/a/103224) in UX testing.

One thing was clear: Quite a few students were interested in data viz, a dense topic that could consume a full-time class for more than a term.

I still struggle with how much time should be spent on this. There are plenty of free tools available that I can demo, but the high water mark of modern data viz (think NY Times or Washington Post) really sits with JavaScript or other programming languages, which cannot be taught in a data literacy workshop.

Of course, I tried to expose students to examples of brilliant, advanced data viz, but when they ask how to do something similar I am forced to refer them to online resources.

I'm not sure how to solve the issue of determining what students are interested in. Creating sessions built around personas might be one way to address that, with one being a datz viz producer.

### Student experience

It was common to hear some students complaining of the pace being too fast and others complaining the pace was too slow.

It's encouraging to know that I found a middle ground, but college students have vastly different experiences with data and I don't know how to best engage with them all. This is a basic issue of a presenter not knowing their audience.

Simple data tools like spreadsheets provide a good example of this issue.

Some students had high school classes that taught spreadsheet techniques as advanced as pivot tables, while others had no formal spreadsheet training.

How am I supposed to create an engaging lesson given the wide range of expertise?

My best guess is to create fast-paced lessons that start with the basics and quickly move to more complex material. This gives a good foundation for those that need it.

### Changing content

I have to take a moment to give credit to teachers everywhere, because I never understood how difficult it is to keep a class current. I created a curriculum in the spring and it was outdated by the fall.

Google's release of [Colaboratory](colab.research.google.com) the week before the final session provides the most striking example of this.

[Jupyter Notebooks](http://jupyter.org/) have been the industry standard for creating sharable, interactive Python notebooks for the past few years. So I created a Jupyter Notebook for the final session to demonstrate [Pandas](https://pandas.pydata.org/) back in the spring.

Then, Google decided to release Colaboratory, a Google-doc-like version of Jupyter Notebooks. No longer do you have to go through the setup process of installing Conda or VirtualEnvs, Python, Jupyter, etc. to run a notebook. You just have to request access to Colaboratory and Google would provide a virtual machine, loaded up with Python, Pandas and a host of other modules for free.

I realized that this would be perfect for the final session and quickly worked to convert everything over to Colaboratory. It was great and I am very excited about the potential Colaboratory has in education.

But it was a real pain to learn a new tool (discovering some bugs along the way) and then teach it two days later.

Another example: On the day of the third session (that covered data viz) I saw [several tweets](https://twitter.com/dancow/status/927935426953805824) about early 1900's NY Times data viz. I scrambled to include them into my slide deck and they went over well, but it took a fair amount of work.

Each weekend I re-wrote the upcoming session. This was somewhat planned, because I knew the online documentation would need to be modified for presentation. But I had underestimated the time it would take to create the presentation materials and find current examples.

## Wrap up

The goal of this workshop was to create a basic data literacy curriculum for students at the University of Oregon who wanted to learn how to work with (relatively) small sets of data. I think we accomplished this.

I'm not sure I followed the path of least resistance though.

Data literacy is a massive topic that cannot be taught effectively as a workshop. This is especially true for a workshop that was set up to mimic a traditional class structure. Workshops need to be more simple.

I think a basic introduction with simple tools and vocabulary in an hour-long presentation would give us the best chance to get students to show up, while providing a decent foundation.

Following that with an hour-long workshop with skill set personas and real-world examples could incorporate advanced strategies and would be a good way to add depth for those that are interested.

Additional documentation online could fill out the gaps in a comprehensive data literacy program.

## Thanks

If anyone has read this far, thank you for your interest. Feel free to drop me a note (rob [at] uohack [dot] com), I'd love to talk about it more.

Thank you to Carolina Hernandez, Jonathan Cain and Sarah Seymore from UO Libraries for reaching out and supporting the workshop.

Thanks to Peri Langlois and Kenny Jacoby who acted as ambassadors and encouraged their fellow students to attend.

And thank you to John Heasly for helping edit the each session.

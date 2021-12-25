# Dev diary

## Day 0

Day 0 is when I first received the email containing the tasks. It was around 10pm or so.

I started by looking at the tasks from a general point of view, making sense of what's required,  and thinking about how much time they would require.

What first stuck out to me is how unfamiliar I was with the requirements of those tasks. It was out of my comfort zone, so I had to think about all the knowledge I had accumelated, and how I should go about implementing those tasks.

For the plotter, I had to think about what gui framework, and by extension, what programming language I would use. The top 2 choices were C++/QT and **Python/Tkinter**. I decided to use python in the end because I'm more familiar with its scientific eco system.

I had considered Matlab, with which I've already implemented very similar applications, however considering that my employer in the future wouldn't want to purchase a matlab licence, I opted for the Free and Open source solutions.

As for the TopologyAPI task, it was a much simpler choice. I could've used either Java or C#. Both are enterprise object-oriented languages, but I chose **Java** because:  

* I'm more familiar with Java, having implemented multiple projects using it.

* I'm familiar with Gradle and Maven on a superficial level as build tools specific for the java world

* IntelliJ IDE provides much better developer experience than Visual Studio, and considering I have pretty much 10 days to finish the tasks, I didn't want to spend time fighting my tools.

* All java pointers are smart pointers, since it's run in a managed envioronment. [Stack overflow thread explaining this.](https://stackoverflow.com/questions/4783636/are-there-smart-pointers-in-java)

In conclusion, I chose what I did based on familiarity and const to employer.

## Day 1

On day 1, I decided to work on the Topology API.

First thing I did what to think about what Build tool to use. after some research, I decided to use Maven because I learned it's opinionatd.

Then, I spent time learning about this unfamiliar tool, in order to use it in my project.

Next, I spent some time to understand the specification of the data, and the requirements of the api library.

I also set up some set up a basic UML class diagram using PlantUML, to serve as a basis for desgining the project once I set it up.

Since I'm working with JSON files, I opted to use the GSON library.

I spent a large portion of my working time this day learning about Maven. It proved to be a task more challenging than I thought. It was hard to find good online resources for beginners with build systems, though I managed to find some videos that together gave me a nice overview about the system.

After finally attaining a good understanding of Maven, It was time to think about the organizaion of classes. This time was spent also learning about GSON.

## Day 2

The beginning of the day was marked with the email I received from MasterMicro about some clarifications I asked about the tasks. I then set out to write the README.md for the second task. For the next while I would be looking at the GSON documentaions, in order to understand deserializers.

Much of the day was spent creatign the deserializer, but I was done before the end of the day.

I had some time left, so I looked into junit, the tool I would use for testing.

## Day 3

With much of the essentials already in place, I quickly began working on the other required functions. with topologies already in memory, deleteTopology and queryDevices were easy to implement.

At first I was looping through the list to find a topology given an Id, however that was ineffecient, so I created and in-memory index using a HashMap. Now I could check for the existance of topologies in O(1) time! not to mention, every operation that required an id is O(1) now.

I implemented some tests, and updated the interface a bit.

Today I had a college classes, so work had to be cut short. After returning, I implemented some more tests, and fixed some typos.

Thinking I had reached a good stopping point, I decided to look into the Plotter task again. I followed a simple tutorial and got a gui app to plot a simple function when I click a button.

However, I soon came to realize, again, that tKinter is an absolute pain to use. So I decided to scrap the project and restart, this time with PyQt5, which turned out to be a good choice.

I followed a simple stack overflow answer and got a gui app to plot a simple function when I click a button. I'm expecting this class not to take more that a day.

## Day 4

I started the day by looking flesh out the gui. this was easy because PyQt5 is simple and friendly. I added text boxes for input which worked pretty well. The font was small, but styling is easy since PyQt5 uses a stylesheet notation similar to CSS.

Getting a nice gui working was only the first step. No I focused my attention on learning sympy.

Overall, it was pretty simple and straightforward, and although I faced some annoying issues at times (problems evaluating a symbolic expression) I got it done. I added some test as I went, thought because most of the logic was tucked away in the plot function, it was hard to write a comprehensive test suit. I spent a long time thinking about how to restructure my code to allow for better testing, but no good changes came to my mind.

The hard part is figuring out every wrong input a user could enter, and handle all those cases.

Tomorrow I would be finalizing this task, and get back to the second task. It seems this task will take more than a day, if we include documentation and more tests, however, it is essentially done.

## Day 5

I started working on the README, thinking about all the relevant information I should include. I'm also thinking about how to document my functions, if it's even necessary. This first task.

A couple hours later and I'm pretty much done with documenting the task. Handled some more error cases, but I don't think I need to loke at this task anymore. Of course, I might remember that I forgot something and return later, but all requirements should be implemented.

I got back to the topology task, and began working on the writing method. It turned out to be a breeze. What I learned from implementing the deserializer came in handy, and I was finished in not time.

I implemented some tests for the writer next. This turned out to be particularly tricky, as json strings weren't guaranteed to be exactly the same. I settled on this method:

* Read from memory using the read method of a particular instance of the api class
* write to disk in a seperate file
* Read that new file using the read method of *another* instance of the api class
* compare different parameters and function outputs of those two api instances.

Quickly then, I implemented the last remaining method, queryDevicesWithNetlistNode. Working on these last two requirements made me proud of the way I structured my classes, as implementing everything turned out to be incredibly simple when every class needs only to focus on a small part of the overall pictures.

By implementing that last method, all the functional requirements are done, and essentially most of the non-functional requirements. Tomorrow I would be focusing on documenting the API and classes, as that's the only taks that remains. Tomorrow should be the last day I work on these tasks in earnest, and I would only revisit them to think about some tests, clean up, or failure cases.

## Day 6

The day started as planned. I've added documentation for API methods, and generated some javadoc html files and hosted them on github pages. They can now be accessed from the web. Doing some clean up, I've come to learn about a new feature introduced in java 15: Records.

While refactoring, documenting, and cleaning, I opted to create an interface containing the API methods. Thanks to IntelliJ's powerful refactoring tools, this was done immediately and easily, and all tests passes no problem. For the coming few day, I'll probably just be thinking about more tests and ways to break the program, though I believe spending any more time is not worth it. I'm essentially done, docs and all.

Thus, I decided to submit today. 6 days before deadline, nice!

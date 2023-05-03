Download Link: https://assignmentchef.com/product/solved-cs341-project-4-web-based-covid-19-app
<br>
The goal of Project #04 is to extend an existing web app that retrieves information about COVID 19 mitigation measures as well as the numbers across USA.  A working application is provided that does 3 things:

<ol>

 <li>Tests the database connection</li>

 <li>Retrieves information about the regions which have been affected by COVID 19</li>

 <li>Analyses the database to form meaningful graphs regarding COVID data up until April 1<sup>st</sup> week</li>

 <li>Look into state wise mitigation strategies formed over USA</li>

</ol>

The app is based on the MVC design pattern, using ASP.NET, C# and ADO.NET.  You must work within this design by extending / creating Views and Models.  To run the provided application, login to Codio and open <strong>project 04</strong>.  Then open a terminal window, change directory to “covid-web”, and “dotnet run” to start a web server (<em>Kestrel</em>) and load the web app:

The web server is now running, waiting for clients to connect via a web browser.  The simplest way to connect is via the “Box URL” command in the next to last menu in Codio.  Drop the menu and select “Box URL”:

The “Box URL” command will browse to the web app and trigger the loading of the home page. After accepting the cookies at the top, the navigation bar below will allow you to access the various functions the application should implement.

The Home Page is as below:

.

The Infection Total Page shows the comparison between positive and negative cases.

The State Census tab pulls the census information of a state:




<h1>Assignment</h1>

The assignment is to extend the given web application in the following ways.

We have 3 major tables given: US Census Data, US COVID Data and US Mitigation Data.




From the above, we have characterized a tabular form of the census data provided a state.

<ol>

 <li>Your <strong>first task</strong> is to graph the tabular form of census data in the form of a line chart.</li>

</ol>




We have shown a way to compare positive vs negative cases in a state with date as x axis.

<ol start="2">

 <li>Your <strong>second task</strong> is to implement a graph displaying the total number of hospitalizations and (hospitalized) and total number of deaths (death) over the dates available for a state which must be provided via a text box. Use us_states_covid19_daily table for this purpose. The graph must enable users to hover over the line and show the raw data for that date. Proper legends are to be present.</li>

</ol>




<ol start="3">

 <li><strong>Next</strong>, implement a way to compare the positive case increase (positiveIncrease)and negative case increase (negativeIncrease) across 3 different states. Choose the 3 different states through either a text box or a dropdownbox. Proper legends are to be present. For more information on drop down box go through <a href="http://csharp.net-informations.com/gui/cs-combobox.htm">http://csharp.net-informations.com/gui/cs-combobox.htm</a></li>

</ol>




<ol start="4">

 <li><strong>Last</strong>, combine US COVID Data and US Mitigation Data by implementing a graph with total cases (total) of a state and by using marker points to find any news (DescriptionOfMeasure) for that day for that particular state. Proper legends are to be present.</li>

</ol>




You should plan to work on <strong>Codio</strong> since this is how submissions will be collected (we will not be using Gradescope for this project, nor Blackboard).  You can work in outside Codio if you want, but then you’ll need to upload your final project to Codio for submission.  To work in <em>Visual Studio for Windows</em> you’ll need to first run <em>Visual Studio Installer</em> to add the ASP.NET workload.  Then you can login to Codio, export the provided files to your local system, unzip, and then open the provided .csproj file.  You should then be able to run (F5) from within Visual Studio.

<h1>Getting Started with ASP.NET</h1>

<strong>ASP</strong> stands for “Active Server Pages”, and the <strong>.NET</strong> refers to the .NET family of languages:  C#, F#, VB, etc.  Most web apps today using a combination of technologies, in our case you can think of ASP.NET =&gt; HTML + C#.  This is a server-side technology, which means that




<ol>

 <li>The user (“client”) uses a browser to request a web page — from any platform, using any browser</li>

 <li>The web server (“server”) loads the web page (in our case a mix of HTML and C#), executes the C# to produce more HTML, and returns pure HTML to the client</li>

</ol>




At this point the client-server interaction is done; the user might request another web page from this site, or surf away to another web site.  A simplified visual is shown to the right.  The difference is that where you see “read file”, think “read file and execute C#”.




Since web applications have a very different architecture, we are providing a working application to help you get started.  Since there are many moving parts to an MVC-based solution, you’ll need to learn your way around app.




<ol>

 <li>Login to Codio using your credentials.</li>

</ol>




<ol start="2">

 <li>There are 2 folders: “covid-web” is the provided web app, “__save” is a backup copy. Run the provided app by changing the working directory to covid-web:</li>

</ol>

cd covid-web

dotnet build

dotnet run




<ol start="3">

 <li>Stop and reflect for a second… The database (our data store) is running in MySQL.  Our web app (our data access and logic tiers) is running in Codio.  But a web app requires a web server, so that is *also* what we’re running when we say dotnet run — we are starting a web server (Kestrel), which in turn is hosting our web app (COVID).  That’s why you must leave the program running in Codio while you run and test your web app.  When you need to make changes to your web app, you’ll stop the web server by typing Ctrl+C in the terminal window.</li>

</ol>




<ol start="4">

 <li>Assuming the web server is running, the last step is to browse to your web app. In theory your Codio VM is public on the internet, but in reality (due to security concerns) it can only be accessed by you.  In particular, it can only be accessed by the browser you have open, since this is the only one that has login credentials to access Codio.</li>

</ol>




The easiest way to access your web app is to use Codio’s “access” menu, which is the next to last menu in Codio. So, once your build and run the program, click on Project Index which will drop the menu. Click on Box URL, this should open a new tab in your browser, and automatically surf to the web app you have running.

The first time you’ll see a “cookie” dialog across the top, which you should accept.  Then you’ll see the web app’s home page with a menu bar above. You can then view and navigate across the tabs.




<ol start="5">

 <li>At this point, all is well, and you have a working web app that you can extend. Close the browser tab containing this web page, and then stop the web server by clicking in the terminal window and pressing Ctrl+C.</li>

</ol>

<strong><u> </u></strong>

<strong><u> </u></strong>

<strong><u>NOTE</u></strong>:  if you take a break or walk away from Codio for an extended period of time, the Codio system will timeout and your login credentials will expire.  If you find yourself in a situation where the web app does not open, the solution is to logout of Codio, close the browser, reopen the browser, and log back into Codio.  Then all should be well.




<ol start="6">

 <li>As discussed earlier, the web app is using a Model-View-Controller architecture, where the Controller portion is supplied. Our job is to provide the Models and Views that constitute our app. The views form the tabs of our webpage which uses the models to implement them.</li>

</ol>

<h1>Debugging</h1>

Debugging is hard in web apps since the C# code runs on the server — e.g. output from System.Console.WriteLine is not visible.  One approach is to print debug to your web page:  add data members to the model, and then display these data members in the view using HTML and C#:

<strong>&lt;br /&gt;</strong>

<strong>Data member contains:  @Model.NameOfDataMember</strong>

<strong>&lt;br /&gt;</strong>

For an example, review how the Connection view and Connection model work together to display the status of the database connection.




<h1>Requirements</h1>

You are required to use ASP.NET, ADO.NET, C#, following the MVC design pattern which strictly separates the model from the view.  You may use LINQ to SQL if you want to experiement with that technology.




You are required to use <strong>try-catch-finally</strong> to perform basic error handling.  If an error occurs, at the very least a meaningful error message (based on the error that occurred) should be displayed in the relevant web page.
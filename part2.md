# Workshop: Creating a Custom Theme with SASS
This workshop will focus on the tools and techniques for creating a custom theming using the SASS source code provided with the Oracle JET distribution.

While this topic is slightly dated as we move toward the use of CSS Variables for theming (available late 2019) the concepts and tooling will be very similar and this is a good topic to have a basic understanding of.

The custom theme changes will focus on the following areas:

* Base brand color
* Font
* Font-size/color
* Button characteristics

## 1: Get Started

For this part of the workshop, we will assume that you have already taken Part I, and have JET properly installed and working.

If you do not have JET installed, please go back to Part I and follow the steps through at least section 1b.

It is also assumed that you already know something about [SASS](http://sass-lang.com/) (Syntactically Awesome StyleSheets). It's not a requirement that you know SASS for this workshop, but if you go any deeper into creating your own theme, you will need to know SASS itself. Some good resources for learning about SASS can be found at:

* [SASS Documentation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)
* [YouTube video series](https://www.youtube.com/playlist?list=PL2CB1F80266E986EA)

### (a) Downloading the sample project

The workshop will use a sample project that has already been put together for you. This project has every JET UI component included in it so that you can very quickly see the effect your custom theme changes will have on JET itself.

1. Download this [sample project](https://github.com/peppertech/OracleJETWorkshop2019/wiki/project/ThemeStarter.zip) and unzip it into a project directory.
2. Open a terminal/command window and goto the directory that you unzipped the sample project into.
3. Change into the *ThemeStarter* directory.
4. From the root of the project folder run this command

```js
ojet restore
```

When the restore command is completed, you should see something like the image below.

![completed restore](images/p2-img001.png)

### (b) Running the sample project

As with your previous work with the JET CLI, you can build and serve the project. Run the below command to see the what the project looks like by default.

```js
ojet serve
```
After you've had a look around, press Ctrl-C in the command window to stop the server.

### (c) Add SASS

Now that you have the sample project working, let's set things up for working with SASS.  From the command line, run the below command.

```js
ojet add sass
```

You will see the library *node-sass* being installed. Once it's completed, you're ready to create your own theme.

### (d) Create custom theme

To create your own theme, you will run the below command. The new theme will be added under the /src/themes folder. **All** work that you will be doing will be in this directory.  

```js
ojet create theme myTheme
```
After your theme has been created, look in the /src folder and you should now see a new /themes folder and inside of that, your /myTheme folder.

![mytheme folder structure](images/p2-img002.png)

**Tip:** The /themes directory that you will see off of the root of the project can, and should, be ignored. It's created as part of the build process. You should not edit or change files in this directory as they will be overwritten. Always do your development work in the /src folder.

You are now ready to start making your own theme!

**Note:** Make sure you have a CSS editor, such as Visual Studio or Apache NetBeans, and open the sources created in step 1 above. Simply using Notepad will not provide the syntax coloring and other helpful CSS editor features. 

## 2: Understanding the Theme structure

As you've seen in the directory structure image above, your new theme has SASS source code (.scss) files for multiple platforms.  When you build a JET application using the JET tooling, a platform specific theme is automatically added to your app for the platform you are targeting.  You can override this by adding the --themes argument to the build/serve command.

For this workshop, you are going to focus on the /web theme only.  You should explore the other themes at another time, to compare some of the differences.

### (a) File dependencies

1. Change into the /src/themes/myTheme/web directory.

    You will see two files by default.
    * _myTheme.web.settings.scss
    * myTheme.scss

2. Open the myTheme.scss file in your editor of choice.

As you will read in the comments at the top of this file, this is the main aggregator for any other SASS source files that you will create for your theme.

The way that theming works with JET, is that the base Alta theme is available by default, and then changes are made to override the various settings where wanted.  Anything that is not overridden will be managed by the base .scss source.

The overridding settings file in this case, is called *_myTheme.web.settings.scss*

### (b) The settings file

Open the *_myTheme.web.settings.scss* file in an editor of your choice.

**Tip:** You may wonder why the settings filename starts with an underscore ( _ ).  In the SASS world, this tells the SASS compiler that this is a *partial* file and that it should not be compiled by itself into a .css file. It must be combined with something else.

One of the first things you will see about the settings file is that it's very large.  There is a lot of information in this one file.  If you plan to create a completely custom theme, it's recommended that you read through the comments in this file completely.  Naming conventions, path structures, and best practices are all discussed throughout the document. It is also recommended that you read the [Theming Chapter of the JET Developers Guide](http://www.oracle.com/pls/topic/lookup?ctx=jet620&id=GUID-E42E9B44-CD53-41D5-A386-9E941A9471CE). 

When you have completed the desired changes to the settings file, and your custom theme looks the way you want it to. It's recommended that you remove all of the remaining commented variables to decrease the size of the file and help with future compilation times.

## 3: The basics

Now that you've looked over the settings file, and how the files are aggregated into a file .css file when compiled, it's time to start making changes.

### (a) Brand color

1. In the settings file (_mytheme.web.settings.scss) search for the variable *brandColor*.  Go to the third instance of the name.  It should take you to approximately line 291 in the file, and looks like this:

![brandcolor variable](images/p2-img003.png);

Uncomment the line for this variable, as well as all of the 

### (b) Font-family (web fonts)

### (c) Buttons

## 4: Loading your custom theme in Visual Builder


```html 
<oj-timeline id='tline' 
             :aria-label="[['Single Series Timeline Demo. Current date is ' + currentDateString()]]"
             minor-axis='{
               "scale": "weeks",
               "zoomOrder": ["months", "weeks", "days"]
             }'
             major-axis.scale='quarters'
             start='[[new Date("Jan 1, 2010").toISOString()]]'
             end='[[new Date("Dec 31, 2010").toISOString()]]'
             selection-mode='single'
             reference-objects='[[referenceObjects]]'
             selection='["e4"]'
             series='[[timelineSeries]]'
             style='width:100%;height:350px'>
</oj-timeline>
```

### (b) Set Up the Service Provider

### (c) Create a Variable

### (d) Install the Web Component

### (e) Use the Web Component

### (f) Tweak the Web Component

![can there ever be enough Pugs in the world?](images/pic-001.jpg)
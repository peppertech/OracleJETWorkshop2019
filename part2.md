# Workshop: Creating a Custom Theme with SASS
This workshop will focus on the tools and technicques for creating a custom theming using thes SASS source code provided with the Oracle JET distribution.

While this topic is slightly dated as we move toward the use of CSS Variables for theming (available late 2019) the concepts and tooling will be very similiar and this is a good topic to have a basic understanding of.

The custom theme changes will focus on the following areas:

* Base brand color
* Font
* Font-size/color
* Button characteristics

## 1: Get Started

For this part of the workshop, we will assume that you have already taken Part I, and have JET properly installed and working.

If you do not have JET installed, please go back to Part I and follow the steps through at least section 1b.

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
After you've had a look around, press Ctrl-C to stop the server.

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

**Tip:** The /themes directory that you will see off of the root of the project, can and should be ignored. It's created as part of the build process. You should not edit or change files in this directory as they will be overwritten.

You are now ready to start making your own theme!

### (c) Creating an Oracle JET Application



![Testing image only](images/pic-001.jpg)

**Note:** Make sure you have a JavaScript editor, such as Visual Studio or Apache NetBeans, and open the sources created in step 1 above. Simply using Notepad will not provide the syntax coloring and other JavaScript editor features you need. 

## 2: Understanding the Theme structure

### (a) File dependencies

### (b) The settings file

## 3: The basics

### (a) Brand color

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


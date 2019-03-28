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

The workshop will use sample project that has already been put together for you.  This project has every JET UI component included in it so that you can very quickly see the effect your custom theme changes will have on JET itself.

1. Download this [sample project](https://github.com/peppertech/OracleJETWorkshop2019/wiki/project/ThemeStarter.zip) and unzip it into a project directory.
2. Change into the *ThemeStarter* directory


### (b) Running the sample project

```js
ojet serve
```

### (c) Add SASS

```js
ojet add sass
```

### (d) Create custom theme

```js
ojet create theme myTheme
```

**Tip:** If the above shows that you have an **earlier** version of the Oracle JET command-line interface, i.e., below 6.1.0, please reinstall Oracle JET, using the command in step 1 above to do so.

You are now ready to get started with Oracle JET!

### (c) Creating an Oracle JET Application

**We will use the Oracle JET 'basic' template so that we have the simplest possible Oracle JET application, enabling us to focus on component creation in the next section, and not on routing. The 'basic' template will give us an 'index.html' file, where we will design the component, with the data initially hardcoded and coming from the 'src/js/appControler.js' file.**

1. Run the following in the terminal:

```js
ojet create BasicApp --template=basic
```
**Note:** This process may take some time.

2. CD into 'BasicApp' and run the following in the terminal and look in the browser:

```js 
ojet serve
```

After a few moments, you should see an empty page in the browser:

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


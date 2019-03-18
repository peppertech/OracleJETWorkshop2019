# Workshop: Develop a Web Component for Visual Builder Interaction with Oracle ERP
This workshop shows how to create a web component for 
use with Oracle JET or Visual Builder, containing a JET Timeline component 
that will read data from an Oracle ERP service showing invoice information.

## Part 1: Get Started

All the activities in this section should be done on the command line in a Terminal window.

### (a) Getting the Node Package Manager

Node.js is a JavaScript runtime, which provides 'npm', that is, the Node Package Manager, that you will use in the sections that follow to set up the environment that you need.

To verify the Node Package Manager is installed, run the following, which should show you the version of the Node Package Manager:
```js #button { border: none; }   
npm -v
```

If version 5.6.0 or higher is not shown, you need to install the latest LTS version of Node.

Download and install the latest LTS version of Node from http://nodejs.org.

### (b) Getting Oracle JET

In this part, you install the Oracle JET command-line interface.

1. Install the Oracle JET command-line interface:

```js #button { border: none; }
npm install -g @oracle/ojet-cli
```

2. Run the following to check installation succeeded and to see the available commands:

```js #button { border: none; }
ojet help
```

You should see information about Oracle JET command line arguments.

3. Run the following to check that you have the correct version of Oracle JET:

```js #button { border: none; }
ojet --version
```

You should see this:

```html #button { border: none; }
Oracle JET Command Line Interface, version: 6.1.0
```

**Tip:** If the above shows that you have an **earlier** version of the Oracle JET command-line interface, i.e., below 6.1.0, please reinstall Oracle JET, using the command in step 1 above to do so.

You are now ready to get started with Oracle JET!

### (c) Creating an Oracle JET Application

We will use the Oracle JET 'basic' template so that we have the simplest possible Oracle JET application, enabling us to focus on component creation in the next section, and not on routing. The 'basic' template will give us an 'index.html' file, where we will design the component, with the data initially hardcoded and coming from the 'src/js/appControler.js' file.

1. Run the following in the terminal:

```js #button { border: none; }
ojet create BasicApp --template=basic
```
**Note:** This process may take some time.

2. CD into 'BasicApp' and run the following in the terminal and look in the browser:

```js #button { border: none; }
ojet serve
```

After a few moments, you should see an empty page in the browser.

3. Make sure you have a JavaScript editor. Simply using Notepad will not provide the syntax coloring and other JavaScript editor features you need. 

## Develop the Web Component

### Create the Web Component

ojet create component my-invoice-timeline (use their initials). Use your company prefix, to make your Web Component unique and not conflict. Never use oj- which is reserved for the JET team.

### Set Up a Timeline Component from the Cookbook

In the View, drop in a timeline component, copied and pasted from the Cookbook, with static data from the Cookbook: https://www.oracle.com/webfolder/technetwork/jet/jetCookbook.html?component=timeline&demo=basicTimeline

We will provide the erpData.json file, with local data in the component – local method and remote method. Show how to customize attributes of the timeline based on the data coming in – thumbnail and svg styling.

Form layout with two select boxes, one for the start year and one for the end year. Year generator, generates years. Set start date and end date of our timeline.

### Use Real Data

The above works against local data. Create a connection to the data using an AJAX, using Basic authentication, so no getJSON, using an array data provider, to the real URL.

Go to index.html, items=[[dataProvider]], add a property in component.json file called 'items', type 'oj.DataProvider', displayName and description must be changed as well for Visual Builder.

In timeline Web Component ViewModel, read the data coming in from the consumer.

## Integrate into Visual Builder

### Set Up the Service Provider

### Create a Variable

### Install the Web Component

### Use the Web Component

### Tweak the Web Component


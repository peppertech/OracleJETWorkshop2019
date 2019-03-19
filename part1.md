# Workshop: Develop a Web Component for Visual Builder Interaction with Oracle ERP
This workshop shows how to create a Web Component for 
use within an Oracle JET Core application or within Visual Builder, containing a JET Timeline component 
that will read data from an Oracle ERP Service, showing invoice information.

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

## Part 2: Develop the Web Component

In the Terminal window, first kill the 'ojet' process, using Ctrl-C. This is because you will be adding new files in this section. Whenever you add new files, first kill the 'ojet' process in the Terminal window, using Ctrl-C, and then, after creating new files as in step 2 below, restart the 'ojet' process via 'ojet serve'. The 'watch' process, provided by 'ojet', will only look for changes to existing files; it will not build and re-serve new files.

### (a) Creating a Web Component

1. In the root of your project, run the following:

```js #button { border: none; }
ojet create component my-invoice-timeline
```

**Note:** Instaed of the 'my-' prefix, use your initials or use your company prefix, to make your Web Component unique and not conflict with others. Remember to never use 'oj-' as prefix, which is reserved for the Oracle JET team.

2. Take a look at your source structure, find the new 'my-invoice-timeline' Web Component, in the 'src/js/jet-composites' folder, and explore its structure. In particular, notice that the message 'Hello from Example Component' is defined in 'my-invoice-timeline-viewModel.js' and rendered in 'my-invoice-timeline-viewModel.html'.


3. Load the loader, i.e., 'my-invoice-timeline/loader', at the end of the dependency list passed into the define() call of the 'src/js/appControler.js', as shown below:

```js #button { border: none; }
define(['ojs/ojcore', 'knockout', 'ojs/ojknockout', 'my-invoice-timeline/loader'],
```

4. Use the 'my-invoice-timeline' custom element a few times in 'index.html', as shown below, **within the 'div' that has its role set to 'main'**.

```html #button { border: none; }
<my-invoice-timeline></my-invoice-timeline>
<my-invoice-timeline></my-invoice-timeline>
```

5. Run 'ojet serve' in the Terminal again, and notice that you now see two instances of the 'Hello from Example Component' message from the 'my-invoice-timeline' Web Component.

**Note:** Remember that you need to run 'ojet serve' to serve the application, since you killed the 'ojet' process in step 1 of this section.

### (b) Set Up a Timeline Component from the Cookbook

We are going to take the [Single Series Timeline from the Oracle JET Cookbook](https://www.oracle.com/webfolder/technetwork/jet/jetCookbook.html?component=timeline&demo=basicTimeline) as a starting point and then customize it to our requirements in subsequent sections.

1. Put [this static data](https://gist.github.com/peppertech/52bee52327ae9a1c0958559da78508a8) into a file named 'data.json', in a new folder named 'data', in the 'src/js/jet-composites/my-invoice-timeline' folder. Load it using the 'text!' protocol, into the Web Component as shown below in the 'my-invoice-timeline-viewModel.js' file, and make sure to reference it in the callback function, for example, as 'data' shown below, in the same order as in the define statement:

```js #button { border: none; }
define(
    ['knockout', 
     'text!./data/seriesOneData.json', 
     'jquery', 'ojL10n!./resources/nls/my-invoice-timeline-strings'], 
        function (ko, data, $, componentStrings) {
```
        
2. In the 'my-invoice-timeline-viewModel.js' file, replace the example variable 'self.messageText' with the following content, which is copied directly from the  [Single Series Timeline from the Oracle JET Cookbook](https://www.oracle.com/webfolder/technetwork/jet/jetCookbook.html?component=timeline&demo=basicTimeline), with the 'data' passed in from the step above into the 'items' variable:

```js #button { border: none; }
var items = ko.observableArray(JSON.parse(data));
self.timelineSeries = ko.computed(function () {
    return [{id: 's1', emptyText: 'No Data.', label: 'Oracle Events', items: items()}]
});
//
self.currentDateString = "Feb 1, 2010";
var currentDate = new Date(self.currentDateString).toISOString();
self.referenceObjects = [{value: currentDate}];
```

3. In the View, that is, the 'my-invoice-timeline-view.html' file, delete all the existing content, and drop in a Timeline component, here it is copied and pasted directly from the [Single Series Timeline from the Oracle JET Cookbook](https://www.oracle.com/webfolder/technetwork/jet/jetCookbook.html?component=timeline&demo=basicTimeline).

```html #button { border: none; }
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

4. In the browser, you should now see the Timeline scenario working and displaying data, exactly as shown in the [Single Series Timeline from the Oracle JET Cookbook](https://www.oracle.com/webfolder/technetwork/jet/jetCookbook.html?component=timeline&demo=basicTimeline).

### (c) Best Practices for Web Component Development

Now that we have the basic Web Component working, let's talk about best practices in Web Components.

1. Read [Best Practices for Web Component Creation](http://www.oracle.com/pls/topic/lookup?ctx=jetlatest&id=GUID-1A0A3469-AB57-4C0D-B1C7-FB49B5FBA0DF).

2. In particular, read 'Expensive Initialization', about Web Components ideally carrying out minimum work inside the constructor function. The constructor is just for setting up the variables, doing basic set up, no data manipulating, no heavy lifting.

3. Where we will do the more complex tasks and processing, will be done through a combination of lifecycle methods and custom Prototype methods.

4. Since we want to keep the constructor as clean as possible for initiatilization, let's create our own Prototype methods and later get and shape data there, too, in 'my-invoice-timeline-viewModel.js'. There, add the following below the constructor.

This is called one time and initialize data in your code:

```js #button { border: none; }
// Used for initialization of the data.
ExampleComponentModel.prototype.bindingsApplied = function (context) {
  var self = this;
  self._extractArrayFromDataProvider(self.properties.items, self._shapeTimelineData, 10)
  .then(function (transformedArray) {
      self.items(transformedArray);
      self.busyResolve();
    });
};
```

Called whenever items properties actually changed:

```js #button { border: none; }
// Used to handle the use case where the dataProvider passed into the component changes at runtime.
ExampleComponentModel.prototype.propertyChanged = function (context) {
  var self = this;
  if (context.property === 'items' && context.updatedFrom ===
    'external') {
    self._extractArrayFromDataProvider(context.value, self._shapeTimelineData, 10)
    .then(function (transformedArray) {
        self.items(transformedArray);
      });
  }
};
```

5. Next, read 'Access to External Data' in [Best Practices for Web Component Creation
](https://docs.oracle.com/en/middleware/jet/6.1/develop/best-practices-web-component-creation.html#GUID-1A0A3469-AB57-4C0D-B1C7-FB49B5FBA0DF) and let's look at our properties. Let's set up an attribute for passing our data in from. To get started, in the Web Component's 'component.json' file, add a property named 'items', as shown below. 

```js #button { border: none; }
"properties": {
    "items": {
      "type": "oj.DataProvider",
      "description": "data items for the timeline series"
    }
},
```
**Note:** We are going to pass in an array, but we're building these components in anticipation of wanting to use them in Visual Builder as well as in Oracle JET Core applications. We use 'oj.DataProvider' here because Visual Builder passes all data declaratively via a service data provider or an array data provider, both of which can be mapped to 'oj.DataProvider'.

6. In the Web Component's 'my-invoice-timeline-viewModel.js' file...

7. In the Web Component's 'my-invoice-timeline-viewModel.html' file...

8. In the 'index.html' file...

### (e) Customize the Timeline Component

1. We provide [the erpData.json file](https://gist.github.com/peppertech/8a9691dc68b0a1466b0b7012b86e2578), with local data in the component – local method and remote method. Show how to customize attributes of the timeline based on the data coming in – thumbnail and svg styling.

2. Form layout with two select boxes, one for the start year and one for the end year. Year generator, generates years. Set start date and end date of our timeline.

### (f) Use Real Data

1. The above works against local data. Create a connection to the data using an AJAX, using Basic authentication, so no getJSON, using an array data provider, to the real URL.

2. Go to index.html, items=[[dataProvider]], add a property in component.json file called 'items', type 'oj.DataProvider', displayName and description must be changed as well for Visual Builder.

3. In timeline Web Component ViewModel, read the data coming in from the consumer.

## Part 3: Integrate into Visual Builder

### (a) Set Up the Service Provider

### (b) Create a Variable

### (c) Install the Web Component

### (d) Use the Web Component

### (e) Tweak the Web Component


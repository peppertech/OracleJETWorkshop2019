# Part 1: Develop a Web Component for Visual Builder Interaction with Oracle ERP
This workshop shows how to create a web component for 
use with JET Core or Visual Builder, that contains a JET Timeline component 
which will read data from the Oracle ERP service showing invoice information.

## Set Up the Oracle JET Application

Use basic template to set up via ojet create. We can focus on component and not focus on routing, etc. That will give us index.html where we will design the component and data will come from appControler.

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


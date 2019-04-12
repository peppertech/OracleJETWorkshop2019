# OracleJET Workshop 2019
This workshop is delivered in two parts.  

The first is focused on how to create a Web Component for use within an Oracle JET Core application or within Visual Builder. The Web Component contains several Oracle JET components, primarily an Oracle JET Timeline component, which reads data from an Oracle ERP service showing invoice information. In this workshop, you will learn techniques and best practices for developing scalable Web Components that can be used in other contexts, in particular, in Visual Builder. Go to [part 1 here](part1.md).

The second part is focused on techniques needed for creating custom Themes for use in Oracle JET Core applications or in Visual Builder. Go to [part 2 here](part2.md).

## Get Started

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
Oracle JET Command Line Interface, version: 6.2.0
```

**Tip:** If the above shows that you have an **earlier** version of the Oracle JET command-line interface, i.e., below 6.2.0, please reinstall Oracle JET, using the command in step 1 above to do so.

You are now ready to get started with Oracle JET!

### (c) Pick a Starting Point

   * Click [here](part1.md) to go to part 1, on Web Component development.

   * Click [here](part2.md) to go to part 2, on techniques for custom theming.




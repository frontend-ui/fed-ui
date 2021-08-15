# FED-UI

The small front-end framework for developing responsive web applications.

[![npm version](https://badge.fury.io/js/%40frontend-ui%2Ffed-ui.svg)](https://badge.fury.io/js/%40frontend-ui%2Ffed-ui)

Minimum requirements:

+ Node `v14.16.0` or later
+ NPM `v6.14.11` or later


## Install

Install the framework using `NPM (Node Package Manager)`. Before installing, remember to include a `.gitignore` file in the root of your project folder to prevent the `node_modules` directory being added to version control.

https://www.npmjs.com/package/@frontend-ui/fed-ui

Remember to create a `package.json` file in your project.

```shell
$ npm init -y
```

Install the framework:

```shell
$ npm install @frontend-ui/fed-ui
```

Once installed the framework will be added to the `node_modules` directory in your project folder and listed as a dependency in the `package.json` file.

To install a specific version:

```shell
$ npm install @frontend-ui/fed-ui@0.2.12
```

## Adding the framework to your project

Now that the framework has been installed, it can now be imported into your project. Open your SCSS main file and import the framework from the `node_modules` directory using the `@use` rule. The file path will be relative to where the `node_modules` directory is located in relation to your main SCSS file.

```scss
// Your SCSS main file

@use '../../node_modules/@frontend-ui/fed-ui/src/scss/index';
```

Save the file and compile your SCSS code to output the CSS with the framework included.


## Default Variables

The framework has a number of default variables. These can be overwritten if needed to apply your own styling. 

Every SCSS variable includes the `!default` flag allowing you to override the variables with your own SCSS variable values without modifying the core source code. 

```scss
// Set the default font 
$body-font: "Nunito", Helvetica Neue, Helvetica, Arial, sans-serif;
// Set the default body background color of the page
$body-bg: $white !default;
// Set the default body color of the page
$body-color: $grey-dark !default;

// Default link colour
$link-color: inherit !default;

// Margin between headings and paragraphs
$spacing: 1.2rem !default;

// Section padding setting the min and max values for browsers that provide support
$section-padding-block: min(20vh, 3rem) !default;

// Set code snippet colours
$pre-color: $grey-light !default;
$pre-bg: $grey-dark !default;

// Button padding
$btn-padding: 1rem 2rem !default;

// Primary button
$btn-primary-bg: $blue !default;
$btn-primary-color: $white !default;
$btn-primary-border: 1px solid $blue !default;
$btn-primary-hover-bg: lighten($blue, 10%) !default;
$btn-primary-hover-color: $white !default;
$btn-primary-hover-color-border: lighten($blue, 10%) !default;

// Secondary button
$btn-secondary-bg: $grey-dark !default;
$btn-secondary-color: $white !default;
$btn-secondary-border: 1px solid $grey-dark !default;
$btn-secondary-hover-bg: lighten($grey-dark, 10%) !default;
$btn-secondary-hover-color: $white !default;
$btn-secondary-hover-color-border: lighten($grey-dark, 10%) !default;

// Success button
$btn-success-bg: $green !default;
$btn-success-color: $white !default;
$btn-success-border: 1px solid $green !default;
$btn-success-hover-bg: lighten($green, 10%) !default;
$btn-success-hover-color: $white !default;
$btn-success-hover-color-border: lighten($green, 10%) !default;

// Active button
$btn-active-bg: darken($blue, 10%) !default;
$btn-active-color: $white !default;
$btn-active-color-border: darken($blue, 10%) !default;
```

## Customise

Whenever possible, avoid modifying core framework files. For SCSS, that means creating your own stylesheet that imports the framework so you can modify and extend it.

Here's the example of how your own SCSS file may look where we can override the default variables:

```scss
// Required
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/variables/variables' with (

    // Default variable overrides
    $body-bg: #000,
    $btn-primary-bg: #efefef

);

// Optional 
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/core/base';

// Optional components imported
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/components/button';
// etc.
```

Your custom variables can be moved into a separate SCSS partial. In this example, our custom variables are placed into a partial named `_custom-variables.scss` but you can name this whatever you would like.

```scss
// src/scss/variables/_custom-variables.scss

// Override default variables of the framework
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/variables/variables' with (
    
    $body-bg: #000,
    $btn-primary-bg: #efefef

);
```

The main SCSS file, named `custom.scss` in our example, will need to be updated to import this partial using the `@use` instruction.

```scss
// src/scss/custom.scss

// Variables
@use 'src/scss/variables/custom-variables';

// Optional 
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/core/base';

// Optional components imported
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/components/button';
// etc.
```

The file structure in our example will look like this:

```
your-project /
  fonts /
      font-file.eot
      font-file.svg
      font-file.ttf
      font-file.woff
      font-file.woff2
  src /
      scss /
        custom.scss
        variables /
            _custom-vaiables.scss
  
  node_modules /
  .gitignore
  package.json
```

## Components

You may not want to include the full framework in your project. For that reason, you can choose to install only the components you want.


### Core (Reset)

The Core contains the initial reset code for your HTML elements, such as setting the `font-size` and `box-sizing`. Within your custom SCSS file, import the `Core` component like so:

```scss
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/core/font';
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/core/base';
```

You will need to also import the `Font` component currently to use only apply the `Core` component in your project.

### Container

`Containers` horizontally add padding to your content. Use the `.fui-container` as a wrapper around your content to provide padding to the left and right of your content.

To import the `.fui-container` class selector, import the `_layout.scss` SCSS partial.

```scss
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/core/layout';
```

Wrap your content using the container.

```html
<main role="main">

    <div class="fui-container">

        <!-- Your content here -->

    </div>

</main>
```

### Grid (Flexbox)

The responsive, mobile-first grid is built using flexbox using a series of containers, rows, and columns to layout and align content.

Import the `Grid` component into your SCSS file:

```scss
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/core/grid';
```

Update the HTML code to apply the grid structure:

```html
<div class="fui-grid-container">
    
    <div class="fui-grid-row">
        <div class="fui-grid-col">

            <!-- Your content here -->

        </div>
    </div>

    <div class="fui-grid-row">
        <div class="fui-grid-col">
            
            <!-- Your content here -->
        
        </div>
        <div class="fui-grid-col">

            <!-- Your content here -->

        </div>
    </div>

    <div class="fui-grid-row">
        <div class="fui-grid-col">

            <!-- Your content here -->

        </div>
        <div class="fui-grid-col">

            <!-- Your content here -->

        </div>
        <div class="fui-grid-col">

            <!-- Your content here -->

        </div>
    </div>
```

To increase the size of the rows across the screen, add the `.fui-grid-row--fluid` modifier class to the row:

```html
<div class="fui-grid-row fui-grid-row--fluid"> ... </div>
```

To extend this further and remove the horizontal padding on the left and right of the row, apply the `fui-grid-row--fluid-full-width` modifier class also.

```html
<div class="fui-grid-row fui-grid-row--fluid fui-grid-row--fluid-full-width"> ... </div>
```

### Section

The HTML5 `<section>` element represents a standalone section of the page. Sections should always have a heading and will be full-width of their parent container.

Adding the `.fui-container` as a wrapper around the content of the `<section>` within your page will provide the horizontal padding to the left and right. The `<section>` element will manage the vertical padding by default.

This is specified within the `_base.scss` partial so only the `Core` of the framework needs to be imported.

```html
<main role="main">

    <h1>Page Heading</h1>

    <section>
        <div class="fui-container">

            <h2>Section Heading</h2>

            <!-- Your content here -->

        </div>
    </section>

</main>
```

### Code snippets

Code snippets are embedded between the `<pre>` and `<code>` HTML tags. The styling is within the `Core` SCSS `_base.scss` partial.

```html
<pre>
    <code>

        .foo {
            color: #000;
        }

    </code>
</pre>
```

### Terminal

As with the code snippets, you may want to display a terminal component on the page showing instructions within the command-line. 

Import the `Terminal` component and add to your page.

```scss
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/components/terminal';
```

Your HTML code:

```html
<div class="terminal terminal--shadow">
    <div class="terminal__top">
        <div class="terminal__buttons">
            <span class="terminal__circle terminal__circle--close"></span>
            <span class="terminal__circle terminal__circle--minimise"></span>
            <span class="terminal__circle terminal__circle--expand"></span>
        </div>
        <div class="terminal__title">bash -- 85x24</div>
    </div>
    <pre class="terminal__body">
              
        $ node server.js
    
    </pre>
</div>
```

### Button

To import a `Button` component:

```scss
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/components/button';
```

Remember to add the `type` attribute to the button element to prevent the button default being submit and to prevent the button refreshing the page when clicked.

Each button should apply the CSS classes for styling and a `js-hook` class to apply any JavaScript code to separate styling and functionality.

```html
<button type="button" class="fui-btn js-fui-btn">Button</button>
```

Classes can be applied to a link to resemble a button element. If a link is used, please remember to include the `role` attribute.

```html
<a href="https://www.example.com" role="button" type="button" class="fui-btn fui-btn--primary">Button</a>
```

To select all buttons with the `js-hook` class applied, use the `querySelectorAll()` document method. You will need to loop over all the button elements to apply functionality to the button that's clicked. This example below will show how to toggle the active class on/off for each button clicked:

```javascript
const btn = document.querySelectorAll('.js-fui-btn');

// Loop through all buttons and toggle the active class on or off
btn.forEach(button => {
    button.addEventListener('click', function() {
    
        // Remove the active class from all buttons
        btn.forEach(activeButton => activeButton.classList.remove('fui-btn--active'));
    
        // Add the active class to the button being clicked
        this.classList.add('fui-btn--active');
    });
});
```

The button component has the following modifier classes:

```html
<button type="button" class="fui-btn">Button</button>

<!-- Add the JavaScript hook to apply JavaScript code to the button -->
<button type="button" class="fui-btn js-fui-btn">Button</button>

<!-- Primary button -->
<button type="button" class="fui-btn fui-btn--primary">Button</button>

<!-- Secondary button -->
<button type="button" class="fui-btn fui-btn--secondary">Button</button>

<!-- Success button -->
<button type="button" class="fui-btn fui-btn--success">Button</button>

<!-- Set the button to show as active, you will need JavaScript to be used -->
<button type="button" class="fui-btn js-fui-btn fui-btn--active">Button</button>

<!-- Set the button to be 100% full width -->
<button type="button" class="fui-btn fui-btn--full-width">Button</button>

<!-- Curved button -->
<button type="button" class="fui-btn fui-btn--curved">Button</button>

<!-- Rounded button -->
<button type="button" class="fui-btn fui-btn--rounded">Button</button>
```

## Setting up your SCSS project

Setting up your own SCSS project is very simple. Begin by creating a new project folder and generating a `package.json` file.

```
$ npm init -y
```

Install the `sass` `NPM (Node Package Manager)` package as a `devDependency`:

```
$ npm install sass --save-dev
```

Create a script within your `package.json` file to run the build and compile your SCSS code into CSS.

```
"scripts": {
  "compile": "sass src/scss/custom.scss dist/css/index.css"
},
```

Your project directory should look something like this:

```
your-project /
  src /
    scss /
      custom.scss
```

Compile your SCSS code by running the NPM script:

```
$ npm run compile
```

When you run the build and compile your SCSS code, your file structure will look like this:

```
your-project /
  dist /
    css /
      index.css

  src /
    scss /
      custom.scss
```

You can now install the framework using `NPM (Node Package Manager)`.


## Clone the repository

You may want to clone the repository to contribute towards this open-source project.

```shell
$ git clone https://github.com/frontend-ui/fed-ui.git

$ cd fed-ui
$ npm install
```

## Compile the framework

The framework is built using `dart sass`. To compile the framework if changes are made to the core code, the `compile` script is executed using NPM (Node Package Manager):

```shell
$ npm run compile
```

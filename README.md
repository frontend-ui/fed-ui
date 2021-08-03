# FED-UI

Open-source UI (User Interface) front-end web framework.

[![npm version](https://badge.fury.io/js/%40frontend-ui%2Ffed-ui.svg)](https://badge.fury.io/js/%40frontend-ui%2Ffed-ui)

## Clone the Repository

Clone the GitHub repository using these instructions:

```
$ git clone https://github.com/frontend-ui/fed-ui.git

$ cd fed-ui
$ npm install
```

## Build & Compile the SCSS

The FED-UI front-end framework uses the `NPM (Node Package Manager)` `sass` package to compile the SCSS code into CSS. This uses Dart Sass rather than Ruby Sass and so we can use the `@use` rule to import our SCSS partials.

```
$ npm run compile
```

## Setting up your Project

Setting up your own SCSS project is very simple. Begin by creating a new project folder and generating a `package.json` file.

```
$ npm init -y
```

Install the `sass` `NPM (Node Package Manager)` package as a devDependency:

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

## Install

Install the framework using `NPM (Node Package Manager)`. This needs to be installed as a dependency to allow the code to be used in production.

Before installing the `NPM package`, it's always worthwhile including a `.gitignore` in your project folder to avoid the `node_modules` being committed when using version control.

```
$ npm install @frontend-ui/fed-ui
```

This will install the latest version of the framework. If you want to install a specific version of the framework set the version using `@`:

```
$ npm install @frontend-ui/fed-ui@0.1.0
```

The `NPM (Node Package Manager)` package can be found here:

https://www.npmjs.com/package/@frontend-ui/fed-ui

The package should now be listed as a dependency in your package.json file.

Whenever possible, avoid modifying FED-UI's core files. For SCSS, that means creating your own stylesheet that imports FED-UI so you can modify and extend it. Assuming you're project has a file structure like this:

```
your-project /
  src /
    scss /
      custom.scss
  
  node_modules /
    @frontend-ui /
      fed-ui /
        src /
          scss /
            index.scss
```

When you compile your code, your file structure may look like this:

```
your-project /
  dist /
    css /
      index.css
  src /
    scss /
      custom.scss
  
  node_modules /
    @frontend-ui /
      fed-ui /
        src /
          scss /
            index.scss
```

If your file structure is as the examples above, your path to the `node_modules` directory will need to be correct.

To install the FED-UI framework, open your custom.scss file (this maybe named something like `index.scss` or `main.scss` in your own project), then import the framework:

```scss
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/index';
```

Save the file and compile your SCSS code to include the FED-UI framework code in your project CSS stylesheet.

## Customise

In your `custom.scss`, you'll import the framework's SCSS files. The FED-UI framework has a partial called `_color.scss` containing the colour variables and a `_variables.scss` partial that sets the default styling variables. Every SCSS variable includes the `!default` flag allowing you to override the variables with your own SCSS variable values without modifying the FED-UI source code.

Here's the example of how your `custom.scss` file may look where we can override the default variables:

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
  src /
    scss /
      custom.scss
      variables /
          _custom-vaiables.scss
  
  node_modules /
```

### Default variables

The default variables located within `variables/_variables.scss` partial that you can override.

```scss
// Set the default body background color of the page
$body-bg: $white !default;
// Set the default body color of the page
$body-color: $grey-dark !default;

// Margin between headings and paragraphs
$spacing: 1.2rem !default;

// Section vertical padding (IE/Edge does not support padding-block so this is a fallback)
$section-padding: 10rem 0 !default;
// Section padding setting the min and max values for browsers that provide support
$section-padding-block: min(20vh, 3rem) !default;

// Button padding
$btn-padding: 0.8rem 1rem !default;

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

## Components

You may not want to include the full FED-UI framework in your project. For that reason, you can choose to install only the components you want.

### Core

The Core contains the initial reset code for your HTML elements, such as setting the `font-size` and `box-sizing`. Within your custom SCSS file, import the FED-UI Core like so:

```scss
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/variables/variables';

@use '../../node_modules/@frontend-ui/fed-ui/src/scss/core/base';

```

### Container

Containers horizontally add padding to your content. Use the `.fui-container` as a wrapper around your content to provide padding to the left and right of your content.

To import the `.fui-container` class selector, import the `_layout.scss` SCSS partial.

```scss
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/variables/variables';

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

### Button

To import a Button component:

```scss
@use '../../node_modules/@frontend-ui/fed-ui/src/scss/variables/variables';

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
```
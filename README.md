# FED-UI

Open-source UI (User Interface) front-end web framework.

## Clone the Repository

Clone the GitHub repository using these instructions:

```
$ git clone https://github.com/frontend-ui/fed-ui.git

$ cd fed-ui
$ npm install
```

## Build & Compile the SCSS

The FED-UI front-end framework uses the NPM (Node Package Manager) sass package to compile the SCSS code into CSS. This uses Dart Sass rather than Ruby Sass and so we can use the @use rule to import our SCSS partials.

```
$ npm run compile
```

## Install

Install the framework using NPM (Node Package Manager). This needs to be installed as a dependency to allow the code to be used in production.

```
$ npm install @frontend-ui/fed-ui
```

This will install the latest version of the framework.


The NPM (Node Package Manager) package can be found here:

https://www.npmjs.com/package/@frontend-ui/fed-ui

The package should now be listed as a dependency in your package.json file.

Whenever possible, avoid modifying FED-UI's core files. For SCSS, that means creating your own stylesheet that imports FED-UI so you can modify and extend it. Assuming you're project has a file structure like this:

```
your-project /
  scss /
    custom.scss
      node_modules /
        @frontend-ui /
          fed-ui /
            src /
              scss /
                index.scss
```

To install the FED-UI framework, open your custom.scss file (this maybe named something like index.scss or main.scss in your own project), then import the framework:

```scss
@import 'node_modules/@frontend-ui/fed-ui/src/scss/index';
```

Save the file and compile your SCSS code to include the FED-UI framework code in your project CSS stylesheet.

## Components

You may not want to include the full FED-UI framework in your project. For that reason, you can choose to install only the components you want.

### Core

The Core contains the initial reset code for your HTML elements, such as setting the font-size and box-sizing. Within your custom SCSS file, import the FED-UI Core like so:

```scss
@import 'node_modules/@frontend-ui/fed-ui/src/scss/core/base';

```

### Button

To import a Button component:

```scss
@import 'node_modules/@frontend-ui/fed-ui/src/scss/components/button';
```

Remember to add the type attribute to the button element to prevent the button default being submit and to prevent the button refreshing the page when clicked.

Each button should apply the CSS classes for styling and a js-hook class to apply any JavaScript code to separate styling and functionality.

```html
<button type="button" class="fui-btn js-fui-btn">Button</button>
```

Classes can be applied to a link to resemble a button element. If a link is used, please remember to include the role attribute.

```html
<a href="https://www.example.com" role="button" type="button" class="fui-btn js-fui-btn">Button</a>
```

To select all buttons with the js-hook class applied, use the querySelectorAll() document method. You will need to loop over all the button elements to apply functionality to the button that's clicked. This example below will show how to toggle the active class on/off for each button clicked:

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

<!-- Success button -->
<button type="button" class="fui-btn fui-btn--success">Button</button>

<!-- Set the button to show as active, you will need JavaScript to be used -->
<button type="button" class="fui-btn js-fui-btn fui-btn--active">Button</button>

<!-- Set the button to be 100% full width -->
<button type="button" class="fui-btn fui-btn--full-width">Button</button>
```
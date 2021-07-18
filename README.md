# FED-UI

## Install

```
$ git clone https://github.com/frontend-ui/fed-ui.git

$ cd fed-ui
$ npm install
```

## NPM (Node Package Manager)

```
$ npm install @frontend-ui/fed-ui
```

https://www.npmjs.com/package/@frontend-ui/fed-ui

## Build & Compile the SCSS

The fed-ui front-end framework uses the NPM (Node Package Manager) sass package to compile the SCSS code into CSS. This uses Dart Sass rather than Ruby Sass and so we can use the @use rule to import our SCSS partials.

```
$ npm run compile
```

## Components

### Button

To import just the button component into your own SCSS code, use NPM (Node Package Manager) to install the fed-ui package and the @use rule to import the button component into your own SCSS index/main file. You will require the 'core/base' to also be imported into your SCSS code.

```
$ npm install @frontend-ui/fed-ui
```

```scss
// Your main SCSS file

@use 'core/base';

// Button component
@use 'components/button';
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

<!-- Set the button to show as active, you will need JavaScript code here -->
<button type="button" class="fui-btn js-fui-btn fui-btn--active">Button</button>

<!-- Set the button to be 100% full width -->
<button type="button" class="fui-btn fui-btn--full-width">Button</button>
```
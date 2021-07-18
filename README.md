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

```
$ npm run compile
```

## Components

### Button

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
<button type="button" class="fui-btn <MODIFIER-CLASSES-HERE>">Button</button>
```

+ fui-btn--full-width: Set the button to be full-width at 100%.
+ fui-btn--active: Active state applied when the button is clicked. You will need to use the above JavaScript code to apply this.
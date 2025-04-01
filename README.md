# Hints

Sometimes we might want to help users complete a form field by providing some additional information in the form of a hint placed under the field. 

![](images/SampleView.png)

## Version 
1.0 - initial

1.1 added check for array; changed px to rem; updated readme to 6.12+

# Setup

## Global Script
1. Create a Global Script called "Hints"
2. Add the input parameters below to the Global Script
   1. Hints
3. Drag a *JavaScript* action into the script
4. Add the Javascript below unchanged into the JavaScript code property
```javascript
/* Stadium Script v1.1 https: //github.com/stadium-software/form-field-hints */
let vals = ~.Parameters.Input.Hints;
if (!Array.isArray(vals)) vals = [];
vals.forEach(function (ob) {
    let elParent = document.querySelector("." + ob.classname);
    if (elParent) {
        let hint = document.createElement("div");
        hint.classList.add("stadium-hint");
        hint.textContent = ob.hint;
        elParent.appendChild(hint);
    }
});
```

## Type
1. Add a type called "hint"
   1. classname (any)
   2. hint (any)

![](images/Type.png)

## Page
1. Drag a form field to the page (e.g. CheckBox, CheckBox List, Date Picker, Drop Down, Radio Button List, Text Box or Upload File)
2. Add a class to the field to uniquely identify the field

## Page.Load
1. Drag a *List* action into the event handler and call it "HintsList"
2. Assign the "hint" type to the List in the *Item Type* property
3. Add the field classes and related hints to the "HintsList" (example below)

```json
= [{
	"classname": "name",
	"hint": "How we will call you"
}]
```

4. Drag the Global Script called "Hints" into the Event Handler
5. Assign the "HintsList" to the Global Script "Hints" input parameter

## CSS
The CSS below is required for the correct functioning of the module. Variables exposed in the [*hints-variables.css*](hints-variables.css) file can be [customised](#customising-css).

### Before v6.12
1. Create a folder called "CSS" inside of your Embedded Files in your application
2. Drag the two CSS files from this repo [*hints-variables.css*](hints-variables.css) and [*hints.css*](hints.css) into that folder
3. Paste the link tags below into the *head* property of your application
```html
<link rel="stylesheet" href="{EmbeddedFiles}/CSS/hints.css">
<link rel="stylesheet" href="{EmbeddedFiles}/CSS/hints-variables.css">
``` 

### v6.12+
1. Create a folder called "CSS" inside of your Embedded Files in your application
2. Drag the CSS files from this repo [*hints.css*](hints.css) into that folder
3. Paste the link tag below into the *head* property of your application
```html
<link rel="stylesheet" href="{EmbeddedFiles}/CSS/hints.css">
``` 

### Customising CSS
1. Open the CSS file called [*hints-variables.css*](hints-variables.css) from this repo
2. Adjust the variables in the *:root* element as you see fit
3. Stadium 6.12+ users can comment out any variable they do **not** want to customise
4. Add the [*hints-variables.css*](hints-variables.css) to the "CSS" folder in the EmbeddedFiles (overwrite)
5. Paste the link tag below into the *head* property of your application (if you don't already have it there)
```html
<link rel="stylesheet" href="{EmbeddedFiles}/CSS/hints-variables.css">
``` 
6. Add the file to the "CSS" inside of your Embedded Files in your application

**NOTE: Do not change any of the CSS in the 'hints.css' file**

## Upgrading Stadium Repos
Stadium Repos are not static. They change as additional features are added and bugs are fixed. Using the right method to work with Stadium Repos allows for upgrading them in a controlled manner. 

How to use and update application repos is described here: [Working with Stadium Repos](https://github.com/stadium-software/samples-upgrading)
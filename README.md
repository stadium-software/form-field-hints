# Hints

Sometimes we might want to help users complete a form field by providing some additional information in the form of a hint placed under the field. 

![](images/SampleView.png)

# Setup

## Global Script
1. Create a Global Script called "Hints"
2. Add the input parameters below to the Global Script
   1. Hints
3. Drag a *JavaScript* action into the script
4. Add the Javascript below into the JavaScript code property
```javascript
/* Stadium Script v1.0 https: //github.com/stadium-software/form-field-hints */
let vals = ~.Parameters.Input.Hints;
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
The CSS below is required for the correct functioning of the module. Some elements can be [customised](#customising-css) using a variables CSS file. 

**Stadium 6.6 or higher**
1. Create a folder called "CSS" inside of your Embedded Files in your application
2. Drag the two CSS files from this repo [*hints-variables.css*](hints-variables.css) and [*hints.css*](hints.css) into that folder
3. Paste the link tags below into the *head* property of your application
```html
<link rel="stylesheet" href="{EmbeddedFiles}/CSS/hints.css">
<link rel="stylesheet" href="{EmbeddedFiles}/CSS/hints-variables.css">
``` 

### Customising CSS
1. Open the CSS file called [*hints-variables.css*](hints-variables.css) from this repo
2. Adjust the variables in the *:root* element as you see fit
3. Overwrite the file in the CSS folder of your application with the customised file

### CSS Upgrading
To upgrade the CSS in this module, follow the [steps outlined in this repo](https://github.com/stadium-software/samples-upgrading)

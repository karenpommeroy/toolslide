# toolslide.js
Minimalistic customizable slide panel (without jQuery)

## Table of contents

- [Quick start](#quick-start)
- [Usage](#usage)
- [Examples](#examples)
- [Options](#options)
- [Methods](#methods)
- [Events](#events)
- [Browser support](#browser-support)
- [Copyright and license](#copyright-and-license)

## Quick start
Several quick start options are available:
#### Download the latest build

###### Development
 * [toolslide.js](https://raw.githubusercontent.com/karenpommeroy/toolslide.js/master/dist/toolslide.js)
 * [toolslide.css](https://raw.githubusercontent.com/karenpommeroy/toolslide.js/master/dist/toolslide.css)

###### Production
 * [toolslide.min.js](https://raw.githubusercontent.com/karenpommeroy/toolslide.js/master/dist/toolslide.min.js)
 * [toolslide.min.css](https://raw.githubusercontent.com/karenpommeroy/toolslide.js/master/dist/toolslide.min.css)

#### Install From Bower
```sh
bower install toolslide.js --save
```

#### Install From Npm
```sh
npm install toolslide.js --save
```

Done!

## Usage
#### Including files:

```xml
<link rel="stylesheet" href="/path/to/toolslide.css">
<script src="/path/to/toolslide.js"></script>
```

#### Required HTML structure

```xml
<div id="toolslide">
	<div class="ts-container">
        <div class="ts-nav-container">
			<div class="ts-nav-item" ts-target="first">
			</div>
			<!-- Add more navigation buttons here -->
		</div>
		<div class="ts-content-container">
			<div id="first" class="ts-content-item">
				<div class="example-panel">
					<span>First panel content goes here</span>
				</div>
			</div>
			<!-- Add more content panels here -->
		</div>
	</div>
</div>
```


###### Attributes

`toolslide.js` makes use of html attributes to bind navigation elements to respective content.


Attribute   | Description                           |
----------- | ------------------------------------- |
ts-target   | Specifies id of a target panel triggered with this navigation item


#### Initialization
All you need to do is invoke toolslide on an element:
```javascript
var myToolslide = toolslide("#elementId", options);
```
You can also initialize with css selector string:

```javascript
var myToolslide = toolslide("#elementId", options);
```

## Examples
There are some example usages that you can look at to get started. They can be found in the [examples folder](https://github.com/karenpommeroy/toolslide.js/tree/master/examples).

 * [Panel on the left](https://rawgit.com/karenpommeroy/toolslide.js/master/examples/example-left.html)
 * [Panel on the right](https://rawgit.com/karenpommeroy/toolslide.js/master/examples/example-right.html)
 * [Panel at the top](https://rawgit.com/karenpommeroy/toolslide.js/master/examples/example-top.html)
 * [Panel at the bottom](https://rawgit.com/karenpommeroy/toolslide.js/master/examples/example-bottom.html)

## Options
`toolslide.js` can accept an options object to alter the way it looks and behaves.
If no options object is passed default values are used.
The structure of an options object is as follows:

```css
{
  position: left",
  height: "100%",
  width: "300px",
  startOpen: true,
  closeable: true,
  autoclose: false,
  autocloseDelay: 5000,
  clickOutsideToClose: true,
  animations: {
    replace: "crossfade 0.5s ease-in-out",
    toggle: "slide 0.5s ease",
  },
  listeners: {
    open: function(panel) {},
    close: function(panel) {},
    toggle: function(oldContent, newContent) {}
  }
```

Here is the explanation of options object:

Option     | Type    | Description                         | Examples
-----------| ------- | ----------------------------------- | -----------
position   | string  | Position of the panel on the screen | "top", "bottom", "left", "right"
height     | string  | Panel height                        | "200px", "20%"
width      | string  | Panel width                         | "200px", "20%"
startOpen  | boolean | Open panel after initialization     | true, false
closeable  | boolean | Allow panel to be closed (by clicking active navigation element)           | true, false
autoclose  | boolean | Allow panel to be auto closed (only when mouse cursor is outside)          | true, false
autocloseDelay  | int | Auto close delay in miliseconds           | 5000
clickOutsideToClose  | boolean | Allow panel to be closed when clicked outside           | true, false
animations.replace   | string  | Animation used when changing active panel | "crossfade 0.5s ease-in-out", "slide 1s ease", "slidefade 2s ease-in-out"
animations.toggle   | string  | Animation used when panel is opened/closed | "slide 0.5s ease"
listeners.beforeOpen | function | Callback fired before panel is opened | function (panel) {...}
listeners.afterOpen | function | Callback fired after panel is opened | function (panel) {...}
listeners.beforeClose | function | Callback fired before panel is closed | function (panel) {...}
listeners.afterClose | function | Callback fired after panel is closed | function (panel) {...}
listeners.beforeToggle | function | Callback fired before active content is changed | function (old, new) {...}
listeners.afterToggle | function | Callback fired after active content is changed | function (old, new) {...}

## Methods
Methods are called on toolslide instances. You shoud save the instances to variable to have further access to it.

#### void open()
Show the slide panel.
```javascript
toolslide.open();
```

#### void close()
Hide the slide panel.
```javascript
toolslide.close();
```

#### bool isOpen()
Check if panel is opened.
```javascript
toolslide.isOpen();
```

#### bool isActive(target)
Check if target content element is  active. Accepts DOM element as well as just the id. 
```javascript
toolslide.isOpen("elementId");
```

#### void setActiveById(elementId)
Sets element with specified id as new active item.
```javascript
toolslide.setActiveById("elementId");
```

#### void setActiveByIndex(index)
Sets element at specified index as active item.
```javascript
toolslide.setActiveByIndex(0);
```


## Events
`toolslide.js` provides custom events for some of it's actions. Appropriate callbacks can be specified in options. 


Event         | Description                             | Arguments
------------- | --------------------------------------- | ------------------ |
beforeOpen    | Fires before panel is opened.           | panelElement
afterOpen     | Fires after panel is opened.            | panelElement
beforeClose   | Fires before panel is closed.           | panelElement
afterClose    | Fires after panel is closed.            | panelElement
beforeToggle  | Fires before active content is changed. | oldContentElement, newContentElement
afterToggle   | Fires after active content is changed.  | oldContentElement, newContentElement



## Copyright and license

Licensed under [MIT license](LICENSE).

[^ back to top](#table-of-contents)

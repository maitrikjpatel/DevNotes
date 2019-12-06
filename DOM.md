---
date: '2019-01-13'
publish: 'true'
category: 'note'
author: 'Maitrik Patel'

title: 'DOM'
description: ' -Document Object Model'

topics: 'tools, development'

source: 'Github'
---

### Resources

- DOM specification : Describes the document structure, manipulations and events, see https://dom.spec.whatwg.org.
- CSSOM specification : Describes stylesheets and style rules, manipulations with them and their binding to documents, see https://www.w3.org/TR/cssom-1/.

### Notes

#### DOM Treee

- An HTML/XML document is represented inside the browser as the DOM tree.
  - Tags become element nodes and form the structure.
  - Text becomes text nodes.
  - …etc, everything in HTML has its place in DOM, even comments.

#### Walking the DOM

- For all nodes: parentNode, childNodes, firstChild, lastChild, previousSibling, nextSibling.
- For element nodes only: parentElement, children, firstElementChild, lastElementChild, previousElementSibling, nextElementSibling.
- For different elements: querySelector, querySelectorAll, getElementById, getElementsByName, getElementsByTagName, getElementsByClassName
- The “nodeType” property
  - elem.nodeType == 1 for element nodes
  - elem.nodeType == 3 for text nodes
  - elem.nodeType == 9 for the document object
- nodeName/tagName
- innerHTML : The HTML content of the element. 
- outerHTML : The full HTML of the element. A write operation into elem.outerHTML does not touch elem itself
- nodeValue/data : The content of a non-element node (text, comment). These two are almost the same, usually we use data.
- textContent : The text inside the element: HTML minus all `<tags>`
- hidden : When set to true, does the same as CSS display:none


#### Attribute vs Properties

- Attribute - HTML, String, Name is not case-sensitive.
- Properties - DOM, Any value, Name is case-sensitive.
- elem.hasAttribute(name) – to check for existence.
- elem.getAttribute(name) – to get the value.
- elem.setAttribute(name, value) – to set the value.
- elem.removeAttribute(name) – to remove the attribute.
- elem.attributes is a collection of all attributes.

#### Create New Nodes

- document.createElement(tag) – creates an element with the given tag,
- document.createTextNode(value) – creates a text node (rarely used),
- elem.cloneNode(deep) – clones the element, if deep==true then with all descendants.

#### Insertion and removal of nodes

- parent.appendChild(node)
- parent.insertBefore(node, nextSibling)
- parent.removeChild(node)
- parent.replaceChild(newElem, node)
- node.append(...nodes or strings) – insert into node, at the end,
- node.prepend(...nodes or strings) – insert into node, at the beginning,
- node.before(...nodes or strings) – insert right before node,
- node.after(...nodes or strings) – insert right after node,
- node.replaceWith(...nodes or strings) – replace node.
- node.remove() – remove the node.
- elem.insertAdjacentHTML(where, html)
  - "beforebegin" – insert html right before elem,
  - "afterbegin" – insert html into elem, at the beginning,
  - "beforeend" – insert html into elem, at the end,
  - "afterend" – insert html right after elem.

#### Style and Class

- className – the string value, good to manage the whole set of classes.
- classList – the object with methods add/remove/toggle/contains, good for individual classes.
- The style property is an object with camelCased styles. 
  - Reading and writing to it has the same meaning as modifying individual properties in the "style" attribute. 
  - To see how to apply important and other rare stuff – there’s a list of methods at MDN.
- The style.cssText property corresponds to the whole "style" attribute, the full string of styles.
- The getComputedStyle(elem[, pseudo]) returns the style-like object with them. Read-only.

#### Element size and scrolling

- [Geometry](https://javascript.info/size-and-scroll#geometry)

#### Coordinates

- document.elementFromPoint(x, y) returns the most nested element at window coordinates (x, y)
- clientX,clientY : When you scroll, clientX,clientY change, because they are relative to the window, but (pageX,pageY) remain the same.
- pageY = clientY + height of the scrolled-out vertical part of the document.
- pageX = clientX + width of the scrolled-out horizontal part of the document.


#### Browser events

- Mouse events:
  click – when the mouse clicks on an element (touchscreen devices generate it on a tap).
  contextmenu – when the mouse right-clicks on an element.
  mouseover / mouseout – when the mouse cursor comes over / leaves an element.
  mousedown / mouseup – when the mouse button is pressed / released over an element.
  mousemove – when the mouse is moved.

- Form element events:
  - submit – when the visitor submits a `<form>`
  - focus – when the visitor focuses on an element, e.g. on an `<input>`

- Keyboard events:
  - keydown and keyup – when the visitor presses and then releases the button.
  - 
- Document events:
  - DOMContentLoaded – when the HTML is loaded and processed, DOM is fully built.

- CSS events:
  - transitionend – when a CSS-animation finishes.

#### Bubbling and capturing

- Bubbling : The bubbling principle is simple.
- When an event happens on an element, it first runs the handlers on it, then on its parent, then all the way up on other ancestors.

- Each handler can access event object properties:
  - event.target – the deepest element that originated the event.
  - event.currentTarget (=this) – the current element that handles the event (the one that has the handler on it)
  - event.eventPhase – the current phase (capturing=1, target=2, bubbling=3).

#### Event delegation

- Capturing and bubbling allow us to implement one of most powerful event handling patterns called event delegation.
- The idea is that if we have a lot of elements handled in a similar way, then instead of assigning a handler to each of them – we put a single handler on their common ancestor.
- In the handler we get event.target, see where the event actually happened and handle it.

```js
let selectedTd;

table.onclick = function(event) {
  let td = event.target.closest('td'); // (1) where was the click?

  if (!td) return; // (2)
  if (!table.contains(td)) return; // (3) not on TD? Then we're not interested

  highlight(td); // highlight it
};

function highlight(td) {
  if (selectedTd) { // remove the existing highlight if any
    selectedTd.classList.remove('highlight');
  }
  selectedTd = td;
  selectedTd.classList.add('highlight'); // highlight the new td
}
```

#### Browser actions:

- mousedown – starts the selection (move the mouse to select).
- click on `<input type="checkbox">` – checks/unchecks the input.
- submit – clicking an `<input type="submit">` or hitting Enter inside a form field causes this event to happen, and the browser submits the form after it.
- wheel – rolling a mouse wheel event has scrolling as the default action.
- keydown – pressing a key may lead to adding a character into a field, or other actions.
- contextmenu – the event happens on a right-click, the action is to show the browser context menu.

#### Mouse Events: 

- The most used simple events are:
  - mousedown/mouseup : Mouse button is clicked/released over an element.
  - mouseover/mouseout : Mouse pointer comes over/out from an element.
  - mousemove : Every mouse move over an element triggers that event.
    - Events flow: ball.mousedown → document.mousemove → ball.mouseup
    - At the drag start – remember the initial shift of the pointer relative to the element: shiftX/shiftY and keep it during the dragging.
    - Detect droppable elements under the pointer using document.elementFromPoint.

- Complex events
  - click : Triggers after mousedown and then mouseup over the same element if the left mouse button was used.
  - contextmenu : Triggers after mousedown if the right mouse button was used.
  - dblclick : Triggers after a double click over an element.
  - Moving: mouseover/out, mouseenter/leave
    - mouseenter/leave Transitions inside the element are not counted.
    - mouseenter/leave Events mouseenter/mouseleave do not bubble.

#### Drag Algo

- The basic Drag’n’Drop algorithm looks like this:
  - Catch mousedown on a draggable element.
  - Prepare the element for moving (maybe create a copy of it or whatever).
  - Then on mousemove move it by changing left/top and position:absolute.
  - On mouseup (button release) – perform all actions related to a finished Drag’n’Drop.

```js
// onmousedown
// remember the distance from the cursor to the left-upper corner of the ball in variables shiftX/shiftY
let shiftX = event.clientX - ball.getBoundingClientRect().left;
let shiftY = event.clientY - ball.getBoundingClientRect().top;

// onmousemove
// ball has position:absoute
// position the ball on the same shift relative to the pointer
ball.style.left = event.pageX - shiftX + 'px';
ball.style.top = event.pageY - shiftY + 'px';
```

#### Key Events

- Keyboard events:
  - keydown – on pressing the key (auto-repeats if the key is pressed for long),
  - keyup – on releasing the key.

- Main keyboard event properties:
  - code – the “key code” ("KeyA", "ArrowLeft" and so on), specific to the physical location of the key on keyboard.
  - key – the character ("A", "a" and so on), for non-character keys, such as Esc, usually has the same value as code.


#### Scroll 

- Scroll events allow to react on a page or element scrolling. 

```js
window.addEventListener('scroll', function() {
  document.getElementById('showScroll').innerHTML = pageYOffset + 'px';
});
```

#### Form properties and methods

- document.forms : A form is available as `document.forms[name/index]`.
- form.elements : Form elements are available as `form.elements[name/index]`, or can use just `form[name/index]`. The elements property also works for `<fieldset>`.
- element.form : Elements reference their form in the form property.
- Value is available as input.value, textarea.value, select.value etc, or input.checked for checkboxes and radio buttons.
- onchange : The change event triggers when the element has finished changing.
- oninput : The input event occurs after the value is modified.
- onsubmit : The submit event triggers when the form is submitted, it is usually used to validate the form before sending it to the server or to abort the submission and process it in JavaScript.

#### Focusing: focus/blur

- An element receives a focus when the user either clicks on it or uses the Tab key on the keyboard. 
- The moment of losing the focus (“blur”) when a user clicks somewhere else or presses Tab to go to the next form field, or there are other means as well.

#### PageLoad 

- DOMContentLoaded event – DOM is ready, so the handler can lookup DOM nodes, initialize the interface.
- load event – external resources are loaded, so styles are applied, image sizes are known etc.
- beforeunload event – the user is leaving: we can check if the user saved the changes and ask them whether they really want to leave.
- unload – the user almost left, but we still can initiate some operations, such as sending out statistics.
- document.readyState is the current state of the document, changes can be tracked in the readystatechange event:
  - loading – the document is loading.
  - interactive – the document is parsed, happens at about the same time as DOMContentLoaded, but before it.
  - complete – the document and resources are loaded, happens at about the same time as window.onload, but before it.

### Extra

- MutationObserver is a built-in object that observes a DOM element and fires a callback in case of changes.
- EventLoop
  - The concept of event loop is very simple. There’s an endless loop, when JavaScript engine waits for tasks, executes them and then sleeps waiting for more tasks.
- The tasks form a queue, so-called “macrotask queue”
- Microtask queue has a higher priority than the macrotask queue.
- After every macrotask, the engine executes all tasks from microtask queue, prior to running any other macrotasks.
- Code -> Promise -> Timeout

- The more detailed algorithm of the event loop (though still simplified compare to the specification):
  - Dequeue and run the oldest task from the macrotask queue (e.g. “script”).
  - Execute all microtasks:
  - While the microtask queue is not empty:
  - Dequeue and run the oldest microtask.
  - Render changes if any.
  - Wait until the macrotask queue is not empty (if needed).
  - Go to step 1.
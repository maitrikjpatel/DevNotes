#DOM

## Resources

- DOM specification : Describes the document structure, manipulations and events, see https://dom.spec.whatwg.org.
- CSSOM specification : Describes stylesheets and style rules, manipulations with them and their binding to documents, see https://www.w3.org/TR/cssom-1/.

## Notes

### DOM Treee

- An HTML/XML document is represented inside the browser as the DOM tree.
  - Tags become element nodes and form the structure.
  - Text becomes text nodes.
  - …etc, everything in HTML has its place in DOM, even comments.

### Walking the DOM

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


### Attribute vs Properties

- Attribute - HTML, String, Name is not case-sensitive.
- Properties - DOM, Any value, Name is case-sensitive.
- elem.hasAttribute(name) – to check for existence.
- elem.getAttribute(name) – to get the value.
- elem.setAttribute(name, value) – to set the value.
- elem.removeAttribute(name) – to remove the attribute.
- elem.attributes is a collection of all attributes.

### Create New Nodes

- document.createElement(tag) – creates an element with the given tag,
- document.createTextNode(value) – creates a text node (rarely used),
- elem.cloneNode(deep) – clones the element, if deep==true then with all descendants.

### Insertion and removal of nodes

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

### Style and Class

- className – the string value, good to manage the whole set of classes.
- classList – the object with methods add/remove/toggle/contains, good for individual classes.
- The style property is an object with camelCased styles. 
  - Reading and writing to it has the same meaning as modifying individual properties in the "style" attribute. 
  - To see how to apply important and other rare stuff – there’s a list of methods at MDN.
- The style.cssText property corresponds to the whole "style" attribute, the full string of styles.
- The getComputedStyle(elem[, pseudo]) returns the style-like object with them. Read-only.

### Element size and scrolling

- [Geometry](https://javascript.info/size-and-scroll#geometry)

### Coordinates

- document.elementFromPoint(x, y) returns the most nested element at window coordinates (x, y)
- clientX,clientY : When you scroll, clientX,clientY change, because they are relative to the window, but (pageX,pageY) remain the same.
- pageY = clientY + height of the scrolled-out vertical part of the document.
- pageX = clientX + width of the scrolled-out horizontal part of the document.


### Browser events

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

### Bubbling and capturing

- Bubbling : The bubbling principle is simple.
- When an event happens on an element, it first runs the handlers on it, then on its parent, then all the way up on other ancestors.

- Each handler can access event object properties:
  - event.target – the deepest element that originated the event.
  - event.currentTarget (=this) – the current element that handles the event (the one that has the handler on it)
  - event.eventPhase – the current phase (capturing=1, target=2, bubbling=3).

### Event delegation

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

### Browser actions:

- mousedown – starts the selection (move the mouse to select).
- click on `<input type="checkbox">` – checks/unchecks the input.
- submit – clicking an `<input type="submit">` or hitting Enter inside a form field causes this event to happen, and the browser submits the form after it.
- wheel – rolling a mouse wheel event has scrolling as the default action.
- keydown – pressing a key may lead to adding a character into a field, or other actions.
- contextmenu – the event happens on a right-click, the action is to show the browser context menu.

### Mouse Events: 

- The most used simple events are:
  - mousedown/mouseup : Mouse button is clicked/released over an element.
  - mouseover/mouseout : Mouse pointer comes over/out from an element.
  - mousemove : Every mouse move over an element triggers that event.

- Complex events
  - click : Triggers after mousedown and then mouseup over the same element if the left mouse button was used.
  - contextmenu : Triggers after mousedown if the right mouse button was used.
  - dblclick : Triggers after a double click over an element.
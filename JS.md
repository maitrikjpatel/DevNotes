---
date: '2019-01-13'
publish: 'true'
category: 'note'
author: 'Maitrik Patel'

title: 'Javascript'
description: 'Javascript is taking over the world'

topics: 'tools, development'

source: 'Github'
---

### Reading Tuts

- [MDN JS](https://developer.mozilla.org/en-US/docs/Learn/JavaScript)
- [JavaScript Information](https://javascript.info/)
- [You don't know JS](https://github.com/getify/You-Dont-Know-JS)
- [Resources for Staying on Top of JavaScript](https://code.tutsplus.com/articles/resources-for-staying-on-top-of-javascript--cms-21369)
- [Eloquent Javascript](http://eloquentjavascript.net/)

### Tuts

- [Javascript Enlightenment](https://frontendmasters.com/books/javascript-enlightenment)
- [JS Video Tuts](https://egghead.io/)

### Articles and Guideline

- [The Basics of Object-Oriented JavaScript](http://code.tutsplus.com/tutorials/the-basics-of-object-oriented-javascript--net-7670)
- [JavaScript Regular Expression](http://tutorialzine.com/2014/12/learn-regular-expressions-in-20-minutes/)
- [JS without JQuery](http://tutorialzine.com/2014/06/10-tips-for-writing-javascript-without-jquery/)
- [Principles of writing consistent, idiomatic JS](https://github.com/rwaldron/idiomatic.js)
- [JS Best Practice](https://www.thinkful.com/learn/javascript-best-practices-1/)
- [AngularJS Style Guide](https://github.com/johnpapa/angular-styleguide)
- [DOM manipulation in vanilla JS](https://medium.freecodecamp.org/dom-manipulation-in-vanilla-js-2036a568dcd9)

### Tools

- [JS Object method explorer](https://sdras.github.io/object-explorer/)
- [JavaScript Visualizer](https://tylermcginnis.com/javascript-visualizer/)

### Javascript.info Basic

- JavaScript is a multi-paradigm language, supporting imperative/procedural programming along with OOP (Object-Oriented Programming) with prototypal inheritance.and functional programming.
- JavaScript interprets the line break as an “implicit” semicolon. This is called an automatic semicolon insertion.
- Object Creation Pattern - Encapsulation
- Object Reuse Pattern - Inheritance

```
<!-- works -->
alert('Hello')
alert('World')

<!-- works -->
alert("There will be an error")
[1, 2].forEach(alert)

```

#### use strict
- To fully enable all features of modern JavaScript, we should start scripts with "use strict".
- The "use strict" directive switches the engine to the “modern” mode, changing the behavior of some built-in features.
- Strict mode is enabled by placing "use strict" at the top of a script or function.

#### Data-Types 

Distinctions between primitives and objects

- A primitive
	-	All other types are called “primitive” because their values can contain only a single thing (be it a string or a number or whatever).
	- Is a value of a primitive type.
	- There are 6 primitive types: string, number, boolean, symbol, null and undefined.

- An object
	- Is capable of storing multiple values as properties.
	- Can be created with {}, for instance: {name: "John", age: 30}. There are other kinds of objects in JavaScript; functions, for example, are objects.

#### Typeof

- We can call typeof thing to figure this out. Generally, the most useful types are "number," "string," "function," and of course, "object."

```
var someObject = {someProperty: someValue};
console.log( typeof someObject );
```

- We show how to use hasOwnProperty in the last two lines. It returns true or false, based on whether an object has a certain property.

ObjectName["PropertyName"]

```
var myObj = {
	name : '"lol"'
};
console.log( myObj.hasOwnProperty('name') );
console.log( myObj.hasOwnProperty('nickname') );
```

#### Type Conversions

- ToString, String(value) – Occurs when we output something. Can be performed with String(value). The conversion to string is usually obvious for primitive values.

- ToNumber, Number(value)– Occurs in math operations. Can be performed with Number(value).

```
undefined	-> NaN
null	-> 0
true / false	-> 1 / 0
string	-> The string is read “as is”, whitespaces from both sides are ignored. An empty string becomes 0. An error gives NaN
```

- ToBoolean, Boolean(value) – Occurs in logical operations. Can be performed with Boolean(value).

```
0, null, undefined, NaN, ""	-> false
any other -> value
```


#### ["===" vs "=="](https://codeburst.io/javascript-double-equals-vs-triple-equals-61d4ce5a121a)

- "===" : same type and have the same value, then === produces true and !== produces false.
- "==" : evil-twins/double-equal operator, however, tries to coerce the values before comparing them
	- Double equals also performs type coercion.
- Falsy values : false, null, undefined, "" (empty string), 0, NaN

#### [Null vs Undefined](https://codeburst.io/javascript-null-vs-undefined-20f955215a2)

- **Null**
	- null is an empty or non-existent value.
	- null must be assigned.
	- when using typeof to test null, it returns object
- **Undefined**
	- Undefined most typically means a variable has been declared, but not defined.

| Tables        | Undefined      |  Null  |
| ------------- |---------------|--------|
| Definition | variable has been declared but not yet been assigned a value | assignment value that means “no value”|
| Type | Undefined | Object|
| JSON | Invalid | Valid|
| Nature | Variable declared but not yet assigned | Represent intentional absence of object value|
| Check | typeof variableName === “undefined” | variableName === null|
| Arithmetic | Not-a-number (NaN) error | treated as zero value|
| Comparison | Equality operator will return true | Identity operator will return false|
| Identifier | Can be an identifier for a property of global object | Not an identifier for a property of the global object|

#### Comparisons

- Comparison operators return a boolean value.
- Strings are compared letter-by-letter in the “dictionary” order.
- When values of different types are compared, they get converted to numbers (with the exclusion of a strict equality check).
- The values null and undefined equal == each other and do not equal any other value.
- Be careful when using comparisons like > or < with variables that can occasionally be null/undefined. Checking for null/undefined separately is a good idea.

#### "While" vs "For" vs "Do/While"

- FOR loops are great for doing the same task over and over when you know ahead of time how many times you'll have to repeat the loop.

- WHILE loops are ideal when you have to loop, but you don't know ahead of time how many times you'll need to loop.

- Sometimes you want to make sure your loop runs at least one time no matter what. When this is the case, you want a modified while loop called a DO/WHILE loop.

```
#FOR Loop
for( var i = 0; i < 10 ; i++){

}

#WHILE Loop
var myCond = true;

while(myCond){
		console.log("While is here!");
		myCond = false;
}

var myCondi = false;

do{
		console.log("Do/While is here!");
}while(myCondi)
```

#### Function 

- Functions are values. They can be assigned, copied or declared in any place of the code.

- **Function Declaration**

	- If the function is declared as a separate statement in the main code flow, that’s called a “Function Declaration”.
	- Function Declarations are processed before the code block is executed. They are visible everywhere in the block.
	- a function, declared as a separate statement, in the main code flow.

	```
	function sum(a, b) {
		return a + b;
	}
	```

- **Function Expression**

	- If the function is created as a part of an expression, it’s called a “Function Expression”.
	- Function Expressions are created when the execution flow reaches them.
	-  A function, created inside an expression or inside another syntax construct. Here, the function is created at the right side of the “assignment expression”
	```
	let sum = function(a, b) {
		return a + b;
	};
	```

- **Callback functions**

	- The arguments of ask are called callback functions or just callbacks.

	```
	// Without CallBack
	function ask(question, yes, no) {
		if (confirm(question)) yes()
		else no();
	}

	function showOk() {
		alert( "You agreed." );
	}

	function showCancel() {
		alert( "You canceled the execution." );
	}
	// usage: functions showOk, showCancel are passed as arguments to ask
	ask("Do you agree?", showOk, showCancel);

	// With CallBack
	ask(
		"Do you agree?",
		function() { alert("You agreed."); },
		function() { alert("You canceled the execution."); }
	);
	```

- **Function Expression vs Function Declaration**

	- A Function Expression is created when the execution reaches it and is usable from then on.
	- Function Declaration is usable in the whole script/code block.

	```
	// The Function Declaration sayHi is created when JavaScript is preparing 
	// to start the script and is visible everywhere in it.
	sayHi("John"); // Hello, John

	function sayHi(name) {
		alert( `Hello, ${name}` );
	}

	// A Function Expression won't work

	sayHi("John"); // error!

	let sayHi = function(name) {  // (*) no magic any more
		alert( `Hello, ${name}` );
	};
	```

#### Object

- Let's go back to the analogy of computer languages being like regular spoken languages. In English, you have nouns (which you can think of as "things") and verbs (which you can think of as "actions"). Until now, our nouns (data, such as numbers, strings, or variables) and verbs (functions) have been separate.

- A constructor, as its name suggests, is designed to create and set up multiple instances of an object. 
- An object literal on the other hand is one-off, like string and number literals, and used more often as configuration objects or global singletons (e.g. for namespacing).
	- **Object literal:**
		- Literal notation creates a single object. Literal notation uses **curly brackets { }** and the object's default properties are defined within the brackets using **property:value** notation.

	```
	var objectName = {};

	var james = {
		job: "programmer",
		married: false,
	};

	var myObject = {
			iAm : 'an object',
			whatAmI : function(){
					alert('I am ' + this.iAm);
			}
	}
	```

	- **Object constructor:**

		- When we write **bob = new Object( );** we are using a built-in constructor called Object. This constructor is already defined by the JavaScript language and just makes an object with **no properties or methods.**

		- Constructor notation involves defining an object constructor. And like defining a function, we use the function keyword. You can think of this constructor as a "template" from which you can create multiple objects. To create a new object from a constructor, we use the new keyword.

	```
	function Object(){
			this.iAm = 'an object';
			this.whatAmI = function(){
					alert('I am ' + this.iAm);
			};
	};

	var objectName = new Object();

	function Person(job, married) {
			this.job = job;
			this.married = married;
	}

	var gabby = new Person("student",true);
	```

	- **Differences between constructor and literal**

		- The constructor object has its properties and methods defined with the keyword 'this' in front of it, whereas the literal version does not.

		- In the constructor object the properties/methods have their 'values' defined after an equal sign '=' whereas in the literal version, they are defined after a colon ':'.

		- The constructor function can have (optional) semi-colons ';' at the end of each property/method declaration whereas in the literal version if you have more than one property or method, they MUST be separated with a comma ',', and they CANNOT have semi-colons after them, otherwise JavaScript will return an error.

- **Bracket Notation : ObjectName["PropertyName"]**

	- An advantage of bracket notation is that we are not restricted to just using strings that is: no spaces and other limitations.
	- Square brackets notation obj["property"]. Square brackets allow to take the key from a variable, like obj[varWithKey].

```
let user = {};

// set
user["likes birds"] = true;

// get
alert(user["likes birds"]); // true

// delete
delete user["likes birds"];
```

- **Additional operators**

	- To delete a property: delete obj.prop.
	- To check if a property with the given key exists: "key" in obj.
	- To iterate over an object: for (let key in obj) loop.

- **Cloning and merging, Object.assign**

	- A variable stores not the object itself, but its “address in memory”, in other words “a reference” to it.
	- When an object variable is copied – the reference is copied, the object is not duplicated.
	- If we imagine an object as a cabinet, then a variable is a key to it. Copying a variable duplicates the key, but not the cabinet itself.

```

let user = {
	name: "John",
	age: 30
};

//-----------Copying object---------

let admin = user; // copy the reference
admin.name = "Pete" // Updated to user reference object
alert( user.name ); // Pete as object reference changed

//-----------Clone using loop---------
// Cloning
let user = {
	name: "John",
	age: 30
};

let clone = {}; // the new empty object
for (let key in user) {
	clone[key] = user[key];
}

clone.name = "Pete"; // changed the data in it
alert( user.name ); // John in original object as clone has its own object reference

//---------Object.Assign------------
let clone = Object.assign({}, user);

```

#### Garbage collection

- The main concept of memory management in JavaScript is reachability.
- Simply put, “reachable” values are those that are accessible or usable somehow. They are guaranteed to be stored in memory.
- If object is unreachable and Garbage collector will junk the data and free the memory.

#### Symbols 

- “Symbol” value represents a unique identifier.
- Symbols are guaranteed to be unique. Even if we create many symbols with the same description, they are different values. 

```
// id is a symbol with the description "id"
let id1 = Symbol("id");
let id2 = Symbol("id");

alert(id1 == id2); // false
```

- Symbols don’t auto-convert to a string
- Symbol in an object literal, we need square brackets.

```
let id = Symbol("id");

let user = {
  name: "John",
  [id]: 123 // not just "id: 123"
};
```

- **Global symbols**
	- Symbols inside the registry are called global symbols. If we want an application-wide symbol, accessible everywhere in the code – that’s what they are for.

	```
	// read from the global registry
	let id = Symbol.for("id"); // if the symbol did not exist, it is created
	```

	- The Symbol.keyFor internally uses the global symbol registry to look up the key for the symbol. So it doesn’t work for non-global symbols. If the symbol is not global, it won’t be able to find it and return undefined.

	```
	alert( Symbol.keyFor(Symbol.for("name")) ); // name, global symbol
	alert( Symbol.keyFor(Symbol("name2")) ); // undefined, the argument isn't a global symbol
	```

#### Methods

- Functions that are stored in object properties are called “methods”.
- Methods allow objects to “act” like object.doSomething().
- Methods can reference the object as "this".

#### The "this" Keyword

- The keyword "this" acts as a placeholder, and will refer to whichever object called that method when the method is actually used.
- When a function is declared, it may use "this", but that "this" has no value until the function is called.

```
let user = {
  name: "John",
  age: 30,

  sayHi() {
    alert(this.name);
  }
};

user.sayHi(); // John
```

- That function can be copied between objects.
- When a function is called in the “method” syntax: object.method(), the value of "this" during the call is object.
- "this" is undefined in strict mode.
- If we try to access this.name, there will be an error.

```
function sayHi() {
  alert(this);
}

sayHi(); // undefined
```

- In non-strict mode the value of "this" in such case will be the global object (window in a browser, we’ll get to it later in the chapter Global object). This is a historical behavior that "use strict" fixes.

- NOTE: Arrow functions are special: they have no this. When this is accessed inside an arrow function, it is taken from outside.

#### Object to primitive conversion

- The object-to-primitive conversion is called automatically by many built-in functions and operators that expect a primitive as a value.

- There are 3 types (hints) of it:
	- "string" (for alert and other string conversions)
	- "number" (for maths)
	- "default" (few operators)

- The specification describes explicitly which operator uses which hint. There are very few operators that “don’t know what to expect” and use the "default" hint. Usually for built-in objects "default" hint is handled the same way as "number", so in practice the last two are often merged together.

- The conversion algorithm is:

- Call obj[Symbol.toPrimitive] (hint) if the method exists,
- Otherwise if hint is "string"
	- try obj.toString() and obj.valueOf(), whatever exists.
- Otherwise if hint is "number" or "default"
	- try obj.valueOf() and obj.toString(), whatever exists.


#### Data Types

##### Number

- All numbers in JavaScript are stored in 64-bit format IEEE-754, also known as “double precision floating point numbers”.
- Append "e" with the zeroes count to the number. Like: 123e6 is 123 with 6 zeroes.
- A negative number after "e" causes the number to be divided by 1 with given zeroes. That’s for one-millionth or such.

- For different numeral systems:
	- Can write numbers directly in hex (0x), octal (0o) and binary (0b) systems
	- parseInt(str, base) parses an integer from any numeral system with base: 2 ≤ base ≤ 36.
	- num.toString(base) converts a number to a string in the numeral system with the given base.
	
- For converting values like 12pt and 100px to a number:
	- Use parseInt/parseFloat for the “soft” conversion, which reads a number from a string and then returns the value they could read before the error.

- For fractions:
	- Round using Math.floor, Math.ceil, Math.trunc, Math.round or num.toFixed(precision).
	- Make sure to remember there’s a loss of precision when working with fractions.

- More mathematical functions:
	- See the Math object when you need them. The library is very small, but can cover basic needs.

##### Strings

- There are 3 types of quotes. Backticks allow a string to span multiple lines and embed expressions.
- Strings in JavaScript are encoded using UTF-16.
- We can use special characters like \n and insert letters by their unicode using \u....
- To get a character, use: [].
- To get a substring, use: slice or substring.
- To lowercase/uppercase a string, use: toLowerCase/toUpperCase.
- To look for a substring, use: indexOf, or includes/startsWith/endsWith for simple checks.
- To compare strings according to the language, use: localeCompare, otherwise they are compared by character codes.

- There are several other helpful methods in strings:
	- str.trim() – removes (“trims”) spaces from the beginning and end of the string.
	- str.repeat(n) – repeats the string n times.

##### Array

- Array is a special kind of object, suited to storing and managing ordered data items.
- The call to new Array(number) creates an array with the given length, but without elements.
```
// square brackets (usual)
let arr = [item1, item2...];

// new Array (exceptionally rare)
let arr = new Array(item1, item2...);

let arr = new Array(2); // will it create an array of [2] ?
alert( arr[0] ); // undefined! no elements.
alert( arr.length ); // length 2
```

- Array implement only toString conversion

```
alert( [] + 1 ); // ( "" + 1 ) -> "1"
alert( [1] + 1 ); // ( "1" + 1 ) -> "11"
alert( [1,2] + 1 ); // ( "1,2" + 1 ) ->  "1,21"
```

- Loop in array

```
for (let i=0; i<arr.length; i++) – works fastest, old-browser-compatible.
for (let item of arr) – the modern syntax for items only,
for (let i in arr) – never use.
```

- We can use an array as a deque with the following operations:

-	**To add/remove elements:**
	- push(...items) adds items to the end.
	- pop() removes the element from the end and returns it.
	- shift() removes the element from the beginning and returns it.
	- unshift(...items) adds items to the beginning.
	- splice(position, deleteCount, ...items) – at index position delete deleteCount elements and insert items.
	- slice(start, end) – creates a new array, copies elements from position start till end (not inclusive) into it.
	- forEach(func(item, index, array){}) – calls func for every element, does not return anything.
	- concat(...items) – returns a new array: copies all members of the current one and adds items to it. If any of items is an array, then its elements are taken.

- **To search among elements:**
	- indexOf/lastIndexOf(item, pos) – look for item starting from position pos, return the index or -1 if not found.
	- includes(value) – returns true if the array has value, otherwise false.
	- find/filter(func) – filter elements through the function, return first/all values that make it return true.
	- findIndex is like find, but returns the index instead of a value.
	- To iterate over elements:
	- forEach(func) – calls func for every element, does not return anything.

- **To transform the array:**
	- map(func) – creates a new array from results of calling func for every element.
	- sort(func) – sorts the array in-place, then returns it.
	- reverse() – reverses the array in-place, then returns it.
	- split/join – convert a string to array and back.
	- reduce(func, initial) – calculate a single value over the array by calling func for each element and passing an intermediate result between the calls.
	- sort(), reverse() and splice() modify the array itself.
	- slice(), concat() and map() create a new array.

- **Additionally:**
	- Array.isArray(arr) checks arr for being an array.

##### Iterables

- Iterable objects is a generalization of arrays. That’s a concept that allows to make any object useable in a for..of loop.
- Objects that can be used in for..of are called iterable.
- Technically, iterables must implement the method named Symbol.iterator.
	- The result of obj[Symbol.iterator] is called an iterator. It handles the further iteration process.
	- An iterator must have the method named next() that returns an object {done: Boolean, value: any}, here done:true denotes the iteration end, otherwise the value is the next value.
- The Symbol.iterator method is called automatically by for..of, but we also can do it directly.
- Built-in iterables like strings or arrays, also implement Symbol.iterator.
- String iterator knows about surrogate pairs.
- Array.from(obj[, mapFn, thisArg]) makes a real Array of an iterable or array-like obj, and we can then use array methods on it. The optional arguments mapFn and thisArg allow us to apply a function to each item.

##### Map, Set, WeakMap and WeakSet

- **MAP**
	- Map is a collection of keyed data items, just like an Object. But the main difference is that Map allows keys of any type.
	- unlike objects, keys are not converted to strings. Any type of key is possible.

	- new Map() – creates the map.
	- map.set(key, value) – stores the value by the key.
	- map.get(key) – returns the value by the key, undefined if key doesn’t exist 	- in map.
	- map.has(key) – returns true if the key exists, false otherwise.
	- map.delete(key) – removes the value by the key.
	- map.clear() – clears the map
	- map.size – returns the current element count.

```
let map = new Map();

map.set('1', 'str1');   // a string key
map.set(1, 'num1');     // a numeric key
map.set(true, 'bool1'); // a boolean key

// remember the regular Object? it would convert keys to string
// Map keeps the type, so these two are different:
alert( map.get(1)   ); // 'num1'
alert( map.get('1') ); // 'str1'

alert( map.size ); // 3
```

- **Map from Object**
- When a Map is created, we can pass an array (or another iterable) with key-value pairs, like this:

```
// array of [key, value] pairs
let map = new Map([
  ['1',  'str1'],
  [1,    'num1'],
  [true, 'bool1']
]);
```

- **Iteration over Map**
	- For looping over a map, there are 3 methods:

		- map.keys() – returns an iterable for keys,
		- map.values() – returns an iterable for values,
		- map.entries() – returns an iterable for entries [key, value], it’s used by default in for..of.

```
let recipeMap = new Map([
  ['cucumber', 500],
  ['tomatoes', 350],
  ['onion',    50]
]);

// iterate over keys (vegetables)
for (let vegetable of recipeMap.keys()) {
  alert(vegetable); // cucumber, tomatoes, onion
}

// iterate over values (amounts)
for (let amount of recipeMap.values()) {
  alert(amount); // 500, 350, 50
}

// iterate over [key, value] entries
for (let entry of recipeMap) { // the same as of recipeMap.entries()
  alert(entry); // cucumber,500 (and so on)
}
```
- **SET**
	- A Set is a collection of values, where each value may occur only once.
	- Its main methods are:
		- new Set(iterable) – creates the set, optionally from an array of values (any iterable will do).
		- set.add(value) – adds a value, returns the set itself.
		- set.delete(value) – removes the value, returns true if value existed at the moment of - the call, otherwise false.
		- set.has(value) – returns true if the value exists in the set, otherwise false.
		- set.clear() – removes everything from the set.
		- set.size – is the elements count.

```
let set = new Set();

let john = { name: "John" };
let pete = { name: "Pete" };
let mary = { name: "Mary" };

// visits, some users come multiple times
set.add(john);
set.add(pete);
set.add(mary);
set.add(john);
set.add(mary);

// set keeps only unique values
alert( set.size ); // 3

for (let user of set) {
  alert(user.name); // John (then Pete and Mary)
}
```
- Iteration over Set

```
let set = new Set(["oranges", "apples", "bananas"]);

for (let value of set) alert(value);

// the same with forEach:
set.forEach((value, valueAgain, set) => {
  alert(value);
});
```
- set.keys() – returns an iterable object for values,
- set.values() – same as set.keys, for compatibility with Map,
- set.entries() – returns an iterable object for entries [value, value], exists for compatibility with Map.

- **WeakMap**
	- WeakMap is a variant of Map that allows only objects as keys and removes them once they become inaccessible by other means.
	- It does not support operations on the structure as a whole: no size, no clear(), no iterations.

- **WeakSet**
	- WeakSet is a variant of Set that only stores objects and removes them once they become inaccessible by other means.

- WeakSet/WeakMap is a special kind of Set/Map that does not prevent JavaScript from removing its items from memory.
- Also does not support size/clear() and iterations.
- WeakMap and WeakSet are used as “secondary” data structures in addition to the “main” object storage.
- Once the object is removed from the main storage, if it is only found in the WeakMap/WeakSet, it will be cleaned up automatically.

##### Destructuring assignment

- Destructuring assignment is a special syntax that allows us to “unpack” arrays or objects into a bunch of variables, as sometimes they are more convenient. 

```
// let [item1 = default, item2, ...rest] = array
// we have an array with the name and surname
let arr = ["Ilya", "Kantor"]

// destructuring assignment
let [firstName, surname] = arr;

alert(firstName); // Ilya
alert(surname);  // Kantor
```

- **Object destructuring**

The destructuring assignment also works with objects.

```
// let {prop : varName = default, ...} = object
let options = {
  title: "Menu",
  width: 100,
  height: 200
};

let {title, width, height} = options;

alert(title);  // Menu
alert(width);  // 100
alert(height); // 200
```

```
let options = {
  title: "Menu"
};

// chnage name
// assign value 
// change order
// function({
//   incomingProperty: parameterName = defaultValue
//.})
let {
	width: w = 100, 
	height: h = 200, 
	title
	} = options;

alert(title);  // Menu
alert(w);      // 100
alert(h);      // 200
```

- Smart function parameters 

```
let options = {
  title: "My menu",
  items: ["Item1", "Item2"]
};

function showMenu({
  title = "Untitled",
  width: w = 100,  // width goes to w
  height: h = 200, // height goes to h
  items: [item1, item2] // items first element goes to item1, second to item2
}) {
  alert( `${title} ${w} ${h}` ); // My Menu 100 200
  alert( item1 ); // Item1
  alert( item2 ); // Item2
}

showMenu(options);
```

##### Date and time

- Use it to store creation/modification times, to measure time, or just to print out the current date.
- Months are counted from zero (yes, January is a zero month).
- Days of week in getDay() are also counted from zero (that’s Sunday).

```
new Date(year, month, date, hours, minutes, seconds, ms)
```

- Access date components
	- getFullYear()
	- getMonth()
	- getDate()
	- getHours()
	- getMinutes()
	- getSeconds()
	- getMilliseconds()
	- getTime()
	- getTime()
	- getTimezoneOffset()

- Setting date components
	- setFullYear(year [, month, date])
	- setMonth(month [, date])
	- setDate(date)
	- setHours(hour [, min, sec, ms])
	- setMinutes(min [, sec, ms])
	- setSeconds(sec [, ms])
	- setMilliseconds(ms)
	- setTime(milliseconds)

- Date.now()
	- There’s a special method Date.now() that returns the current timestamp.
	- It is semantically equivalent to new Date().getTime(), but it doesn’t create an intermediate Date object. So it’s faster and doesn’t put pressure on garbage collection.

##### JSON 
- The JSON (JavaScript Object Notation) is a general format to represent values and objects. 
- JavaScript provides methods:
		- JSON.stringify to convert objects into JSON.
		- JSON.parse to convert JSON back into an object.

- **JSON.stringify**
	- JSON is data-only cross-language specification, so some JavaScript-specific object properties are skipped by JSON.stringify.
	- Namely:
		- Function properties (methods).
		- Symbolic properties.
		- Properties that store undefined.

	```
	let user = {
		sayHi() { // ignored
			alert("Hello");
		},
		[Symbol("id")]: 123, // ignored
		something: undefined // ignored
	};

	alert( JSON.stringify(user) ); // {} (empty object)
	```

	- The important limitation: there must be no circular references.

	```
	let room = {
		number: 23
	};

	let meetup = {
		title: "Conference",
		participants: ["john", "ann"]
	};

	meetup.place = room;       // meetup references room
	room.occupiedBy = meetup; // room references meetup

	JSON.stringify(meetup); // Error: Converting circular structure to JSON
	```

	- Excluding and transforming: replacer
		- `let json = JSON.stringify(value[, replacer[, space]])`
		- JSON.stringify is used with the first argument only. But if we need to fine-tune the replacement process, like to filter out circular references, we can use the second argument of JSON.stringify.

	```
	let room = {
		number: 23
	};

	let meetup = {
		title: "Conference",
		participants: [{name: "John"}, {name: "Alice"}],
		place: room // meetup references room
	};

	room.occupiedBy = meetup; // room references meetup

	alert( JSON.stringify(meetup, ['title', 'participants', 'place', 'name', 'number']) );
	/*
	{
		"title":"Conference",
		"participants":[{"name":"John"},{"name":"Alice"}],
		"place":{"number":23}
	}
	*/
	```

- **JSON.parse**

	```
	//Syntax : let value = JSON.parse(str[, reviver]);
	let schedule = `{
		"meetups": [
			{"title":"Conference","date":"2017-11-30T12:00:00.000Z"},
			{"title":"Birthday","date":"2017-04-18T12:00:00.000Z"}
		]
	}`;
	// JSON.parse(str[, reviver]);
	// JSON.parse(schedule, function());
	schedule = JSON.parse(schedule, function(key, value) {
		if (key == 'date') return new Date(value);
		return value;
	});

	alert( schedule.meetups[1].date.getDate() ); // works!
	```

- **Custom “toJSON”**
	- Like toString for string conversion, an object may provide method toJSON for to-JSON conversion. JSON.stringify automatically calls it if available.

	```
	let room = {
		number: 23,
		toJSON() {
			return this.number;
		}
	};

	let meetup = {
		title: "Conference",
		room
	};

	alert( JSON.stringify(room) ); // 23

	alert( JSON.stringify(meetup) );
	/*
		{
			"title":"Conference",
			"room": 23
		}
	*/
	```

#### Recursion

- Recursion is a programming term that means a “self-calling” function. Such functions can be used to solve certain tasks in elegant ways.

- When a function calls itself, that’s called a recursion step. The basis of recursion is function arguments that make the task so simple that the function does not make further calls.

- A recursively-defined data structure is a data structure that can be defined using itself.
	- For instance, the linked list can be defined as a data structure consisting of an object referencing a list (or null).
	- `list = { value, next -> list }`
	- Linked list 
	```
	let list = { value: 1 };
	list.next = { value: 2 };
	list.next.next = { value: 3 };
	list.next.next.next = { value: 4 };
	```
	- Trees like HTML elements tree or the department tree from this chapter are also naturally recursive: they branch and every branch can have other branches.

#### Rest Parameters "..."
- A function can be called with any number of arguments, no matter how it is defined.
- The rest parameters must be at the end

```
function showName(firstName, lastName, ...titles) {
  alert( firstName + ' ' + lastName ); // Julius Caesar

  // the rest go into titles array
  // i.e. titles = ["Consul", "Imperator"]
  alert( titles[0] ); // Consul
  alert( titles[1] ); // Imperator
  alert( titles.length ); // 2
}

showName("Julius", "Caesar", "Consul", "Imperator");
```

- **The “arguments” variable**
	- There is also a special array-like object named arguments that contains all arguments by their index.
	- arguments is both array-like and iterable, it’s not an array. It does not support array methods, so we can’t call arguments.map(...) for example.
	- In old times, rest parameters did not exist in the language, and using arguments was the only way to get all arguments of the function, no matter their total number.
	- All arguments of a function call are also available in “old-style” arguments: array-like iterable object.
	- Arrow functions do not have "arguments"

```
function showName() {
  alert( arguments.length );
  alert( arguments[0] );
  alert( arguments[1] );

  // it's iterable
  // for(let arg of arguments) alert(arg);
}

// shows: 2, Julius, Caesar
showName("Julius", "Caesar");

// shows: 1, Ilya, undefined (no second argument)
showName("Ilya");
```

#### Spread operator
- ...Spread Operator
- The spread operator internally uses iterators to gather elements, the same way as for..of does.
- there’s a subtle difference between Array.from(obj) and [...obj]:
	- Array.from operates on both array-likes and iterables.
	- The spread operator operates only on iterables.
- the task of turning something into an array, Array.from tends to be more universal.

```
let arr = [3, 5, 1];
let arr2 = [8, 9, 15];
let str = "Hello";

let merged = [0, ...arr, 2, ...arr2];
alert( [...str] ); // H,e,l,l,o
alert(merged); // 0,3,5,1,2,8,9,15 (0, then arr, then 2, then arr2)
```

#### Rest parameters vs spread operator.

- There’s an easy way to distinguish between them:
	- When ... is at the end of function parameters, it’s “rest parameters” and gathers the rest of the list of arguments into an array.
	- When ... occurs in a function call or alike, it’s called a “spread operator” and expands an array into a list.

- Use patterns:
	- Rest parameters are used to create functions that accept any number of arguments.
	- The spread operator is used to pass an array to functions that normally require a list of many arguments.

- Together they help to travel between a list and an array of parameters with ease.

#### JS Closures

- **Lexical Environment**
	- In JavaScript, every running function, code block {...}, and the script as a whole have an internal (hidden) associated object known as the Lexical Environment.
	- “Lexical Environment” is a specification object. We can’t get this object in our code and manipulate it directly.
	- A Lexical Environment is created when a code block runs and contains block-local variables. Example : If, For, While and {...}
	- The Lexical Environment object consists of two parts:
		1. Environment Record – an object that stores all local variables as its properties (and some other information like the value of this).
		2. A reference to the outer lexical environment, the one associated with the outer code.
	
	- A “variable” is just a property of the special internal object, associated with the currently executing block/function/script Environment Record.
	- Working with variables is actually working with the properties of that object.
	- “To get or change a variable” means “to get or change a property of that object.
	- When the code wants to access a variable – the inner Lexical Environment is searched first, then the outer one, then the more outer one and so on until the global one.
	- A function gets outer variables as they are now; it uses the most recent values.
	- One call – one Lexical Environment : a new function Lexical Environment is created each time a function runs.
	- Lexical Environment is cleaned up and deleted after the function run

```
//----No Clousre----
//----Access outer Lexical Envrionment Object variable---
let name = "John";

function sayHi() {
  alert("Hi, " + name);
}

name = "Pete"; // (*)

sayHi(); // Pete
```

- **Closures**
	- A closure is a function that remembers its outer variables and can access them.
	- All functions in JavaScript are closures
	- A closure is an inner function that has access to the outer (enclosing) function’s variables—scope chain.
	- The closure has three scope chains: 
		1. it has access to its own scope (variables defined between its curly brackets), 
		2. it has access to the outer function’s variables, and 
		3. it has access to the global scope variables.

	```
	function makeWorker() {
		let name = "Pete";
		return function() {
			alert(name);
		};
	}
	let name = "John";
	// create a function
	let work = makeWorker();
	// call it
	work(); // Pete

	// ----- Example Two ------

	let count = 100;
	function makeCounter() {
		let count = 0;
		return function() {
			return count++; // has access to the outer counter
		};
	}

	let counter = makeCounter();

	alert( counter() ); // 0
	alert( counter() ); // 1
	alert( counter() ); // 2

	// ----- Example Three ------

	let c = 4
	const addX = x => n => n + x
	const addThree = addX(3)
	let d = addThree(c)
	console.log('example partial application', d) // example partial application 7

	//---Real life example------

	function makeSizer(size) {
		return function() {
			document.body.style.fontSize = size + 'px';
		};
	}

	var size12 = makeSizer(12);
	var size14 = makeSizer(14);
	var size16 = makeSizer(16);

	document.getElementById('size-12').onclick = size12;
	document.getElementById('size-14').onclick = size14;
	document.getElementById('size-16').onclick = size16;

	//--- html code
	<a href="#" id="size-12">12</a>
	<a href="#" id="size-14">14</a>
	<a href="#" id="size-16">16</a>						
	```

- **Immediately-invoked function expressions - IIFE**
	- The Function Expression is wrapped with parenthesis (function {...})
	- Parentheses around the function is a trick to show JavaScript that the function is created in the context of another expression, and hence it’s a Function Expression: it needs no name and can be called immediately.
	```
	// Ways to create IIFE
	(function() {
		alert("Parentheses around the function");
	})();

	(function() {
		alert("Parentheses around the whole thing");
	}());

	!function() {
		alert("Bitwise NOT operator starts the expression");
	}();

	+function() {
		alert("Unary plus starts the expression");
	}();
	```

#### Var vs Let vs Const

- Var : Global and Function scope
	- var variables are either function-wide or global, they are visible through blocks.

- Let : Will provide true block scoping, unlike var
	- Ideal to use it for programming as it will help to avoid hosting.

- Const
	- will make variable Read only
	- Never change , will give error if you try to change it.
	- Will shadow outer declaration
	- Block Scoping
	- We generally use upper case for constants that are “hard-coded”. Or, in other words, when the value is known prior to execution and directly written into the code.


### Topics

#### Hoisting

- **[Hoisting](https://scotch.io/tutorials/understanding-hoisting-in-javascript)**
- Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution.
- variable and function declarations are put into memory during the compile phase, but stays exactly where you typed it in your coding.
- The variables can be initialized and used before declared. But they cannot be used without initialization.
- all undeclared variables are global variables.
- JavaScript only hoists declarations, not initializations.
- Hoisted : Use -> Initialize (Hoisted variable is initialised with a value of undefined)

```
var x = 1; // Initialize x
console.log(x + " " + y); // '1 undefined'
var y = 2; // Initialize y
```

- Hoisted : Declare -> Use -> Initialize (Hoisted variable is initialised with a value of undefined)

```
// The following code will behave the same as the previous code:
var x = 1; // Initialize x
var y; // Declare y
console.log(x + " " + y); // '1 undefined'
y = 2; // Initialize y
```

- Avoid Hoisting pitfall : Initialize -> Use -> Declare

```
num = 6;
num + 7;
var num;
/* gives no errors as long as num is declared*/
```

- Avoid Hoisting pitfall : Declare -> Initialize -> Use

```
var x = 1; // Declare and Initialize x
console.log(x); // '1'
```

- "use strict" : strict mode can help expose undeclared variables.
- ES6 let : The interpreter throws an error if we use a constant before declaring and initialising it.

```
console.log(hoist); // Output: ReferenceError: hoist is not defined
let hoist = 'The variable has been hoisted.';
```

- ES6 const : The interpreter throws an error if we use a constant before declaring and initialising it.

```
const PI;
console.log(PI); // Ouput: SyntaxError: Missing initializer in const declaration
PI=3.142;

function getCircumference(radius) {
	console.log(circumference)
	circumference = PI*radius*2;
	const PI = 22/7;
}

getCircumference(2) // ReferenceError: circumference is not defined
// PI was used before it was declared, which is illegal for const variables.
```

- Function declarations are hoisted over variable declarations but not over variable assignments.

```
var double = 22;

function double(num) {
	return (num*2);
}

console.log(typeof double); // Output: number

var double;

function double(num) {
	return (num*2);
}

console.log(typeof double); // Output: function
```

#### CallBack Hell

- [CallBack Hell](http://callbackhell.com/)
- Don't nest functions. Give them names and place them at the top level of your program
- Use **function hoisting** to your advantage to move functions 'below the fold'
- Handle **every single error** in every one of your callbacks. Use a linter like standard to help you with this.
- Create reusable functions and place them in a module to reduce the cognitive load required to understand your code.
- Splitting your code into small pieces like this also helps you handle errors, write tests, forces you to create a stable and documented public API for your code, and helps with refactoring.

#### Promise

- [Promise for dummies](https://scotch.io/tutorials/javascript-promises-for-dummies)
- [Video with Code Example](http://plnkr.co/edit/1ArvFxI0gWmajTpDaOSB?p=preview)
- Promise are made of two parts. Control/Promise
- Control : One type of callback. Succeeded or Failed.
- Promise : Pending/Fullfilled/Rejected

```
// promise syntax look like this
new Promise(/* executor*/ function (resolve, reject) { ... } );
```

- .then for go inside next chain.
- .catch for find an error.
- Promise.all to execute after all promises resolved.
- Promise.race to execute after first promise resolved.
- Use Generator to make async code more readable.

#### Aync and Await

- [Understanding Async and Await](https://ponyfoo.com/articles/understanding-javascript-async-await)
- [Async/Await Blows Promises](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9)
- Async/await is a new way to write asynchronous code. Previous options for asynchronous code are callbacks and promises.
- Async/await is, like promises, non blocking.
- Async/await makes asynchronous code look and behave a little more like synchronous code. This is where all its power lies.
- Async - declares an asynchronous function (async function someName(){...}). - Automatically transforms a regular function into a Promise. - When called async functions resolve with whatever is returned in their body. - Async functions enable the use of await.

- Await - pauses the execution of async functions. (var result = await someAsyncCall();). - When placed in front of a Promise call, await forces the rest of the code to wait until that Promise finishes and returns a result. - Await works only with Promises, it does not work with callbacks. - Await can only be used inside async functions.

#### Event delegation

- [How JavaScript Event Delegation Works](https://davidwalsh.name/event-delegate)
- [Event delegation](https://javascript.info/event-delegation)
- [Bubbling and capturing](https://javascript.info/bubbling-and-capturing#stopping-bubbling)
	- event.target – the deepest element that originated the event.
	- event.currentTarget (=this) – the current element that handles the event (the one that has the handler on it)
	- event.eventPhase – the current phase (capturing=1, bubbling=3).
	- addEventListener without the 3rd argument or with the 3rd argument false.

```
el.addEventListener('click', listener, false) // listener doesn't capture
el.addEventListener('click', listener) // listener doesn't capture
```

#### Functional Programming

- [MPJ FP Videos](https://www.youtube.com/watch?v=BMUiFMZr7vk&list=PL0zVEGEvSaeEd9hlmCXrk5yUyqUag-n84)
- Less Code, Less Bugs, Less time.
- Functions are values, exploit them by divide in small simple function.
- Higher order function: Function taker other function as argument.
- Filter take another function as argument and process array.
- Composition : Composing them together using higher order function.
- **Map** : Higher Order Function, take callback function.

```
var names = animals.map(function(animal){
	return animal.name;
})
```

- Reduce
- **Currying** : Currying is a way of constructing functions that allows partial application of a function’s arguments. - What this means is that you can pass all of the arguments a function is expecting and get the result, or pass a subset of those arguments and get a function back that’s waiting for the rest of the arguments. - Use external library like lodash to get currying funcitonlity.
- Recursion

### JS Good Parts [Book]

#### Best Practice

- use UPPERCASE for global variable
- x +=1 instead of x++
- Use JSLint
- Use " for external strings.
- Use ' for internal strings and characters.
- Convert a number to a string - Use number’s method (toString) - Use String function

```
str = num.toString();
str = String(num);
```

- Convert a string to a number - Use the Number function. - Use the + prefix operator. - Use the parseInt function.

```
		num = Number(str);
		num = +str;
```

- Declare all variables at the top of the function.
- Declare all functions before you call them.
- Return statement
	- If there is no expression, then the return value is undefined.
	- Except for constructors, whose default return value is this.

```
return expression; or return;
```

- Tennent’s Principle of Correspondence

```
expression
(function () {
	return expression;
}())
```

#### Good Part

- Prototype
- Objects
- Only one number type
- Array : No need to provide a length or type when creating an array.
- Use array.splice(number,1) than delete arry[number] for deleting arry element.
- Use objects when the names are arbitrary strings.
- Use arrays when the names are sequential integers.
- Falsy values : false, null, undefined, "" (empty string), 0, NaN
- JS is loosely typed language
- It is always better to use === and !==, which do not do type coercion.

#### Bad Part

- NaN : Not a Number , NaN is not equal to anything, including NaN - NaN === NaN is false - NaN !== NaN is true
  -Equal and not equal : These operators can do type coercion

### ---------------CODEACADEMY-----------------

#### Passing Objects into Functions

- Making arrays of Objects, we can use objects as parameters for functions as well. That way, these functions can take advantage of the methods and properties that a certain object type provides.

```
// Our person constructor
function Person (name, age) {
		this.name = name;
		this.age = age;
}

// We can make a function which takes persons as arguments
// This one computes the difference in ages between two people
var ageDifference = function(person1, person2) {
		return person1.age - person2.age;
}

var alice = new Person("Alice", 30);
var billy = new Person("Billy", 25);

// get the difference in age between alice and billy using our function
var diff = ageDifference(alice,billy)
```

#### Getting IN-timate

- To print out all elements and properties, we can use a for/in loop, like this:

```
for(var property in dog) {
	console.log(property);
}

// write a for-in loop to print the value of nyc's properties
for(var x in nyc) {
	console.log(nyc[x]);
}
```

#### Prototype

- What a class has or doesn't have? That is the job of the prototype.
- JavaScript automatically defines the prototype for class with a constructor.
- If you want to add a method to a class such that all members of the class can use it, we use the following syntax to extend the prototype:

```
className.prototype.newMethod = function() {
	statements;
};
//-----
function Dog (breed) {
	this.breed = breed;
}
Dog.prototype.bark = function() {
	console.log("Woof");
};
var buddy = new Dog("golden Retriever");
var snoopy = new Dog("Beagle");
snoopy.bark();
buddy.bark();
```

#### DRY Penguins - Inheritance

- In object-oriented programming, inheritance allows one class to see and use the methods and properties of another class. You can think of it as a child being able to use his or her parent's money because the child inherits the money.

- We will learn more about inheritance as we continue this lesson, but for now let's just refresh our memories about how classes and object

- **Prototype chain**

	- If JavaScript encounters something it can't find in the current class's methods or properties, it looks up the prototype chain to see if it's defined in a class that it inherits from. This keeps going upwards until it stops all the way at the top: the mighty Object.prototype (more on this later).

```
// original classes
function Animal(name, numLegs) {
		this.name = name;
		this.numLegs = numLegs;
		this.isAlive = true;
}
function Penguin(name) {
		this.name = name;
		this.numLegs = 2;
}
function Emperor(name) {
		this.name = name;
		this.saying = "Waddle waddle";
}

// set up the prototype chain
Penguin.prototype = new Animal();
Emperor.prototype = new Penguin();

var myEmperor = new Emperor("Jules");

console.log(myEmperor.saying); // should print "Waddle waddle"
console.log(myEmperor.numLegs); // should print 2
console.log(myEmperor.isAlive); // should print true
```

#### Private Number and Methods

- Just as functions can have local variables which can only be accessed from within that function, objects can have private variables. Private variables are pieces of information you do not want to publicly share, and they can only be directly accessed from within the class.

```
function Person(first,last,age) {
	this.firstname = first;
	this.lastname = last;
	this.age = age;
	var bankBalance = 7500; // PRIVATE NUMBER

	var returnBalance = function() {
		return bankBalance;
	};

	// create the new function here
	this.askTeller = function() {
		return returnBalance;
	};
}

var john = new Person('John','Smith',30);
console.log(john.returnBalance);
var myBalanceMethod = john.askTeller();
var myBalance = myBalanceMethod();
console.log(myBalance);
```

#### Pseudoclassical Inheritance

```
function Gizmo(id) {
	this.id = id;
}
Gizmo.prototype.toString = function () {
	return "gizmo " + this.id;
};
function Hoozit(id) {
	this.id = id;
}
Hoozit.prototype = new Gizmo();
Hoozit.prototype.test = function (id) {
	return this.id === id;
};
```

#### Functional Inheritance

```
function gizmo(id) {
	return {
		id: id,
		toString: function () {
			return "gizmo " + this.id;
		}
	};
}
function hoozit(id) {
	var that = gizmo(id);
	that.test = function (testid) {
		return testid === this.id;
	};
	return that;
}
```

#### MONAD

- Monad is a design pattern used to describe computations as a series of steps. They are extensively used in pure functional programming languages to manage side effects but can also be used in multiparadigm languages to control complexity.

```
function MONAD() {
	return function unit(value) {
		var monad = Object.create(null);
		monad.bind = function (func) {
			return func(value);
		};
		return monad;
	};
}

var identity = MONAD();
var monad = identity("Hello world.");
monad.bind(alert);
```
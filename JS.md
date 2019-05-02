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

### Javascript Basic

- JavaScript is a multi-paradigm language, supporting imperative/procedural programming along with OOP (Object-Oriented Programming) with prototypal inheritance.and functional programming.
- JavaScript interprets the line break as an “implicit” semicolon. This is called an automatic semicolon insertion.

```
<!-- works -->
alert('Hello')
alert('World')

<!-- works -->
alert("There will be an error")
[1, 2].forEach(alert)

```

- Object Creation Pattern - Encapsulation
- Object Reuse Pattern - Inheritance

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

#### Array

- Learned about heterogenous arrays

```
var myArray = [ 23,true,"lol"]
```

- Learned about multidimensional arrays

```
var newArray = [[1,1,1], [1,1,1], [1,1,1]]
```

- Learned about jagged arrays

```
var jagged = [[1,1,1],[1],[1,1]]
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
	function myObject(){
			this.iAm = 'an object';
			this.whatAmI = function(){
					alert('I am ' + this.iAm);
			};
	};

	var objectName = new myObject();

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
alert( user.name ); // John

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
alert( user.name ); // still John in the original object

//---------Object.Assign------------
- let clone = Object.assign({}, user);
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
- Methods can reference the object as this.

#### The "this" Keyword

- The keyword this acts as a placeholder, and will refer to whichever object called that method when the method is actually used.
- When a function is declared, it may use this, but that this has no value until the function is called.

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
- When a function is called in the “method” syntax: object.method(), the value of this during the call is object.

- "this" is undefined in strict mode. If we try to access this.name, there will be an error.

```
function sayHi() {
  alert(this);
}

sayHi(); // undefined
```

- In non-strict mode the value of this in such case will be the global object (window in a browser, we’ll get to it later in the chapter Global object). This is a historical behavior that "use strict" fixes.

- NOTE: Arrow functions are special: they have no this. When this is accessed inside an arrow function, it is taken from outside.

#### Object to primitive conversion

- The object-to-primitive conversion is called automatically by many built-in functions and operators that expect a primitive as a value.

- There are 3 types (hints) of it:
	- "string" (for alert and other string conversions)
	- "number" (for maths)
	- "default" (few operators)

- The specification describes explicitly which operator uses which hint. There are very few operators that “don’t know what to expect” and use the "default" hint. Usually for built-in objects "default" hint is handled the same way as "number", so in practice the last two are often merged together.

- The conversion algorithm is:

- Call obj[Symbol.toPrimitive](hint) if the method exists,
- Otherwise if hint is "string"
	- try obj.toString() and obj.valueOf(), whatever exists.
- Otherwise if hint is "number" or "default"
	- try obj.valueOf() and obj.toString(), whatever exists.

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

#### JS Closures

- A closure is the combination of a function and the lexical environment within which that function was declared.
- A closure is an inner function that has access to the outer (enclosing) function’s variables—scope chain.
- The closure has three scope chains: 1. it has access to its own scope (variables defined between its curly brackets), 2. it has access to the outer function’s variables, and 3. it has access to the variables.
- Coding Example.

```
// Clouser in ES6
function createCounter() {
let counter = 0
const myFunction = function() {
	counter = counter + 1
	return counter
}
return myFunction
}
const increment = createCounter()
const c1 = increment()
const c2 = increment()
const c3 = increment()
console.log('example increment', c1, c2, c3) // example increment 1 2 3

------------------------------

let c = 4
const addX = x => n => n + x
const addThree = addX(3)
let d = addThree(c)
console.log('example partial application', d) // example partial application 7

------------------------------

function showName (firstName, lastName) {
	var nameIntro = "Your name is ";

// this inner function has access to the outer function's variables, 		including the parameter​

	function makeFullName () {
		​return nameIntro + firstName + " " + lastName;
	}
	​return makeFullName ();
}

showName ("Michael", "Jackson"); // Your name is Michael Jackson

// Closure with argument

var digit_name = (function () {
	var names = ['zero', 'one', 'two','three', 'four', 'five', 'six', 'seven','eight', 'nine'];

	return function (n) {
		return names[n];
	};

}());

alert(digit_name(3)); // 'three'

------------------------------

(function outer() {
	var x;
	// The inner circle function cannot see y, In Diagram

	return function inner(n) {
		// The outer circle function can see x, In Diagram
		var y = x;
	};

}());

------------------------------

//---Real life example

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

#### Favor object composition over class inheritance

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


### ES6

- [ES6](http://es6-features.org/)
- [ES6 vs ES5](https://github.com/addyosmani/es6-equivalents-in-es5)
- [ES6 Tools](https://github.com/addyosmani/es6-tools)
- [What is ES6](http://gonodejs.com/es6-interview-questions-answers/#what-is-javscript-es6)
- Broweer Runtime Traceur but will be slow.
- Production side : ESnext, Babel, Traceur using grunt/gulp/webpack
- Polyfill manually of add ES6 Shim file.

#### Variables and Parameters

##### Let

- Var : Global and Function scope
- Let : Will provide true block scoping, unlike var
- Ideal to use it for programming as it will help to avoid hosting.

```
var doWork = function(flag){
	if(flag){
		let  x = 3;
		return x;
	}
}
```

##### Const

- will make variable Read only
- Never change , will give error if you try to change it.
- Will shadow outer declaration
- Block Scoping
- We generally use upper case for constants that are “hard-coded”. Or, in other words, when the value is known prior to execution and directly written into the code.

##### Destructing

- Can destructure arrays
- Can destructure objects
- Work with parameters
- [x, y] = [y, x]
- let [ , x, y] = [1, 2, 3]
- let [ , x, y, z] = [1, 2, 3] // "z" undefined

```
let  doWork = function(url, {data, cache, headers}){
	return data;
}

let result = doWork(
	"api/test", {
		data: "test",
		cache: false
	}
);

expect(result).toBe("test");
```

##### Default Parameters

- Nice syntax for explicitly stating what the default value of parameter will be if missing.
- Provide Defaults
- Will Provide a value for undefined
- Works with Destructing

```
var doWok  = function (name="Scott"){
	return name
};
var result = doWork(); // Scott
var result = doWork("undefined"); // Scott
var result = doWork(""); // No
```

##### REST Parameters

- It works as VAR Arguments.
- It is true array
- ...RESTParameters
- let doWork = function(url, ...numbers){};

##### Spread Operator

- ...Spread Operator
- Can spread an array across parameters
- Can build arrays
- var result = doWork(...[1,2,3])
- var a = [4,5,6]
- var b = [1,2,3,...a,7,8,9]; // [1,2,3,4,5,6,7,8,9]

##### Template Literals

- Can easily combine literals and data
- Can help build URLs
- Can use tags
- let url = "http://apiserver/" + category + "/" + id; // Old
- let url = 'http://apiserver/${category}/${id}'; // Template Literals
- USE : Domain specific language stays inside template

#### Classes

- Class like c, c++, java
- Do not have private or public visibility accessibility
- Constructor: Class can have constructor
- Encapsulation : Getter & Setter , hide implementation details or logic
- Inheritance : Use "extends" to inherits from class.
- Every class extends itself to object
- every class extends Object as super class // Object(SuperClass) , Perosn(BaseClass)
- A closure is the combination of a function and the lexical environment within which that function was declared.

```
class Person{
	//---Constructor
	constructor(name){
		this.name = name;
	}

	//---Getter
	get name(){
		return this._name.toUpperCase();
	}

	//---Setter
	set name(newValue){
		if(newValue){
			this._name = nameValue;
		}
	}
	doWork(){
		return "Not work and free";
	}
}
//---Inheritance, Person(SuperClass) , Employee(BaseClass)
class Employee extends Person {
	constructor(title, name){
		//---Can invoke Super methods
		super(name);
		this.title = title;
	}

	get title(){
		return this._title;
	}

	//---Override super methods
	doWork(){
		return `${this._name} is working and get paid`;
		return "Paid" ;
		//---Can invoke Super methods
		return super() + "Paid" ;
	}
}

let e1 = new Employee("Dev","Maitrik");
let p1 = new Person("Kruti");
```

#### ES6 Functional Programming

##### Arrows

- Provide compact syntax to define a function
- let add = (x,y) => x + y;
- Allow passing function as parameter.
- Can be used with array methods

```
var numbers = [1,2,3,4];
var sum = numbers.forEach(n => += n); // output 10
var doubled = numbers.map(n => n * 2); // output [2,4,6,8]
```

- Arrow function lexically binds "this" of the parents function. No need to worry about self closure by "var self = .this"
- Can be used with array methods lexically binds to 'this'

##### Iterators

- An object is an iterator when it knows how to access items from a collection one at a time, while keeping track of its current position within that sequence. In JavaScript an iterator is an object that provides a next() method which returns the next item in the sequence.
- Iterators : Iterators allows to walk through the collection one item at the time.
- Iterators is an object with a next method.
- This method returns an object with two properties: done and value.
- Symbol.iterator function that every Iterable object must implement.

##### Iterables

- Any sequence of objects , Collection of items. Like Array, Map, Set or DOM.
- An object is iterable if it defines its iteration behavior, such as what values are looped over in a for...of construct.
- Some built-in types, such as Array or Map, have a default iteration behavior, while other types (such as Object) do not.
- **Built-in iterables** : String, Array, TypedArray, Map and Set are all built-in iterables, because their prototype objects all have a Symbol.iterator method.

##### For of

- Loop over values instead of key/indexes - for (let i of numbers){console.log(i)};
- Work with Iterables at a high level

##### Generators

- While custom iterators are a useful tool, their creation requires careful programming due to the need to explicitly maintain their internal state.
- Generators provide a powerful alternative: they allow you to define an iterative algorithm by writing a single function which can maintain its own state.
- Add \* in front of function in class to make it generator.
- Pauseable/Iterable function. It pause every-time yield comes in function.

```
//---Generators with for of loop

let numbers = function*(start, end){
	for (let i = start; i <= end; i++){
		console.log(i);
	}
}

let sum = 0 ;
console.log("next");

//---For of
for(let n of numbers(1,5)){
	sum += n;
	console.log("next");
}
```

- Can built by implementing symbol.iterator
- Can take parameter from next(parm)

```
//---Generators to avoid it for not loop through entire array.

let count = 0;
let company = new Company();
company.addEmployees("Tim", "Maitrik", "Kruti", "Tom", "Parth")

let filter = function*(items, predicate){
	for(let item of items){
		console.log("filter", item);
		if(predicate(item)){
			yield item;
		}
	}
}

for (let employee of filter(company, e => e[0] == 'T')){
	count += 1;
}

// Output will be 2
```

##### Comprehensions ( Not supported anymore)

- Array comprehension is greedy and build concrete data structure.
- Generator comprehension syntax with parentheses is more like the generator function that use yields.

```
var numbers = [for (n of [1,2,3]) n * n]; / [1,4,9]
var numbers = [for (n of [1,2,3]) if(n > 1) n * n]; / [4,9]
var numbers - (for (n of [1,2,3]) n * n); / [1,4,9]
```

#### Built-In Objects

##### Numbers

- Octal Literals : var octal = 0o71; // 57
- Binary Literals : var bin = 0b1101; // 13
- Parse octal value with number function : var octNum = Number("0o71"); // 57
- Parse binary value with number function : var binNum = Number("0b101"); // 5
- Correctly detect integer with isInteger.

##### [Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)

- Math new hyperbolic achosine, cosine functions.
- Math.cbrt(x) function returns the cube root of a "x" number.

##### [New Array Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

- find function.

```
var ary  = [1,5,10];
var match = ary.find(item => item > 8); // 10
```

- findIndex function.

```
var ary = [1,5,10].find(item => item > 3); // Index 1 of number 5
```

- fill function : arr.fill(value, start, end)
- copyWithin function : arr.copyWithin(target, start, end)
- Array.of() method creates a new Array instance with a variable number of arguments, regardless of number or type of the arguments.

```
Array.of(7);       // [7]
Array.of(1, 2, 3); // [1, 2, 3]
```

- Array.from() method creates a new Array instance from an array-like or iterable object.

```
const bar = ["a", "b", "c"];
Array.from(bar); // ["a", "b", "c"]
Array.from('foo'); // ["f", "o", "o"]
```

- The entries() method returns a new Array Iterator object that contains the key/value pairs for each index in the array.

```
var a = ['a', 'b', 'c'];
var iterator = a.entries();

for (let e of iterator) {
console.log(e);
}
// [0, 'a']
// [1, 'b']
// [2, 'c']
```

##### [SETS](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/)

- The Set object lets you store unique values of any type, whether primitive values or object references.

```
var mySet = new Set();
mySet.add(1);
mySet.add(5);
mySet.add('some text')

mySet.size; // 3
```

##### [MAPS](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)

- The Map object holds key-value pairs. Any value (both objects and primitive values) may be used as either a key or a value.

```
var myMap = new Map();
myMap.set('a', 'alpha');
myMap.set('b', 'beta');
myMap.set('g', 'gamma');
myMap.get('b');  // Returns "beta".
myMap.size // 3
```

##### WAEKMAPS & WEAKSETS

- Invented to resolve garbage collector issue

#### Objects

- Object.is() : Compare like ===

```
if( -0 === 0) // true
Object.is( -0, 0) // false

if( NaN === NaN) // false
Object.is( NaN, NaN) // true
```

- [Object.assign()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)
	- Behave like extend/mixin
	- It will new functionality to existing objects.

```
Object.assign(target, ...sources)
var o1 = { a: 1 };
var o2 = { b: 2 };
var o3 = { c: 3 };

var obj = Object.assign(o1, o2, o3);
console.log(obj); // { a: 1, b: 2, c: 3 }
console.log(o1);  // { a: 1, b: 2, c: 3 }, target object itself
```

- [Object literals](http://www.benmvp.com/learning-es6-enhanced-object-literals/)
- [Proxy object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy) - The Proxy object is used to define custom behavior for fundamental operations (e.g. property lookup, assignment, enumeration, function invocation, etc). - var p = new Proxy(target, handler);

```
let view = new Proxy({
	selected: null
},
{
set: function(obj, prop, newval) {
	let oldval = obj[prop];

	if (prop === 'selected') {
	if (oldval) {
		oldval.setAttribute('aria-selected', 'false');
	}
	if (newval) {
		newval.setAttribute('aria-selected', 'true');
	}
	}

	// The default behavior to store the value
	obj[prop] = newval;

	// Indicate success
	return true;
}
});

let i1 = view.selected = document.getElementById('item-1');
console.log(i1.getAttribute('aria-selected')); // 'true'

let i2 = view.selected = document.getElementById('item-2');
console.log(i1.getAttribute('aria-selected')); // 'false'
```

#### Modules

- JavaScript does not have built-in support for modules
- Module pattern is easily transformed into a powerful constructor pattern.

```
var singleton = (function () {
	var privateVariable;

	function privateFunction(x) {
		...privateVariable...
	}

	return {
		firstMethod: function (a, b) {
			...privateVariable...
		},
		secondMethod: function (c) {
			...privateFunction()...
		}
	};

}());
```

- IIFE (immediately invoked function expression) modules pattern

- CommonJS Modules: The dominant implementation of this standard is in Node.js (Node.js modules have a few features that go beyond CommonJS). Characteristics: - Compact syntax - Designed for synchronous loading - Main use: server

- Asynchronous Module Definition (AMD): The most popular implementation of this standard is RequireJS. Characteristics: - Slightly more complicated syntax, enabling AMD to work without eval() (or a compilation step). - Designed for asynchronous loading - Main use: browsers

- [ECMAScript 6 modules](http://2ality.com/2014/09/es6-modules-final.html) - Similar to CommonJS, they have a compact syntax, a preference for single exports and support for cyclic dependencies. - Similar to AMD, they have direct support for asynchronous loading and configurable module loading. - Named exports (several per module)

```
//------ lib.js ------
export const sqrt = Math.sqrt;
export function square(x) {
	return x * x;
}
export function diag(x, y) {
	return sqrt(square(x) + square(y));
}

//------ main.js ------
import { square, diag } from 'lib';
console.log(square(11)); // 121
console.log(diag(4, 3)); // 5

//------ main.js Import whole module------
import * as lib from 'lib';
console.log(lib.square(11)); // 121
console.log(lib.diag(4, 3)); // 5
```

- Default exports (one per module)

```
//------ myFunc.js ------
export default function () { ... };

//------ main1.js ------
import myFunc from 'myFunc';
myFunc();
```

- Importing

```
// Default exports and named exports
import { named } from 'src/mylib';
import { named1, named2 } from 'src/mylib';
import theDefault from 'src/mylib';
import theDefault, { named1, named2 } from 'src/mylib';

// Renaming: import named1 as myNamed1
import { named1 as myNamed1, named2 } from 'src/mylib';

// Importing the module as an object
// (with one property per named export)
import * as mylib from 'src/mylib';
import theDefault, * as mylib from 'src/mylib';

// Only load the module, don’t import anything
import 'src/mylib';
```

- Exporting

```
// All export can work with default naming too.
export var myVar1 = ...;
export let myVar2 = ...;
export const MY_CONST = ...;

export function myFunc() {
	...
}

export function* myGeneratorFunc() {
	...
}
export class MyClass {
	...
}

//  list everything you want to export at the end of the module

const MY_CONST = ...;
function myFunc() {
	...
}

export { MY_CONST, myFunc };
export { MY_CONST as THE_CONST, myFunc as theFunc };
```

- Use symbols to implement lightweight hiding technique.

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

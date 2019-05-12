---
date: '2019-01-05'
publish: 'true'
category: 'note'
author: 'Maitrik Patel'

title: 'Javascript ES6'
description: 'Javascript is taking over the world'

topics: 'tools, development'

source: 'Github'
---

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

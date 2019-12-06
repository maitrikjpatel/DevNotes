---
date: '2019-01-13'
publish: 'false'
category: 'note'
author: 'Maitrik Patel'

title: 'JS Questions'
description: 'Javascript is taking over the world'

topics: 'tools, development'

source: 'Github'
---

## JS Questions

### JS Basics

```js
// Index of Max in array

array.indexOf(Math.max(...array))
```

```js
var text = 'outside';
function logIt(){
    console.log(text);
    var text = 'inside';
};
logIt(); // undefined
```

```js
let threatLevel = 1;

function inspireFear(threatLevel){
  threatLevel += 100;
}

inspireFear(threatLevel);
console.log(threatLevel); // Whoops! It's still 1!
```

```js
<button id="btn-0">Button 1</button>
<button id="btn-1">Button 2</button>
<button id="btn-2">Button 3</button>

<script type="text/javascript">
  const prizes = ['A Unicorn!', 'A Hug!', 'Fresh Laundry!'];
  for (var btnNum = 0; btnNum < prizes.length; btnNum++) {

    // For each of our buttons, when the user clicks it...
    document.getElementById(`btn-${btnNum}`).onclick = () => {

      // Tell her what she's won!
      alert(prizes[btnNum]);
    };
  }
</script>

// fix it, change var to let in for loop
```

```js
conole.log([]+ []) // Empty
conole.log({}+ []) // Empty
```

```js
var ninja = function myNinja(){ 
  console.log('This function is named two things')
};
ninja(); // works

// myNinja isn't defined outside of the function.
myNinja(); // undefined
```

```js

let x = {
  a: 1,
  b: 2
}
let maArray = Object.values(x)
console.log(maArray); // [1,2]
```

```js
// let x = 'hi' 
let y = x.split('').reverse().join(''); // 'ih'
console.log(y);
```

```js 
function a() {
  return 'hello';
}
const sentence = a `hi` // simmilar to a('hi') 
conole.log(sentence) // hello 
```

```js 
<div contentEditable="true">Hello</div> // make content editable
```

```js
function y(){
  console.log(this.length);
}
let x = {
  length: 5,
  method: function(y){
    argument[0]()'
  }
};
x.method(y,1); // 2 not 5
// Argument length is going to be length
```

```js
const x = 'constructor'
console.log(x[x])(01)); // 1
// x is string
// x[x] = x['constructor'] = x.constructor
// x[x] will convert 01 to string means 1 answer
```

```js
console.log(0.1 + 0.2) // 0.30000000000004
// Decimal in base 10 
// Computer only understand base 2
// Need conversion
```

```js
console.log('hi') // hi
console.log(('hi').__proto__) // String as "hi" is created using String 
console.log(('hi').__proto__.__proto__.__proto__) // Constructor as String is created using Object which is Constructor
console.log(('hi').__proto__.__proto__.__proto__) // null as there is nothing beyond Object so null
```

```js
let x = function(){
  return [].slice.call(arguments).length
  return arguments.length // easy way
}

x(1,2,3) // 3, output length of arguments 
x(1,2,3,4) // 4, output length of arguments 
x(1,2,3,4,5) // 5, output length of arguments 
```

```js
var A = {
  x: function(){
    console.log('x');
    return this  // return this
    return A // This is answer/trick
  },
  y: function(){
    console.log('y')
    return this  // return this
    return A; // This is answer/trick
  },
  z: function(){
    console.log('z')
  }
}

A.x().y().z();
// Question. Want to do method chaining.
// First Return : A.y().z();
// Second Return : A.z();
```

```js
console.log(2 + '2') // 22
// + work on string, number
// convert both value to string and concat

console.log(2 - '2') // 0
// - is number operator
// concert both value to number
```

```js
let nums = [1,2,2,3]; // [1,2,3]
console.log(new Set(nums)); // Set{1,2,3}
console.log([...new Set(nums)]); // [1,2,3]
```

```js
let myFunc = function(){
  {
 		let lt = "let";
		var vr = 'var';
	}   
	console.log(vr)
	console.log(lt)
}
myFunc()
// vr have function scop, fix it to have block scope.
let myFunc = function(){
  {
    (function() {
      let lt = "let";
      var vr = 'var';
    })();
	}   
	console.log(vr)
	console.log(lt)
}
myFunc()
```

```js
console.log( 5 < 6 < 7) // True
console.log( 7 > 6 > 5) // false (7>6)=True -> (True>7) = false
```

```js
let a = () => arguments;
console.log(a('hi')) 
// Argument don't bind to arrow function 
// Use spread operator
let a = (...n) => {return n};
```

```js
let profile = {
  name: 'maitrik'
}

// Prevent new property and update
profile.age = 3;
profile.name = 'matt'

// No update to name or age. 
Object.freeze(profile)
// Update name but not allow to add age
Object.seal(profile) 
```

```js
// write Clone obj to kep Obj value as it is
const obj = {
  a: {
    b:{
      c: 1
    }
  }     
}

// Fail
// Shallow cloning  -> 2 
const clone = obj;
const clone = Object.assign({}, obj);

// Success
// Shallow cloning  -> 1
const clone = JSON.parse(JSON.stringify(obj))

clone.a.b.c = 2
console.log(obj.a.b.c); // 1
```


```js
// make age readable
let profile = {
  name: 'maitrik'
}

Object.defineProperty( profile, 'age', {
  value: 3;
  writable: false
})

profile.name = "matt" // change 
pro
```

```js
console.log(Math.max()) // -infinity
```

```js
// Closures in for loop
for ( var i = 0; i < 3; i++){
  setTimeout(() =>{
    console.log(i)
  },1000)
}
// 3, 3, 3 
// Why ? , Fix it
// Answer 1, use let in for loop
// Answer 2, use immediate invoked function
```

```js
const x = [1,2,3]
x[-1] = -1;
console.log(x[x.indexOf(1000)]) // -1 
// x[x.indexOf(1000)] -> x[-1] -> -1
```

```js
let myArray = [2,3,4,3,4,11,8,-21,9,1, -10];
myArray.sort((a,b) => (b-a)); // [ 11, 9, 8, 4, 4, 3, 3, 2, 1, -10, -21 ]
myArray.sort((a,b) => (a-b)); // [ -21, -10, 1, 2, 3, 3, 4, 4, 8, 9, 11 ]
```

```js
// let i = ?
let i = Number.MIN_VALUE;
console.log(i * i) // 0
console.log(i + 1) // 1
console.log(i - 1) // -1
console.log(i / i) // 1
```

```js
let x = [1,2,3] + [4,5,6]
console.log(x) // 1,2,34,5,6, fix it
// Use spread operator
let x = [...[1,2,3], ...[4,5,6]]
```

```js
console.log(555555555555555555) // 555555555555555600
// console.log(Number.MAX_SAFE_INTEGER)
// 9007199254740991
// 00 after max number 
```

```js
(function(){
  let a = b = 100 ; // b becomes global
})();

console.log(b); // 100
console.log(a); // undefined
```

```js
console.log(NaN === NaN) // False
```

```js
// Explan This
//---------------This of window----------------------
this.table = "window table"
const cleanTable = function(soap){
  // this will come from window , global scope
  console.log(`Please Clean ${this.table} using ${soap}`); 
}

console.log(this.table)

// Won't work under 'use strict'
cleanTable(this.table)

// call method 
cleanTable.call(this, 'fancy soap')

// bind
cleanTable.bind(this)('fancy soap') // Please Clean window table using fancy soap

//---------------This of object----------------------
console.log('---------------------------------------')
let myRoom = {
  table: "myRoom table",
  cleanTable() {
    console.log(`Please Clean ${this.table}`);
  }
}
console.log(myRoom.table)
myRoom.cleanTable() // Please Clean myRoom table
```

```js
// fix this, that, call, bind, arrow function
this.table = "window table"
const cleanTable = function(soap){

  // this will give error on this 
  const innerFunction = function(_soap) {
    console.log(`Please Clean ${this.table} using ${_soap}`); 
  }
  innerFunction(soap)
  
  // Solution 1: store this in variable and pass in innerfunction 
  let that = this
  const innerFunction = function(_soap) {
    console.log(`Please Clean ${that.table} using ${_soap}`); 
  }
  innerFunction(soap)
  
  // Solution 2: Call/Bind 
  const innerFunction = function(_soap) {
    console.log(`Please Clean ${this.table} using ${_soap}`); 
  }
  innerFunction.call(this,soap);
  innerFunction.bind(this)(soap);
  
  // Solution 3: arrow function
  // Arrow function don't have `this` so it take outterScope `this`
  const innerFunction = (_soap) => {
    console.log(`Please Clean ${this.table} using ${_soap}`); 
  }
  innerFunction(soap);

}
cleanTable.call(this, 'fancy soap')

```

### JS Native Methods

```js
// make your own forEach
Array.prototype.newForEach = function (callback, context) {
  for (let index = 0; index < this.length; index++) {
    // This is primarily to check if the item
    // exists in the array, 
    if (this.indexOf(this[index]) > -1) {
      callback.call(context, this[index], index, this)
    }
  }
}
// example
const words = ["adam", "ate", "an", "apple"]
const upperCaseList = []
words.newForEach((word, index, context) => {
  upperCaseList.push(word.toUpperCase())
})
console.log(upperCaseList)

```

```js
function getElementsByClass(klass, node) { //
  var node = node || document.body; //1
  var found = []; //2
  if (hasClass(node, klass)) { //
    found.push(node);
  }
  for (var i=0; i<node.children.length; i++) {
    found = found.concat(getElementsByClass(klass, node.children[i])); //
  }
  return found;
}

function hasClass(node, klass) {
  for(var i=0; i<node.classList.length; i++) {
    if (node.classList[i] === klass) {
      return true;
    }
  }
  return false;
}

// root = document.body -> node.children returns a collection of child nodes of the given node
// node.classList -> returns a token list of the class attribute of the node
// div.classList = ['this-is-a-class', 'this-is-too']

<div class='this-is-a-class this-is-too'> // div.classList = ['this-is-a-class', 'this-is-too']
  <p>hello</p>
</div>
```

```js
// myReduce as per following
// arr.reduce(function(previousValue, item, index, array) {}, initial);
// Add || to not override possible already defined functions.
Array.prototype.myReduce = Array.prototype.myReduce || function(callbackFn, startingValue) {

  let accumulator = startingValue || undefined;

  for ( let index = 0; index < this.length; index++ ) {

    if ( accumulator ) {
      accumulator = callbackFn.call(accumulator, accumulator, this[index], index, this)
    } else {
      accumulator = this[index]
    }
  }
  
  return accumulator;
}

console.log([1,2,3].myReduce((c,v) => c + v, 0))
```

```js
// myMap as per following
// arr.map(function callback(currentValue, index, array))

Array.prototype.myMap = Array.prototype.myMap || function(callbackFn) {
  const resultArray = [];
  for ( let index = 0; index < this.length; index++ ) {
    if( this.indexOf(this[index]) > -1 ){
      resultArray[index] = callbackFn(this[index], index, this)
    }
  }
  return resultArray;
}

console.log([1,2,3,'',9].myMap((item) => item * 2))
```

```js
// myFilter as per following
// arr.filter(function callback(currentValue, index, array))

Array.prototype.myFilter = Array.prototype.myFilter || function(callbackFn) {
  
  const resultArray = [];  
  for ( let index = 0; index < this.length; index++ ) {
    
    if(callbackFn(this[index], index, this)){
      resultArray.push(this[index]);
    }
  }
  return resultArray;
}
console.log([1,2,3,11,9,2,1,9].myFilter(item => item > 3));
```

```js
// Write your own throttle
const throttle = (func, limit) => {
  let lastFunc
  let lastRan
  return function() {
    const context = this
    const args = arguments
    if (!lastRan) {
      func.apply(context, args)
      lastRan = Date.now()
    } else {
      if ((Date.now() - lastRan) >= limit) {
        func.apply(context, args)
        lastRan = Date.now()
      }
    }
  }
}
```

```js
// ---------Prob 4--------------
// [1,2].myPrint(); // 1,2

Array.prototype.myPrint = function() {
  const resultArray = [];
  for ( let index = 0; index < this.length; index++ ) {
    resultArray.push(`${this[index]}`)
  }
  return resultArray.join(',');
  
  // Object to Stringify
  return this.toString();
}
console.log([1,2,3,9].myPrint())
```

```js
// sort array without sort
let array = [10,230,34,123,123,1,3,4]
for( let i = 0; i <array.lengh; i++){
  setTimeout(() => {
    console.log(array[i]);
  }, array[i])
}
// 1,3,4,10....
```


```js
// Emmiter
const Emitter = function() {
  this.events = {}
};

Emitter.prototype.subscribe = function( eName, cb ) {
  this.events[eName] = this.events[eName] || [];
  this.events[eName].push(cb);

  return {
    release: () => {
      let i = this.events[eName].indexOf(cb);
      this.events[eName].splice(i, 1);
      if (!this.events[eName].length) delete this.events[eName];
    }
  }
};

Emitter.prototype.emit = function( eName, ...args ) {
  if ( !this.events[eName] ) throw new Error(`Event ${eName} doesn't exist`);
  this.events[eName].forEach(el =&gt; el.call(this, ...args));
};
```

```js
// Searching for a Symmetric Node

// This function returns a real array of Nodes, so we can use methonds like "indexOf"
function getChildren(node) {
    // or you can use Array.from(node.childNodes);
    return Array.prototype.slice.call(node.childNodes);
}

// This function returns an array of indices from given node to the root
function getPath(root, node) {
    const path = [];
    let curElement = node;

    // This is important as if a node is null or doesn't have a parent
    // there is no need of searching further
    while(curElement !== root && curElement && curElement.parentNode) {
     const index = getChildren(curElement.parentNode).indexOf(curElement);
     path.push(index);
        curElement = curElement.parentNode;
    }

    return path;
}

// Popping all values from the array of indices we go to the symmetrical node
function getNodeByPath(root, originalPath) {
    const path = [].concat(originalPath);
    let element = root;
    while (path.length) {
       element = getChildren(element)[path.pop()];
    }
    return element;
}

// For convenience
function getSymmetricNode(root1, root2, node) {
 const path = getPath(root1, node);
 return getNodeByPath(root2, path);
}

const root1 = document.getElementById('root1');
const root2 = document.getElementById('root2');
const node1 = document.getElementById('node1');
const node2 = document.getElementById('node2');

const nodeX = getSymmetricNode(root1, root2, node1);

console.log(nodeX === node2); // true
```

```js
// Promise 
// Function Solution
// https://medium.com/@cmakyr12/understanding-promises-by-writing-your-own-promise-library-14c739eb9a42
const states = {
  0: 'pending',
  1: 'fulfilled',
  2: 'rejected'
}
function MyPromise (cb) {
  if (typeof cb!== 'function') {
    throw new TypeError('callback must be a function')
  }
  let state = states[0]
  let value = null
  let handlers = []
function fulfill (result) {
    state = states[1]
    value = result
    handlers.forEach(handle)
    handlers = null
}
function reject (error) {
    state = states[2]
    value = error
    handlers.forEach(handle)
    handlers = null
}
function resolve (value) {
    try {
      let then = getThen(value)
      if (then) {
        resolveAnotherPromise(then.bind(value), resolve, reject)
        return
      }
      fulfill(value)
    } catch (err) {
      reject(err) 
    }
}
function handle (handler) {
  if (state === states[0]) handlers.push(handler)
  else {
    if (state === states[1] && 
       typeof handler.onFulfill === 'function') {
       handler.onFulfill(value)
    }
    if (state === states[2] && 
       typeof handler.onReject === 'function') {
       handler.onReject(value)
    }
  }
}
this.done = function (onFulfill, onReject) {
  setTimeout(() => handle(onFulfill, onReject), 0)
}
this.then = function (onFulfill, onReject) {
  let self = this
  return new Promise((resolve, reject) => {
    return self.done(result => {
      if (typeof onFulfill === 'function') {
        try {
          return resolve(onFulfill(result))
        } catch (err) {
          return reject(err)
        }
      } else {
        return resolve(result)
      }
   }, error => {
      if (typeof onReject === 'function') {
        try {
          return resolve(onReject(error))
        } catch (err) {
          return reject(err)
        }
      } else {
        return reject(error)
      }
   })
  })
 }
}  
function getThen (value) {
    if (typeof(value) === 'object' 
        || typeof(value) === 'function') {
      let then = value.then
      if (typeof(then) === 'function') return then
    }
    return null
  }
    
function resolveAnotherPromise (cb, Onfulfill, Onreject) {
    let finished = false
    try {
      cb(value => {
        if (finished) return
        finished = true
        Onfulfill(value)
      }, reason => {
        if (finished) return
        finished = true
        Onreject(reason)
      })
    } catch (err) {
      if (finished) return
      finished = true
      Onreject(err)
    }
  }
}
// Class Solution
// https://www.promisejs.org/implementing/
class PromiseSimple {
  constructor(executionFunction) {
    this.promiseChain = [];
    this.handleError = () => {};

    this.onResolve = this.onResolve.bind(this);
    this.onReject = this.onReject.bind(this);

    executionFunction(this.onResolve, this.onReject);
  }

  then(onResolve) {
    this.promiseChain.push(onResolve);

    return this;
  }

  catch(handleError) {
    this.handleError = handleError;

    return this;
  }

  onResolve(value) {
    let storedValue = value;

    try {
      this.promiseChain.forEach((nextFunction) => {
         storedValue = nextFunction(storedValue);
      });
    } catch (error) {
      this.promiseChain = [];

      this.onReject(error);
    }
  }

  onReject(error) {
    this.handleError(error);
  }
}
```

```js
// Observer

function Click() {
    this.handlers = [];  // observers
}
 
Click.prototype = {
 
    subscribe: function(fn) {
        this.handlers.push(fn);
    },
 
    unsubscribe: function(fn) {
        this.handlers = this.handlers.filter(
            function(item) {
                if (item !== fn) {
                    return item;
                }
            }
        );
    },
 
    fire: function(o, thisObj) {
        var scope = thisObj || window;
        this.handlers.forEach(function(item) {
            item.call(scope, o);
        });
    }
}
 
// log helper
 
var log = (function() {
    var log = "";
 
    return {
        add: function(msg) { log += msg + "\n"; },
        show: function() { alert(log); log = ""; }
    }
})();
 
function run() {
 
    var clickHandler = function(item) { 
        log.add("fired: " + item); 
    };
 
    var click = new Click();
 
    click.subscribe(clickHandler);
    click.fire('event #1');
    click.unsubscribe(clickHandler);
    click.fire('event #2');
    click.subscribe(clickHandler);
    click.fire('event #3');
 
    log.show();
}
```

### JS Problem Solving

```js
// Add array and sort 
const a = [1,2,3,4,5,5,6,9];
const b = [2,5,6,12,100];
  
const c = [ ...a, ...b ].sort((a,b) => a-b)
console.log(c)
```

```js
// --------COPY SORTED--------
let copySorted = (array) => array.slice().sort()

let myArray = ["HTML", "JavaScript", "CSS"];
let sorted = copySorted(myArray);

console.log(sorted);
```

```js
// Remove duplicates from array
let a = [1, 2, 5, 2, 1, 8] // [1,2,5,8]

let b = []
let len = a.length

for ( let i = 0; i < len, i++) {
  if(b.indexOf(a[i]) === -1 ){
    b.push(a[i]);
  }
}

// After sorting
a.sort()
let _temp;
for ( let i = 0; i < len, i++) {
  if(a[i] !== _temp){
    b.push(a[i]);
    _temp = a[i];
  }
}

// Object way
obj = {};
for(let i of a) {
  obj[i] = true;
}
let b = Object.keys(obj);

//Object
let b = [...new Set(a)];
```

```js
let myMatrix = [
  [1,1,1,1],
  [1,1,1,1],
  [1,1,1,1],
  [1,1,1,1]
]

function matrixSum(matrix){
  let sum = 0;
  let rows = matrix.length;
  let columns = matrix[0].length;
  
  // Brut force
  for( let i = 0; i < columns; i++ ){
    sum += matrix[0][i];
  }
  for( let i = 0; i < columns; i++ ){
    sum += matrix[rows-1][i];
  }
  for( let i = 1; i < columns-1; i++ ){
    sum += matrix[i][0];
  }
  for( let i = 1; i < columns-1; i++ ){
    sum += matrix[i][columns-1];
  }

  // Optimized
  for( let i = 0; i < rows; i++ ){
    for( let j = 0; j < columns; j++ ){
      if( i % (rows - 1) == 0 || j % (columns - 1) == 0) {
        sum += matrix[i][j];
      } 
    }
  }
  
  console.log(sum)
}

matrixSum(myMatrix)
```

```js
//Currying$$
function f(a,b,c){
  if( a && b && c ){
    return ( (a + b) * c )
  } else if( a && b ){
    return function(valC){
      return ( (a + b) * valC )
    }
  } else if( a){
    return function(valB){
      return function(valC){
          return ( (a + valB) * valC )
      }
    }
  } else {
    return 0;
  }
}

console.log(f(1)(2)(3)); //9
console.log(f(2)(2)(1)); //4
console.log(f(2,2)(1)); //4
console.log(f(2,2,1)); //4
console.log(f()); // 0
```

```js
let mergeFiles = function(array) {
  let totalSum = 0;
  let accumulator = 0;
  let sortedArray = array.sort((a,b) => a - b);
  for( let i = 1; i < sortedArray.length ; i++ ){
    if( i == 1) {
      // 4 + 6
      totalSum = sortedArray[i-1] + sortedArray[i];
      accumulator += totalSum;
    } else if (  i > 1) {
      // 8 + 10 -> 12 + 18 -> 28 + 30 
      totalSum = sortedArray[i] + totalSum;
      accumulator += totalSum;
    }
  }
  return accumulator;
}

let myArray = [8,4,6,12]
console.log(mergeFiles(myArray))

```

```js
// --------CAMELIZE String--------
let camelize = (str) => {
//  ------My Solution------
  let myArray = str.split('-');
  for(let i = 1; i < myArray.length; i++){
    myArray[i] = myArray[i].charAt(0).toUpperCase() + myArray[i].slice(1);
  }
  return myArray.join('')

  // ------Ideal Solution------
  return str
    .split('-')
    .map(  (word, index) =>
         index == 0
         ?
         word
         :
         word[0].toUpperCase() + word.slice(1))
    .join('');
}
let result = camelize('background-color-best');
```

```js
// --------FILTER RANGE--------
let filterRange = (array, a, b) => {
//  ------My Solution------
  let filteredArray = [];
  for(let item of array) {
    if( item >= a && item <= b ) {
      filteredArray.push(item);
    }
  }
  return filteredArray;
  
  // ------Ideal Solution------ 
return array.filter(item => (a <= item && item <= b));
}
```

```js
// --------FILTER RANGE IN SAME ARRAY--------
let filterRangeInPlace = (array, a, b) => {
  // ------Ideal Solution------ 
  for (let i = 0; i < array.length; i++) {
    let val = array[i];
    console.log(`val:${val}`)
    console.log(`i:${i}`)
    console.log(`arrayBefor:${array}`)
    if( val < a || val > b ) {
      array.splice(i,1);
      i--;
    }
    console.log(`arrayAfter:${array}`)
    console.log(`------`)
  }
}

```

```js
// --------CALCULATOR--------
function Calculator() {
  let methods = {
    '+': (a,b) => a+b,
    '-': (a,b) => a-b
  };
  
  this.calculate = (str) => {
    let splitStr = str.split(' '),
        valueA = +splitStr[0],
        valueOp = splitStr[1],
        valueB = +splitStr[2]
    return methods[valueOp](valueA,valueB);
  }

  this.addMethod = (name, func) => {
    methods[name] = func;
  };
}

let calc = new Calculator;
calc.addMethod("**", (a, b) => a ** b);
console.log(calc.calculate("4 + 5"));
console.log(calc.calculate("4 ** 5"));
```

```js
// --------MAP NAMES--------
let john = { name: "John", age: 25 };
let pete = { name: "Pete", age: 30 };
let mary = { name: "Mary", age: 28 };

let users = [ john, pete, mary ];

let names = users.map(item => item.name);

console.log( names ); // ["John", "Pete", "Mary"]
```

```js
// --------MAP OBJECTS--------
let john = { name: "John", surname: "Smith", id: 1 };
let pete = { name: "Pete", surname: "Hunt", id: 2 };
let mary = { name: "Mary", surname: "Key", id: 3 };

let users = [ john, pete, mary ];

let usersMapped = users.map(user => ({
  fullName: `${user.name} ${user.surname}`,
  id: user.id
}))

/*
usersMapped = [
  { fullName: "John Smith", id: 1 },
  { fullName: "Pete Hunt", id: 2 },
  { fullName: "Mary Key", id: 3 }
]
*/

console.log( usersMapped[0].id ) // 1
console.log( usersMapped[0].fullName ) // John Smith
```

```js
// --------SORT BY AGE--------
let john = { name: "John", age: 25 };
let pete = { name: "Pete", age: 30 };
let mary = { name: "Mary", age: 28 };

let users = [ pete, john, mary ];

let sortByAge = (array) => {
  // ----mysolution----
  array.sort((a,b) => a.age - b.age);
  // ----idealsolution----
  array.sort((a,b) => a.age > b.age ? 1 : -1);
}

sortByAge(users);

// now: [john, mary, pete]
console.log(users[0].name); // John
console.log(users[1].name); // Mary
console.log(users[2].name); // Pete
```

```js
// -------SHUFFLE ARRAY--------
let array = [2,3,4,3,4,11,8,-21,9,1, -10];

let shuffleArray = (array) => {
  //------Ideal shuffle-------
  array.sort( () => { 
    Math.random() - 0.5
  });
  
  // ------Fisher Yates shuffle-------
  for (let i = array.length - 1; i > 0; i--) {
    let j = Math.floor(Math.random() * (i + 1)); // random index from 0 to i
    [array[i], array[j]] = [array[j], array[i]]; // swap elements
  }
}

shuffleArray(array);
console.log(array)
```

```js
// -------GET AVARAGE--------
let john = { name: "John", age: 25 };
let pete = { name: "Pete", age: 30 };
let mary = { name: "Mary", age: 29 };

let users = [ john, pete, mary ];

let getAverageAge = (array) => {
  return array.reduce((prev, arrayItem) => prev + arrayItem.age, 0) / array.length;
}

console.log( getAverageAge(users) ); 
```

```js
// --------UNIQUE IN ARRAY----------
function unique(array) {
  let tempValue = [];
  for ( let str of array) {
    // if (!tempValue.includes(str)) {
    if(tempValue.indexOf(str) == -1){
      tempValue.push(str);
    }
  }
  return tempValue;
}

let strings = ["Hare", "Krishna", "Hare", "Krishna",
  "Krishna", "Krishna", "Hare", "Hare", ":-O"
];

console.log(`unique:${unique(strings)}`); // Hare, Krishna, :-O
```

```js
// Flat array
let myArray = ["1","2",["3","4",["5",["6"],"7"],"8"],"9"]
// let myArray = [1,2,3,[1,2,3,4, [2,3,4]]]

function flatIt(array) {
  
  // -------FAIL : Solution concat/Apply-------
  let flatArray = [].concat.apply([], array);
  
  // -------FAIL : Solution reduce-------
  let flatArray = myArray.reduce(function(prev, curr) {
    return prev.concat(curr);
  });
  
  // -------FAIL : Solution for-------
  let flatArray = [];
  for (var i = 0; i < myArray.length; ++i) {
    for (var j = 0; j < myArray[i].length; ++j)
      flatArray.push(myArray[i][j]);
  }
  
  // -------FAIL : Concat ES6-------
  let flatArray = [].concat(...myArray);
  
  // -------Solution Recursion45-------
  let flatArray = [];
  for(let item of array) {
    Array.isArray(item) ? flatArray.push(...flatIt(item)) : flatArray.push(item);
  }
  return flatArray;
  
  // -------Recusion Without ES6-------
  return array.reduce((acc, item) => Array.isArray(item) ? acc.concat(flatIt(item)) : acc.concat(item), []);
  
  // -------ES6 Small Recusion-------
  return flatArray = Array.isArray(array) ? [].concat(...array.map(flatIt)) : array;

}

console.log(flatIt(myArray));
```

```js
// Given string contains the word `hackerrank`
// hereiamstackerrank -> YES
// hackerworld -> NO
// hhaacckkekraraannk -> YES
// rhbaasdndfsdskgbfefdbrsdfhuyatrjtcrtyytktjjt -> NO

function hackerrankInString(s) {
    let sArray = s.split('');
    let ss = 'hackerrank';
    let ssArray = ss.split('');
    let next, foundAt = 0;

    for (let i = 0; i < ssArray.length; i++){
        next = sArray.slice(foundAt).indexOf(ssArray[i])
        if(next == -1) {
            return 'NO';
        }
        foundAt += next + 1;
    }
    return 'YES';
}

// Optimised 
function hackerrankInString(s) {
    return /.*h.*a.*c.*k.*e.*r.*r.*a.*n.*k/.test(s) ? 'YES' : 'NO'
}
```

```js
// 1 1 3 1 2 1 3 3 3 3 -> 4
// 10 20 20 10 10 30 50 10 20 -> 3

function sockMerchant(n, ar) {
    ar.sort((a,b) => a-b);
    let pairs = 0;
    for (let i = 0; i < n - 1; i++) {
        if (ar[i] === ar[i + 1]) {
            pairs++;
            //incrementing i again to avoid double counting the pair
            i++;
        }
    }
    return pairs;
}
```

```js
var input = [[1,  2,   3,  4],
             [5,  6,   7,  8],
             [9,  10, 11, 12],
             [13, 14, 15, 16]];

function spiral(array){
  if (!array || array.length === 0) {
    return [];
  }
  
  let result = [];
  let arrLength = array.length;
  
  let startRow = 0;
  let startCol = 0;

  let endCol = arrLength - 1;
  let endRow = arrLength - 1;
  
  while (startRow <= endRow && startCol <= endCol) {
    for (let i = startCol; i <= endCol; i++) {
      result.push(array[startRow][i]);
    }

    startRow++;

    for (let i = startRow; i <= endRow; i++) {
      result.push(array[i][endCol]);
    }
    endCol--;

    if (startRow <= endRow) {
      for (let i = endCol; i >= startCol; i--) {
        result.push(array[endRow][i]);
      }
      endRow--;
    }

    if (startCol <= endCol) {
      for (let i = endRow; i >= startRow; i--) {
        result.push(array[i][startCol]);
      }
      startCol++;
    }
  }
  return result;
}

function spiralES6(array) {
    const result = [];

    while (array.length) {
        result.push(
            // Shift -> [ 1  2  3  4 ]
            ...array.shift(),
            // Pop each -> [ 8  12  16  ]
            ...array.map(a => a.pop()),
            // Pop -> [13, 14, 15, 16] => Reverse [16, 15, 14, 13]
            ...array.pop().reverse(),
            // Shift each -> [5, 9] => Reverse [9, 5]
            ...array.map(a => a.shift()).reverse()
        );
    }
  
    return result;
}


console.log( spiral(input) )
console.log( spiralES6(input) )
```

```js
// Given a square matrix, calculate the absolute difference between the sums of its diagonals.
// 1 2 3
// 4 5 6
// 9 8 9  
// The left-to-right diagonal = 1+5+9 = 15
// The right to left diagonal = 3+5+9 + 17
// 17-15 = 2 , always give positive answer

function diagonalDifference(arr) {
    var LtR = 0;
    var RtL = 0;
    for (var i = 0; i < arr.length; i++) {
        LtR += arr[i][i]; // arr[0][0] + arr[1][1] + arr[2][2]
        RtL += arr[i][Math.abs((arr.length - 1) - i)]; // arr[0][2] + arr[1][1] + arr[2][0]
    }
    return Math.abs(LtR - RtL);
}
```

```js
// n = 4
//    #
//   ##
//  ###
// ####
function staircase(n) {
    // mySolution
    let result = ''
    for (let i = 1; i < n+1; i++){
        for (let j = 0; j < n - i; j++) {
            result += ' '
        }
        for (let k = 0; k < i; k++) {
            result += '#'
        }
        result += `\n`
    }
    console.log(result);

    // optimized
    for (let i = 1; i < n+1; i++) {
        console.log(" ".repeat(n - i) + "#".repeat(i))
    }   
}
```

```js
// [1,2,3,4,5]
// minSum = 1+2+3+4 -> (0, sortedLen-1)
// maxSum = 2+3+4+5 -> (1, sortedLen)
function miniMaxSum(arr) {
    let sortedArray = arr.sort();
    let sortedLen = arr.length;
    let minSum = sortedArray.slice(0, sortedLen-1).reduce((a,b) => a + b);
    let maxSum = sortedArray.slice(1, sortedLen).reduce((a, b) => a + b);
    console.log(`${minSum} ${maxSum}`)
}
// 10 14
```

```js
// number of times highest number in array repeat
function highestNumberInArray(ar) {
    let max = Math.max(...ar);
    return ar.filter(c => c === max).length;
}
highestNumberInArray([3,2,1,3])
// 2
```

```js
// Animate function for JS  

function animate(element, direction){
  let pos = 0;
  let frameId = setInterval(frame, 1);
  function frame(){
    if( pos > 500) {
      clearInterval(frameId);
    } else {
      pos++
      console.log(pos)
      element.style[direction] = `${pos}px`;
    } 
  }
}
var elem = document.getElementById("myID");
animate(elem, 'right')
```

```js
// time = '09:30' to 24 hour time format

function timeConversion(s) {
    let time = s.split(':');
    let typeOfDay = time[2].slice(2, 4)

    let hours = (typeOfDay == 'AM') ? (time[0] == 12) ? '00' : time[0] : (time[0] == 12) ? '12' : +time[0] + 12
    let mins = time[1]
    let secs = time[2].slice(0, 2)

    let result = `${hours}:${mins}:${secs}`
    return result
}
```

```js
//Greatest common divisor
function gcd_two_numbers(x, y) {
  
  if ((typeof x !== 'number') || (typeof y !== 'number')) {
    return false;
  }
  
  x = Math.abs(x);
  y = Math.abs(y);

  while(y) {
    var t = y;
    y = x % y;
    x = t;
  }
  return x;
}

// Array

// greatestCommonFactor([46, 14, 20, 88]); // --> 2
function gcd(a,b) {
    return (!b) ? a : gcd(b, a%b);
}

function greatestCommonFactor(arr) {
    return arr.reduce((a,b) => gcd(a,b));
}

greatestCommonFactor([46, 14, 20, 88])
```

```js
// n kids are sitting in a circle
// k toys available to distribute
// i position to start from
// 3.4.1 => 2

function getLastKis(n, k, i) {
  if(k>n){
    return i+(k%n) - 1;
  }else {
    return i+n - 1;
  }
}
```

```js
function power(x,y){
  if(y===0){
    return 1
  } else if (y%2 ===0){
    return power(x,parseInt(y/2))*power(x,parseInt(y/2))
  } else{
    return x*power(x,parseInt(y/2))*power(x,parseInt(y/2))
  }
}

console.log(power(3,2))
```

```js
/*
  find(collection, predicate) { ... }
  --
  collection (Array): The collection to inspect.
  predicate (Function|Object|Array|String): The function invoked per iteration.
    format - function (currentElement, i, collection) { ... }
*/

// returns the first object with the property 'active' which has a truthy value
// find(loans, 'active');
// => object for 'ABC123'

// find(loans, ['active', false]);
// => object for 'DEF456'

// find(loans, function(loan) { return loan.amount < 20000; });
// => object for 'ABC123'

// find(loans, { 'amount': 30401, 'active': true });
// => object for 'GHI789'

let loans = [
  { 'id': 'ABC123', 'amount': 10036, 'active': true },
  { 'id': 'DEF456', 'amount': 20040, 'active': false },
  { 'id': 'GHI789', 'amount': 30401, 'active': true }
];


let find = function(collection, predicate){
  let collectionLength = collection.length;

  for( let i = 0; i < collectionLength ; i++) {
    
    if( typeof predicate === "string" ) {   
      
      return (predicate in collection[i]) ? collection[i] : false;
    } else if ( Array.isArray(predicate) ) {
      
        if (predicate[0] in collection[i]) {
          let valuesArray = Object.values(collection[i])
          for(let item of valuesArray) {
            if(predicate[1] === item) {
              return collection[i];
            }
          }
        }
    } else if( typeof predicate === "function" ) {
      
      function isFunction(predicate, loan){
        return predicate(loan);
      }
      if(isFunction(predicate,collection[i])) {
        return collection[i];
      }
    } else if ( typeof predicate === "object" ) {

      let tempArray = [];
      for ( let pre in predicate) {
        for ( let col in collection[i]) {        
          if( pre == col && collection[i][col] == predicate[pre]) { 
            tempArray.push(`${collection[i][col]}`);
          }
          if(tempArray.length == 2){
            return collection[i];
          }
        }
      }
    }
  }
}

console.log(find(loans, 'active'));
console.log(find(loans, ['active', false]));
console.log(find(loans, function(loan) { return loan.amount < 20000; }))
console.log(find(loans, { 'amount': 30401, 'active': true }))
```

```js
// result = change(76, [5, 10, 1, 25])
// print "Result: {}".format(result)

// Result: {1:1, 10:0, 25:3, 5:0}
// aka: 1 Penny, 0 Dimes, 3 Quarters, 0 Nickels

let change = function (value, coinsArray) {
  value = (value % 1) ? value*100 : value;
  
  let sortedCA = coinsArray.sort((a,b) => b-a);
  let result = [];
  let coins = 0;

  if(value < sortedCA[sortedCA.length-1]){
     return "dont have change for this amount"
  }
  
  for ( let i = 0; i < sortedCA.length; i++) {
    coins = Math.floor(value / sortedCA[i])
    result.push(`${sortedCA[i]}: ${coins}`);
    value = value - coins*sortedCA[i];
  }
  return result;
}
    
console.log(`result : ${change(76, [5, 10, 1, 25])}`)
console.log(`result : ${change(20.12, [5, 10, 1, 25])}`)
console.log(`result : ${change(5, [10, 25])}`)
```

```js
var arr = [
  ['I','B','C','A','K','E','A'],
  ['D','R','F','C','A','E','A'],
  ['G','H','O','E','L','A','D']
];

var row = 0, col = 0;
var totalCols = arr[0].length;
var totalRows = arr.length;
var goingDown = false;
var msg = '';

while (col < totalCols) {
  msg += arr[row][col];
  // row++ if less than total rows
  // row-- if back at row 0

  if (row === 0 || (row < totalRows - 1 && goingDown)) {
    row += 1;
    goingDown = true;
  } else {
    row -= 1;
    goingDown = false;
  }

  // always go forward in column
  col++;
}

console.log(msg) // IROCKED
```

```js
let entry = [1, 2, 9, 5, 5]
let exit = [4, 5, 12, 9, 12]

function findMaxGuests(entry, exit) {
  let guestsIn = 1;
  let maxGuests = 1;  
  let time = entry[0];
  let times = [...entry, ...exit];
  let i = 1;
  let j = 0;
  
  while( i < entry.length &&  j < entry.length ) {
    // If next event in sorted
    // order is arrival,
    // increment count of guests
    if (entry[i] <= exit[j]) {
      guestsIn++;
   
      // Update max_guests if needed
      if (guestsIn > maxGuests) {
        maxGuests = guestsIn; 
        time = entry[i]; 
      }
      
      // increment index of  
      // arrival array 
      i++;
    } else {
      // If event is exit, decrement 
      // count of guests. 
      guestsIn--;
      j++; 
    }
  }
  return `Maximum Number of Guests = ${maxGuests} at ${time}`;
}

console.log(findMaxGuests(entry, exit))
```

```js
// If given an empty string, countAllCharacters should return an empty object.
// var output = countAllCharacters('banana');
// console.log(output); // --> {b: 1, a: 3, n: 2}

function countAllCharacters(str) {
    let opObj = {};
    let strArray =  [...str];
    let strArrayKeys = [...new Set(str)];
    
    for(let item in strArrayKeys) {
        opObj[strArrayKeys[item]] = countChar(strArray, strArrayKeys[item]);
    }
    
    return opObj;
}

function countChar(array, key) {
    let totalNumber = 0;
    for(let i = 0; i < array.length ; i++) {
        if(array[i] === key) {
            totalNumber++;
        }
    }
    return totalNumber;
}

// Better Solution using Reduce
function countAllCharacters(str) {
  return str.split("").reduce(function(obj, s){
    obj[s] = (obj[s] || 0) + 1;
    return obj;
  }, {});
}
console.log(countAllCharacters('banana'));
```

```js
// Complex Array to Object
// var input = [
//     [
//         ['firstName', 'Joe'], ['lastName', 'Blow'], ['age', 42], ['role', 'clerk']
//     ],
//     [
//         ['firstName', 'Mary'], ['lastName', 'Jenkins'], ['age', 36], ['role', 'manager']
//     ]
// ];
// Result should look like this
// var result = [
//     {firstName: 'Joe', lastName: 'Blow', age: 42, role: 'clerk'},
//     {firstName: 'Mary', lastName: 'Jenkins', age: 36, role: 'manager'}
// ]

// Two Loop solution
function transformEmployeeData(employeeData) {
  var obj = {};
  var arr = [];
  
  for (var i = 0; i < employeeData.length; i ++) {
      
    for (var j = 0; j < employeeData[i].length; j ++) {
        
      var key = employeeData[i][j][0];
      var value = employeeData[i][j][1];
      obj[key] = value;
      
    }
    
    arr.push(obj);
  }
  
  return arr;
}

// Array Map/Reduce solution 
function transformEmployeeData(employeeData) {
    let result = employeeData.map(item => {
      return item.reduce((acc, item) => {
        acc[item[0]] = item[1];
        return acc;
      }, {});
    });
    
    return result;
}
```

```js
// Complex Object to Array
// var input = {
//   name: 'Holly',
//   age: 35,
//   role: 'producer'
// }

function convertObjectToArray(obj) {
    let myArray = [];
    
    // myArray = Object.entries(obj);
    myArray = Object.keys(obj).map(v => new Array(v, obj[v]));
    
    return myArray
}

console.log(convertObjectToArray(input))

// Output : [ [ 'name', 'Holly' ], [ 'age', 35 ], [ 'role', 'producer' ] ]
```

```js
// https://res.cloudinary.com/css-tricks/image/upload/c_scale,w_850,f_auto,q_auto/v1497692795/stagger_bjqqml.gif
```

```js
Please use this Google doc during your interview (your interviewer will see what you write here). To free your hands for typing, we recommend using a headset or speakerphone.

// No HTML
// 4 Colors and repeat itSelf, Arry of any number
// Input will be string

const myColors = ["4285F4", "EA4335", "FBBC04", "34A853"];
const myStr = "Lorem ipsum dolor sit amet";

const printColoredLetter = (hexString, letter) => {
    // Implementation not required
}

// param {array}
// param {string}
const myColors = ["4285F4", "EA4335", "FBBC04", "34A853"];
const myStr = "Lorem ipsum dolor sit amet";
// param {array}
// param {string}

function colorString( colorArray, string) {

  // stringArray = [L,o,r,e,m, ,i,p,s,u,m, ,d,l,o,r, s,i,t, a,m,e,t];
  let stringArray = string.split('');
  let isSpace = 0;
  
// Color a String
  for(let i = 0; i < stringArray.length; i++) {
    
    // compare if its not space
    if(stringArray[i] !== ' '){
      // Color L with myColors[0]
      // L o r e m[5] i[7] …
      let colorIndex = ((i-isSpace) % (myColors.length));
      printColoredLetter(colorIndex,stringArray[i])
    }
    else {
      // _[6] … 
      isSpace++;
      console.log(`${stringArray[i]}`);
      printColoredLetter(stringArray[i])

    }
  }
}

colorString(myColors, myStr)
```

```js
let d = {
  'a': 5,
  'b': 6,
  'c': {
    'f': 9,
    'g': {
      'm': 17,
      'n': 3
    }
  }
}

// Output
// flatten(d) = {
//   'a': 5,
//   'b': 6,
//   'c.f': 9,
//   'c.g.m': 17,
//   'c.g.n': 3,
// }

let tempKey
let flatData = {};

function flatten(data) {
  
  for( let key in data) {
    if(typeof data[key] === "object") {
      tempKey = tempKey ? `${tempKey}.${key}` : key
      flatten(data[key])
    } else {
      if(tempKey){ 
        flatData[`${tempKey}.${key}`] = data[key]
      } else {
        flatData[key] = data[key]
      }
    }
  }  

  return flatData;
}


console.log(flatten(d))
```

```js
// Given a 2D board and a word, find if the word exists in the grid.
function exist(board, word) {
  if (board.length === 0) return false;

  const h = board.length;
  const w = board[0].length;

  function go(i, j, k) {
    if (i < 0 || j < 0 || i >= h || j >= w) return false;
    if (board[i][j] !== word[k]) return false;
    if (k === word.length - 1) return true;

    board[i][j] = '*';      // mark as visited

    if (go(i - 1, j, k + 1)) return true;  // up
    if (go(i + 1, j, k + 1)) return true;  // down
    if (go(i, j - 1, k + 1)) return true;  // left
    if (go(i, j + 1, k + 1)) return true;  // right

    board[i][j] = word[k];  // reset
    return false;
  }

  for (let i = 0; i < h; i++) {
    for (let j = 0; j < w; j++) {
      if (go(i, j, 0)) return true;
    }
  }

  return false;
}
```

```js
/*
* Code a function in JavaScript that receives a variable
* containing any valid number and returns that
* number as a string with comma thousand separators. For example:
*     Input: 3450272 will return  “3,450,272”
*     Input: 3450272.323 will return  “3,450,272.323”
*/

function convertNumber(num) {
  // split number
  let splitNum = num.toString().split(".");
  
  // splitNum[0]
  let newPattern = /(\d)(?=(\d{3})+(?!\d))/g
  splitNum[0] = splitNum[0].replace(newPattern, '$1,');
  
  // splitNum[1]
  return splitNum.join('.');
}

function test(num, expectedValue) {
  var result = convertNumber(num);
  console.log('Test[' + (result === expectedValue ? '✓' : '☓') + '] ' + num + ' -> ' + result);
}

test(306567, '306,567');
test(1003567, '1,003,567');
test(3567, '3,567');
test(3567.2345, '3,567.2345');
test(-35672345, '-35,672,345');
test(-135672345, '-135,672,345');
test(0.0003, '0.0003');
test(2e5, '200,000');
test(0x1234, '4,660');
test(Infinity, 'Infinity');
```

```js
function maxRecurringChar(str) {
  let charMap = {};
  let charArray;
  let valueArray;
  let maxCharValue;
  
  for(let letter of str) {
    if(charMap.hasOwnProperty(letter)){
      charMap[letter]++;
    } else {
      charMap[letter] = 1
    }
  }
  
  charArray = Object.keys(charMap)
  valueArray = Object.values(charMap)
  maxCharValue = Math.max(...valueArray)
  
  console.log(charArray[valueArray.indexOf(maxCharValue)])
  console.log(maxCharValue)
}


console.log(maxRecurringChar('aabacada')) // a
console.log(maxRecurringChar('aabbcadbdocbbbbsfdicbacada')) // b
console.log(maxRecurringChar('aabaclpdfjcpdjjccccpaofjecpaklsdkccccada')) // c
```

```js
// Sentence Capitalization
function capSentence(text) {
  let charArray = text.split(' ');
  
  let capArray = charArray.map((item) => {
    return item = item.charAt(0).toUpperCase() + item.slice(1);
  })
  
  return capArray.join(' ')
  
}

console.log(capSentence('the tales of scotch!'))
```

```js
// Palindrome
function palindromeChecker(text){
  return (text === text.split('').reverse().join('')) ? true : false
}

// Palindrome with Permutation
function hasPalindromePermutation(theString) {

  // Track characters we've seen an odd number of times
  const unpairedCharacters = new Set();

  for (let char of theString) {
    if (unpairedCharacters.has(char)) {
      console.log(`delete: ${char}`)
      unpairedCharacters.delete(char);
    } else {
      console.log(`add: ${char}`)
      unpairedCharacters.add(char);
    }
  }

  // The string has a palindrome permutation if it
  // has one or zero characters without a pair
  return unpairedCharacters.size <= 1;
}

console.log(palindromeChecker('dracecar')) // false
console.log(hasPalindromePermutation('naman')) // true
console.log(hasPalindromePermutation('nnaam')) // true
```

```js
function hammingDistance(str1, str2) {
  let result = 0;
  if(str1.length === str2.length) {
    for( let i = 0; i < str1.length; i++) {
      if(str1[i] !== str2[i]) { result++ }
    }
  } else {
    return "Not same sime size string"
  }
  
}

console.log(hammingDistance('rokklver', 'rillkver')) // should return 1
```

```js
// Longest word in sentence
function longestWord(str) {
  let strArray = str.split(' ');
  let maxChar = '';
  strArray.map((char) => {
    maxChar = (char.length > maxChar.length) ? char : maxChar
  })
  return maxChar
  
  // Sort
  return str.split(' ').sort((wa, wb) => wa.length < wb.length)[0]
}

console.log(longestWord('Top Shelf Web Development Training on Scotch')) // Development
```

```js
// Anagrams
function isAnagram(str1, str2) {
  const sanitizeString = function (str) {
    return str.toLowerCase().replace(/[^a-z\d]/g, '').split('').sort().join('');
  }
  
  if(str1.length === str2.length) {
    return sanitizeString(str1) === sanitizeString(str2) 
  } else {
    console.log("Strings are not same size")
  }
}

console.log(isAnagram('silent', 'listen'))
```

```js
// Pig Latin

function pigLatin(str) {
  const vowels = ["a","e","i","o","u"];
  
  if(vowels.includes(str[0])) {
    return `${str}way`
  } else {
    let charIndex;
    for( let char of str) {
      if (vowels.includes(char)) {
        charIndex = str.indexOf(char)
        break
      }
    }
    return str.slice(charIndex) + str.slice(0, charIndex) + 'ay'
  }
}

console.log(pigLatin("explain")) // explainway
console.log(pigLatin("glove")) // oveglay
console.log(pigLatin("pig")) // igpay
```

```js
function chunkArray(array, size) {
  
  if(array.length < size) {
   return [array]
  } 
  
  return [array.slice(0,size), ...chunkArray(array.slice(size), size)]
}

console.log(chunkArray([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13], 5))
// should return [[1, 2, 3, 4, 5], [6, 7, 8, 9, 10], [11, 12, 13]]

```

```js
// frequencySort

function customSort(arr) {
    // Write your code here
    let customSortArray = [];
    let sortedArray = [];
    let countObj = {};
    
    // create countObj with key repeat value
    for(let key of arr) {
        if(key in countObj){
            countObj[key] = countObj[key] + 1;
        } else {
            countObj[key] = 1;
        }
    }

    for(let key in countObj) {
        sortedArray.push([key, countObj[key]])
    }

    sortedArray.sort((a,b) => a[1] - b[1])

    sortedArray.forEach((obj) => {
        for(let i=0; i < obj[1]; i++) {
            customSortArray.push(obj[0]);
        }
    })

    return customSortArray;
}

customSort([1,3,2,4,2])
customSort([1,2,3,3,4,4,2,2,3,1,3,9,2,4,11])
```

```js
 // falsyBouncer([1, 0, null, NaN, '', 5]) // should return [1,5]

 function falsyBouncer(array) {
  // use loop
  let result = [];
  for(let value of array){
    if(value) {
      result.push(value)
    }
  }
  return result
  
  // Optomized version
  return array.filter((value) => {
      return Boolean(value)
  })
}

console.log(falsyBouncer([1, 0, null, NaN, '', 5])) // should return [1,5]
```

```js
function reverseInteger(str) {  
  let reverseStr = []
  let strArray = str.toString().split('')
  
  
  for(let elem of strArray) {
    reverseStr.unshift(elem);
  }
  
  return (parseInt(reverseStr.join(''))) * Math.sign(str)
}


console.log(reverseInteger(-123))
```

```js
// Range Sum
function rangeSum(arr) {
  // Best
  return ((arr[1] - arr[0] +1) * (arr[0] + arr[1])) / 2;

  // Forloop
  let sum = 0;
  for (i = arr[0]; i <= arr[1]; i++) {
    sum += i;
  }
  return sum;

  // Recursion
  if (arr[0] == arr[1]) {
    return arr[0];
  } else {
    return rangeSum([arr[0], arr[1] - 1]) + arr[1];
  }
}

rangeSum([1,9]) 
// Should return 45 i.e 1+2+3+4+5+6+7+8+9
```

```js
let d = {
  'a': 5,
  'b': 6,
  'c': {
    'f': 9,
    'g': {
      'm': 17,
      'n': 3
    }
  }
}

flatten(d) = {
  'a': 5,
  'b': 6,
  'c.f': 9,
  'c.g.m': 17,
  'c.g.n': 3,
}

let tempKey
let flatData = {};

function flatten(data) {
  
  for( let key in data) {
    if(typeof data[key] === "object") {
      tempKey = tempKey ? `${tempKey}.${key}` : key
      flatten(data[key])
    } else {
      if(tempKey){ 
        flatData[`${tempKey}.${key}`] = data[key]
      } else {
        flatData[key] = data[key]
      }
    }
  }  

  return flatData;
}


console.log(flatten(d))
```

### Others

```js
// Write a parser for Javascript floating point numbers
// Write a JSON parser
// OOP design of a banking system: bank account, transactions and owner
// Create a simple image gallery using HTML/CSS/JS that rotates through images once per second.  
// How would you architect a chess app?  
// How would you write the HTML for YouTube's landing page?  
// Write an async forEach function with and without promises.  
// Talk about one of WorktypeOfDay's actual UI components and explain how you would implement it.  
// What is a technology that you are passionate about and why? 
// Promise
// Observer
// - Implement the tabs in vanilla JS and css
// - Stream/Observer API
// - Build Amazon's Marketplace system design
// - https://www.geeksforgeeks.org/find-the-point-where-maximum-intervals-overlap/
// - https://leetcode.com/problems/maximum-subarray/
// - https://leetcode.com/problems/linked-list-cycle-ii/
// - arrays, maps, sets, and DOM trees 
// - Big O notation and tree traversal
// - iteration, closures, scope, and writing asynchronous code
// - Given two identical DOM tree structures, A and B, and a node from A, find the corresponding node in B.  
// - Given two identical DOM trees (but not equal) and one element of the first DOM tree, how would you find this element in the second DOM tree?
// - DONE - Can you write a function that deeply flattens an array? 
// - What are the advantages of using ES6 maps over objects? What about using ES6 sets over arrays? 
// - MAP vs ForEach
// - Array vs Object
// - call vs Apply
// -------
// @keyframes scale-in-tl {
//   0% {
//     transform: scale(0);
//     transform-origin: 0% 0%;
//     opacity: 1;
//   }
//   100% {
//     transform: scale(1);
//     transform-origin: 0% 0%;
//     opacity: 1;
//   }
// }
```
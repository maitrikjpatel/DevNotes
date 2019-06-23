## JS Questions

### JS Basics

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
<div contentEditable="tue">Hello</div> // make content editable
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
      totalSum = sortedArray[i] + sortedArray[i-1] + totalSum;
      accumulator += totalSum;
    } else if (  i > 1) {
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

### Others

```js
// Write a parser for Javascript floating point numbers

// Write a JSON parser

// OOP design of a banking system: bank account, transactions and owner

// Create a simple image gallery using HTML/CSS/JS that rotates through images once per second.  

// How would you architect a chess app?  

// How would you write the HTML for YouTube's landing page?  

// Write an async forEach function with and without promises.  

// Talk about one of Workday's actual UI components and explain how you would implement it.  

// What is a technology that you are passionate about and why? 
```

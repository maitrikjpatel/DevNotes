## JS Questions

## EASY

```js 
conole.log([]+ []) // Empty
conole.log({}+ []) // Empty
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
    return A // This is answer/trick
  },
  y: function(){
    console.log('y')
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
console.log(2 + '2') // 2
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
console.log( 5 > 6 > 7) // false (5<6)=true -> (True>7) = false
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
const myArray = [1,2,15,30,5,45,7]
console.log(myArray.sort() // [1,15,2,30,45,5,7]
console.log(myArray.sort((a,b) => a-b))
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
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

### JS Problem Solving

```js
// Given Merge two sorted arrays, merge them into a new array that is also sorted.
let a = [1,2,4]
let b = [1,3,4,5,6,8]

function mergeArray(a,b) {
  let result = []
  let indexA = 0;
  let indexB = 0;
  let current = 0;
  
  while(current < (a.length + b.length)){
    let unmergedA = a[indexA]
    let unmergedB = b[indexB]
    
    if(unmergedA < unmergedB) {
      result[current] = unmergedA;
      indexA++;
    } else {
      result[current] = unmergedB;
      indexB++;
    }
    current++;
  }

  return result
}

console.log(mergeArray(a,b))

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

//----

function displayColorfulText(colors, text){
const strArray = text.split(' ');

const createSpanElementWithColor = (text, color) => {
let elm = document.createElement('span');
// set the innner text and then add color to it
elm.innerText = text+ ' ';
elm.style.color = color;

console.log(elm);
return elm;
}

// get element by id and then set the inner html to it
let parent = document.createElement('result');
strArray
.map((str, i) => createSpanElementWithColor(str, colors[i]))
.forEach(el => parent.appendChild(el));
document.body.appendChild(parent);

}

displayColorfulText(["red", "blue", "green", "yellow"], "Lorem ipsum dolor sit amet");

// ---

const colorPrinter = (str, colorsArray) => {
	let i = 0;
	str.split('').forEach((ch, ind) => {
  	if(ch !== ' '){
    		i = (i === colorsArray.length) ? 0 : i;
      	console.log(`Character ${ch} : ${colorsArray[i]}`);
        i++;
    }
  });
}

colorPrinter('Lorem ipsum in the world', ['red', 'blue', 'green', 'yellow', 'white']);

// ---

const colorPrinter = (str, colorsArray) => {
let i = 0;
str.split('').forEach((ch, ind) => {
if(ch !== ' '){
i = (i === colorsArray.length) ? 0 : i;
console.log(`Character ${ch} : ${colorsArray[i]}`);
i++;
}
});
}


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
// all permutations of string

function permutations(str) {
  let results = [];

  if (str.length == 1) {
    return [ str ];
  }

  for (let i = 0; i < str.length; i++) {
    const first = str[i];
    const charsRemaining = str.substring(0, i) + str.substring(i + 1);
    const remainingPerms = permutations(charsRemaining);
    for (let j = 0; j < remainingPerms.length; j++) {
      results.push(first + remainingPerms[j]);
    }
  }
  return results;
}

console.log(permutations('abc'));
```

### Leetcode

- [X] Isomorphic strings
- [X] Valid Parentheses
- [X] Longest Palindromic Substring
- [X] Best Time to Buy and Sell Stock 1 & 2 - Math
- [X] Integer to English Words - math and string

- [X] Two Sum - Hash Object
- [X] Longest Substring Without Repeating Characters - Hash Object  
- [X] Group Anagrams - Hash Object

- [X] Trapping Rain Water - left and  right pointers
- [X] Product of Array Except Self - left and  right pointers

- [X] Number of Islands - dfs search

- [X] LRU Cache

- [X] Word Break - dynamic programming

- [X] Merge Two Sorted Lists - linkedin list
- [X] Merge k Sorted Lists - linkedin list
- [X] Copy List with Random Pointer - linkedin list

```js
// We are given a list schedule of employees, which represents the working time for each employee.
// Each employee has a list of non-overlapping Intervals, and these intervals are in sorted order.
// Return the list of finite intervals representing common, positive-length free time for all employees, also in sorted order.

// Input: schedule = [[[1,3],[6,7]],[[2,4]],[[2,5],[9,12]]]
// Output: [[5,6],[7,9]]

// Input: schedule = [[[1,2],[5,6]],[[1,3]],[[4,10]]]
// Output: [[3,4]]

let schedule = [[[1,3],[6,7]],[[2,4]],[[2,5],[9,12]]]

let employeeFreeTime = function(schedule) {
  
  let flatSchedule = [].concat(...schedule)
  let sortSchedule = flatSchedule.sort((a,b) => a[0] - b[0])
  let intervals = [flatSchedule[0]];
  
  for(let i = 1; i < sortSchedule.length; i++) {

    let prev = intervals.pop();
    let current = flatSchedule[i];

    if (prev[1] >= current[0]) {
        const start = Math.min(prev[0], current[0]);
        const end = Math.max(prev[1], current[1]);
        intervals.push([start, end]);
    } else {
        intervals.push(prev);
        intervals.push(current);
    }
  }
  
  let result = [];
  for (let i = 1; i < intervals.length; i++) {
      const prev = intervals[i - 1];
      const current = intervals[i];
      // gap
      result.push([prev[1],current[0]])
  }

  return result;
};

console.log(employeeFreeTime(schedule))
```

```js
// Word Search
// Leetcode: Given a 2D board and a word, find if the word exists in the grid.
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
// Leetcode: Word Break from word dictionary
/**
 * @param {string} s
 * @param {string[]} wordDict
 * @return {boolean}
 */
const wordBreak = (s, wordDict) => {
  if (wordDict == null || wordDict.length === 0) return false;

  // use set to have unique keys
  const set = new Set(wordDict);
  
  // [f,f,...,f] - length +1
  const dp = Array(s.length + 1).fill(false);
  
  // start with true
  dp[0] = true;

  for (let end = 1; end <= s.length; end++) {
    for (let start = 0; start < end; start++) {
      
      // travel from 0-1, 0-2, 1-2, 0-3, 1-3, 2-3, ....
      const w = s.slice(start, end);
      
      // Check if work match with set of dictionary
      if (dp[start] === true && set.has(w)) {
        dp[end] = true;
        break;
      }
    }
  }
  // if end has true and then its true else false
  return dp[s.length];
};
```

```js
// Leetcode : Sell Stock
/**
 * @param {number[]} prices
 * @return {number}
 */
const maxProfit = (prices) => {
  let min = Infinity;
  let max = 0;
  
  for (let i = 0; i < prices.length - 1; i++) {
    min = Math.min(min, prices[i]);
    max = Math.max(max, prices[i + 1] - min)
    console.log(`i:${i}, min:${min}, max:${max}`)
  }
  return max;
};
```

```js
// justify content 
var fullJustify = function(words, limit) {
    let result = []
    let rowObj = {words:[], letters:0}
    result.push(rowObj)
  
    for(let word of words) {
      if(rowObj.words.length && rowObj.letters + word.length + (rowObj.words.length - 1) >= limit){
        rowObj = {words:[], letters:0}
        result.push(rowObj)
      }
      
      rowObj['words'].push(word)
      rowObj['letters'] = ('letters' in rowObj ? rowObj.letters : 0) + word.length;
    }
    
    // console.log(result)
  
    for(let i = 0; i < result.length; i++){
      let row = result[i]
      let line = row.words[0];
      let totalWordsLength = (row.words.length)
      
      if (totalWordsLength === 1 || i === result.length - 1) {
        row['line'] = row.words.join(' ') + ' '.repeat(limit - row.letters - row.words.length + 1);
        continue;
      }
      
      let spaces = limit - row.letters;
      let minSpaces = ' '.repeat(Math.floor(spaces / ( totalWordsLength - 1 )))
      let addSpaces = spaces % ( totalWordsLength - 1 )
      
      for(let w = 1; w < totalWordsLength; w++) {
        line += minSpaces + (w <= addSpaces ? ' ' : '') + row.words[w]
      }
        
      row['line'] = line
    }
  
    return result.map(item => item.line)
};
```

### Others

```js
// hello from okta hello

// Part 2:
// "Hello Human" isn't very friendly - let's customize it to take in a human's name
function bind(arguments, context) {
  
  let func = this;
  /* let funcArgs = [].splice.call() */;
  
  // two arguments
  // one : i splied (3)
  // second: function splied
  
  // splice it 
  // currentArgs
  // funcArgs 
  // [...currentArgs, ...funcArgs]
  
  return function() {
  	let currentArgs = [].splice.call(arguments)
    let combinedArgs = [...currentArgs]
  	func.apply(context, currentArgs)
  }
  
}
 
var Robot = function (robotName) {
  this.robotName = robotName;
};
Robot.prototype.sayHello = function (humanName) {
  console.log('Hello', humanName + ',', 'my name is', this.robotName);
};
Robot.prototype.sayHelloDelayed = function (humanName, numSeconds) {
  setTimeout(bind(this.sayHello, this, humanName), numSeconds * 1000);
};
var robby = new Robot('Robby');
robby.sayHello('Hector'); // "Hello Hector, my name is Robby"
robby.sayHelloDelayed('Hector', 1); // "Hello Hector, my name is Robby" after 1 second
```

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
// - Given two identical DOM trees (but not equal) and one element of the first DOM tree, how would you find this element in the second /// - DOM tree?
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
// React
// - Question was simply to design a stop watch component in React. Two states, and the following buttons - Start, Pause, Continue, Stop
// attlasian 
// - About javascript prototype, this scope.  
// - Implement the tabs in vanilla JS and css
// - Stream/Observer API
// - Design a job scheduling service. 
// - String manipulation
// - How would you implement a least frequently used cache? 
// - Build Amazon's Marketplace system design
// - Designing a micro-service within the Atlassian architecture. Nothing too difficult. Microservice should be able to calculate time based metrics. 
// - median of unsorted array in O(nlog n ) time - quick sort
// - Reverse a int[] array in place  
// - How to convert numbers from one base to another 
// - What are the differences between React and Angular? 
// - When should you use a linked list vs an array?
// - calculating frequencies of powersets of many sets.
// - Implement a hash map  
// - write a hash function
// - A binary tree traversal problem.
// - Find the area of the shade a skyline casts
// - https://leetcode.com/problems/maximum-subarray/
// - https://leetcode.com/problems/linked-list-cycle-ii/
// - Roll forward a string by 1 digit and repeat it based on digits given in an array 
// - https://www.tutorialandexample.com/reactjs-interview-questions/
```

```js
// Write a class called DOMStore that stores a Node and a value (reimplement Map). DOMStore contains the following functions:
// has(node) // returns boolean
// get(node) // returns node or undefined
// set(node, value) // "upsert", update or insert
// Flatten an array with unknown depth (reimplement .flat(Infinity)).
// a. Write it both recursively and iteratively.
// https://www.w3schools.com/graphics/game_controllers.asp  


class DOMStore {
  constructor() {
    this.keys = [];
    this.values = [];
  }

  set(node, value) {
    const index = this.keys.indexOf(node);
    if (index >= 0) {
      this.values[index] = value;
    } else {
      this.values.push(value);
      this.keys.push(node);
    }
  }

  get(node) {
    const index = this.keys.indexOf(node);
    return index >= 0 ? this.values[index] : undefined;
  }

  has(node) {
    return !!this.get(node);
  }
}

const uuid = () => ...;
const uidSymbol = Symbol('uidSymbol');

class DOMStore {
  constructor() {
    this.map = {};
  }

  set(node, value) {
    if (!node[uidSymbol]) {
      node[uidSymbol] = uuid();
    }

    this.map[node[uidSymbol]] = value;
  }

  get(node) {
    return this.map[node[uidSymbol]];
  }

  has(node) {
    return !!this.get(node);
  }
}
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
// Answer 1, use let in for loop
// Answer 2, use immediate invoked function
```

```js
List of intervals: [1,3], [4,10], [20,30]. check if given interval like [5,10] are occupied by the intervals.
Find any one peak element from an unsorted array.pick element is an element having previous and next items bigger.  
```

### Not IMP

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
let closureFunc = b =>  b ? sum(a + b) : a;
  closureFunc.toString = () => a;
  return closureFunc;
}
alert(sum(10)(2)(3)(4));
```

```js
// Add array and sort
const a = [1,2,3,4,5,5,6,9];
const b = [2,5,6,12,100];
  
const c = [ ...a, ...b ].sort((a,b) => a-b)
console.log(c)
```

```js
let myArray = ['1','2', '0', 4, 5, 'six', 'seven', null, undefined, NaN]

// 3 array 
	// number // 4, 5
	// string -> all string
	// all numbers -> 1, 2, 0, 4, 5

function splitArrayByTypeof(array) {
  let onlyNumArray = []
  let strArray = []
  let allNumArray = []
  
  array.forEach((item) => {
    if(typeof item === "number" && !isNaN(item)) {
      onlyNumArray.push(item)
    } 
    if(typeof item === "string") {
      strArray.push(item)
    } 
    if(typeof Number(item) === "number" && !isNaN(item) && item !== null) {
      allNumArray.push(item)
    }
  })
  
  console.log(onlyNumArray)
  console.log(strArray)
  console.log(allNumArray)
}

splitArrayByTypeof(myArray)
```

```js
// Implement a class called LinkedList using the provided Node class  
class Node {  
  constructor(value) {  
    this.value = value;  
    this.next = null;  
  }  
}  
// push  
// - accepts a value and places it at the tail of the linked list  
//  
// pop  
// - returns and removes a node from the tail of the linked list  
//  
// unshift  
// - accepts a value and places it at the head of the linked list  
//  
// shift  
// - returns and removes a node from the head of the linked list  
//  
// [if you have time]  
// insertAt  
// - accepts a value and position and inserts a node at the new position  
//  
// [if you have time]  
// deleteAt  
// - accepts a position and deletes the node at that position  
//  
class LinkedList {  
  constructor() {  
    this.head = null;  
    this.length = 0;  
  }  
  
  push(item) {
    const nodeToAdd = new Node(item);
    let nodeToCheck = this.head
    
    if(!nodeToCheck) {
      this.head = nodeToAdd;
      this.length++
      return nodeToAdd;
    }
    
    // data: 1
    // next: {} empty
    while(nodeToCheck.next) {
      nodeToCheck = nodeToCheck.next 
    }
    
    // next: {nextToAdd}
    nodeToCheck.next = nodeToAdd
    this.length++;
    return nodeToAdd;
  
  } // add to tail 
  
  pop() {
    let nodeToCheck = this.head
    let counter = 0;
    let popData;
    let preNodeToCheck ;
    
    // 1->2 
    while(counter !== this.length-1) {
      preNodeToCheck = nodeToCheck
      nodeToCheck = nodeToCheck.next      
      counter++      
    }
    
    preNodeToCheck.next = null
    this.length--;
    return nodeToCheck
  } // remove from tail  
  

  unshift(item) {
    const nodeToAdd = new Node(item);
    let headNode = this.head
    
    nodeToAdd.next = headNode
    this.head = nodeToAdd
    this.length++;
  } // add to head  
  
  
  shift() {} // remove from head  
  insertAt() {} // adds anywhere based on index  
  deleteAt() {} // removes anywhere based on index  
}  


let newLL = new LinkedList()
newLL.push('1')
newLL.push('apple')
// console.log(newLL.pop())
// newLL.unshift('iphone')
console.log(newLL)
```

```js
// Find the sum of all the numbers in the array, expected 550
const mixedArrayEmpty = []

const mixedArray = ['dog', 10, 15, 'cat', 'giraffe', 500, true, 'elephant', 25, 'snuffleupagus', 'armadillo', 'ant'];


function sumNumer(array) {
  if(!array.length) return 'Empty Array'
  
  let result = 0;
  
  array.forEach(item => {
     if(typeof item === "number") {
        result += item; 
     }
  }) 
  
  return result
}

// console.log(sumNumer(mixedArray))
// Apply a discount of 5% to each item in the cart and return the new discounted cart
const cart = [
  {
    item: 'bananas',
    price: 2
  },
  {
    item: 'milk',
    price: 1.50
  },
  {
    item: 'cereal',
    price: 3
  }
];


function numDiscount(number, discountInPer) {
  let ramainPercentage = (100-discountInPer)/100
  return Number((number * ramainPercentage).toFixed(2))  
}


function discountedCart(cartItems, discountInPer) {
  if(!cartItems.length) return 'Empty Array'
  
  let result = cartItems.map((item) => {
    return {
      ...item,
      price: numDiscount(item.price, discountInPer)
    }
  })
  
  return result
}

console.log(discountedCart(cart, 5))
```

```js
/**
Create a service provider which provides following set of numerical services:
A(+1) , B(-1), C(*2), D(/5), E(**2)..... can be extended to complex services

updateServiceGroup(serviceGroupId, serviceId, dependencyArray)
    updateServiceGroup("W22K2CE4", A, [D, B])
    updateServiceGroup("W22K2CE4", C, [D, A])
    updateServiceGroup("W22K2CE4", B, [D])
    updateServiceGroup("W22K2CE4", D, [])

    callServiceGroup(serviceGroupId, Input, endpoint)
    For example, callServiceGroup("W22K2CE4", 5, "https://localhost:9000/api/endpoint")
    output: 2, posted at the given endpoint       
*/

// A -> D,B
// C -> [D,A]
// B -> [D]
// D

// two pointers

// walking through graph
function dependencyResolve(node, resolved) {
  for (let edge in node.edges) {
    dependencyResolve(edge, resolved);
  }
  resolved.push(node);
}

const serviceGroupMap = {};
function updateServiceGroup(serviceGroupId, serviceId, dependencyArray) {
  if (!serviceGroupMap[serviceGroupId]) {
    serviceGroupMap[serviceGroupId] = {
      resolvedOrder: [],
      resolvedServices: [],
      dependencyServices: {}
    };
  }
  serviceGroupMap[serviceGroupId].dependencyServices[
    serviceId
  ] = dependencyArray;
}

const A = input => input + 1;
const B = input => input - 1;
const C = input => input * 2;
const D = input => input / 5;

updateServiceGroup("W22K2CE4", A, [D, B]);
updateServiceGroup("W22K2CE4", C, [D, A]);
updateServiceGroup("W22K2CE4", B, [D]);
updateServiceGroup("W22K2CE4", D, []);
updateServiceGroup("W22K2CE4", A, [D, B, E]);
```
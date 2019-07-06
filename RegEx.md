### RegEx

- [Undersrtand Regular Expression in hour](https://www.youtube.com/watch?v=ZfQFUJhPqMM)
- [Regular Expression FreeCodeCamp](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures/regular-expressions)

### Match, Test and Replace

- Match
  - `RegexObject.test( String )`
  - Executes the search for a match between a regular expression and a specified string. Returns true or false.

- Test
  - `string.match( RegExp )`
  - Used to retrieve the matches when matching a string against a regular expression. Returns an array with the matches or null if there are none.

- Replace
  - `str.replace(regexp|substr, newSubstr|function)` 
  - method returns a new string with some or all matches of a pattern replaced by a replacement. 
  - The pattern can be a string or a RegExp, and the replacement can be a string or a function to be called for each match.

```js
// Match Literal Strings
let waldoIsHiding = "Somewhere Waldo is hiding in this text.";
let waldoRegex = /Waldo/;
let result = waldoRegex.test(waldoIsHiding);

//Match a Literal String with Different Possibilities
let petString = "James has a pet cat.";
let petRegex = /pet|cat/;
let result = petRegex.test(petString);

// Ignore Case While Matching
let myString = "freeCodeCamp";
let fccRegex = /freeCodeCamp/i;
let result = fccRegex.test(myString);

// Extract Matches
let extractStr = "Extract the word 'coding' from this string.";
let codingRegex = /coding/;
let result = extractStr.match(codingRegex);

// Find More Than the First Match
let twinkleStar = "Twinkle, twinkle, little star";
let starRegex = /Twinkle/ig;
let result = twinkleStar.match(starRegex);

// Match Anything with Wildcard Period
let exampleStr = "Let's have fun with regular expressions!";
let unRegex = /.un/;
let result = unRegex.test(exampleStr);

// Match Single Character with Multiple Possibilities
let quoteSample = "Beware of bugs in the above code; I have only proved it correct, not tried it.";
let vowelRegex = /[aeiou]/ig;
let result = quoteSample.match(vowelRegex);

// Match Numbers and Letters of the Alphabet
let quoteSample = "Blueberry 3.141592653s are delicious.";
let myRegex = /[2-6h-s]/ig;
let result = quoteSample.match(myRegex);

// Match Single Characters Not Specified
let quoteSample = "3 blind mice.";
let myRegex = /[^aeiou0-9]/ig;
let result = quoteSample.match(myRegex);

// Match Characters that Occur One or More Times
let difficultSpelling = "Mississippi";
let myRegex = /s+/g;
let result = difficultSpelling.match(myRegex);

// Match Characters that Occur Zero or More Times
let chewieQuote = "Aaaaaaaaaaaaaaaarrrgh!";
let chewieRegex = /Aa*/;
let result = chewieQuote.match(chewieRegex);

// Find Characters with Lazy Matching
// "*" greedy match finds the longest possible part of a string that fits the regex pattern
// "?" lazy match, which finds the smallest possible part of the string that satisfies the regex pattern
let text = "<h1>Winter is coming</h1>";
let myRegex = /<h.*>/;
let result = text.match(myRegex); // <h1>Winter is coming</h1>

let text = "<h1>Winter is coming</h1>";
let myRegex = /<h.*?>/;
let result = text.match(myRegex); // <h1>

// Match Beginning String Patterns
let rickyAndCal = "Cal and Ricky both like racing.";
let calRegex = /^Cal/; 
let result = calRegex.test(rickyAndCal);

// Match Ending String Patterns
let caboose = "The last car on a train is the caboose";
let lastRegex = /caboose$/; 
let result = lastRegex.test(caboose);

// Match All Letters, Numbers and underscore
let quoteSample = "The five boxing wizards jump quickly.";
let alphabetRegexV2 = /\w/g; 
let result = quoteSample.match(alphabetRegexV2).length;

// Match Everything But Letters, Numbers and underscore
let quoteSample = "The five boxing wizards jump quickly.";
let nonAlphabetRegex = /\W/g; 
let result = quoteSample.match(nonAlphabetRegex).length;

// Match All Numbers
let numString = "Your sandwich will be $5.00";
let numRegex = /\d/g; 
let result = numString.match(numRegex).length;

// Match All Non-Numbers
let numString = "Your sandwich will be $5.00";
let noNumRegex = /\D/g; 
let result = numString.match(noNumRegex).length;

// Match Whitespace
let sample = "Whitespace is important in separating words";
let countWhiteSpace = /\s/g; 
let result = sample.match(countWhiteSpace);

//  Match Non-Whitespace Characters
let sample = "Whitespace is important in separating words";
let countNonWhiteSpace = /\S/g; 
let result = sample.match(countNonWhiteSpace);

// Restrict Possible Usernames 
let username = "JackOfAllTrades";
let userCheck = /^[A-Za-z]{2,}\d*$/; 
let result = userCheck.test(username);

// quantity specifiers can specify the lower and upper number of patterns 
let A4 = "aaaah";
let A2 = "aah";
let multipleA = /a{3,5}h/;
multipleA.test(A4); // Returns true
multipleA.test(A2); // Returns false

// Check for All or None
let favWord = "favorite";
let favRegex = /favou?rite/; 
let result = favRegex.test(favWord);

// Positive and Negative Lookahead
// "(?=...)" positive lookahead will look to make sure the element in the search pattern is there, but won't actually match it.
// "(?!...)" negative lookahead will look to make sure the element in the search pattern is not there
let quit = "qu";
let noquit = "qt";
let quRegex= /q(?=u)/;
let qRegex = /q(?!u)/;
quit.match(quRegex); // Returns ["q"]
noquit.match(qRegex); // Returns ["q"]
``` 


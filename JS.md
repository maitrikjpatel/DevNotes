#JS Notes

---

## Good Read

- [The Basics of Object-Oriented JavaScript](http://code.tutsplus.com/tutorials/the-basics-of-object-oriented-javascript--net-7670)

- [JS Best Practice](https://www.thinkful.com/learn/javascript-best-practices-1/)

- [You don't know JS](https://github.com/getify/You-Dont-Know-JS)

- [Resources for Staying on Top of JavaScript](https://code.tutsplus.com/articles/resources-for-staying-on-top-of-javascript--cms-21369)

- [Human Javascript](http://read.humanjavascript.com/ch00-foreword.html)

- [Getting Started JS](http://www.web-crunch.com/really-learn-javascript-series-part-1-getting-started/)

---

### JS Guidelines and Tuts

- [Google JS Styleguide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)

- [Principles of writing consistent, idiomatic JS](https://github.com/rwaldron/idiomatic.js)

- [JQuery Guidelines](http://contribute.jquery.org/style-guide/js/)

- [AngularJS Style Guide](https://github.com/johnpapa/angular-styleguide)

- [JS Video Tuts](https://egghead.io/)

- [JavaScript Regular Expression](http://tutorialzine.com/2014/12/learn-regular-expressions-in-20-minutes/)

- [JS without JQuery](http://tutorialzine.com/2014/06/10-tips-for-writing-javascript-without-jquery/)

---

### JS/Jquery Libraries


- [A tidy repository of jQuery plugins](http://www.unheap.com/mobile/)

- [JQuery Popular plugin lists](http://www.sitepoint.com/jquery-popular-plugins-list/)

- [JS + Hardware](http://www.sitepoint.com/javascript-beyond-web-2014/)

- [JQuery Plugin](http://jquery-plugins.net/)

- [JQuery Boilerplate](http://jqueryboilerplate.com/)

---

### Angular

- [Share Data between controller ](http://crudbetter.com/angular-share-data-between-controllers/ "")

- [Custom Deactives](http://www.toptal.com/angular-js/angular-js-demystifying-directives)

- [component based angularjs directives](https://www.airpair.com/angularjs/posts/component-based-angularjs-directives "")

---


## Javascript Basic

- JS is class less programming language.

- Object Creation Pattern - Encapsulation

- Object Reuse Pattern - Inheritance

#### "While" vs "For" vs "Do/While"


- FOR loops are great for doing the same task over and over when you know ahead of time how many times you'll have to repeat the loop.

- WHILE loops are ideal when you have to loop, but you don't know ahead of time how many times you'll need to loop.

- Sometimes you want to make sure your loop runs at least one time no matter what. When this is the case, you want a modified while loop called a DO/WHILE loop.

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


#### Array

- Learned about heterogenous arrays

		var myArray = [ 23,true,"lol"]

- Learned about multidimensional arrays

		var newArray = [[1,1,1], [1,1,1], [1,1,1]]


- Learned about jagged arrays

		var jagged = [[1,1,1],[1],[1,1]]


#### Object

- Let's go back to the analogy of computer languages being like regular spoken languages. In English, you have nouns (which you can think of as "things") and verbs (which you can think of as "actions"). Until now, our nouns (data, such as numbers, strings, or variables) and verbs (functions) have been separate.

- A constructor, as its name suggests, is designed to create and set up multiple instances of an object. **An object literal** on the other hand is one-off, like string and number literals, and used more often as configuration objects or global singletons (e.g. for namespacing).

-	**Object literal:**

	- Literal notation creates a single object. Literal notation uses **curly brackets { }** and the object's default properties are defined within the brackets using **property:value** notation.

			var objectName = {};

			//---

			var james = {
		    job: "programmer",
		    married: false,
			};

			//---

			var myObject = {
			    iAm : 'an object',
			    whatAmI : function(){
			        alert('I am ' + this.iAm);
			    }
			}

-	**Object constructor:**

	- When we write **bob = new Object( );** we are using a built-in constructor called Object. This constructor is already defined by the JavaScript language and just makes an object with **no properties or methods.**

	- Constructor notation involves defining an object constructor. And like defining a function, we use the function keyword. You can think of this constructor as a "template" from which you can create multiple objects. To create a new object from a constructor, we use the new keyword.

			function myObject(){
					this.iAm = 'an object';
					this.whatAmI = function(){
							alert('I am ' + this.iAm);
					};
			};

			var objectName = new myObject();

			//-----

			function Person(job, married) {
			    this.job = job;
			    this.married = married;
			}

			var gabby = new Person("student",true);


- Differences between constructor and literal

	- The constructor object has its properties and methods defined with the keyword 'this' in front of it, whereas the literal version does not.

	- In the constructor object the properties/methods have their 'values' defined after an equal sign '=' whereas in the literal version, they are defined after a colon ':'.

	- The constructor function can have (optional) semi-colons ';' at the end of each property/method declaration whereas in the literal version if you have more than one property or method, they MUST be separated with a comma ',', and they CANNOT have semi-colons after them, otherwise JavaScript will return an error.

- Bracket Notation : ObjectName["PropertyName"]

	- An advantage of bracket notation is that we are not restricted to just using strings in the brackets. We can also use variables whose values are property names:

			var dog = {
				species: "greyhound",
				weight: 60,
				age: 4
			};

			var species = dog["species"];
			var weight = dog["weight"];
			var ageProp = "age"

			console.log(dog.age);
			console.log(dog[ageProp]);

- Dot Notation : ObjectName.PropertyName

		var bob = {
		  name: "Bob Smith",
		  age: 30
		};

		var name1 = bob.name;
		var age1 = bob.age;

#### Methods

- Functions can only use parameters as an input, but methods can make calculations with object properties.

		var bob = new Object();
		bob.age = 17;
		// this time we have added a method, setAge
		bob.setAge = function (newAge){
		  bob.age = newAge;
		};

		bob.getYearOfBirth = function () {
		  return 2014 - bob.age;
		};
		console.log(bob.getYearOfBirth());

#### JS Closures

- A closure is an inner function that has access to the outer (enclosing) function’s variables—scope chain.
- The closure has three scope chains:
	1. it has access to its own scope (variables defined between its curly brackets),
	2. it has access to the outer function’s variables, and
	3. it has access to the variables.
- Coding Example.

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



#### The "this" Keyword

- The keyword this acts as a placeholder, and will refer to whichever object called that method when the method is actually used.

		var setAge = function (newAge) {
		  this.age = newAge;
		};

		// now we make bob
		var bob = new Object();
		bob.age = 30;
		// and down here we just use the method we already made
		bob.setAge = setAge;

		// change bob's age to 50 here
		bob.setAge(50);


#### Passing Objects into Functions

- Making arrays of Objects, we can use objects as parameters for functions as well. That way, these functions can take advantage of the methods and properties that a certain object type provides.

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

#### Type of

 - We can call typeof thing to figure this out. Generally, the most useful types are "number," "string," "function," and of course, "object."

		var someObject = {someProperty: someValue};
		console.log( typeof someObject );

- We show how to use hasOwnProperty in the last two lines. It returns true or false, based on whether an object has a certain property.

		var myObj = {
		    name : '"lol"'
		};
		console.log( myObj.hasOwnProperty('name') );
		console.log( myObj.hasOwnProperty('nickname') );

#### Getting IN-timate

- To print out all elements and properties, we can use a for/in loop, like this:

		for(var property in dog) {
		  console.log(property);
		}

		// write a for-in loop to print the value of nyc's properties
		for(var x in nyc) {
		  console.log(nyc[x]);
		}

#### Prototype

- What a class has or doesn't have? That is the job of the prototype.
- JavaScript automatically defines the prototype for class with a constructor.
- If you want to add a method to a class such that all members of the class can use it, we use the following syntax to extend the prototype:

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

#### DRY Penguins - Inheritance

- In object-oriented programming, inheritance allows one class to see and use the methods and properties of another class. You can think of it as a child being able to use his or her parent's money because the child inherits the money.

- We will learn more about inheritance as we continue this lesson, but for now let's just refresh our memories about how classes and objec

- **Prototype chain**

	- If JavaScript encounters something it can't find in the current class's methods or properties, it looks up the prototype chain to see if it's defined in a class that it inherits from. This keeps going upwards until it stops all the way at the top: the mighty Object.prototype (more on this later).

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

#### Private Number and Methods

- Just as functions can have local variables which can only be accessed from within that function, objects can have private variables. Private variables are pieces of information you do not want to publicly share, and they can only be directly accessed from within the class.

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


### A Module Pattern

- Module pattern is easily transformed into a powerful constructor pattern.

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

### Pseudoclassical Inheritance

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

### Functional Inheritance

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

### MONAD

- Monad is a design pattern used to describe computations as a series of steps. They are extensively used in pure functional programming languages to manage side effects but can also be used in multiparadigm languages to control complexity.

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

## JS Good Parts

---

### Best Practice

- use UPPERCASE for global variable
- x +=1 instead of x++
- Use JSLint
- Use " for external strings.
- Use ' for internal strings and characters.
- Convert a number to a string
	- Use number’s method (toString)
	- Use String function

			str = num.toString();
			str = String(num);

- Convert a string to a number
	- Use the Number function.
	- Use the + prefix operator.
	- Use the parseInt function.

 		num = Number(str);
 		num = +str;

- Declare all variables at the top of the function.
- Declare all functions before you call them.
- Return statement

		return expression; or return;

	- If there is no expression, then the return value is undefined.
	- Except for constructors, whose default return value is this.

- Tennent’s Principle of Correspondence

		expression
		(function () {
			return expression;
		}())

### Good Part

- Prototype
- Objects
- Only one number type
- Array :  No need to provide a length or type when creating an array.
- Use array.splice(number,1) than delete arry[number] for deleting arry element.
- Use objects when the names are arbitrary strings.
- Use arrays when the names are sequential integers.
- Falsy values : false,  null,  undefined,  "" (empty string),  0,  NaN
- JS is loosely typed language
- It is always better to use === and !==, which do not do type coercion.

### Bad Part

- NaN :  Not a Number , NaN is not equal to anything, including NaN
	- NaN === NaN is false
	- NaN !== NaN is true
-Equal and not equal : These operators can do type coercion  


### Problem

- Problem 1: Write a function that takes an argument and returns that argument.

		function identity(x) {
		 	return x;
		}
		var identity = function identity(x) {
		 	return x;
		};

- Problem 2: Write two binary functions, add and mul, that take two numbers and return their sum and product.

		function add(x, y) {
		 	return x + y;
		}
		function mul(x, y) {
		 	return x * y;
		}

- Problem 3: Write a function that takes an argument and returns a function that returns that argument.

		function identityf(x) {
		 	return function () {
		 		return x;
		 	};
		}

- Problem 4: Write a function that adds from two invocations.

		function addf(x) {
			return fucntion (y) {
				return x + y;
			}
		}

- Problem 5: Write a function that takes a binary function, and makes it callable with two invocations.

		addf = applyf(add);
		addf(3)(4) // 7
		applyf(mul)(5)(6) // 30

		fucntion applyf(binary) {
			return function (x){
				return function (y) {
					return binary(x,y);
				}
			}
		}

- Problem 6: Write a function that takes a function and an argument, and returns a function that can supply a second argument.

		add3 = curry(add, 3);
		add3(4) // 7
		curry(mul, 5)(6) // 30

		function curry(func, first) {
		 	return function (second) {
		 		return func(first, second);
		 	};
		} 		

		function curry(func, first) {
 			return applyf(func)(first);
		}

- Problem 7: Without writing any new functions, show three ways to create the inc function.

		inc = addf(1);
		inc = applyf(add)(1);
		inc = curry(add,1);

- Problem 8: Write methodize, a function that converts a binary function to a method.

		Number.prototype.add = methodize(add);
		(3).add(4) // 7

		function methodize(func) {
		 	return function (y) {
		 		return func(this, y);
		 	};
		}

- Problem 9: Write demethodize, a function that converts a method to a binary function.

		demethodize(Number.prototype.add)(5, 6) // 11

		function demethodize(func) {
			return function (that, y) {
		 		return func.call(that, y);
		 	};
		}

- Write a function twice that takes a binary function and returns a unary function that passes its argument to the binary function twice.

		var double = twice(add);
		double(11) // 22
		var square = twice(mul);
		square(11) // 121

		function twice(binary) {
		 	return function (a) {
		 		return binary(a, a);
		 	};
		}

- Write a function compseu that takes two unary functions and returns a unary function that calls both of them

		composeu(double, square)(3) // 36
		function composeu(f, g) {
		 	return function (a) {
		 		return g(f(a));
		 	};
		}

- Write a function compseb that takes two binary functions and returns a function that calls both of them.

		composeb(add, mul)(2, 3, 5) // 25
		function composeb(f, g) {
 			return function (a, b, c) {
 				return g(f(a, b), c);
 			};
		}

- Problem 13: Write a function that allows another function to only be called once.

		add_once = once(add);
		add_once(3, 4) // 7
		add_once(3, 4) // throw!

		function once(func) {
			return function () {
				var f = func;
			 	func = null;
			 	return f.apply(
			 		this,
			 		arguments
			 	);
			 };
		}

- Problem 14: Write a factory function that returns two functions that implement an up/down counter.

		counter = counterf(10);
		counter.inc() // 11
		counter.dec() // 10

		function counterf(value) {
		 	return {
		 		inc: function () {
		 			value += 1;
		 			return value;
		 		},
		 		dec: function () {
		 			value -= 1;
		 			return value;
		 		}
		 	};
		}

- Problem 15: Make a revocable function that takes a nice function, and returns a revoke

		temp = revocable(alert);
		temp.invoke(7); // alert: 7
		temp.revoke();
		temp.invoke(8); // throw!

		function revocable(nice) {
		 	return {
		 		invoke: function () {
		 			return nice.apply(
		 				this,
		 				arguments
		 			);
		 		},
		 		revoke: function () {
		 			nice = null;
		 		}
		 	};
		} 				

---

## Jquery

---

#### Basic Syntax

- jQuery is a library, or set of helpful add-ons, to the JavaScript programming language. It may seem counterintuitive to learn how to use a library before learning the actual language, but there are a few good reasons for this.

- It takes a while to become comfortable with JavaScript, and it's trickier to manipulate HTML elements directly with JavaScript than with jQuery. In order to help you build awesome websites faster, we're starting you off with jQuery.

- jQuery provides a simple interface for the underlying JavaScript. It's easier for many users to learn jQuery first, then dive into the nitty-gritty JavaScript details later.
- jQuery is much better at giving you immediate, visual results than regular JavaScript. By the end of this lesson, you'll have built your own interactive button!

        $(document).ready(function() {
          $('div').action(howfast);
        });

#### $p vs $('p')

- $p is just a variable name. There is no magic associated with the $ in $p; it's just a convention for saying, "hey, this variable contains a jQuery object." We could call $p anything we want: $paragraph, paragraph, space_cows, whatever! It's just helpful for people reading our code to see $p, since this is a concise way of saying "hey, there's a 'p' jQuery object in here."

        var $div= $('div');
        $p = $("<p>I'm a new paragraph!</p>");

#### 'this' is Important!

- $('div').hide(); won't just hide the div you mouse into; it will hide all the divs on the page. How can we tell jQuery we only want to affect this particular div?
- With this, of course! The this keyword refers to the jQuery object you're currently doing something with. Its complete rules are a little tricky, but the important thing to understand is if you use an event handler on an element—that's the fancy name for actions like .click() and .mouseenter(), since they handle jQuery events—you can call the actual event that occurs (such as fadeOut()) on $(this), and the event will only affect the element you're currently doing something with (for example, clicking on or mousing over).

        $(document).ready(function() {
          $('div').click(function() {
              $(this).fadeOut('slow');
          });
        });

#### Inserting Elements

- .append() inserts the specified element as the last child of the target element. .prepend() inserts the specified element as the first child of the target element.

        $(".info").append("<p>Stuff!</p>");
        $(".info").prepend("<p>Stuff!</p>");

- .appendTo() does the same as .append(), but it just reverses the order of "what to add" and "where to add it." The code has the same effect as the .append() code above. .prependTo() has a similar relationship to .prepend().

        $('<p>Stuff!</p>').appendTo('.info');
        $('<p>Stuff!</p>').pretendTo('.info');

#### Before and After

- We can specify where in the DOM we insert an element with the .before() and .after() functions.

        $(document).ready(function(){
        var $paragraph = $('<p>text goes here</p>');
        $('div#one').after($paragraph);
        $('div#two').after($paragraph);
        });


#### Moving Elements Around

- Moving elements around in the DOM is a snap—all we need to do is use the jQuery functions we just learned on existing elements instead of creating new ones.

        var $paragraph = $("p"); // existing element
        $("div").after($paragraph); // Move it!
        // Same as:
        $("div").after($("p"));

- We can select an element using $("p") and assign it to a variable
- We can move the position in the DOM by using the variable in our after() statement
- Note: This does not copy the element from one location to another, it moves the original element effectively saving you from having to delete the original

        $(document).ready(
          function(){
              $('#one').after("<p>You are my sunshine</p>");
              $('#two').after($('p'));
          }
        );

#### Removing Elements

- we have two jQuery functions, .empty() and .remove(), that help us delete content from our pages

- .empty() deletes an element's content and all its descendants. For instance, if you .empty() an 'ol', you'll also remove all its 'li's and their text.

- .remove(), not only deletes an element's content, but deletes the element itself.

        $('selector').remove();
        $('selector').empty();

#### Adding and Removing Classes

- jQuery includes two functions, .addClass() and .removeClass(), that can be used to add or remove a class from an element.

- You aren't selecting anything, you are modifying your element. This means that you do not need # or . before your class.

        $('selector').addClass('className');
        $('selector').removeClass('className');

#### Toggling Classes

- As you probably guessed, jQuery includes a .toggleClass() function that does exactly this. If the element it's called on has the class it receives as an input, .toggleClass() removes that class; if the target element doesn't have that class, .toggleClass() adds it.

        $('#text').toggleClass()('highlighted');


#### Changing Your Style

- resizing elements is so common, jQuery has specific .height() and .width() functions that can be used to change the heights and widths of HTML elements

        $("div").height("100px");
        $("div").width("50px");

#### Modifying CSS + HTML

- jQuery also includes a general-purpose .css() function that takes two inputs: the first is the CSS element to alter, and the second is the value to set it to.

        $("div").css("background-color","#008800");

- .html() can be used to set the contents of the first element match it finds. For instance, will get the HTML contents of the first div it finds, and will set the contents of the first div it finds to "I love jQuery!"
s
        $('div').html();
        $('div').html("I love jQuery!");

- .val() is used to get the value of form elements. For example, would get the value of the first checked checkbox that jQuery finds.

        $('input:checkbox:checked').val();

#### The .keydown() Event

- The .keydown() event is triggered whenever a key on the keyboard is pressed. It only works on whatever page element has focus, so you'll need to click on the window containing your div before pressing a key in order for you to see its effects.

- Let's go ahead and combine our new event with a new effect: .animate()! We'll use this to move an object on the screen whenever we press a key.

- The .animate() effect takes two inputs: the animation to perform, and the time in which to perform the animation. Here's an example:

        $(document).ready(function() {
          $(document).event(function() {
            $('div').effect(anim, duration);
          });
        });
        //--Example
        $(document).ready(function() {
           $('div').animate({left:'+=10px'},500);
        });

#### jQuery UI

- jQuery UI includes a number of ultra-fancy animations you can use to make your websites do incredible things.

#### Example

- Key Animate

        $(document).ready(function() {
            $(document).keydown(function(key) {
                switch(parseInt(key.which,10)) {
                    // Left arrow key pressed
                    case 37:
                        $('img').animate({left: "-=10px"}, 'fast');
                        break;
                    // Up Arrow Pressed
                    case 38:
                        $('img').animate({top: "-=10px"},'fast');
                        break;
                    // Right Arrow Pressed
                    case 39:
                        $('img').animate({left: "+=10px"}, 'fast');
                        break;
                    // Down Array Pressed
                    case 40:
                        $('img').animate({top: "+=10px"}, 'fast');
                        break;
                }
            });
        });

---

## Author

- Maitrik Patel || maitrikpatel.com || maitrik1419[at]gmail[dot]com

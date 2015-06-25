#JS Tips

---


####"While" vs "For" vs "Do/While"


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


####Array

- Learned about heterogenous arrays

		var myArray = [ 23,true,"lol"]

- Learned about multidimensional arrays

		var newArray = [[1,1,1], [1,1,1], [1,1,1]]


- Learned about jagged arrays

		var jagged = [[1,1,1],[1],[1,1]]


####Object

- Let's go back to the analogy of computer languages being like regular spoken languages. In English, you have nouns (which you can think of as "things") and verbs (which you can think of as "actions"). Until now, our nouns (data, such as numbers, strings, or variables) and verbs (functions) have been separate.

- JS is class less programming language.

- Object Creation Pattern - Encapsulation

- Object Reuse Pattern - Inheritance

		var myObject = {};

		myObject.name = 'Maitrik';
		myObject["job"] = 'SapientNitro'
		myObject.number = '(555) 555-5555';
		myObject.phone = function() {
		  console.log('Calling ' + this.name + ' at ' + this.number + 'who works at' + this.job);
		};

		myObject.phone();

- A constructor, as its name suggests, is designed to create and set up multiple instances of an object. **An object literal** on the other hand is one-off, like string and number literals, and used more often as configuration objects or global singletons (e.g. for namespacing).

-	Object literal:

	- Literal notation creates a single object. Literal notation uses **curly brackets { }** and the object's default properties are defined within the brackets using **property:value** notation.

			var objectName = {};
			//---
			var james = {
		    job: "programmer",
		    married: false,
			};

-	Object constructor:

	- When we write **bob = new Object( );** we are using a built-in constructor called Object. This constructor is already defined by the JavaScript language and just makes an object with **no properties or methods.**

	- Constructor notation involves defining an object constructor. And like defining a function, we use the function keyword. You can think of this constructor as a "template" from which you can create multiple objects. To create a new object from a constructor, we use the new keyword.

			var objectName = new Object();
			//-----
			function Person(job, married) {
			    this.job = job;
			    this.married = married;
			}
			var gabby = new Person("student",true);

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

####Methods

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

####JS Closures

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
		
		//This is bad.
		var myName = showName("Maitrik");// At this juncture, the celebrityName outer function has returned.​
		// The closure (lastName) is called here after the outer function has returned above​
		​// Yet, the closure still has access to the outer function's variables and parameter​
		
		mjName ("Jackson"); // This celebrity is Michael Jackson  
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
		


####The "this" Keyword

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


####Passing Objects into Functions

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

####Type of

 - We can call typeof thing to figure this out. Generally, the most useful types are "number," "string," "function," and of course, "object."

		var someObject = {someProperty: someValue};
		console.log( typeof someObject );

- We show how to use hasOwnProperty in the last two lines. It returns true or false, based on whether an object has a certain property.

		var myObj = {
		    name : '"lol"'
		};
		console.log( myObj.hasOwnProperty('name') );
		console.log( myObj.hasOwnProperty('nickname') );

####Getting IN-timate

- To print out all elements and properties, we can use a for/in loop, like this:

		for(var property in dog) {
		  console.log(property);
		}

		// write a for-in loop to print the value of nyc's properties
		for(var x in nyc) {
		  console.log(nyc[x]);
		}

####Prototype

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

####DRY Penguins - Inheritance

- In object-oriented programming, inheritance allows one class to see and use the methods and properties of another class. You can think of it as a child being able to use his or her parent's money because the child inherits the money.

- We will learn more about inheritance as we continue this lesson, but for now let's just refresh our memories about how classes and objects work.

- #####Prototype chain

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

####Private Number and Methods

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

- [OOP JS TUTS](http://code.tutsplus.com/tutorials/the-basics-of-object-oriented-javascript--net-7670)
- [JS Best Practice](https://www.thinkful.com/learn/javascript-best-practices-1/)
 

---
##Author

- Maitrik Patel
- maitrikpatel.com
- maitrik1419[at]gmail[dot]com

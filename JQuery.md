---
date:  "2015-05-28T22:40:32.169Z"
publish: "true" 
category: "note"
author: "Maitrik Patel"

title: "Jquery"
description: "Description Here"

role: "tools, development"

source: "Github"
postColor: "#440000"
---

## Jquery Libraries


- [A tidy repository of jQuery plugins](http://www.unheap.com/mobile/)

- [JQuery Popular plugin lists](http://www.sitepoint.com/jquery-popular-plugins-list/)

- [JS + Hardware](http://www.sitepoint.com/javascript-beyond-web-2014/)

- [JQuery Plugin](http://jquery-plugins.net/)

- [JQuery Boilerplate](http://jqueryboilerplate.com/)

## Jquery



## Jquery

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

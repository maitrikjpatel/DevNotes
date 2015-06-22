#Famo.us note

Famo.us is an open source technology for building
high-performing JavaScript Web and mobile applications without requiring native code or plug-ins. Following are my finding which I learn during private beta program at Famo.us HQ. 

---

##Famous FrameWork

---
### 1. context

-   context, the container for the Famous display environment.
-   Famous engine using require and then create our main context from
    the engine.

<!-- -->

            define(function(require, exports, module) {
                var Engine = require('famous/core/Engine');
                // The context holds the root node of our render tree.ca
                var mainContext = Engine.createContext();
            }); 

---
### 2. surface

-   Surface === DIV .
-   Import the Surface class using require and then create a surface
    instance, passing in an options object.
-   Surface Content :  String, an HTML text string, or a document
    fragment.
-   Surface Size :   size of our surface,  the css classes, and  in-line
    css properties.

<!-- -->

            define(function(require, exports, module) {
                var Engine = require("famous/core/Engine");
                var Surface = require("famous/core/Surface");
                var mainContext = Engine.createContext();
                //It's famous's core renderable
                var testSurface = new Surface({
                    size: [200, 80],
                    content: "Your Name",
                    classes: ["test"],
                    properties: {
                        backgroundColor: 'blue',
                        fontSize: '16px'
                    }
                });
                // Attach the surface to the context.
                mainContext.add(testSurface);
            });

---
### 3. Modifier

-   Surface gets positioned in the top-left corner of the context as
    default origin [ 0,0].
-   Position the surface : Modifier object  for change origin +
    translation.
-   Origin  :  [X,Y] ,  [0,0]  - \> Top-Left,  [0.5,0.5]  -\> Center,
    [1,1] -\> Bottom-Right
-   Transform.translate( x, y , z )  :  The x, y, and z translations in
    pixels.

<!-- -->

         define(function(require, exports, module) {                        
                var Engine = require("famous/core/Engine");
                var Surface = require("famous/core/Surface");
                var Modifier = require("famous/core/Modifier");
                var Transform = require("famous/core/Transform");
                var mainContext = Engine.createContext();
                var testSurface = new Surface({...});

           // A transform is an object that modifies any renderables it precedes
           // by changing its origin, opacity, or size.
                var modifier = new Modifier({
                    origin: [0.5, 0.5],
                    transform: Transform.translate(0, 100, 0)
                });             mainContext.add(modifier).add(testSurface);
            });

---
### 4. EVENTS

-   .on() method to listen for events and trigger a callback.
-   Events  : Click, touch, wheel, and other standard DOM events.

<!-- -->

            define(function(require, exports, module) {            
                var Engine = require("famous/core/Engine");    
                var Surface = require("famous/core/Surface");
                var Modifier = require("famous/core/Modifier");
                var Transform = require("famous/core/Transform");
                var mainContext = Engine.createContext();
                var testSurface = new Surface({...})
                testSurface.on('click', function(e) {
                    alert("that feels like a surface click");
                });          
            mainContext.add(modifier).add(testSurface);
            });

---
### 5. Transitions

-   Perform animations at 60fps.
-   Modifier.setTransform(1st Argument, 2nd Argument) to move our
    surface.
-   1st Argument : Where to move the surface
-   2nd Argument : Transition object that defines the animation
    properties

<!-- -->

          define(function(require, exports, module) {            
                var Engine = require("famous/core/Engine");
                Var Surface = require("famous/core/Surface");
                var Modifier = require("famous/core/Modifier");
                var Transform = require("famous/core/Transform");
                var mainContext = Engine.createContext();
                var testSurface = new Surface({...});
                var modifier = new Modifier({...}); 
                testSurface.on('click', function(e) {
                // Animation duration of 1000ms with an easeOut curve
                    var transition = {
                        duration: 1000,
                        curve: 'easeOut'
                    };
                // Moves the surface back to its origin
                    modifier.setTransform(Transform.translate(0, 0, 0), transition);
                });
                mainContext.add(modifier).add(testSurface);
            });

---
### 6. Chaining and Physics Transitions

-   .setTransform(), pass in a callback function as a third argument.
-   Modifier.setTransform(1st Argument, 2nd Argument, 3rd Argument)
-   3rd Argument gets executed once the transition completes.

<!-- -->

          define(function(require, exports, module) {            
                var Engine = require("famous/core/Engine");
                Var Surface = require("famous/core/Surface");
                var Modifier = require("famous/core/Modifier");
                var Transform = require("famous/core/Transform");
                var Transitionable = require("famous/transitions/Transitionable");
                var SpringTransition = require("famous/transitions/SpringTransition") 
                var mainContext = Engine.createContext(); 
                // Register the spring transition
                Transitionable.registerMethod('spring', SpringTransition);                
                var testSurface = new Surface({...});
                var modifier = new Modifier({...}); 
                testSurface.on('click', function(e) {
                // Animation duration of 1000ms with an easeOut curve
                    var transition = {
                        duration: 1000,
                        curve: 'easeOut'
                    };
                var spring = {
                        method: 'spring',
                        period: 400,
                        dampingRatio: 0.3
                    };

                modifier.setTransform(Transform.translate(0, 0, 0), transition,
                function() { modifier.setTransform(
                   Transform.move(Transform.rotateY(Math.PI/3), [0, 0, 200]), spring);
                });
                });
            }); 

* * * * *

Famous File/FRamework Structure
-------------------------------

``` {.tree}
    timbre-tutorial
    ├── css
    ├── img
    │   ├── band.png
    │   ├── body.png
    │   ├── hamburger.png
    │   ├── icon.png
    │   ├── search.png
    │   └── strip-icons
    │       ├── friends.png
    │       ├── search.png
    │       ├── settings.png
    │       └── starred.png
    ├── index.html
    ├── js/src
        ├── app
        │   ├── AppView.js
        │   ├── HeaderView.js
        │   ├── MenuView.js
        │   ├── MyView.js
        │   ├── PageView.js
        │   └── StripView.js
        ├── [famous modules]
        ├── [lib]    
        └── main.js
```

* * * * *

Brief on submodule
------------------

-   Alternative of grunt
-   Clonegit@github.com:FamousPrivateBeta/timbre-tutorial-newBase.git
-   run git submodule update --init
-   Goto src/famous folder and run git submodule update
-   [Example to explain submodule](https://github.com/FamousPrivateBeta)
-   [More about
    Submodule](http://git-scm.com/book/en/Git-Tools-Submodules)

<!-- -->

    ├── famous/
    │   ├── famous-input
    │   ├── famous-math
    │   ├── famous-modifiers
    │   ├── famous-physics
    │   ├── famous-surfaces
    │   ├── famous-transitions
    │   ├── famous-utilities
    │   ├── famous-views
    │   ├── famous-widgets
    ├── lib/
    ├── app/
    └── main.js

* * * * *

Advantage
---------

-   Everything is in DOM. JS, HTML, CSS. No plugins or app downloads
-   Makes use of WebGL power
-   Light weight. The entire library has 355k, but with require.js, the
    developers can include only the modules they need. It can get as low
    as 65k1.
-   60 fps
-   Easy learning curve.

* * * * *

Disadvantage
------------

-   Tiny issues in Internet Explorer.
-   Internet Explorer has a couple of bugs with preserve-3D, 
-   but Famo.us and Microsoft are working together to get that fixed.
-   Difficult to tweak using Dev Tools
-   Difficult to pass on knowledge of existing project
-   Still has bugs

* * * * *

Resource
--------

-   [Vimeo Channel ](https://vimeo.com/famousindustries)
-   [Famous University](http://launch.famo.us/)
-   [Famous Forum ](https://forum.famo.us/t/welcome-to-famo-us/19/last)
-   [Getting started at
    famo.us](https://github.com/Famous/internal/wiki/Getting-started-at-famo.us)
-   [Creating a new
    project](https://github.com/Famous/internal/wiki/Creating-a-new-project)
-   [Githow](https://github.com/Famous/internal/wiki/Githowto)
-   [Famo.us-Angular](http://thomasstreet.com/blog/famous-angular/2014/04/28/famous-angular.html)

I personally feel that, famous is sandbox like Flash or AS3. Famo.us
promises significantly better performance than standard mobile websites,
it's more flexible for UI development than normal HTML5. It is simpler
for developers to use than native code. I see great potential in Famo.us
in future run. 

---
##Author

- Maitrik Patel
- maitrikpatel.com
- maitrik1419[at]gmail[dot]com

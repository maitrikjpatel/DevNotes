---
title: "React Notes"
publish: "true"
author: "Maitrik Patel"
tags: "tools, development"
category: "note"
---

## Learning Articles
  - [React Setup Articles](https://www.codecademy.com/articles/react-setup-i)
  - [JS React](https://jscomplete.com/repl)
  - [JS basics refresh](https://jscomplete.com/learn-javascript)

## Notes

### Intro

- It is JS library not framework.
- Declarative
- MVC - Only View
- Three main reasons

  - Components | functions, reusable, manage private states
  - Reactive updates | reach will react , take updates to brwosers
  - Virtual views in memory | html in JS

- Two type of Components

  - Function Components - Use JSX
  - Class Components - Virtual

### Codecademy - REACT-1

- Use **require** and **module.exports** to access one file from another
- A React app is basically just a lot of components, setting **state** and passing **props** to one another.

#### JSX

  - JSX is a syntax extension for JavaScript. It was written to be used with React. JSX code looks a lot like HTML.
  - There's a rule that we haven't mentioned: a JSX expression must have exactly one outermost element.
  - class become className
  - you have to include the slash in end of tag. If you write a self-closing tag in JSX and forget the slash, you will raise an error.<br>

  - Wrapping your code in curly braces between JSX tags, treat it like ordinary JavaScript and not like JSX.

        var theBestString = 'tralalalala i am da best';
        var judgmental = Math.random() < 0.5;
        var math = (
            <h1>
            2 + 3 = {2 + 3}
            </h1>
        );
        var JSKIf = (
            <h1>
                { if (purchase.complete) 'Thank you for placing an order!' }
            </h1>
        );
        function myfunction (e) {

        ReactDOM.render(
            <h1>{2 + 3}</h1>,
            <h1 className="big">{2 + 3}</h1>,
            <h1>{theBestString}</h1>,
            <h1 onClick={myfunction} >Click Here</h1>,
            { !judgmental && <h1>Nacho Cheez Straight Out The Jar</h1> }
            math,
            document.getElementById('app')
        );

#### React Component

  - React.Component is an abstract base class, so it rarely makes sense to refer to React.Component directly.
  - Instead, you will typically subclass it, and define at least a render() method.

        var React = require('react');
        var ReactDOM = require('react-dom');

        var Button = React.createClass({
        scream: function () {
            alert('AAAAAAAAHHH!!!!!');
        },
        name : "Ths is button",

        render: function () {
            return <button onClick={this.scream}>{this.name}</button>;
        }
        });

        ReactDOM.render (
        <Button />,
        document.getElementById('app')
        );

#### Props

  - Every component has something called props
  - A component's props is an object. It holds information about that component.
  - To see a component's props object, you use the expression this.props
  - props (short for properties) are a Component's configuration, its options if you may. They are received from above and immutable as far as the Component receiving them is concerned.
  - A Component cannot change its props, but it is responsible for putting together the props of its child Components.

#### State

  - The state starts with a default value when a Component mounts and then suffers from mutations in time (mostly generated from user events). It's a serializable* representation of one point in time--a snapshot.
  - React components will often need dynamic information in order to render.
  - There are two ways for a component to get dynamic information: props and state. Besides props and state, everything in a component should always stay exactly the same.
  - Unlike props, a component's state is not passed in from the outside. A component decides its own state
  - you can't call "this.setState" from inside of the "render" function! "this.setState" automatically calls "render". If "render" calls "this.setState", you will create an infinite loop.
  
        var React = require('react');
        var ReactDOM = require('react-dom');

        var green = '#39D1B4';
        var yellow = '#FFD712';

        var Toggle = React.createClass({
        getInitialState: function () {
            return { color: green };
        },

        changeColor: function () {
            var color = this.state.color == green ? yellow : green;
            this.setState({ color: color });
        },

        render: function () {
            return (
            <div style={{background: this.state.color}}>
                <h1>
                Change my color
                </h1>
                <button onClick={this.changeColor}>
                Change color
                </button>
            </div>
            );
        }
        });

        ReactDOM.render(
        <Toggle />,
        document.getElementById('app')
        );

#### Prop vs State

  - props and state both hold information relating to the component, they are used differently and should be kept separate.
  - "props" is short for "properties" so nothing particularly fancy there.
  - props should not change
  - props contains information set by the parent component (although defaults can be set) and should not be changed.
  - props are a way of passing data from parent to child. ...
  - state contains "private" information for the component to initialise, change, and use on it's own.
  - State is reserved only for interactivity, that is, data that changes over time.

### Codecademy - REACT-2 - Programming Patterns

#### Stateless Components Inherit From Stateful Components

##### Pattern 1 : A stateful component passes its state down to a stateless component.

  - Stateful <Parent /> passes a prop to stateless <Child />.
  - A stateful component class stores information as state.
  - A stateless component class displays that state.
  - A different stateless component class displays a way to change that state.

##### Pattern 2 : The stateless, child component will update the state of the parent component.

  - A stateful, parent component passes down an event handler to a stateless, child component.
  - The child component then uses that event handler to update its parent's state.

##### Pattern 3 : You will have one stateless component display information, and a differenstateless component offer the ability to change that information.**

  - An instance of the stateful component class is rendered. 
  - One stateless child component displays the `state`, and a different stateless child component displays a way to change the stateful component 
  - Files

  - `Stateful / Parent.js`

        var React = require('react');
        var ReactDOM = require('react-dom');
        var Child = require('./Child');
        var Sibling = require('./Sibling');

        var Parent = React.createClass({
          getInitialState: function () {
            return { name: 'Frarthur' };
          },
          
          changeName: function (newName) {
            this.setState({
              name: newName
            });
          },

          render: function () {
            return (
              <div>
                <Child onChange={this.changeName} />
                <Sibling name={this.state.name} />
              </div>
            );
          }
        });

        ReactDOM.render(
          <Parent />,
          document.getElementById('app')
        );

  - `Stateless / Child.js`

        var React = require('react');

        var Child = React.createClass({
          handleChange: function (e) {
            var name = e.target.value;
            this.props.onChange(name);
          },
          
          render: function () {
            return (
              <div>
                <select 
                  id="great-names" 
                  onChange={this.handleChange}>
                  
                  <option value="Frarthur">Frarthur</option>
                  <option value="Gromulus">Gromulus</option>
                  <option value="Thinkpiece">Thinkpiece</option>
                </select>
              </div>
            );
          }
        });

        module.exports = Child;

  - `Stateless / Sibling.js`

        var React = require('react');

        var Sibling = React.createClass({
          render: function () {
            var name = this.props.name;
            return (
              <div>
                <h1>Hey, my name is {name}!</h1>
                <h2>Don't you think {name} is the prettiest name ever?</h2>
                <h2>Sure am glad that my parents picked {name}!</h2>
              </div>
            );
          }
        });

        module.exports = Sibling;

#### Advance React

##### Pattern 4 : Inline Styles, dividing components into presentational components and containecomponents.**

  - `<h1 style={{ color: 'red' }}>Hello world</h1>`
  - The outer curly braces inject JavaScript into JSX. They say, "everything between us should be read as JavaScript, not JSX."
  - The inner curly braces create a JavaScript object literal. They make this a valid JavaScript object
  - Nicer approach is to store a style object in a variable, and then inject that variable into JSX.
  - Normally Style names are written in hyphenated-lowercase but in React, those same names are instead written in camelCase. `backgroundColor: "green"`
  - A style value as a number, then the unit "px" is assumed. `fontSize: 50`

  - `Style file / style.js`

        var blue  = 'rgb(139, 157, 195)';
        var darkBlue  = 'rgb(059, 089, 152)';
        var lightBlue = 'rgb(223, 227, 238)';
        var grey      = 'rgb(247, 247, 247)';
        var white     = 'rgb(255, 255, 255)';
        var fontSize   = '4em';

        module.exports = {
          blue: blue,
          darkBlue: darkBlue,
          lightBlue: lightBlue,
          grey: grey,
          white: white,
          fontSize:   fontSize
        };

  - `Stateless / Sibling.js`

        var React = require('react');
        var ReactDOM = require('react-dom');
        var styles = require('./facebookStyles');

        var divStyle = {
          backgroundColor: styles.darkBlue,
          color:           styles.white,
          fontSize:           styles.fontSize
        };

        var Wow = React.createClass({
          render: function () {
            return (
              <div style={divStyle}>
                Wow, I stole these colors from Facebook!
              </div>
            );
          }
        });

        ReactDOM.render(
          <Wow />, 
          document.getElementById('app')
        );


##### Pattern 5 : Separating presentational components from display components.

  - Separating container components from presentational components is a popular React programming pattern.
  - If a component has to have state, make calculations based on props, or manage any other complex logic, then that component shouldn't also have to render HTML-like JSX.
  - Following this pattern separates your business logic from your presentational logic.
  - HTML code in presentational component component file and Export by exports in end.
  - Business logic in container file and import component by require on top.  
  - When you separate a container component from a presentational component, the presentational component will always end up with `one render function`, and no other properties.
  - A container does data fetching and then renders its corresponding sub-component. That’s it.


- **Stateless functional components**
  - If you have a component class with nothing but a render function, then you can rewrite that component class in a very different way. 
  - Instead of using React.createClass, you can write it as JavaScript function!

        // Normal way to display a prop:
        var MyComponentClass = React.createClass({
          render: function () {
            return <h1>{this.props.title}</h1>;
          }
        });

        // Stateless functional component way to display a prop:
        function MyComponentClass (props) {
          return <h1>{props.title}</h1>;
        }

##### propTypes
  - propTypes are useful for two reasons
    - **Prop validation** : Validation can ensure that your props are doing what they're supposed to be doing. If props are missing, or if they're present but they aren't what you're expecting, then a warning will print in the console. 
    - **Documentation** : Documenting props makes it easier to glance at a file and quickly understand the component class inside. When you have a lot of files, and you will, this can be a huge benefit.
    
          var React = require('react');

          var MessageDisplayer = React.createClass({
            // This propTypes object should have
            // one property for each expected prop:
            propTypes: {
              message: React.PropTypes.string
            },

            render: function () {
              return <h1>{this.props.message}</h1>;
            }
          });

##### Forms
  - A traditional form doesn't update the server until a user hits "submit." 
  - **Controlled component** : An uncontrolled component is a component that maintains its own internal state. 
  - **Uncontrolled component** : A controlled component is a component that does not maintain any internal state. 

        var React = require('react');
        var ReactDOM = require('react-dom');

        var Input = React.createClass({
          
          getInitialState: function () {
            return {
              userInput: ''
            };
          },
          
          handleUserInput: function (e) {
            this.setState({
              userInput: e.target.value
            });
          },
          
          render: function () {
            return (
              <div>
                <input 
                  type="text" 
                  onChange={this.handleUserInput}
                  value={this.state.userInput}
                />
                <h1>{this.state.userInput}</h1>
              </div>
            );
          }
        });

        ReactDOM.render(
          <Input />,
          document.getElementById('app')
        );

#### Lifestyle methods

  - Lifecycle methods are methods that get called at certain moments in a component's life.
  - Lifecycle method can get called at :
    - Right before a component renders for the first time.
    - Right after a component renders, every time except for the first time.
    - At different moments in a component's life.

##### Mounting lifecycle methods

  - When a component mounts, Mounting lifecycle method automatically calls these three methods :
    1. ComponentWillMount
    2. Render
    3. ComponentDidMount
  - If you need to do something only the first time that a component renders, then it's probably a job for a mounting lifecycle method!

        var React = require('react');
        var ReactDOM = require('react-dom');

        var Flashy = React.createClass({
          componentWillMount: function () {
            alert('AND NOW, FOR THE FIRST TIME EVER...  FLASHY!!!!');
          },
          
          componentDidMount: function () {
            alert('YOU JUST WITNESSED THE DEBUT OF...  FLASHY!!!!!!!');
          },

          render: function () {

            alert('Flashy is rendering!');
            return (
              <h1 style={{ color: this.props.color }}>
                OOH LA LA LOOK AT ME I AM THE FLASHIEST
              </h1>
            );
          }

        });

        ReactDOM.render(
          <Flashy color='red' />,
          document.getElementById('app')
        );

        setTimeout(function () {
          ReactDOM.render(
            <Flashy color='green' />,
            document.getElementById('app')
          );
        }, 2000);

##### Updating lifecycle methods
  - The first time that a component instance renders, it does not update. 
  - A component updates every time that it renders, starting with the second render.
  - There are five updating lifecycle methods:
    1. componentWillReceiveProps
    2. shouldComponentUpdate
    3. componentWillUpdate
    4. render
    5. componentDidUpdate

##### Unmounting lifecycle methods
  - componentWillUnmount gets called right before a component is removed from the DOM. 

        var React = require('react');

        var Enthused = React.createClass({
          interval: null,

          componentDidMount: function () {
            this.interval = setInterval(function(){
              this.props.addText('!');
            }.bind(this), 15);
          },
          componentWillUnmount: function (prevProps, prevState) {
            clearInterval(this.interval);
          },
          render: function () {
            return (
              <button onClick={this.props.toggle}>
                Stop!
              </button>
            );
          }
        });

        module.exports = Enthused;
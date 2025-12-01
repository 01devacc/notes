# notes

Objects can be defined using object literal syntax.

<details>
	<summary>Object literal syntax</summary>

```javascript  
const myObject = {
  property: 'Value!',
  otherProperty: 77,
  "obnoxious property": function() {
    // do stuff!
};
}
```
</details>
<br>  

There are 2 ways to get information out of an object:

<details>
  <summary>Methods to get object values</summary>

```javascript
// dot notation - NOTE: does not work with strings that have spaces or variables
myObject.property; // 'Value!'

// bracket notation
myObject["obnoxious property"]; // [Function]
```
</details>
<br> 

If you want to make multiple similar objects using a template you can create an object constructor (which is a function):

<details>
  <summary>Constructor/ object template</summary>

```javascript
function Player(name, marker) {
  this.name = name;
  this.marker = marker;
}
```
</details>
<br>

The keyword **this** is used to reference to the object that is executing the current running function.

<details>
  <summary>Examples explaining this</summary>

```javascript
function test() {
  console.log(this)
}

test() // returns the window object because test() is being executed from global scope.

cont user = {
  name: "Bob",
  checker: function() {
    console.log(this)
  }
}

user.checker() // returns the user object because checker() is being executed from the user object. NOTE: does not work with arrow functions.
```
</details>
<br>

You can use an object constructor by calling the function with the keyword **new**:

<details>
  <summary>Making an object with constructor</summary>

```javascript
const player = new Player('steve', 'X');
console.log(player.name); // 'steve'
// The new keyword will make a new object instance using that constructor.
```
</details>
<br> 

To prevent calling a constructor without the **new** keyword we can use the **new.target** meta property:

<details>
  <summary>Safeguarding constructors</summary>

```javascript
function Player(name, marker) {
  if (!new.target) {
    throw Error("You must use the 'new' operator to call the constructor");
  }
  this.name = name;
  this.marker = marker;
  this.sayName = function() {
    console.log(this.name)
  };
}
// Without the throw error, you could accidentally not make a new object but rather add properties/functions to the global object or do something weird as 'this' in 'this.name' for example could point to the global object instead of the desired object.
// 
```
</details>
<br> 

All objects in javascript have a prototype.
A prototype is another object that the original inherits from i.e. the original object has access to all of the prototype's methods and properties.
We can define properties and functions common among all objects on the prototype to save memory.

<details>
  <summary>How to use prototypes</summary>

```javascript
// Making an object constructor.
function Book(title, author, pages, read) {
    this.title = title;
    this.author = author;
    this.pages = pages;
    this.read = read;
}

// Adding method to prototype so all Book objects can share it and save memory.
Book.prototype.info = function() {
    return `${this.title} by ${this.author}, ${this.pages} pages, ${this.read}`
}

console.log(theHobbit.info()); //'The Hobbit by J.R.R. Tolkien, 295 pages, not read yet'
```
</details>
<br> 



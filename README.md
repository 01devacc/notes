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
  <summary>Methods</summary>

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



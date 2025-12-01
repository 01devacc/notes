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

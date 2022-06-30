## ES6
ReactJS uses `ES6`.  `ES6` stands for `ECMAScript 6`, also known as `ECMAScript 2015`. ES6 was created to standardize Javascript, and was published in 2016 by [Ecma International](https://en.wikipedia.org/wiki/Ecma_International)

Some features of ES6 include the following:

- Classes
- Arrow Functions
- Variables
- Array Methods
- Destructuring
- Modules
- Ternary Operator
- Spread Operator

# Classes
### _A Simple Example_
Below is a simple example of a class (take careful note of the comments within the code, these will guide you). In your project directory where `App.js` file is found, create a new JS file, `Car.js`. Then add the following code:
```js
class Car {
    // This is how to declare a constructor
    constructor(name) {
      this.brand = name;
    }

    // This is a method of the class. 
    // It is called like a function on the class instance
    showBrand(){
        return this.brand;
    }
  }
  
// Export the default object for this JS file
export default Car;
```

Now go back to your `App.js` file that you edited previously, and overwrite the contents with this code:

```js
// import the Car class we created previously
import Car from './Car'

function App() {

  // Declare a Car insance
  const myCar = new Car("Ford");

  return (
    <div className="App">
      {/* Display car brand here */}
      <h1>This is my car: {myCar.showBrand()} </h1>
    </div>
  );
}

export default App;
```
Your browser should now refresh, display the brand of the Car instance we created.

### _Class Inheritance_
To create a class inheritance, use the `extends` keyword. Replace the previous code of the `Car.js` with the following:
```js
class Car {
    // This is how to declare a constructor
    constructor(name) {
      this.brand = name;
    }

    // This is a method of the class. 
    // It is called like a function on the class instance
    showBrand(){
        return this.brand;
    }
  }
  

// This is the inherited class of Car
export class Model extends Car {
  constructor(name, model) {
    // The super() method refers to the parent class.
    // By calling the super() method in the constructor method,
    // we call the parent's constructor method and gets access 
    // to the parent's properties and methods
    super(name);
    this.model = model;
  }  
  // This is the new method of the Model class.  
  // 'showBrand', the other method of Car, still exists
  showModel() {
      return this.model
  }
}

// Export the default object for this JS file
export default Car;
```
Once again, replace the contents of `App.js` with this code:
```js
// import the Model class we created previously
import { Model } from './Car' 

function App() {

  // Declare a Model instance
  const myCarModel = new Model("Ford","Mustang");

  return (
    <div className="App">
      {/* Display car brand here */}
      <h1>This is my car: {myCarModel.showBrand() + ' ' + myCarModel.showModel()} </h1>
    </div>
  );
}

export default App;
```
# Arrow Functions
Arrow functions allow us to write shorter function syntax.
#### _original_
```js
hello = function() {
  return "Hello World!";
}
```
#### _arrow functions_
```js
hello = () => {
  return "Hello World!";
}
```
#### _shorter_  
_If function has only one statement and returns a value_
```js
hello = () => "Hello World!";
```
#### _with parameters_  
```js
hello = (val) => "Hello "+val;
```
#### _with parameters (even shorter)_ 
_you can remove the parenthisis of the function_
```js
hello = val => "Hello " + val;
```
# Variables
With ES6, there are three ways of defining your variables: `var`, `let`, and `const`. Before we proceed, let us define the variable scopes.

Global Scope
`Variables declared Globally (outside any function) have Global Scope`

Function Scope
`Variables defined inside a function are not accessible (visible) from outside the function.
`

Block Scope
`Variables declared inside a { } block cannot be accessed from outside the block`

| Variable  | Global Scope   | Function Scope  | Block Scope  | Remarks  |
|---|---|---|---|---|
| var  | YES  | YES  |  NO | Original way of defining JS variables
| let  |  YES | YES  |  YES | Value can be changed
| const  | YES  | YES  |  YES | Value can't be changed

The keyword `const` does not define a constant value. It defines a constant reference to a value.

Because of this you can NOT:
- Reassign a constant value
- Reassign a constant array
- Reassign a constant object

But you can:
- Change the elements of constant array
- Change the properties of constant object

### _Examples_
**Global Scope**
_var_
```js
var carName = "Volvo";
// code here can use carName

function myFunction() {
// code here can also use carName
}
```
_let_
```js
let carName = "Volvo";
// code here can use carName

function myFunction() {
// code here can also use carName
}
```
_const_
```js
const carName = "Volvo";
// code here can use carName

function myFunction() {
// code here can also use carName
}
```

**Function Scope**
_var_
```js
// code here can NOT use carName

function myFunction() {
  var carName = "Volvo";
  // code here CAN use carName
}

// code here can NOT use carName
```
_let_
```js
// code here can NOT use carName

function myFunction() {
  let carName = "Volvo";
  // code here CAN use carName
}

// code here can NOT use carName
```
_const_
```js
// code here can NOT use carName

function myFunction() {
  const carName = "Volvo";
  // code here CAN use carName
}

// code here can NOT use carName
```
**Block Scope**
_var_
```js
{
  var x = 2;
}
// x CAN be used here
```

_let_
```js
{
  let x = 2;
}
// x can NOT be used here
```
_const_
```js
{
  const x = 2;
}
// x can NOT be used here
```

# Array Methods
In React, map() can be used to generate lists.

The `.map()` method allows you to run a function on each item in the array, returning a new array as the result.

In your `App.js`, replace the code with the following:

```js
function App() {
  // Declare your array
  const myArray = ['apple', 'banana', 'orange'];

  // Make each member of the array part of a <p> element
  const myList = myArray.map((item) => <p>{item}</p>)

  return (
    <div className="App">
      {/* Display mapped elements */}
      {myList}
    </div>
  );
}

export default App;
```
In your browser you should see something like this:

```
apple
banana
orange
```

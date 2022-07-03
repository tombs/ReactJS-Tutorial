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

# Destructing
Destructuring is a method used to take out sections of data from an array or objects, which can be assigned to new variables.

**Destructuring Arrays**
Before
```js
const vehicles = ['mustang', 'f-150', 'expedition'];

// old way
const car = vehicles[0];
const truck = vehicles[1];
const suv = vehicles[2];
```
With destructuring
```js
const vehicles = ['mustang', 'f-150', 'expedition'];

const [car, truck, suv] = vehicles;
```


> _NOTE: When destructuring arrays, the order that variables are declared is important._

**Destructuring Objects**
Before
```js
const vehicleOne = {
  brand: 'Ford',
  model: 'Mustang',
  type: 'car',
  year: 2021, 
  color: 'red'
}

myVehicle(vehicleOne);

// old way
function myVehicle(vehicle) {
  const message = 'My ' + vehicle.type + ' is a ' + vehicle.color + ' ' + vehicle.brand + ' ' + vehicle.model + '.';
}
```
With destructuring
```js
const vehicleOne = {
  brand: 'Ford',
  model: 'Mustang',
  type: 'car',
  year: 2021, 
  color: 'red'
}

myVehicle(vehicleOne);

function myVehicle({type, color, brand, model}) {
  const message = 'My ' + type + ' is a ' + color + ' ' + brand + ' ' + model + '.';
}
```

# Spread Operator

The JavaScript spread operator (`...`) allows us to quickly copy all or part of an existing array or object into another array or object.
_Example_
```js
const numbersOne = [1, 2, 3];
const numbersTwo = [4, 5, 6];
const numbersCombined = [...numbersOne, ...numbersTwo];
```
The spread operator is often used in combination with destructuring.
_Example_
```js
const numbers = [1, 2, 3, 4, 5, 6];

const [one, two, ...rest] = numbers;
```
We can use the spread operator with objects too:
_Example_
```js
const myVehicle = {
  brand: 'Ford',
  model: 'Mustang',
  color: 'red'
}

const updateMyVehicle = {
  type: 'car',
  year: 2021, 
  color: 'yellow'
}

const myUpdatedVehicle = {...myVehicle, ...updateMyVehicle}
```
# Modules
To help  maintain the code-base, JavaScript modules allow you to break up your code into separate files. Module variables can then use `export` to share variables, functions, objects, or classes with other JS files, or `import` to gain access to the same from other files.\
**Export**
Create a file, `person.js`, and use any of the code below
_In line_
```js
export const name = "Jesse"
export const age = 40
```
_At the bottom_
```js
const name = "Jesse"
const age = 40

export { name, age }
```
**Import**
Create another file, `message.js`. Let's import the variables we created above
```js
import { name, age } from "./person.js";
```

**Default Export**
You can only have one default export in a file. Overwrite the file `person.js` with the following code:

```js
const person = () => {
  const name = "Jesse";
  const age = 40;
  return name + ' is ' + age + 'years old.';
};

export default person;
```

**Default Import**
Overwrite `message.js` with the following code,importing the default export from the file `person.js` above:
>NOTE: Notice the lack of curly braces. Importing in this way means you only import the default export variable or function

```js
import person from "./person.js";
```
# Ternary Operator
The ternary operator is a simplified conditional operator like if / else.
> SYNTAX: condition ? <expression if true> : <expression if false>

**Example**
_Before_
```js
if (authenticated) {
  renderApp();
} else {
  renderLogin();
}
```
_Ternary_
```js
authenticated ? renderApp() : renderLogin();
```

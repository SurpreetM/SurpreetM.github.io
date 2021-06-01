---
layout: post
title:      "Arrow and Regular Functions "
date:       2021-06-01 14:34:59 +0000
permalink:  arrow_and_regular_functions
---


This is my final blog post and so I thought I'd us this time and space to talk write about something I only got to grips with properly considering and understand towards the end of the react-redux section, and that is: 

**What really are the differences between arrow and regular functions**

On the face of it to me, the seemed equivalent and interchangable: 

```
// Regular Function declaration
function add (a, b) {
  return a + b;
}

// Regular Function expression
const add = function(a, b) {
  return a + b;
}

// The equivalent arrow function would be
const add  = (a + b) => {
 return a + b
}
```

After doing a fair amount of reading on this, here are the main differences to consider: 

### Using the keyword this

For regular functions, the value of this is dynamic. Therefore the value of this depends on how the function is invoked.

However, the value of this inside an arrow function remains the same throughout the lifecycle of the function and is always bound to the value of this in the closest non-arrow parent function.

```
let name ={ 
     firstName:'Claire',
		 
     printInRegular =  function() {
        console.log(`My Name is ${this.firstName}`);  // this refers to the object name
     },       
		 
     printInArrow = ()=>{
		  console.log(`My Name is ${this.firstName}`);  // this refers to the outter object where name is declared
		 }
} 
	
  name.printInRegular();   // My Name is Claire
  name.printInArrow();     // My Name is undefined
```

### Using the keyword new

Regular functions created using function declarations or expressions are constructible and callable, whereas arrow functions are only callable. 

A constructible function is one that can be called using the new keyword.

With a regular function we can do the following: 

```
function Car(color) {
  this.color = color;
}

const redCar = new Car('red');
redCar instanceof Car; // => true
```

Car is a regular function. When invoked with new keyword new Car('red') — new instances of Car type are created.

With doing the equivalent with an arrow function we get an error as arrow functions are not constructible and therefore cannot be used as a constructor to create a new instance.

```
const Car = (color) => {
  this.color = color;
};

const redCar = new Car('red'); // TypeError: Car is not a constructor
```

### Arguements binding

The arguments object inside the regular functions contains the list of arguments. However arrow functions does not define this special keyword arguements. 

With a regular function we can access the arguments being passed to it as follows: 
```
function showData() {
  console.log(arguments);
}

showData('a', 'b'); // logs { 0: 'a', 1: 'b', length: 2 }
```

With an arrow function however, we cannot call arguements, the way to access its arguments would be to use the rest parameter feature. 



```
const showData = () =>  {
  console.log(arguments);
}

showData(1,2,3); 
// Uncaught ReferenceError: arguments is not defined
```

...args rest parameter collects the execution arguments of the arrow function. 

```
const showData = (...args) =>  {
    console.log(args);
}
showData(1, 2, 3, 4); // logs [1, 2, 3, 4]
```



### Methods
Ususally we use regular methods to define methods inside classes, however in some instances when you need to also supply the class method as a callback (e.g. to a setTimeout method) accessing this can be difficult.

```
class Hero {
  constructor(heroName) {
    this.heroName = heroName;
  }

  logName() {
    console.log(this.heroName);
  }
}

const batman = new Hero('Batman');

setTimeout(batman.logName, 1000);
// after 1 second logs "undefined"
```

The issue here is that logName is being called but it is being called on the global object rather than the instance batman. To make this work we would need to bind the value of this to the instance batman. 

```
setTimeout(batman.logName.bind(batman), 1000);
// after 1 second logs "Batman"
```

Alternatively we can use arrow functions as a solution as the value of this is not dynamic. The value of this inside logName() method is always the class instance

```
class Hero {
  constructor(heroName) {
    this.heroName = heroName;
  }

  logName = () => {
    console.log(this.heroName);
  }
}

const batman = new Hero('Batman');

setTimeout(batman.logName, 1000);
// after 1 second logs "Batman"

```



### Implicit Returns

Return expression statement returns the result from both a regular and arrow functions. If the return statement is missing, or there’s no expression after return statement, the functions will implicitely returns undefined. 

However for arrow function that contain just one expression, you can omit the function’s curly braces, then the expression is implicitly returned. These are refered to as inline arrows functions.

```
const increment = (num) => num + 1;

increment(41); // => 42
```

### Duplicate Name Parameters

Arrow functions can never have duplicate named parameters, whether in strict or non-strict mode, whereas regular functions can. Therefore in non-strict mode the following is possible with a regular function: 

```
function add(x, x){}

(x, x) => {}
// SyntaxError: duplicate argument names not allowed in this context
```


### Summary
In summary I'm sure there maybe other differences to understand, but getting to grips with the context of the keyword this was really helpful especially when trying to refactor methods defined as regular funtions into the arrow syntax. 

Thanks for reading :) 



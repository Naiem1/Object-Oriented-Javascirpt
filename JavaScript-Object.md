# Object-Oriented Programming

### 4 Pillars 

||| 4 Pillars||
|--------| --------| ----| ----|
|Encapsulation | Abstraction | Inheritance |Polymorphism|

### In Object-oriented programming we combine a group of related variables and functions into a unit. we call that unite an object

|Property | Method |
|---------|--------|
|   x|f(x) Function|

___

### **Object Literal**
```javaScript
obj = {};
```

* An Object in javaScript essentially a collection of key Value paris
* Object Literal is a simple way to defined an object
  
```Object Literal
const circle = {
  radius: 1,
  location: {
    x: 1, 
    y: 1
  },
  draw: function () {
    console.log('Draw');
  }
};
```
* But we can also define object using `factories` and **`construction`**

---

### **Factory Function**

```Factory function
function createCircle(radius) {
  return {
    radius,
    draw: function () {
      console.log('draw!');
    }
  }
}

const newCircle = createCircle(2);
```
* Factory function just a regular function. it return only object.
* When a regular function return any object it called factory function.

---

### **Construction Function**
The naming convention of constructor function is different. The first latter should be uppercase
```function Circle(radius) {
  this.radius = radius;
  this.draw = function () {
    console.log('Draw');
  }
}
const another = new Circle(1);
```

* in the body instead of returning an object we're going to use the _`this`_ keyword to set the properties of this object.
* _`this`_ -> _`this`_ is basically a reference to the object that is executing this piece of code.

### **New Keyword**
* When we use the _`new`_ operator to call a function. 3 thing happen.
 * First, this _`new`_ operator will create empty object, 
 * Then it will set this to point to the object and
 * Finally, it will return that object from this function.
 * _NOTE_ - so note that here we don't have an explicit return statement, you're not retuning `this`
 * This will happen automatically when we use the _`new `_ operator.

___

### **Constructor Property**

 * Every Object in javaScript has a property call `constructor` 
 * and that references the function that was used to construct or create an object
 * here we have 2 objects, circle and another. Let's look at the constructor property for this 2 object.
 * Object() -> Built in constructor function in javascript
 * if we create an object using literal syntax, internally the javaScript engine uses the constructor function.
 * ```let x = {}``` -> let's define an object like this. when we use this syntax, object,
 * JavaScript engine will translate that to something like this `let x = new Object()`
 * In JavaScript we have other built in constructor function
  
  ```
  const string = new String(); // '', "", 
  const boolean = new Boolean() // true, false
  const number = new Number(); // 1, 2, 3
  const array = new Array(); // []
  ```

 * Every object has a constructor property and, that references the function that was used to create the object
  
___


 ### **FUNCTION ARE OBJECT**


 * We know that javascript function are object.
 * so this circle function we have here is actually an object
  ```
  function Circle(radius) {
    this.radius = radius
    this.draw = function() {
    console.log(draw)
  }
 }
  ```

  ```
    Circle.name; //  return name of the function
    Circle.length; // number of the arguments
    Circle.apply();
    Circle.call();
  ```

 * Every object in javaScript has a constructor property, and 
 * that references the function that was used to create an object.
 * Now, Who do you think created this object?
 * Circle.constructor -> Function() { [native code] }
 * Here we have another built in constructor call Function.
 * When we declare a function using a this syntax internally javaScript engine will use 'Function' constructor to create this object
 
  ```
  const Circle1 = new Function(radius, `
      this.radius = radius
      this.draw = function() {
      console.log(draw)
    }
  `);
  ```
  
 * when we declare a function internally, it's represented like this.
 * Now we can call this circle1 jus like calling our circle function.
  
  ```
  const circle = new Circle1(1); // return {radius: 1, draw: f}
  
  ```
  
  
**Method**
 
  ```
    Circle.call({}, radius); //
  ```
 * First argument is empty object. _`this`_ operator will reference empty object that we pass here as argument.
 * then we add our argument explicitly. here have on argument, we pass 1.
 * `Circle.call({}, 1)` this expression is like,  `new Circle(1);`
 * when we use `new` keyword, `new` keyword internally create an empty object, and pass that as the first argument to the `call` method. this argument determine the context for `this` so this well reference first argument.
 * if we not use `new` keyword this pont global object or `window` object.
  
  **another Method apply()**
  ```
    Circle.apply({}, [1, 2, 3]); apply take array as a 2nd argument
  ```
  
 * _**Takeway**_ : In JavaScript function are objects

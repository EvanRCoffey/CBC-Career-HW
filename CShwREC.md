## Core JavaScript Questions

1. What is the difference between `undefined` and `not defined` in JavaScript?  "Not defined" means there is currently no variable with that name.  "Undefined" means there is a variable whose value is null

2. What is "Hoisting" in JavaScript?  Hoisting is JavaScript's default behavior of moving declarations to the top.

3. What would be the output of the following code?
```javascript
    var y = 1;
      if (function f(){}) {
        y += typeof f;
      }
     console.log(y);
```
1undefined

4. What is a "private method"?  A method that can only be used by the object that created it.

5. What is the drawback of creating true private methods in JavaScript?  They can't be used outside of the object that created it.

6. What is a “closure” in JavaScript? Provide an example.  A closure is a function having access to the parent scope, even after the parent function has closed.  Example:

var add = (function () {
    var counter = 0;
    return function () {return counter += 1;}
})();

add();

7. Write a mul function which will produce the following outputs when invoked.
```javascript
console.log(mul(2)(3)(4)); // output : 24 
console.log(mul(4)(3)(4)); // output : 48
```

Looks like the code is already there?

8. How would you empty an array in JavaScript? Provide at least 2 methods of doing so.  

1) given array x,
x = []
2) given array x,
x.length = 0

9. What will be the output of the following code?
```javascript
var output = (function(x){
    delete x;
    return x;
  })(0);
  
  console.log(output);
```
0

What about this code?
```javascript
var x = 1;
var output = (function(){
    delete x;
    return x;
  })();
  
  console.log(output);
```
1

And what about this one?
```javascript
var x = { foo : 1};
var output = (function(){
    delete x.foo;
    return x.foo;
  })();
  
  console.log(output);
```
undefined

And finally, what about this one?
```javascript
var Employee = {
  company: 'xyz'
}
var emp1 = Object.create(Employee);
delete emp1.company
console.log(emp1.company);
```
xyz

10. What would this code return?
```javascript
var trees = ["xyz","xxxx","test","ryan","apple"];
delete trees[3];
  
  console.log(trees.length);
```
5

11. What will be the output of the code below?
```javascript
var bar = true;
console.log(bar + 0);   
console.log(bar + "xyz");  
console.log(bar + true);  
console.log(bar + false);   
```
1
truexyz
2
1

12. What will be the output of the code below?
```javascript
var z = 1, y = z = typeof y;
console.log(y);  
```
undefined

13. What would be the output of the code below?
```javascript
 var salary = "1000$";

 (function () {
     console.log("Original salary was " + salary);

     var salary = "5000$";

     console.log("My New Salary " + salary);
 })();
```
Original salary was undefined
My New Salary 5000$

14. What is the instanceof operator in JavaScript? What would be the output of the code below?
```javascript
function foo(){ 
  return foo; 
}
new foo() instanceof foo;
```
The instanceof operator tests whether an object has in its prototype chain the prototype property of a constructor.  No output.

15. What constitutes a "Primitive" value in Javascript?  One of these:
-undefined
-null
-boolean
-string
-number

16. What is the difference between a reference type variable and a value type variable?  Reference Type variables are stored in the heap while Value Type variables are stored in the stack.

17. How would you describe the difference between class-based inheritance and prototypical inheritance?  Classes inherit from classes and create subclass relationships.  Prototypes inherit from the objects which model them.



## ES6 Questions

1. What is the difference between JavaScript and ECMAScript?  ECMAScript is the language that forms the basis of JavaScript.  ECMAScript is standardized by the ECMA International standards organization.

2. What do `const` and `let` do? And when would we use them?  Const declares a variable whose value cannot be changed.  Let declares a variable that is limited in scope to the block, statement, or expression on which it is used.  Const is used when you want a value that can't change, and let is used when you have a value that you don't want to get confused with another variable.

3. How would you describe the difference between `function` and `function*`?  function* is a Generator, i.e. a function which can be exited and later re-entered

4. When would you NOT use an arrow function in the place of a regular function expression?  Defining methods on an object, callback functions with dynamic context, invoking constructors,

5. Refactor the following code to use an ES6 Template Literal.
```javascript
var name = 'Tiger';
var age = 13;

console.log('My cat is named ' + name + ' and is ' + age + ' years old.');
```
console.log('My cat is named ${name} and is ${age} years old.')

6. How would you refactor the following code to use ES6 default parameters?
```javascript
function addTwoNumbers(x, y) {
    x = x || 0;
    y = y || 0;
    return x + y;
}
```
nah I'm good

7. What is a "Promise" in ES6? And how many different states do they have?
The Promise object is used for asychronous computations.  It's like a callback.  It represents a value which may be available now, or in the future, or never.  PENDING/FULFILLED/REJECTED

8. What is a practical use case for Promises?  Have a function with a promise that has two case handlers, like an asychronous "if" statement.

9. What is wrong with the following code? And how could it be better?
```javascript
new Promise((resolve, reject) => {  
  throw new Error('error')
}).then(console.log)
```
Console.log could actually print something.  Also there's no use of resolve/reject.

10. Describe the .fetch() method. What is one disadvantage to using the .fetch() method over existing methods?  .fetch() allows you to make network requests similar to XMLHttpRequests.  The main difference is that the Fetch API uses Promises, avoiding callback hell and having to remember the complex API of XMLHttpRequest.



## Node.js Questions

1. What is Node.js?  Node.js is an open-source, cross-platform JavaScript runtime environment for executing JavaScript code server-side, and uses the Chrome V8 Javascript engine.

2. What is an "Error-First" Callback?  The first argument of the callback is reserved for an error object, and the secone argument of the callback is reserved for any successful response data.

3. What is the Node.js Event Loop?  The event loop is what allows Node.js to perform non-blocking I/O operations -- despite the fact that JavaScript is single-threaded -- by offloading operations to the system kernel whenever possible.  Node thread keeps an event loop and whenever a task gets completed, it fires the corresponding event which signals the event-listener to execute.

4. Why might someone choose to use the Node.js Async single-threaded 
model over a more traditional multi-threaded model?  To have a single-page app.

5. What is meant by the term "non-blocking I/O"?  It means the same thing as asynchronous I/O or non-sequential I/O.  It's a form of input/output processing that permits other processing to continue before the transmission has finished.

6. What is the "memory stack"? And what happens when you exceed it?  The memory stack is the memory set aside as scratch space for a thread of execution.  When you exceed it, an error is thrown.





## React.js Questions

1. What makes React.js more efficient at updating the DOM?  It only updates that which has changed.

2. What is the difference between a Logical component and a Pure component?  A logical component's purpose is to perform logic on some data.  The pure component doesn't do anything to its data.

3. What happens when you call "setState" in React?  You enqueue any changes to the component state and tells React that this component and its children need to be re-rendered with the updated state.

4. What is the React method to create a component? Alternatively, how 
would you accomplish the same thing using ES6 classes?  React.createClass().  Dunno.

5. In which React lifecycle event would you make AJAX requests? And why?  componentDidMount.  This way you guarantee you get the data after the component mounts.

6. Why would you use `React.Children.map(props.children, () => )` instead of `props.children.map(() => )`?  Dunno.

7. What is JSX?  Java Serialization to XML.  It's used all over React.



## Internet/Network Questions

1. What does TCP/IP stand for?  Transmission Control Protocol/Internet Protocol

2. Behind the scenes, how does HTTPS differ from HTTP?  Using HTTPS, two computers agree on a "code" between them, and then they scramble the messages using that "code" so that no one in between can read them.  This keeps your information safe from hackers.

3. Define the general response status code categories.
1xx Information responses
2xx Success
3xx Redirection
4xx Client errors
5xx Server error

4. What does DDOS stand for?  Distributed denial of service

5. What is CORS? How does it work?  Cross-origin resource sharing - it's a mechanism that allows restricted resources (e.g. fonts) on a web page to be requested from another domain outside the domain from which the first resource was served.

6. What does REST stand for when we refer it in the context of a "RESTful API"?  Representational state transfer.
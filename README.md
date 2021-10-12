# Activity2-Closure

## What is closure

A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In JavaScript, closures are created every time a function is created, at function creation time. To use a closure, define a function inside another function and expose it.

Nest functions wich remembers a set of variables that they can access no matter where they are called.

## An example of closure.

*/
- function crearContador() {
- let contador = 0; // La variable contador está vinculada a la función incrementar.
- 
- return function incrementar(){
- contador = contador + 1;
- return contador;
- }
- }
- 
- const contador1 = crearContador();
- contador1(); 
/*

## What is ()() in code?

Double-parentheses, refers to code that immediately invokes the return value of another function. Code that looks like this:

- require( "thing" )( options )
- connect( thisthing )( thatthing )

Other way is, if one of the function arguments is, itself, a function call. Code that looks like this:
- withStuff( getthing() )( stuff )

## Move the variable after the closure (the function inside the function) and explain what happens. 

## Change var for let and explain why the logic is not affected:

let allows you to declare variables that are limited to the scope of a block statement, or expression on which it is used, unlike the var keyword, which declares a variable globally, or locally to an entire function regardless of block scope. The other difference between var and let is that the latter is initialized to a value only when a parser evaluates it.


## Scope chain, an example of it, how many closures can we nest.

### Example:

*/
const language = 'brazillian portuguese'
const name = 'Ana'

function displayIntroduction() {
  const name = 'Maria'
  const country = 'Brazil'

  function displayInfo() {
    const name = 'Joana'
    console.log(`My name is ${name}, I'm from ${country} and I speak ${language}`)
  }

  return displayInfo() 
}

displayIntroduction() // My Name is JOana, I`m from Brazil and I speak Brazilian portuguese.
/*

Execution context is an environment in which javascript code is evaluated and executed. When the code first starts running it creates a global execution context and a function execution context is created on each function invocation. The scope chain of this code looks similar to this:

![image](https://user-images.githubusercontent.com/90293791/137033854-b8009c0f-1ca4-4e9c-b2c7-2eeb631fb29b.png)

Each execution context has a scope chain. It consists of the variables and objects referenceable by the execution context. Besides the variables and objects it has a property called outer that stores the reference to the parent's scope chain. When the displayInfo function is executed and reaches name it searches for it in the local scope chain, finding Joana as the value. The same process happens for country but it is not in the local scope.

When the constant is not found in the local scope javascript reaches to the parent's local memory accessible by the reference stored in outer, getting Brazil as the value. The same thing happens to language in this case the javascript engine goes all the way up the scope chain reaching the global scope to find the constant, retrieving the value brazillian portuguese. It is important to know that the scope chain works only one way, from the inner scope to the outer scopes, making it impossible for the global execution context to have access to country, for example.

Also know that since the global execution context is the top context the outer points to null, so if the variable wasn't there it would be implicitly declared, if not in strict mode, or an error would be returned.

## They are conflicts between the closure and the global scope? 

## Advantages of closures.
As we all know variables which we create inside function have local scope and only accessible in side the function not outside the function. 

### Problem 1
Also variable defined inside the function created when we call function and destroyed which function close. We can define global variables which created when program starts till the end of program and accessible any where in the program.
### Problem 2
If we define the global variable these can be changed any where in program.
### Solution: Data Encapsulation
we can overcome above problems by using closures.

1. By using a closure we can have private variables that are available even after a function task is finished.
2. With a function closure we can store data in a separate scope, and share it only where necessary.

### ¿What is data hiding and encapsulation? 

Data hiding is the ability of objects to shield variables from external access. It is a useful consequence of the encapsulation principle. Those variables marked as private can only be seen or modified through the use of public accessor (getter) and mutator (setter) methods. This permits validity checking at run time.

While data hiding focuses on restricting data use in a program to assure data security, data encapsulation focuses on wrapping (or encapsulating) the complex data to present a simpler view to the user. In data hiding, the data has to be defined as private only. In data encapsulation, the data can be public or private

## Give me an example of privacy with closures. 
## What happens if you create two counters with the same closure?
## How can we add more functions as a decrement counter? Give an example of it. 

## What are the disadvantages of closures?

Closures not only have advantages it also have disadvantages. If you are using closures there are two disadvantages which you need to take care while using.

1. As long as the closure are active , the memory can’t be garbage collected.
### Example:
If we are using closure in ten places then unless all the ten process complete it hold the memory which cause memory leak. 
### How to fix this?
If there come a point in you program where you are done using closure then you need to set closure to null.

2. Creating a function inside a function leads to duplicity in memory and cause slowing down the application.
### How to fix?
Use closures only when you need privacy otherwise use module pattern to create new objects with shared methods.

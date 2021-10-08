# Activity2-Closure

## What is closure

A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In JavaScript, closures are created every time a function is created, at function creation time. To use a closure, define a function inside another function and expose it.

Nest functions wich remembers a set of variables that they can access no matter where they are called.

## An example of closure.

function crearContador() {
let contador = 0; // La variable contador está vinculada a la función incrementar.

return function incrementar(){
contador = contador + 1;
return contador;
}
}

const contador1 = crearContador();
contador1(); 

## What is ()() in code? 

Move the variable after the closure (the function inside the function) and explain what happens. 

Change var for let and explain why the logic is not affected 

Scope chain, an example of it, how many closures can we nest 

They are conflicts between the closure and the global scope? 

Advantages of closures. 

¿What is data hiding and encapsulation? 

Give me an example of privacy with closures. 

What happens if you create two counters with the same closure? 

How can we add more functions as a decrement counter? Give an example of it. 

What are the disadvantages of closures?

# Js-Interview-Question
Ques - What is the difference between var, let, and const in JavaScript?
Ans - var is function scoped, while let and const are block scoped.
var can be re-declared and re-assigned. let can be re-assigned but not re-declared in the same scope. const cannot be re-assigned after declaration.
Also, var is hoisted with undefined, whereas let and const are hoisted but stay in the temporal dead zone until initialized.

Ques - What is hoisting in JavaScript?

Ans - Hoisting is JavaScript’s default behavior where variable and function declarations are moved to the top of their scope before execution.
In case of var, it is hoisted and initialized with undefined.
But let and const are also hoisted, although they remain in the Temporal Dead Zone until they are initialized.

Ques - What is the difference between == and === in JavaScript?

Ans - == is loose equality, which compares values after type conversion if needed.
=== is strict equality, which compares both value and data type without type coercion.
For example, 5 == "5" is true, but 5 === "5" is false.

Ques - What is a closure in JavaScript?

Ans - A closure in JavaScript occurs when a function retains access to its lexical scope, meaning it can access variables from its outer function even after the outer function has already executed.

      A closure is created when an inner function remembers and can access variables from its outer function even after the outer function has finished execution.

      Agar interviewer puche:

“Where have you used closures in real projects?”

Best answer:

I have used closures in utility functions like debounce, throttle, private variable handling, and sometimes in event handlers or callback-based logic.

Ques - What is the difference between null and undefined?

Ans - undefined is the default value of a declared variable that has not been assigned yet.
null is explicitly assigned by the developer to indicate that the variable currently has no value.

Ques - What is the difference between map() and forEach()? 

Ans - map() creates and returns a new array by transforming each element of the original array.
forEach() is used only for iteration and does not return a new array.
I use map() when I need transformed data, and forEach() when I just want side effects like logging or updating values externally.

Real Project Tip (Important for You)

Since tum React use karte ho, interviewer agar puche:

“Why is map() used more in React?”

Best answer:

In React, map() is commonly used to render lists because it returns a new array of JSX elements, which can be directly displayed in the UI.

👉 Ye answer React exposure instantly show karta hai.

Ques - What is the difference between let and const?

Ans -Both let and const are block-scoped.
let allows re-assignment, while const does not allow re-assignment after declaration.
However, in case of objects or arrays declared with const, their internal properties can still be modified because the reference remains constant, not the contents.

Ques - What is hoisting, and are let and const hoisted?

Ans - Hoisting is JavaScript’s default behavior where variable and function declarations are processed before code execution.
var is hoisted and initialized with undefined.
let and const are also hoisted, but they remain in the Temporal Dead Zone until they are initialized, so accessing them before declaration throws an error.

Ques - What is a Promise in JavaScript?

Ans - A Promise is an object that represents the future result of an asynchronous operation.
Its states are pending, fulfilled, and rejected.
It helps handle async code in a cleaner way compared to deeply nested callbacks.

Why do we use Promises instead of callbacks?”

Best answer:

Promises make async code more readable and easier to manage.
They help avoid callback hell and provide better error handling using .then() and .catch().


Ques - What is the difference between Promise and async/await?

Ans - Promises are used to handle asynchronous operations using methods like .then(), .catch(), and .finally().
async/await is a cleaner and more readable syntax built on top of Promises.
It makes asynchronous code look more like synchronous code, but internally it still works with Promises.

Ques - What is the Event Loop in JavaScript?

Ans - JavaScript is single-threaded, so it uses the Event Loop to handle asynchronous operations without blocking the main thread.
Synchronous code runs in the Call Stack, while async tasks like timers and API callbacks are handled by browser or Node APIs and then moved to queues.
The Event Loop continuously checks if the Call Stack is empty, and then pushes tasks from the queue into the stack for execution.
Also, microtasks like Promise callbacks are executed before macrotasks like setTimeout.

The Event Loop is the mechanism that allows JavaScript to handle asynchronous operations even though it is single-threaded.
It checks whether the Call Stack is empty, and if it is, it moves tasks from the microtask queue or callback queue into the stack.
Microtasks like Promise callbacks run before macrotasks like setTimeout.

Ques - console.log("start");

setTimeout(() => console.log("timeout"), 0);

Promise.resolve().then(() => console.log("promise"));

console.log("end");

Ans - First synchronous code runs, so start and end print first.
Then Promise callback runs because it goes to the microtask queue, which has higher priority than the macrotask queue.
So promise comes before timeout

Ques - What is the difference between call(), apply(), and bind()?

Ans - call(), apply(), and bind() are used to explicitly set the this value of a function.
call() invokes the function immediately and accepts arguments separately.
apply() also invokes immediately, but accepts arguments as an array.
bind() does not invoke immediately; it returns a new function with the bound this value.

All three are used to control the this context of a function.
call() takes arguments one by one, apply() takes arguments in an array, and bind() returns a new function instead of executing immediately.

Agar interviewer puche:

“Where do we use bind()?”

Best answer:

bind() is useful when we want to preserve the this context for later execution, such as in event handlers, callbacks, or class methods.

function greet(city) {
  console.log(this.name, city);
}

const user = { name: "Jai" };

greet.call(user, "Kanpur"); 
// Jai Kanpur

greet.apply(user, ["Kanpur"]); 
// Jai Kanpur

const fn = greet.bind(user, "Kanpur");
fn(); 
// Jai Kanpur

Ques - What is the difference between filter() and find()?

Ans - filter() returns a new array containing all elements that match the given condition.
find() returns only the first element that matches the condition.
If no match is found, find() returns undefined.

“Which one is better for a single match?”

Best answer:

If I only need the first matching element, I prefer find() because it stops once a match is found, so it can be more efficient than filter().

Ques - What is the difference between localStorage, sessionStorage, and cookies?

Ans - localStorage stores data on the client side and the data remains even after the browser is closed.
sessionStorage also stores client-side data, but it is cleared when the browser tab or session is closed.
Cookies store small pieces of data and can be sent automatically to the server with each request.
For authentication, cookies—especially HttpOnly secure cookies—are generally safer than localStorage because they reduce XSS exposure.

Ques - Where should JWT token be stored?”

Best answer:

Access token can be stored in memory or sometimes localStorage for simplicity, but it has XSS risk.
A more secure production approach is to store refresh tokens in HttpOnly secure cookies and keep access tokens short-lived.

Ques - What is the difference between a normal function and an arrow function in JavaScript?

Ans - A normal function is declared using the function keyword, while an arrow function provides a shorter syntax.
The main difference is that a normal function has its own this, while an arrow function does not have its own this and instead inherits it from the surrounding lexical scope.
Also, arrow functions do not have their own arguments object and cannot be used as constructors with new.

“Can we use arrow function as constructor?”

✅ Answer:

No, arrow functions cannot be used as constructors because they do not have their own this and do not have a prototype.

Ques - What is this keyword in JavaScript?

Ans - this in JavaScript refers to the current execution context or the object that is calling the function.
Its value depends on how the function is invoked, not where it is defined.
In object methods, this usually refers to that object.
In arrow functions, this is lexical, meaning it is inherited from the surrounding scope.

Ques - What is event delegation in JavaScript, and why is it useful?

Ans -
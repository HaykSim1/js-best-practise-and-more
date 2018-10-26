# Useful collection for JavaScript

### Content
* Hoisting
* Closures
* Event Loop
* Code style
    * ESLint
* Best practises

## Hoisting

In JavaScript, a variable can be declared after it has been used.
To understand this, you have to understand the term **"hoisting"**.

**Hoisting** is JavaScript's default behavior of moving all declarations to the top of the current scope (to the top of the current script or the current function).

![Hoisting](http://www.tutorialsteacher.com/Content/images/js/hoisting.png)

Variables and constants declared with **let** or **const** are not hoisted!

JavaScript only hoists **declarations**, not initializations.

## Closures

A **closure** is the combination of a function and the lexical environment within,
which that function was declared. 

```
function justCalculate(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = justCalculate(5);
var calcWidth10 = justCalculate(10);

console.log(add5(2));  // 7
console.log(add10(2)); // 12
```

In this example, we have defined a **function justCalculate(x)**, which takes a single argument, x, and returns a new function. The function it returns takes a single argument, y, and returns the sum of x and y.

In essence, **justCalculate** is a function factory — it creates functions which can add a specific value to their argument. In the above example we use our function factory to create two new functions — one that adds 5 to its argument, and one that adds 10.

**add5** and **add10** are both closures. They share the same function body definition, but store different lexical environments. In **add5's** lexical environment, x is 5, while in the lexical environment for **add10**, x is 10.

## Event Loop

### JUST CHECK THIS
[Event loop](http://latentflip.com/loupe/)

## Code style
    
   Whether you’re just starting to learn JavaScript, or getting ready for your big interview with AirBnB, here are 5 style guides that can help you write cleaner code.
    
   **What the heck is a style guide?**
   A style guide is a set of standards that outline how code should be written and organized. As you read through these guides, you can get an idea for how code is written at the respective companies.
    
   **Why do we need style guides?**
   For one main reason: Everyone writes code differently. I may like to do something one way, and you may like to do it a different way. That’s all fine and dandy as long as we each work on our code. But what happens when you have 10, 100, or even 1,000 developers all working on the same codebase? Things get messy very quickly. Style guides are created so new developers can get up to speed on a code base quickly, and then write code that other developers can understand quickly and easily!
    
   Use **ESLint**
   
   * Airbnb JavaScript Style Guide
   * Google JavaScript Style Guide
   * Idiomatic JavaScript Style Guide
   * JavaScript Standard Style Guide
   * jQuery JavaScript Style Guide
   
   Set up one of this style guides or create yours.
   
    
## Best practises

##### Make it Understandable
Choose easy to understand and short names for variables and functions.

```
// DON'T
let d
let elapsed
const ages = arr.map((i) => i.age)

// DO
let daysSinceModification
const agesOfUsers = users.map((user) => user.age)
```
Also, make meaningful distinctions and don't add extra, unnecessary nouns to the variable names

```javascript
// DON'T
let nameString
let theUsers

// DO
let name
let users
```

```javascript
// DON'T
/**
 * Invite a new user with its email address
 * @param {String} user email address
 */
function inv (user) { /* implementation */ }

// DO
function inviteUser (emailAddress) { /* implementation */ }
```

##### Use Shortcut Notations
Global variables are a terribly bad idea.

Shortcut notations keep your code snappy and easier to read once you get used to it.

```javascript
// BAD
let lunch = new Array();
lunch[0]='Dosa';
lunch[1]='Roti';
lunch[2]='Rice';
lunch[3]='what the heck is this?';

// GOOD
const lunch = [
   'Dosa',
   'Roti',
   'Rice',
   'what the heck is this?'
];

// BAD
if(v){
   var x = v;
} else {
   var x =10;
}

// GOOD
const x = v || 10;

```
##### Modularize
Keep your code modularized and specialized.

It is tempting and easy to write one function that does everything. However, as you extend the functionality you will find that you do the same things in several functions.

To prevent that, make sure to write smaller, generic helper functions that fulfill one specific task rather than catch-all methods.

At a later stage you can also expose these functions when using the revealing module pattern to create an API to extend the main functionality.

Good code should be easy to build upon without rewriting the core.

##### How to write nice async code?

Use Promises whenever you can.

Promises are natively available from Node 4. Instead of writing nested callbacks, you can have chainable Promise calls.

```javascript
// AVOID
asyncFunc1((err, result1) => {
  asyncFunc2(result1, (err, result2) => {
    asyncFunc3(result2, (err, result3) => {
      console.lor(result3)
    })
  })
})

// PREFER
asyncFuncPromise1()
  .then(asyncFuncPromise2)
  .then(asyncFuncPromise3)
  .then((result) => console.log(result))
  .catch((err) => console.error(err))
```


# Do some commits, I write only a little part, thank you.


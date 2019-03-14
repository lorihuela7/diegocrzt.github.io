# EcmaScript (AKA JavaScript)

## FRONT-END VS BACK-END

![](https://i.ytimg.com/vi/nMtgFZSdtwk/maxresdefault.jpg)

## JavaScript

JavaScript is among the most powerful and flexible programming languages of the web. It powers the dynamic behavior on most websites.

Programming language

* Interpreted
* Multi-Paradigm (Object Oriented / Functional)

![](https://3.bp.blogspot.com/-JInnywuZLZE/VUrkEbhgfKI/AAAAAAAAJAU/29CVGI45W4A/s1600/java-vs-javascript.jpg)

_(Lately, not so much, see [ES6](https://ponyfoo.com/articles/es6))_

JavaScript is dynamically typed, which simply means that types can change at **runtime**.

_Quick example: the following code is completely valid in JS (which doesn't mean that it's a good use of the language)._

```javascript 1.7
let myVar = 1;
myVar = 'Toyota';
myVar = ["Saab", "Volvo", "BMW"];
```

## History

Created by Brendan Eich of Netscape orignally named `Mocha`, later `LiveScript` and finally in 1995 is announced as `JavaScript`

Standardized in 1997 by ECMA International as `ECMA-262` and also know as  `ISO/IEC 16262`

Nine Editions published until 2018

| Version | Date | Changes |
|:---:|:---:|---|
| 1 | June/1997 | First release |
| 2 | July/1998 | Changes to make it compatible with ISO/IEC 16262 |
| 3 | December/1999 | There are now regular expresions! wiiiiii |
| 4 | -- | Abandoned |
| 5 | December/2009 | strict mode, fixing ambiguities, acommodate to real world implementations, supports getter, setters, JSON library, reflection |
| 5.1 | June/2011 | Algined with ISO/IEC 16262:2011 |
| 6 | June/2015 | ECMAScript 2015 / ECMAScript 6, adds classes, modules, for/of iterators, Python style generators and generators expression, arrow functions, binary data, type arrays, collections (maps, sets and weak maps), promises, number and math enhancements, also know as ECMAScript Harmony  | 
| 7 | June/2016 | ECMAScript 2016 Language reform, code isolation, exponentiation operator **, Array.prototypes.includes |
| 8 | June/2017 | ECMASCript 2017 Concurrency/atomics async/await syntax |
| 9 | June 2018 | ECMAScript 2018 Async iteration, generators, new regular expressions (that make developres cry blood) and rest, spread parameters |

**ECMAScript** is the official name for JavaScript. For common usage, these rules apply:

* JavaScript means the programming language.
* ECMAScript is the name used by the language specification. Therefore, whenever referring to versions of the language, people say ECMAScript.
Some of the versions of JavaScript are ECMAScript 2015(ES6/ES2015), ES2016, ES2017 and ES2018 (they aren't supported by all the browsers yet); ES.Next is currently being developed (the specification has not been finalized yet).

## Important notions to understand JavaScript

### Variables

![](https://cdn-images-1.medium.com/max/1600/1*kZXDtoVrpI8Ynwjo2jtKSA.png)

#### Mutability

A `const` variable is just like any other variable with some exceptions:

- Need to initialize the value when declared. It throws an error otherwise.
- A new value can’t be assigned afterward. Not very variable, right?

The variables declared with `var` or `let` are both mutable.

#### Scope

What happen when we use `var`?

`var` ignores the blocks and is defined to the closest function or global scope.
Here an example,

```javascript 1.7
function foo() {
  if (false) {
    var bar = 'hello';
  }
  console.log(bar);
}
foo(); // prints undefined
```

The code above, will be override it as:

```javascript 1.7
function foo() {
  var bar; // hoisted the declaration but not assignment
  if (false) {
    bar = 'hello';
  }
  console.log(bar); // undefined but no reference error
}

foo(); // prints undefined
```

On the other hand, `let` doesn't need such hoisted declaration.
If we use the same example, but we define the variables using `let` instead of `var`,

```javascript 1.7
function foo() {
  if (false) {
    let bar = 'hello';
  }
  console.log(bar); // reference error 
}

foo(); // prints Uncaught ReferenceError: bar is not defined
```

_When you define a variable in JavaScript, you should prefer `let` and `const` over `var` just to maintain the simplicity._

### Functions

#### Anonymous functions

It's a function without a name.

For example:

```javascript 1.7
(function () {
    console.log('anonymous function');
})();
```

### Lambda functions

It's a function (anonymous or not) used as data. So, basically, it can be passed, exported or assigned.

For example: 
```javascript 1.7
function someRandomFunction(f) {
  f();
}

const print = function() {
  console.log('not anonymous function');
};

someRandomFunction(print); // here the message will be printed
someRandomFunction(function() {
    console.log('using an anonymous function');
});
```

### Arrow functions

It's a syntactic sugar that can be used to express functions (anonymous or not).
For example, the function above will become:

```javascript 1.8
const print = () => console.log('not anonymous function');

const someRandomFunction = (f) =>  f();
someRandomFunction(print);
someRandomFunction(() => console.log('using an anonymous arrow function'));
```

## Callback

 A callback is a function that is to be executed after another function has finished executing.

_Why do we need Callbacks?_

For one very important reason — JavaScript is an event driven language. 
This means that instead of waiting for a response before moving on, 
JavaScript will keep executing while listening for other events. 

Let's see an example:

```javascript 1.8
const first = () => {
  // Simulate a code delay
  setTimeout( function(){
    console.log(`1`);
  }, 500 );
}

const second = () => {
    console.log(`2`);
}

first();
second();
```

Can you guess what message will be printed first?
That's why we need a callback function.

Here an example using a callback:

```javascript 1.8
const first = (f2) => {
   // Simulate a code delay
   setTimeout( function(){
     console.log(`1`);
     f2();
   }, 500 );
 }

 const second = () => {
     console.log(`2`);
 }

 first(second);
```

## DOM manipulation

JavaScript can access and change all the elements of an HTML document. The HTML DOM views a HTML document as a `tree-structure`. The tree structure is called a **node-tree**.  DOM is Document object model.

Let's try some examples in our page of the CV.
Important!: You can use the CSS selector to modify the style.

* Change the name `Carpincho` for something else.

```js
document.querySelector('h1').innerHTML = 'Something else';
```

* Remove the section with id `obective`.

```js
document.getElementById('objective').remove()
```

* Change the color of all the titles on the left side

```js
const titles = document.querySelectorAll('section dl dt');
titles.forEach(title => {
    title.style.color = 'red';
});
```

## AJAX (XMLHttpRequest)

Short for **A**synchronous **J**avaScript **A**nd **X**ML

![](https://upload.wikimedia.org/wikipedia/commons/0/0b/Ajax-vergleich-en.svg)

Consist in using the builtin object [`XMLHttpRequest`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) to make asynchronous calls to http servers in order to receive the answer, parse the response and if necessary modify the document.

```js
const xhr = new XMLHttpRequest();

xhr.onreadystatechange = () => { console.log(xhr.readyState); console.log(xhr.status); console.log(xhr.responseText); };

xhr.open('GET','https://task-backend-fpuna.herokuapp.com/tasks');

xhr.send();
```

## References

* [Declaring Variables in ES6+ JavaScript](https://codeburst.io/declaring-variables-in-es6-javascript-60ea37e38765)
* [Scoping with var, let & const](https://blog.usejournal.com/scoping-with-var-let-const-c0060135e09d)
* [DOM Manipulation in JavaScript](http://codeparadox.in/dom-manipulation-in-javascript-part-2/) Check this tutorial!
* [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
* [AJAX](https://developer.mozilla.org/en-US/docs/Web/Guide/AJAX/Getting_Started)
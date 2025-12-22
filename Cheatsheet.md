# JavaScript Cheat Sheet – COMPLETE LEARNING VERSION 📘 (ES6+)

This cheat sheet explains **WHY** and **HOW** things work.  
Suitable for beginners and refreshers (Browser & Node.js).

---

## Table of Contents

- [JavaScript Cheat Sheet – COMPLETE LEARNING VERSION 📘 (ES6+)](#javascript-cheat-sheet--complete-learning-version--es6)
  - [Table of Contents](#table-of-contents)
  - [1. Basics](#1-basics)
  - [2. Variables \& Data Types](#2-variables--data-types)
  - [3. Operators](#3-operators)
  - [4. Control Structures](#4-control-structures)
  - [5. Functions](#5-functions)
  - [6. Arrays](#6-arrays)
  - [7. Objects](#7-objects)
  - [8. Classes](#8-classes)
  - [9. Modules (ESM)](#9-modules-esm)
  - [10. Asynchronous JavaScript](#10-asynchronous-javascript)
  - [11. Error Handling](#11-error-handling)
  - [12. Scope \& Closures](#12-scope--closures)
  - [13. this](#13-this)
  - [14. DOM Manipulation (Browser)](#14-dom-manipulation-browser)
  - [15. Events](#15-events)
  - [16. Browser APIs](#16-browser-apis)
  - [17. Storage](#17-storage)
  - [18. JSON](#18-json)
  - [19. Regular Expressions](#19-regular-expressions)
  - [20. Modern Features](#20-modern-features)
  - [21. Best Practices](#21-best-practices)
  - [End](#end)

---

## 1. Basics

~~~javascript
// Single-threaded, event-driven
// Code executes top to bottom

// Comments
// single-line
/* multi-line */

// Console output
console.log("Hello World");

// Template literals
const name = "Max";
console.log(`Hello ${name}`); // "Hello Max"

// Debugger
// debugger; // pause execution in dev tools
~~~

---

## 2. Variables & Data Types

~~~javascript
var old = 1; // outdated, function-scoped
old = 2;

let person = "Nick"; // block-scoped, reassignable
person = "John";

const pi = 3.14; // cannot be reassigned

// Primitives
const text = "Hello"; // string
const age = 30;       // number
const active = true;  // boolean
const nothing = null; // null
let undef;            // undefined
const id = Symbol("id"); // symbol
const big = 123n;        // bigint

// Type checking
console.log(typeof text); // "string"
console.log(typeof null); // "object" (JS quirk)
~~~

---

## 3. Operators

~~~javascript
// Arithmetic
5 + 3;  // 8
5 - 3;  // 2
5 * 3;  // 15
5 / 2;  // 2.5
5 % 2;  // 1
2 ** 3; // 8

// Comparison
1 == "1";  // true (loose)
1 === "1"; // false (strict)
5 != "5";  // false
5 !== "5"; // true

// Logical
true && false; // false
true || false; // true
!true;         // false

// Ternary
const status = age >= 18 ? "adult" : "minor";

// Nullish coalescing
const value = null;
const result = value ?? "Default";

// Boolean cast
!!"text"; // true
!!0;      // false
~~~

---

## 4. Control Structures

~~~javascript
// if / else
let score = 85;
let grade;

if(score > 90) {
  grade = "A";
} else if(score > 80) {
  grade = "B";
} else {
  grade = "C";
}

// switch
const role = "admin";
switch(role){
  case "admin":
    console.log("Admin");
    break;
  default:
    console.log("User");
}

// loops
for(let i=0;i<3;i++) console.log(i);

let i = 0;
while(i<3) {
  console.log(i);
  i++;
}

do {
  console.log("Executed at least once");
} while(false);

// Iteration
const arr = [10,20,30];
for(const value of arr) console.log(value); // values
for(const key in arr) console.log(key);    // indexes
~~~

---

## 5. Functions

~~~javascript
// Normal function
function add(a,b) { return a+b; }

// Arrow function
const addArrow = (a,b) => a+b;

// Arrow without {}
const square = x => x*x;

// Default parameters
function greet(name="Guest"){ return `Hello ${name}`; }

// Rest parameters
function sum(...numbers){ return numbers.reduce((a,b)=>a+b,0); }
~~~

---

## 6. Arrays

~~~javascript
const numbers = [1,2,3];

// Adding/removing
numbers.push(4);
numbers.pop();
numbers.shift();
numbers.unshift(0);

// Iteration (functional)
numbers.map(n=>n*2);
numbers.filter(n=>n>1);
numbers.reduce((a,b)=>a+b,0);
numbers.find(n=>n===2);
numbers.includes(3);

// Copy
const copy = [...numbers];

// Other useful
numbers.slice(1,3);
numbers.splice(1,2); // remove
numbers.sort((a,b)=>b-a);
~~~

---

## 7. Objects

~~~javascript
const user = {
  name: "Max",
  age: 30,
  greet() { console.log(this.name); }
};

// Access
user.name;
user["age"];

// Destructuring
const { name, age } = user;

// Copy
const user2 = { ...user };

// Keys, Values, Entries
Object.keys(user);   // ["name","age","greet"]
Object.values(user); // ["Max",30, f]
Object.entries(user); // [["name","Max"],...]
~~~

---

## 8. Classes

~~~javascript
class Person {
  constructor(name){ this.name = name; }
  greet(){ console.log(this.name); }
}

class Student extends Person {
  constructor(name, course){
    super(name); // call parent constructor
    this.course = course;
  }
  study(){ console.log("Studying " + this.course); }
}

const s = new Student("Anna","JS");
s.greet();
s.study();
~~~

---

## 9. Modules (ESM)

~~~javascript
// export
export const value = 42;
export default function main(){}

// import
import main, { value } from "./file.js";
~~~

---

## 10. Asynchronous JavaScript

~~~javascript
// callback
setTimeout(()=>console.log("Later"),1000);

// Promise
fetch("/api")
.then(res=>res.json())
.then(data=>console.log(data))
.catch(err=>console.error(err));

// async / await
async function loadData(){
  try{
    const res = await fetch("/api");
    const data = await res.json();
    return data;
  }catch(e){ console.error(e); }
}

// Multiple promises
Promise.all([fetch("/a"), fetch("/b")])
.then(([a,b])=>console.log(a,b));
~~~

---

## 11. Error Handling

~~~javascript
try{
  throw new Error("Something went wrong");
}catch(e){
  console.error(e.message);
}finally{
  console.log("Always executed");
}
~~~

---

## 12. Scope & Closures

~~~javascript
function outer(){
  let secret = 42;
  return function inner(){ return secret; };
}
const fn = outer();
fn(); // 42
~~~

---

## 13. this

~~~javascript
const obj = {
  value:10,
  normal(){ console.log(this.value); },
  arrow:()=>console.log(this.value)
};
obj.normal(); // 10
obj.arrow();  // undefined
~~~

---

## 14. DOM Manipulation (Browser)

~~~javascript
document.querySelector(".box");
document.getElementById("id");

element.textContent = "Text";
element.innerHTML = "<b>HTML</b>";
element.classList.add("active");
~~~

---

## 15. Events

~~~javascript
button.addEventListener("click", e => e.preventDefault());
~~~

---

## 16. Browser APIs

~~~javascript
navigator.userAgent;
window.location.href;
window.history.back();
~~~

---

## 17. Storage

~~~javascript
localStorage.setItem("key","value");
localStorage.getItem("key");

sessionStorage.setItem("key","value");
~~~

---

## 18. JSON

~~~javascript
const json = JSON.stringify(user);
const objBack = JSON.parse(json);
~~~

---

## 19. Regular Expressions

~~~javascript
const emailRegex = /^\S+@\S+\.\S+$/;
emailRegex.test("test@test.com"); // true
~~~

---

## 20. Modern Features

~~~javascript
// Optional chaining
obj?.prop;
obj?.method?.();

// Sets & Maps
const unique = [...new Set([1,1,2])];
const map = new Map([["a",1],["b",2]]);
const weakMap = new WeakMap();
const weakSet = new WeakSet();

// Deep copy
structuredClone(user);
~~~

---

## 21. Best Practices

- use `const` before `let`
- use `===` instead of `==`
- small, pure functions
- prefer immutability
- prefer async/await over callbacks
- avoid global scope
- readability > cleverness

---

## End

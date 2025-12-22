# JavaScript Cheat Sheet – LERNVERSION 📘 (ES6+)

Diese Version erklärt **WARUM** und **WIE** Dinge funktionieren.  
Geeignet für Einsteiger & Auffrischer (Browser & Node.js).

---

## Inhaltsverzeichnis

- [JavaScript Cheat Sheet – LERNVERSION 📘 (ES6+)](#javascript-cheat-sheet--lernversion--es6)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
  - [1. Grundlagen](#1-grundlagen)
  - [2. Variablen \& Datentypen](#2-variablen--datentypen)
  - [3. Operatoren](#3-operatoren)
  - [4. Kontrollstrukturen](#4-kontrollstrukturen)
  - [5. Funktionen](#5-funktionen)
  - [6. Arrays](#6-arrays)
  - [7. Objekte](#7-objekte)
  - [8. Klassen](#8-klassen)
  - [9. Module (ESM)](#9-module-esm)
  - [10. Asynchrones JavaScript](#10-asynchrones-javascript)
  - [11. Fehlerbehandlung](#11-fehlerbehandlung)
  - [12. Scope \& Closures](#12-scope--closures)
  - [13. this](#13-this)
  - [14. DOM Manipulation (Browser)](#14-dom-manipulation-browser)
  - [15. Events](#15-events)
  - [16. Browser APIs](#16-browser-apis)
  - [17. Storage](#17-storage)
  - [18. JSON](#18-json)
  - [19. Reguläre Ausdrücke](#19-reguläre-ausdrücke)
  - [20. Moderne Features](#20-moderne-features)
  - [21. Best Practices](#21-best-practices)
  - [Ende](#ende)

---

## 1. Grundlagen

~~~javascript
// JavaScript ist single-threaded und event-basiert
// Code wird von oben nach unten ausgeführt

// Einzeiliger Kommentar
/* Mehrzeiliger Kommentar */

console.log("Hello World");
~~~

---

## 2. Variablen & Datentypen

~~~javascript
// var → veraltet, function-scoped
var old = 1;
old = 2;
console.log(old); // 2
~~~

~~~javascript
// let → veränderbar, block-scoped
let person = "Nick";
person = "John";
console.log(person); // "John"
~~~

~~~javascript
// const → keine Neuzuweisung erlaubt
const pi = 3.14;
// pi = 3.15 ❌ Fehler
~~~

~~~javascript
// Primitive Datentypen
const text = "Hallo";     // string
const age = 30;           // number
const active = true;      // boolean
const nothing = null;     // null
let undef;                // undefined
~~~

~~~javascript
typeof "abc";   // "string"
typeof 123;     // "number"
typeof null;    // "object" (JS-Bug)
~~~

---

## 3. Operatoren

~~~javascript
1 == "1";   // true (lose Gleichheit)
1 === "1";  // false (strikte Gleichheit)
5 != "5";   // false
5 !== "5";  // true
~~~

~~~javascript
true && false; // false
true || false; // true
!true;         // false
~~~

~~~javascript
const age = 18;
const status = age >= 18 ? "adult" : "minor";
~~~

~~~javascript
const value = null;
const result = value ?? "Default"; // Nullish Coalescing
~~~

~~~javascript
!!"text"; // true
!!0;      // false
~~~

---

## 4. Kontrollstrukturen

~~~javascript
let score = 85;
let grade;

if (score > 90) {
  grade = "A";
} else if (score > 80) {
  grade = "B";
} else {
  grade = "C";
}
console.log(grade); // "B"
~~~

~~~javascript
switch (role) {
  case "admin":
    console.log("Admin");
    break;
  default:
    console.log("User");
}
~~~

~~~javascript
for (let i = 0; i < 3; i++) {
  console.log(i);
}

let i = 0;
while (i < 3) {
  console.log(i);
  i++;
}

do {
  console.log("executed at least once");
} while(false);
~~~

---

## 5. Funktionen

~~~javascript
// normale Funktion
function add(a, b) {
  return a + b;
}
console.log(add(2,3)); // 5
~~~

~~~javascript
// Arrow Function
const addArrow = (a, b) => a + b;
console.log(addArrow(2,3)); // 5
~~~

~~~javascript
// Arrow ohne {}
const square = x => x * x;
console.log(square(5)); // 25
~~~

~~~javascript
// Default Parameter
function greet(name = "Gast") {
  return `Hallo ${name}`;
}
console.log(greet());      // "Hallo Gast"
console.log(greet("Max")); // "Hallo Max"
~~~

---

## 6. Arrays

~~~javascript
const numbers = [1, 2, 3];
numbers.push(4);
numbers.pop();
console.log(numbers); // [1,2,3]
~~~

~~~javascript
numbers.map(n => n * 2);       // [2,4,6]
numbers.filter(n => n > 1);    // [2,3]
numbers.reduce((a,b) => a+b, 0); // 6
numbers.find(n => n===2);      // 2
numbers.includes(3);           // true
~~~

~~~javascript
const copy = [...numbers];
console.log(copy); // [1,2,3]
~~~

---

## 7. Objekte

~~~javascript
const user = {
  name: "Max",
  age: 30,
  greet() {
    console.log(this.name);
  }
};

user.name;      // "Max"
user["age"];    // 30

const { name, age } = user;
console.log(name, age); // "Max" 30

const user2 = { ...user };
~~~

---

## 8. Klassen

~~~javascript
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    console.log(this.name);
  }
}

const p = new Person("Max");
p.greet(); // "Max"
~~~

~~~javascript
class Student extends Person {
  study() {
    console.log("Studying");
  }
}

const s = new Student("Anna");
s.greet(); // "Anna"
s.study(); // "Studying"
~~~

---

## 9. Module (ESM)

~~~javascript
// export
export const value = 42;
export default function main() {}

// import
import main, { value } from "./file.js";
~~~

---

## 10. Asynchrones JavaScript

~~~javascript
setTimeout(() => {
  console.log("Später");
}, 1000);
~~~

~~~javascript
fetch("/api")
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));
~~~

~~~javascript
async function loadData() {
  try {
    const res = await fetch("/api");
    const data = await res.json();
    return data;
  } catch(e) {
    console.error(e);
  }
}
~~~

---

## 11. Fehlerbehandlung

~~~javascript
try {
  throw new Error("Fehler!");
} catch(e) {
  console.error(e.message);
} finally {
  console.log("Done");
}
~~~

---

## 12. Scope & Closures

~~~javascript
function outer() {
  let secret = 42;
  return function inner() {
    return secret;
  };
}

const fn = outer();
console.log(fn()); // 42
~~~

---

## 13. this

~~~javascript
const obj = {
  value: 10,
  normal() {
    console.log(this.value);
  },
  arrow: () => {
    console.log(this.value);
  }
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
button.addEventListener("click", event => {
  event.preventDefault();
});
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
localStorage.setItem("key", "value");
localStorage.getItem("key");

sessionStorage.setItem("key", "value");
~~~

---

## 18. JSON

~~~javascript
const json = JSON.stringify(user);
const objBack = JSON.parse(json);
~~~

---

## 19. Reguläre Ausdrücke

~~~javascript
const emailRegex = /^\S+@\S+\.\S+$/;
emailRegex.test("test@test.de"); // true
~~~

---

## 20. Moderne Features

~~~javascript
obj?.prop;
obj?.method?.();
~~~

~~~javascript
const unique = [...new Set([1,1,2])];
~~~

~~~javascript
structuredClone(user);
~~~

---

## 21. Best Practices

- const vor let
- === statt ==
- kleine, reine Funktionen
- Immutability bevorzugen
- async/await statt Callbacks
- kein globaler Scope
- Lesbarkeit > Cleverness

---

## Ende

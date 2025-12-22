# JavaScript Cheat Sheet – LERNVERSION 📘 (ES6+)

Diese Version erklärt **WARUM** und **WIE** Dinge funktionieren.
Geeignet für Einsteiger & Auffrischer (Browser & Node.js).

---

## 1. Grundlagen

// JavaScript läuft single-threaded und ist ereignisbasiert
// Code wird von oben nach unten gelesen

// Einzeiliger Kommentar
/* Mehrzeiliger Kommentar */

console.log("Hello World"); // Ausgabe in der Konsole

---

## 2. Variablen & Datentypen

// var → veraltet, function-scoped (nicht benutzen)
var old = 1;

// let → veränderbar, block-scoped
let counter = 0;
counter++;

// const → NICHT neu zuweisen (Objekte/Arrays bleiben veränderbar)
const pi = 3.14;

// Primitive Datentypen (immutable)
string
number
boolean
null        // absichtlich leer
undefined   // nicht definiert
symbol
bigint

typeof "abc";   // "string"
typeof null;    // "object" ← JS Bug (merken!)

---

## 3. Operatoren

// Vergleich
1 == "1";   // true  (Typumwandlung!)
1 === "1";  // false (EMPFOHLEN)

!=   !==   >   <   >=   <=

// Logische Operatoren
true && false; // UND
true || false; // ODER
!true;         // NICHT

// Ternärer Operator
const status = age >= 18 ? "volljährig" : "minderjährig";

// Nullish Coalescing (nur null / undefined)
value ?? "Default";

// Boolean Cast
!!value;

---

## 4. Kontrollstrukturen

if (score > 90) {
  grade = "A";
} else if (score > 80) {
  grade = "B";
} else {
  grade = "C";
}

// switch → gut für feste Werte
switch (role) {
  case "admin":
    break;
  default:
}

// Schleifen
for (let i = 0; i < 3; i++) {}
while (condition) {}
do {} while (false);

// Iteration
for (const value of array) {}   // Werte
for (const key in object) {}    // Schlüssel

---

## 5. Funktionen

// Normale Funktion
function add(a, b) {
  return a + b;
}

// Arrow Function
const addArrow = (a, b) => a + b;

// Arrow ohne {}
const square = x => x * x;

// Default Parameter
function greet(name = "Gast") {
  return `Hallo ${name}`;
}

---

## 6. Arrays

const numbers = [1, 2, 3];

// Mutation
numbers.push(4);
numbers.pop();

// Iteration (functional, bevorzugt!)
numbers.map(n => n * 2);        // transformieren
numbers.filter(n => n > 1);     // filtern
numbers.reduce((a, b) => a + b, 0); // reduzieren

numbers.find(n => n === 2);
numbers.includes(3);

// Kopieren
const copy = [...numbers];

---

## 7. Objekte

const user = {
  name: "Max",
  age: 30,
  greet() {
    console.log(this.name); // this → aktuelles Objekt
  }
};

// Zugriff
user.name;
user["age"];

// Destructuring
const { name, age } = user;

// Kopieren
const user2 = { ...user };

---

## 8. Klassen

// Klassen sind syntaktischer Zucker für Prototypen
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log(`Hi ${this.name}`);
  }
}

// Vererbung
class Student extends Person {
  study() {}
}

---

## 9. Module (ESM)

// export
export const value = 42;
export default function main() {}

// import
import main, { value } from "./file.js";

---

## 10. Asynchrones JavaScript

// Callback
setTimeout(() => {
  console.log("Später");
}, 1000);

// Promise
fetch(url)
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));

// Async / Await (EMPFOHLEN)
async function loadData() {
  try {
    const res = await fetch(url);
    return await res.json();
  } catch (e) {
    console.error(e);
  }
}

---

## 11. Fehlerbehandlung

try {
  throw new Error("Fehler!");
} catch (e) {
  console.error(e.message);
} finally {
  console.log("Immer ausgeführt");
}

---

## 12. Scope & Closures

// Scope = Sichtbarkeit von Variablen
function outer() {
  let secret = 42;

  // Closure merkt sich den Scope
  return function inner() {
    return secret;
  };
}

---

## 13. this (wichtig!)

// this ist KONTEXTabhängig
// Arrow Functions haben KEIN eigenes this

const obj = {
  value: 10,
  normal() {
    console.log(this.value); // 10
  },
  arrow: () => {
    console.log(this.value); // undefined
  }
};

---

## 14. DOM Manipulation (Browser)

document.querySelector(".box");
document.getElementById("id");

element.textContent = "Text";
element.innerHTML = "<b>HTML</b>";
element.classList.add("active");

---

## 15. Events

button.addEventListener("click", event => {
  event.preventDefault();
});

---

## 16. Browser APIs

navigator.userAgent;
window.location.href;
window.history.back();

---

## 17. Storage

// Persistente Daten
localStorage.setItem("key", "value");
localStorage.getItem("key");

// Session-bezogen
sessionStorage.setItem("key", "value");

---

## 18. JSON

const json = JSON.stringify(user);
const objBack = JSON.parse(json);

---

## 19. Reguläre Ausdrücke

const emailRegex = /^\S+@\S+\.\S+$/;
emailRegex.test("test@test.de");

---

## 20. Moderne Features

obj?.prop;
obj?.method?.();

const unique = [...new Set([1,1,2])];

// Deep Copy
structuredClone(obj);

---

## 21. Best Practices (MERKEN!)

- const vor let
- === statt ==
- kleine, reine Funktionen
- Immutability bevorzugen
- async/await statt Callbacks
- kein globaler Scope
- Lesbarkeit > Cleverness

---

## Ende

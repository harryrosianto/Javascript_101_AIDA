## Table of Contents

- Apa itu JavaScript
- Paradigma JavaScript
- Integrasi dengan HTML
- Hello World
- Variabel & Tipe Data
- Control Flow
- Function
- DOM
- DOM Selection
- Manipulasi Konten
- CSS Manipulation
- Manipulasi Elemen
- Attribute
- Event Handling
- DOM Traversing
- Hands-On Projects
- Async JavaScript
- Fetch API
- Modern JavaScript Syntax
- Common Pitfalls
- Best Practice

---

## Apa itu JavaScript

JavaScript adalah bahasa pemrograman yang digunakan untuk membuat halaman web menjadi interaktif.

Karakteristik:
- High-level (tidak mengatur memori manual)
- Dynamic typing
- Single-threaded (dengan async support)
- Bisa berjalan di browser dan server (Node.js)

---

## Paradigma JavaScript

### Imperative
```js
let total = 0;
total = total + 5;
````

### Declarative

```js
let numbers = [1,2,3];
let doubled = numbers.map(n => n * 2);
```

### Object-Oriented

```js
let user = {
  name: "Harry",
  greet() {
    console.log("Hello " + this.name);
  }
};
```

### Functional

```js
function sayHello() {
  return function() {
    console.log("Hello!");
  }
}
```

---

## Integrasi dengan HTML

### Inline

```html
<button onclick="alert('Hello')">Klik</button>
```

### Internal

```html
<script>
  console.log("Hello");
</script>
```

### External (Best Practice)

```html
<script src="script.js"></script>
```

---

## Hello World

### HTML

```html
<h1 id="judul">Hello</h1>
<script src="script.js"></script>
```

### JavaScript

```js
let judul = document.getElementById("judul");
judul.innerText = "Hello JavaScript!";
```

---

## Variabel & Tipe Data

```js
let nama = "Harry";
const umur = 20;
let aktif = true;
let array = [1,2,3];
let obj = {nama:"A"};
let kosong = null;
let undefinedVar;
```

---

## Control Flow

### If Else

```js
if (umur >= 18) {
  console.log("Dewasa");
} else {
  console.log("Anak-anak");
}
```

### Loop

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

---

## Function

```js
function tambah(a, b) {
  return a + b;
}

const tambah2 = (a, b) => a + b;
```

---

## DOM (Document Object Model)

DOM adalah representasi HTML dalam bentuk objek yang bisa dimanipulasi oleh JavaScript.

---

## DOM Selection

```js
document.getElementById("id");
document.querySelector(".class");
document.querySelectorAll("li");
document.getElementsByClassName("item");
```

---

## Manipulasi Konten

```js
element.innerText = "Text";
element.innerHTML = "<b>Bold</b>";
element.textContent = "Text";
```

---

## CSS Manipulation

### Inline Style

```js
element.style.backgroundColor = "red";
```

### classList

```js
element.classList.add("active");
element.classList.remove("active");
element.classList.toggle("active");
element.classList.contains("active");
```

---

## Manipulasi Elemen

```js
let el = document.createElement("li");
document.body.appendChild(el);

el.remove();
```

---

## Attribute

```js
element.getAttribute("href");
element.setAttribute("href", "https://google.com");
element.removeAttribute("target");
```

---

## Event Handling

```js
button.addEventListener("click", function() {
  console.log("Klik!");
});
```

### Input Event

```js
input.addEventListener("input", (e) => {
  console.log(e.target.value);
});
```

---

## DOM Traversing

```js
element.parentElement;
element.children;
element.nextElementSibling;
element.previousElementSibling;
```

---

## Hands-On Projects

### Dark Mode Toggle

```html
<button id="btn">Toggle</button>
<div id="box">Hello</div>
```

```css
.dark {
  background: black;
  color: white;
}
```

```js
let btn = document.getElementById("btn");
let box = document.getElementById("box");

btn.addEventListener("click", () => {
  box.classList.toggle("dark");
});
```

---

### Counter App

```js
let angka = 0;

function tambah() {
  angka++;
  document.getElementById("angka").innerText = angka;
}

function kurang() {
  angka--;
  document.getElementById("angka").innerText = angka;
}
```

---

### Todo List

```js
function tambahTask() {
  let input = document.getElementById("inputTask");
  let li = document.createElement("li");

  li.innerText = input.value;

  document.getElementById("list").appendChild(li);

  input.value = "";
}
```

---

## Async JavaScript

### Callback

```js
setTimeout(() => {
  console.log("Delay");
}, 2000);
```

### Promise

```js
new Promise((resolve) => {
  resolve("OK");
}).then(res => console.log(res));
```

### Async/Await

```js
async function getData() {
  let res = await fetch("https://api.com");
}
```

---

## Fetch API

```js
fetch("https://jsonplaceholder.typicode.com/users")
  .then(res => res.json())
  .then(data => console.log(data));
```

---

## Modern JavaScript Syntax

### Template Literal

```js
let nama = "Harry";
console.log(`Halo ${nama}`);
```

### Destructuring

```js
let {nama, umur} = {nama:"A", umur:20};
```

### Spread Operator

```js
let arr = [1,2];
let baru = [...arr, 3];
```

### Array Methods

```js
arr.map(x => x*2);
arr.filter(x => x>1);
arr.reduce((a,b)=>a+b);
```

---

## Common Pitfalls

```js
5 == "5"   // true
5 === "5"  // false
```

* Hindari penggunaan `var`
* Perhatikan hoisting
* Gunakan `===`

---

## Best Practice

* Gunakan `const` sebagai default
* Gunakan `let` jika perlu perubahan
* Hindari `var`
* Gunakan `querySelector`
* Gunakan `classList` untuk styling
* Pisahkan file HTML, CSS, dan JavaScript

---

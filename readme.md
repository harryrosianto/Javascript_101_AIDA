# JavaScript untuk Web: Panduan Lengkap

Materi ini mencakup JavaScript dari dasar hingga manipulasi DOM dan CSS secara menyeluruh, dirancang sebagai referensi komprehensif untuk pengembangan web.

---

## Daftar Isi

1. [Apa itu JavaScript?](#1-apa-itu-javascript)
2. [Fakta-Fakta JavaScript](#2-fakta-fakta-javascript)
3. [Paradigma Pemrograman JavaScript](#3-paradigma-pemrograman-javascript)
4. [Cara Menyisipkan JavaScript ke HTML](#4-cara-menyisipkan-javascript-ke-html)
5. [Sintaks Dasar](#5-sintaks-dasar)
6. [Tipe Data](#6-tipe-data)
7. [Variabel](#7-variabel)
8. [Operator](#8-operator)
9. [Kontrol Alur (Control Flow)](#9-kontrol-alur-control-flow)
10. [Fungsi (Function)](#10-fungsi-function)
11. [Array](#11-array)
12. [Object](#12-object)
13. [Destructuring](#13-destructuring)
14. [Spread dan Rest Operator](#14-spread-dan-rest-operator)
15. [Iterasi dan Looping](#15-iterasi-dan-looping)
16. [Error Handling](#16-error-handling)
17. [Asynchronous JavaScript](#17-asynchronous-javascript)
18. [ES6+ Modern Syntax](#18-es6-modern-syntax)
19. [DOM (Document Object Model)](#19-dom-document-object-model)
20. [Event Handling](#20-event-handling)
21. [Manipulasi CSS dengan JavaScript](#21-manipulasi-css-dengan-javascript)
22. [Form Handling](#22-form-handling)
23. [Local Storage dan Session Storage](#23-local-storage-dan-session-storage)
24. [Fetch API dan HTTP Request](#24-fetch-api-dan-http-request)
25. [Pola Umum dan Best Practice](#25-pola-umum-dan-best-practice)

---

## 1. Apa itu JavaScript?

JavaScript adalah bahasa pemrograman tingkat tinggi, dinamis, dan interpreted yang awalnya diciptakan untuk membuat halaman web menjadi interaktif. Diciptakan oleh **Brendan Eich** pada tahun **1995** saat bekerja di Netscape, JavaScript awalnya bernama Mocha, lalu LiveScript, sebelum akhirnya dinamai JavaScript.

Saat ini JavaScript bukan hanya bahasa untuk browser. Dengan hadirnya **Node.js**, JavaScript juga dapat berjalan di sisi server, sehingga menjadi bahasa yang bersifat full-stack.

**Peran JavaScript dalam web:**

- **HTML** mendefinisikan struktur dan konten halaman.
- **CSS** menentukan tampilan dan gaya visual.
- **JavaScript** mengatur perilaku, logika, dan interaktivitas halaman.

JavaScript dieksekusi langsung oleh mesin JavaScript (JavaScript Engine) yang ada di dalam browser, seperti:

| Browser | JavaScript Engine |
|---|---|
| Google Chrome | V8 |
| Mozilla Firefox | SpiderMonkey |
| Safari | JavaScriptCore (Nitro) |
| Microsoft Edge | V8 (Chromium-based) |

---

## 2. Fakta-Fakta JavaScript

- JavaScript adalah salah satu dari tiga bahasa inti web, bersama HTML dan CSS.
- JavaScript **bukan** Java. Meski namanya mirip, keduanya adalah bahasa yang berbeda dengan desain dan ekosistem yang berbeda pula. Penamaan "JavaScript" lebih bersifat strategis marketing di era 1990-an.
- JavaScript merupakan bahasa yang **weakly typed** (tidak perlu mendeklarasikan tipe data secara eksplisit) dan **dynamically typed** (tipe data ditentukan saat runtime).
- JavaScript menggunakan model concurrency berbasis **event loop** dan **single-threaded**, artinya hanya bisa mengeksekusi satu hal dalam satu waktu, namun mampu menangani operasi asynchronous melalui callback, Promise, dan async/await.
- JavaScript mengikuti standar **ECMAScript (ES)** yang dikelola oleh ECMA International. Versi penting: ES5 (2009), ES6/ES2015 (2015), dan update tahunan setelah itu.
- JavaScript adalah bahasa yang **interpreted**, namun engine modern seperti V8 menggunakan teknik **Just-In-Time (JIT) Compilation** untuk meningkatkan performa.
- JavaScript mendukung **first-class functions**, artinya fungsi adalah nilai (value) yang dapat disimpan dalam variabel, dikirim sebagai argumen, dan dikembalikan dari fungsi lain.
- JavaScript menggunakan **prototype-based inheritance**, bukan class-based inheritance seperti Java atau C++ (meskipun sintaks `class` hadir di ES6, di baliknya tetap berbasis prototype).
- JavaScript dapat berjalan di **browser** maupun di **server** (Node.js), bahkan di perangkat IoT.
- JavaScript adalah bahasa nomor satu yang paling banyak digunakan di dunia berdasarkan survei Stack Overflow secara berturut-turut.

---

## 3. Paradigma Pemrograman JavaScript

JavaScript adalah bahasa **multi-paradigma**, yang berarti mendukung lebih dari satu gaya pemrograman:

### 3.1 Pemrograman Prosedural (Procedural)

Gaya yang paling sederhana. Kode dieksekusi baris per baris, dari atas ke bawah. Logika dikemas dalam fungsi yang dipanggil secara berurutan.

```js
// Contoh pemrograman prosedural
function hitungLuasLingkaran(r) {
  return Math.PI * r * r;
}

var r = 7;
var luas = hitungLuasLingkaran(r);
console.log("Luas lingkaran:", luas);
```

### 3.2 Pemrograman Berorientasi Objek (OOP - Object-Oriented Programming)

JavaScript mendukung OOP melalui sistem prototype dan sintaks `class` (ES6).

```js
// Contoh OOP dengan class (ES6)
class Hewan {
  // constructor adalah metode khusus yang dipanggil saat objek dibuat
  constructor(nama, suara) {
    this.nama = nama;   // 'this' merujuk ke instance objek saat ini
    this.suara = suara;
  }

  // Metode instance - tersedia untuk setiap objek yang dibuat dari class ini
  bersuara() {
    return `${this.nama} berkata: ${this.suara}`;
  }
}

// Inheritance (pewarisan) - Anjing mewarisi sifat Hewan
class Anjing extends Hewan {
  constructor(nama) {
    super(nama, "Guk guk"); // super() memanggil constructor dari class induk
  }

  // Metode tambahan khusus Anjing
  mengambilBola() {
    return `${this.nama} mengambil bola!`;
  }
}

const anjing = new Anjing("Rex");
console.log(anjing.bersuara());      // Rex berkata: Guk guk
console.log(anjing.mengambilBola()); // Rex mengambil bola!
```

### 3.3 Pemrograman Fungsional (Functional Programming)

Paradigma yang memperlakukan komputasi sebagai evaluasi fungsi matematika. Menghindari perubahan state dan data mutable.

Konsep utama:
- **Pure function**: Fungsi yang selalu menghasilkan output sama untuk input yang sama, tanpa efek samping.
- **Immutability**: Data tidak diubah, melainkan dibuat salinan baru.
- **Higher-order function**: Fungsi yang menerima fungsi lain sebagai argumen atau mengembalikan fungsi.

```js
// Pure function - tidak mengubah data di luar fungsi
const tambah = (a, b) => a + b;

// Higher-order function - menerima fungsi sebagai argumen
const angka = [1, 2, 3, 4, 5];

// .map() mengambil setiap elemen dan mengubahnya berdasarkan fungsi yang diberikan
const dikuadratkan = angka.map(n => n * n);
// Hasil: [1, 4, 9, 16, 25]

// .filter() menyaring elemen yang memenuhi kondisi
const genap = angka.filter(n => n % 2 === 0);
// Hasil: [2, 4]

// .reduce() mengakumulasi semua elemen menjadi satu nilai
const total = angka.reduce((akumulator, nilaiSaatIni) => akumulator + nilaiSaatIni, 0);
// Hasil: 15

// Chaining - menggabungkan beberapa method sekaligus
const hasil = angka
  .filter(n => n % 2 !== 0)  // ambil yang ganjil: [1, 3, 5]
  .map(n => n * 10)           // kalikan 10: [10, 30, 50]
  .reduce((acc, n) => acc + n, 0); // jumlahkan: 90
```

### 3.4 Pemrograman Event-Driven

JavaScript di browser sangat bergantung pada paradigma event-driven, di mana eksekusi kode dipicu oleh kejadian (event) seperti klik mouse, input keyboard, atau respon jaringan.

```js
// Kode dieksekusi hanya ketika event "click" terjadi pada tombol
document.getElementById("tombol").addEventListener("click", function () {
  console.log("Tombol diklik!");
});
```

---

## 4. Cara Menyisipkan JavaScript ke HTML

### 4.1 Inline (langsung di tag HTML)

```html
<!-- Tidak disarankan untuk kode yang kompleks -->
<button onclick="alert('Halo!')">Klik Saya</button>
```

### 4.2 Internal Script (di dalam tag `<script>`)

```html
<!DOCTYPE html>
<html>
<head>
  <title>Contoh JS</title>
</head>
<body>
  <h1>Halaman Saya</h1>

  <!-- Tag script sebaiknya diletakkan sebelum penutup </body>
       agar HTML dimuat lebih dulu sebelum script dieksekusi -->
  <script>
    console.log("JavaScript berjalan!");
  </script>
</body>
</html>
```

### 4.3 External Script (file `.js` terpisah)

```html
<!-- Di dalam HTML -->
<!-- defer: script dieksekusi setelah HTML selesai di-parse -->
<script src="app.js" defer></script>

<!-- async: script diunduh secara asynchronous, langsung dieksekusi saat selesai -->
<script src="analytics.js" async></script>
```

**Perbedaan `defer` vs `async`:**

| Atribut | Unduh | Eksekusi | Urutan |
|---|---|---|---|
| Tanpa atribut | Memblokir parsing | Segera | Berurutan |
| `async` | Paralel | Segera setelah selesai unduh | Tidak dijamin |
| `defer` | Paralel | Setelah HTML selesai di-parse | Berurutan |

---

## 5. Sintaks Dasar

### 5.1 Statement dan Semicolon

```js
// Setiap statement (pernyataan) diakhiri dengan titik koma
// JavaScript sebenarnya memiliki Automatic Semicolon Insertion (ASI),
// namun praktik terbaik adalah selalu menuliskan titik koma secara eksplisit

let x = 5;
let y = 10;
let z = x + y;
```

### 5.2 Komentar

```js
// Ini adalah komentar satu baris - diabaikan oleh JavaScript engine

/*
  Ini adalah komentar
  multi-baris
  - cocok untuk penjelasan panjang
*/

/**
 * JSDoc comment - digunakan untuk dokumentasi fungsi
 * @param {number} a - angka pertama
 * @param {number} b - angka kedua
 * @returns {number} hasil penjumlahan
 */
function tambah(a, b) {
  return a + b;
}
```

### 5.3 console

```js
console.log("Pesan biasa");          // output teks ke konsol browser
console.warn("Ini peringatan");       // output dengan gaya peringatan (kuning)
console.error("Ini error");           // output dengan gaya error (merah)
console.info("Informasi");            // output informasi
console.table([1, 2, 3]);            // output dalam format tabel
console.group("Grup");               // mulai grup yang bisa dilipat
console.groupEnd();                  // akhir grup
console.time("timer");               // mulai timer
console.timeEnd("timer");            // akhir timer, tampilkan durasi
console.dir(document.body);         // menampilkan properti DOM element secara detail
console.clear();                     // bersihkan konsol
```

---

## 6. Tipe Data

JavaScript memiliki **8 tipe data**, dibagi menjadi dua kategori:

### 6.1 Tipe Primitif (Primitive Types)

Primitif disimpan **berdasarkan nilai** (by value). Saat disalin, nilai aslinya tidak terpengaruh.

```js
// 1. Number - semua angka, integer maupun desimal
let umur = 25;
let tinggi = 170.5;
let negatif = -10;
let besar = 1e6;      // notasi ilmiah: 1.000.000
let hex = 0xFF;       // hexadecimal: 255
let biner = 0b1010;   // binary: 10
let oktal = 0o17;     // octal: 15

// Nilai spesial Number
console.log(Infinity);          // tak terhingga
console.log(-Infinity);         // tak terhingga negatif
console.log(NaN);               // Not a Number - hasil operasi matematika yang tidak valid
console.log(Number.MAX_SAFE_INTEGER); // 9007199254740991

// 2. String - teks, diapit tanda kutip tunggal, ganda, atau backtick
let nama = "Budi";
let kota = 'Bandung';
let salam = `Halo, nama saya ${nama} dari ${kota}`; // template literal

// String methods
console.log(nama.length);           // 4 - panjang string
console.log(nama.toUpperCase());    // "BUDI"
console.log(nama.toLowerCase());    // "budi"
console.log("  spasi  ".trim());    // "spasi" - hilangkan spasi di awal/akhir
console.log("halo".includes("al")); // true
console.log("halo".startsWith("ha")); // true
console.log("halo".endsWith("lo"));   // true
console.log("halo".replace("al", "el")); // "helo"
console.log("a,b,c".split(","));    // ["a", "b", "c"]
console.log("ha".repeat(3));        // "hahaha"
console.log("abc".charAt(1));       // "b"
console.log("abc"[1]);              // "b" - akses via index
console.log("abc".indexOf("b"));    // 1
console.log("abc".slice(1, 3));     // "bc"
console.log("abc".substring(1, 3)); // "bc"
console.log("5".padStart(3, "0"));  // "005"
console.log("5".padEnd(3, "0"));    // "500"

// 3. Boolean - hanya dua nilai: true atau false
let aktif = true;
let sudahLogin = false;

// 4. undefined - variabel yang dideklarasikan tapi belum diberi nilai
let belumDiisi;
console.log(belumDiisi); // undefined

// 5. null - nilai kosong yang disengaja (intentional absence of value)
let dataPengguna = null; // sengaja dikosongkan

// 6. Symbol - nilai unik yang tidak dapat disamakan (ES6)
const id1 = Symbol("id");
const id2 = Symbol("id");
console.log(id1 === id2); // false - setiap Symbol selalu unik

// 7. BigInt - angka integer yang sangat besar melebihi batas Number (ES2020)
const angkaBesar = 9007199254740991n; // diakhiri dengan "n"
const juga = BigInt("123456789012345678901234567890");
```

### 6.2 Tipe Referensi (Reference Types)

Referensi disimpan **berdasarkan referensi** (by reference). Saat disalin, keduanya merujuk ke objek yang sama.

```js
// Object, Array, dan Function adalah tipe referensi

// Demonstrasi by reference
const obj1 = { nilai: 10 };
const obj2 = obj1;        // obj2 menunjuk ke objek YANG SAMA dengan obj1
obj2.nilai = 99;
console.log(obj1.nilai);  // 99 - obj1 juga berubah karena berbagi referensi

// Untuk membuat salinan yang benar-benar terpisah, gunakan spread:
const obj3 = { ...obj1 }; // shallow copy
obj3.nilai = 0;
console.log(obj1.nilai);  // 99 - obj1 tidak terpengaruh
```

### 6.3 Pemeriksaan Tipe Data

```js
// typeof - mengembalikan tipe data dalam bentuk string
console.log(typeof 42);          // "number"
console.log(typeof "halo");      // "string"
console.log(typeof true);        // "boolean"
console.log(typeof undefined);   // "undefined"
console.log(typeof null);        // "object" -- ini adalah bug terkenal di JS!
console.log(typeof {});          // "object"
console.log(typeof []);          // "object" -- array juga object
console.log(typeof function(){}); // "function"
console.log(typeof Symbol());    // "symbol"
console.log(typeof 1n);          // "bigint"

// Cara memeriksa array secara akurat
console.log(Array.isArray([]));  // true
console.log(Array.isArray({}));  // false

// instanceof - memeriksa apakah objek adalah instance dari class tertentu
console.log([] instanceof Array);   // true
console.log({} instanceof Object);  // true
```

---

## 7. Variabel

### 7.1 `var` (cara lama, hindari)

```js
// var memiliki function scope, bukan block scope
// var juga mengalami "hoisting" - deklarasi diangkat ke atas scope

function contohVar() {
  if (true) {
    var pesan = "Halo"; // dideklarasikan di dalam block if
  }
  console.log(pesan); // "Halo" - masih bisa diakses di luar block!
}

// Hoisting var - deklarasi terangkat, tapi nilainya tidak
console.log(x); // undefined - tidak error, tapi nilainya belum ada
var x = 5;
console.log(x); // 5
```

### 7.2 `let` (blok scope, dapat diubah)

```js
// let memiliki block scope - hanya bisa diakses dalam block { } tempat ia dideklarasikan

function contohLet() {
  if (true) {
    let pesan = "Halo"; // hanya ada di dalam block if ini
  }
  // console.log(pesan); // ReferenceError! - tidak bisa diakses di luar block
}

let counter = 0;
counter = 1;  // bisa diubah nilainya
counter++;    // bisa di-increment
```

### 7.3 `const` (blok scope, tidak dapat di-reassign)

```js
// const tidak bisa di-reassign (diganti nilainya),
// namun untuk object/array, propertinya masih bisa diubah

const PI = 3.14159;
// PI = 3; // TypeError! - tidak bisa di-reassign

const orang = { nama: "Andi" };
orang.nama = "Budi"; // BOLEH - properti bisa diubah
// orang = {};       // TypeError! - variabelnya tidak bisa di-reassign

const buah = ["apel", "mangga"];
buah.push("jeruk");  // BOLEH - array bisa dimodifikasi
// buah = [];         // TypeError!

// Gunakan const sebagai default, pakai let hanya jika nilai perlu diubah
// Hindari var dalam kode modern
```

### 7.4 Scope dan Hoisting

```js
// Global Scope - dapat diakses dari mana saja
const globalVar = "saya global";

function fungsi() {
  // Function Scope - hanya dapat diakses di dalam fungsi ini
  const lokal = "saya lokal";

  if (true) {
    // Block Scope - hanya dapat diakses di dalam block ini
    const dalamBlock = "saya dalam block";
    let jugaDalamBlock = "saya juga";
    console.log(globalVar);    // bisa - akses ke luar
    console.log(lokal);        // bisa - akses ke luar
    console.log(dalamBlock);   // bisa
  }

  // console.log(dalamBlock); // ReferenceError!
}
```

---

## 8. Operator

### 8.1 Operator Aritmatika

```js
let a = 10, b = 3;

console.log(a + b);   // 13 - penjumlahan
console.log(a - b);   // 7  - pengurangan
console.log(a * b);   // 30 - perkalian
console.log(a / b);   // 3.333... - pembagian
console.log(a % b);   // 1  - modulus (sisa bagi)
console.log(a ** b);  // 1000 - eksponen (10 pangkat 3)

// Increment dan decrement
let x = 5;
x++;       // post-increment: gunakan dulu, baru tambah
++x;       // pre-increment: tambah dulu, baru gunakan
x--;       // post-decrement
--x;       // pre-decrement

// Assignment operators
x += 5;   // x = x + 5
x -= 3;   // x = x - 3
x *= 2;   // x = x * 2
x /= 4;   // x = x / 4
x %= 3;   // x = x % 3
x **= 2;  // x = x ** 2
```

### 8.2 Operator Perbandingan

```js
// == (loose equality) - membandingkan nilai, mengabaikan tipe
console.log(5 == "5");   // true  - angka dikonversi ke string (atau sebaliknya)
console.log(0 == false); // true  - false dikonversi ke 0

// === (strict equality) - membandingkan nilai DAN tipe - SELALU gunakan ini
console.log(5 === "5");  // false - tipe berbeda
console.log(5 === 5);    // true

// != (loose inequality) vs !== (strict inequality)
console.log(5 != "5");   // false - dianggap sama karena coercion
console.log(5 !== "5");  // true  - tipe berbeda

// Perbandingan lainnya
console.log(5 > 3);      // true
console.log(5 < 3);      // false
console.log(5 >= 5);     // true
console.log(5 <= 4);     // false
```

### 8.3 Operator Logika

```js
// && (AND) - true jika KEDUA sisi true
console.log(true && true);   // true
console.log(true && false);  // false

// || (OR) - true jika SALAH SATU sisi true
console.log(true || false);  // true
console.log(false || false); // false

// ! (NOT) - membalik nilai boolean
console.log(!true);  // false
console.log(!false); // true

// Short-circuit evaluation
// && berhenti jika menemukan false pertama
const hasil1 = null && "tidak pernah dieksekusi"; // null

// || berhenti jika menemukan true pertama
const hasil2 = null || "nilai default"; // "nilai default"

// ?? (Nullish Coalescing - ES2020) - hanya mengembalikan sisi kanan jika sisi kiri null/undefined
const nama = null ?? "Anonim";       // "Anonim"
const umur = 0 ?? 18;               // 0 - tidak seperti ||, 0 bukan dianggap falsy oleh ??

// ?. (Optional Chaining - ES2020) - aman mengakses property yang mungkin null/undefined
const pengguna = null;
console.log(pengguna?.nama);         // undefined - tidak throw error
console.log(pengguna?.alamat?.kota); // undefined
```

### 8.4 Operator Lainnya

```js
// Ternary operator - kondisi ? nilaiJikaTrue : nilaiJikaFalse
const umur = 20;
const status = umur >= 18 ? "Dewasa" : "Remaja"; // "Dewasa"

// Comma operator - mengevaluasi semua ekspresi, mengembalikan yang terakhir
const z = (1, 2, 3); // z = 3

// typeof dan instanceof (sudah dibahas di bagian Tipe Data)

// in - memeriksa apakah property ada dalam object
const mobil = { merek: "Toyota", tahun: 2020 };
console.log("merek" in mobil);    // true
console.log("warna" in mobil);    // false

// delete - menghapus property dari object
delete mobil.tahun;
console.log(mobil); // { merek: "Toyota" }
```

---

## 9. Kontrol Alur (Control Flow)

### 9.1 `if`, `else if`, `else`

```js
const nilai = 75;

if (nilai >= 90) {
  // Block ini dieksekusi jika nilai >= 90
  console.log("A");
} else if (nilai >= 80) {
  // Diperiksa jika kondisi pertama false
  console.log("B");
} else if (nilai >= 70) {
  // Diperiksa jika kondisi sebelumnya false
  console.log("C");
} else {
  // Dieksekusi jika semua kondisi di atas false
  console.log("D atau E");
}
```

### 9.2 `switch`

```js
const hari = "Senin";

switch (hari) {
  case "Senin":       // jika hari === "Senin"
  case "Selasa":      // atau hari === "Selasa" (fall-through)
  case "Rabu":
  case "Kamis":
  case "Jumat":
    console.log("Hari kerja");
    break; // penting! tanpa break, eksekusi berlanjut ke case berikutnya

  case "Sabtu":
  case "Minggu":
    console.log("Hari libur");
    break;

  default: // dieksekusi jika tidak ada case yang cocok
    console.log("Hari tidak valid");
}
```

### 9.3 Truthy dan Falsy

JavaScript secara otomatis mengonversi nilai ke boolean dalam konteks kondisi.

```js
// Nilai-nilai yang dianggap FALSY (dianggap false dalam konteks boolean):
// false, 0, -0, 0n (BigInt nol), "" (string kosong), null, undefined, NaN

// Semua nilai lainnya dianggap TRUTHY

if (0)         { console.log("tidak dieksekusi"); }
if ("")        { console.log("tidak dieksekusi"); }
if (null)      { console.log("tidak dieksekusi"); }
if (undefined) { console.log("tidak dieksekusi"); }

if (1)         { console.log("dieksekusi"); }   // angka selain 0
if ("a")       { console.log("dieksekusi"); }   // string tidak kosong
if ([])        { console.log("dieksekusi"); }   // array kosong pun truthy!
if ({})        { console.log("dieksekusi"); }   // object kosong pun truthy!
```

---

## 10. Fungsi (Function)

### 10.1 Function Declaration

```js
// Function declaration - di-hoist ke atas scope, bisa dipanggil sebelum dideklarasikan

function sapa(nama, salam = "Halo") {
  // parameter 'salam' memiliki nilai default "Halo"
  return `${salam}, ${nama}!`;
}

console.log(sapa("Budi"));          // "Halo, Budi!"
console.log(sapa("Andi", "Selamat pagi")); // "Selamat pagi, Andi!"
```

### 10.2 Function Expression

```js
// Function expression - tidak di-hoist, hanya bisa dipanggil setelah dideklarasikan

const tambah = function(a, b) {
  return a + b;
};

// Named function expression - nama fungsi hanya tersedia di dalam fungsinya sendiri
const faktorial = function fakt(n) {
  if (n <= 1) return 1;
  return n * fakt(n - 1); // rekursi menggunakan nama 'fakt'
};
```

### 10.3 Arrow Function (ES6)

```js
// Sintaks lebih singkat, dan 'this' merujuk ke konteks luar (lexical this)

// Satu parameter, satu baris - tidak perlu kurung dan return
const kuadrat = n => n * n;

// Beberapa parameter - perlu tanda kurung
const kali = (a, b) => a * b;

// Tanpa parameter - kurung kosong wajib
const salam = () => "Halo!";

// Body lebih dari satu baris - perlu kurung kurawal dan return eksplisit
const hitungLuas = (panjang, lebar) => {
  const luas = panjang * lebar;
  return luas;
};

// Mengembalikan object literal - bungkus dengan tanda kurung
const buatOrang = (nama, umur) => ({ nama, umur });
```

### 10.4 Parameter Khusus

```js
// Rest parameter - mengumpulkan sisa argumen ke dalam array
function jumlahkan(pertama, ...sisanya) {
  // 'sisanya' adalah array yang berisi semua argumen setelah 'pertama'
  return sisanya.reduce((total, n) => total + n, pertama);
}

console.log(jumlahkan(1, 2, 3, 4, 5)); // 15

// arguments object - tersedia di function biasa (bukan arrow function)
function infoArgumen() {
  console.log(arguments);       // Array-like object semua argumen
  console.log(arguments.length);
}

infoArgumen(1, "a", true); // Arguments [1, "a", true]
```

### 10.5 Closure

Closure adalah fungsi yang "mengingat" lingkungan (variabel) tempat ia dibuat, bahkan setelah fungsi luar selesai dieksekusi.

```js
function buatCounter() {
  let hitungan = 0; // variabel ini "terperangkap" dalam closure

  return {
    tambah: function() { hitungan++; },
    kurang: function() { hitungan--; },
    nilai: function() { return hitungan; }
  };
}

const counter = buatCounter();
counter.tambah();
counter.tambah();
counter.tambah();
counter.kurang();
console.log(counter.nilai()); // 2
// 'hitungan' tidak bisa diakses langsung dari luar, tapi tetap hidup

// Contoh practical: fungsi yang menghasilkan fungsi lain
function pengali(faktor) {
  return function(angka) {
    return angka * faktor; // 'faktor' diingat melalui closure
  };
}

const kaliDua = pengali(2);
const kaliTiga = pengali(3);

console.log(kaliDua(5));   // 10
console.log(kaliTiga(5));  // 15
```

### 10.6 IIFE (Immediately Invoked Function Expression)

```js
// Fungsi yang langsung dieksekusi saat dideklarasikan
// Berguna untuk mengisolasi scope dan menghindari polusi global

(function() {
  const lokal = "Hanya ada di sini";
  console.log("IIFE dijalankan!");
})();

// Versi arrow function
(() => {
  console.log("Arrow IIFE");
})();
```

---

## 11. Array

Array adalah koleksi data terurut dengan index berbasis nol.

```js
// Membuat array
const buah = ["apel", "mangga", "jeruk"];
const campuran = [1, "dua", true, null, { nama: "budi" }]; // bisa mix tipe
const kosong = [];
const dariKonstruktor = new Array(3); // array dengan 3 slot kosong

// Akses elemen
console.log(buah[0]);    // "apel" - index dimulai dari 0
console.log(buah[2]);    // "jeruk"
console.log(buah.at(-1)); // "jeruk" - index negatif dari belakang (ES2022)
console.log(buah.length); // 3

// Modifikasi elemen
buah[1] = "pisang"; // ganti "mangga" dengan "pisang"
```

### 11.1 Method Dasar Array

```js
const arr = [1, 2, 3];

// Menambah elemen
arr.push(4);          // tambah di akhir: [1, 2, 3, 4]
arr.unshift(0);       // tambah di awal: [0, 1, 2, 3, 4]

// Menghapus elemen
arr.pop();            // hapus dari akhir, mengembalikan elemen yang dihapus
arr.shift();          // hapus dari awal, mengembalikan elemen yang dihapus

// splice - menambah/menghapus elemen di posisi tertentu
// splice(startIndex, deleteCount, ...itemsToAdd)
arr.splice(1, 0, 99); // di index 1, hapus 0, sisipkan 99
arr.splice(2, 1);     // di index 2, hapus 1 elemen

// Mencari elemen
const angka = [10, 20, 30, 20, 40];
console.log(angka.indexOf(20));      // 1 - index pertama kali ditemukan
console.log(angka.lastIndexOf(20));  // 3 - index terakhir ditemukan
console.log(angka.includes(30));     // true - apakah ada nilai 30?
console.log(angka.find(n => n > 15));     // 20 - elemen pertama yang memenuhi kondisi
console.log(angka.findIndex(n => n > 15)); // 1 - index elemen pertama yang memenuhi kondisi

// Menyalin dan mengiris
const salinan = angka.slice(1, 3); // [20, 30] - dari index 1 sampai (tidak termasuk) 3

// Menggabungkan array
const a = [1, 2];
const b = [3, 4];
const gabung = a.concat(b);       // [1, 2, 3, 4]
const gabungSpread = [...a, ...b]; // [1, 2, 3, 4] - cara modern

// Mengubah array menjadi string
console.log([1, 2, 3].join("-")); // "1-2-3"
console.log([1, 2, 3].toString()); // "1,2,3"

// Membalik array
const dibalik = [1, 2, 3].reverse(); // [3, 2, 1] - mutates original!

// Mengurutkan array
const huruf = ["b", "a", "d", "c"];
huruf.sort(); // ["a", "b", "c", "d"] - sort() mengubah array asli

// sort() dengan angka membutuhkan comparator
const nums = [10, 1, 5, 2];
nums.sort((a, b) => a - b); // [1, 2, 5, 10] - urutan menaik
nums.sort((a, b) => b - a); // [10, 5, 2, 1] - urutan menurun

// Meratakan array bersarang
const bersarang = [1, [2, 3], [4, [5, 6]]];
console.log(bersarang.flat());    // [1, 2, 3, 4, [5, 6]] - satu level
console.log(bersarang.flat(2));   // [1, 2, 3, 4, 5, 6] - dua level
console.log(bersarang.flat(Infinity)); // semua level
```

### 11.2 Method Iterasi Array (Higher-Order)

```js
const siswa = [
  { nama: "Andi", nilai: 80 },
  { nama: "Budi", nilai: 65 },
  { nama: "Cici", nilai: 90 },
  { nama: "Dodi", nilai: 55 },
];

// forEach - iterasi tanpa menghasilkan array baru
siswa.forEach((s, index) => {
  console.log(`${index + 1}. ${s.nama}: ${s.nilai}`);
});

// map - mengubah setiap elemen, menghasilkan array baru dengan panjang sama
const namaSaja = siswa.map(s => s.nama);
// ["Andi", "Budi", "Cici", "Dodi"]

const nilaiBonus = siswa.map(s => ({ ...s, nilai: s.nilai + 5 }));
// Setiap siswa mendapat +5 ke nilainya

// filter - menyaring elemen yang memenuhi kondisi
const lulus = siswa.filter(s => s.nilai >= 70);
// [{ nama: "Andi", nilai: 80 }, { nama: "Cici", nilai: 90 }]

// reduce - mengakumulasi semua elemen menjadi satu nilai
const totalNilai = siswa.reduce((total, s) => total + s.nilai, 0);
// 290

// some - true jika setidaknya satu elemen memenuhi kondisi
const adaYangLulus = siswa.some(s => s.nilai >= 70); // true

// every - true jika SEMUA elemen memenuhi kondisi
const semuaLulus = siswa.every(s => s.nilai >= 70); // false

// flatMap - gabungan map dan flat (satu level)
const kata = ["halo dunia", "selamat pagi"];
const dipisah = kata.flatMap(k => k.split(" "));
// ["halo", "dunia", "selamat", "pagi"]

// Array.from - membuat array dari iterable atau array-like object
const dariString = Array.from("halo"); // ["h", "a", "l", "o"]
const dariRange = Array.from({ length: 5 }, (_, i) => i + 1); // [1, 2, 3, 4, 5]

// Array.of - membuat array dari argumen
const arr = Array.of(1, 2, 3); // [1, 2, 3]
```

---

## 12. Object

Object adalah koleksi pasangan key-value (properti dan nilainya).

```js
// Membuat object
const orang = {
  nama: "Andi",      // key: "nama", value: "Andi"
  umur: 25,
  aktif: true,
  alamat: {           // nested object
    kota: "Bandung",
    provinsi: "Jawa Barat"
  },
  sapa: function() {  // method - fungsi di dalam object
    return `Halo, saya ${this.nama}`; // 'this' merujuk ke object orang
  },
  // Shorthand method (ES6)
  perkenalan() {
    return `Nama saya ${this.nama}, umur ${this.umur}`;
  }
};

// Akses properti
console.log(orang.nama);           // dot notation
console.log(orang["umur"]);        // bracket notation - berguna untuk key dinamis
console.log(orang.alamat.kota);    // akses nested

const kunci = "aktif";
console.log(orang[kunci]);         // bracket notation dengan variabel

// Memodifikasi dan menambah properti
orang.email = "andi@mail.com";     // tambah properti baru
orang.umur = 26;                   // ubah nilai

// Menghapus properti
delete orang.aktif;

// Memeriksa keberadaan properti
console.log("nama" in orang);                   // true
console.log(orang.hasOwnProperty("email"));     // true
```

### 12.1 Method Object Bawaan

```js
const produk = { nama: "Laptop", harga: 15000000, stok: 10 };

// Object.keys() - array semua key
console.log(Object.keys(produk)); // ["nama", "harga", "stok"]

// Object.values() - array semua value
console.log(Object.values(produk)); // ["Laptop", 15000000, 10]

// Object.entries() - array pasangan [key, value]
console.log(Object.entries(produk));
// [["nama", "Laptop"], ["harga", 15000000], ["stok", 10]]

// Object.assign() - menyalin properti dari satu/beberapa objek ke target
const target = { a: 1 };
const sumber = { b: 2, c: 3 };
Object.assign(target, sumber);
console.log(target); // { a: 1, b: 2, c: 3 }

// Object.freeze() - membuat object tidak bisa diubah sama sekali
const konstanta = Object.freeze({ PI: 3.14, E: 2.71 });
konstanta.PI = 99; // akan gagal diam-diam (atau error di strict mode)
console.log(konstanta.PI); // 3.14

// Object.fromEntries() - mengubah array [key, value] kembali ke object
const entries = [["nama", "Andi"], ["umur", 25]];
const objDariEntries = Object.fromEntries(entries);
// { nama: "Andi", umur: 25 }
```

### 12.2 Computed Property Names dan Shorthand

```js
// Shorthand property - jika nama variabel sama dengan nama key
const nama = "Budi";
const umur = 30;
const orang = { nama, umur }; // sama dengan { nama: nama, umur: umur }

// Computed property names - nama key dinamis dalam object literal
const prefix = "get";
const obj = {
  [prefix + "Nama"]: function() { return "Budi"; },
  [`${prefix}Umur`]: function() { return 30; }
};

console.log(obj.getNama()); // "Budi"
console.log(obj.getUmur()); // 30
```

---

## 13. Destructuring

Destructuring adalah cara mengekstrak nilai dari array atau object menjadi variabel terpisah.

### 13.1 Array Destructuring

```js
const koordinat = [10, 20, 30];

// Tanpa destructuring
const x = koordinat[0];
const y = koordinat[1];

// Dengan destructuring - jauh lebih ringkas
const [x, y, z] = koordinat;
console.log(x, y, z); // 10 20 30

// Melewati elemen dengan koma
const [pertama, , ketiga] = koordinat; // lewati elemen kedua
console.log(pertama, ketiga); // 10 30

// Nilai default
const [a = 0, b = 0, c = 0, d = 0] = [1, 2];
console.log(d); // 0 - nilai default karena tidak ada elemen ke-4

// Rest dalam destructuring
const [kepala, ...ekor] = [1, 2, 3, 4, 5];
console.log(kepala); // 1
console.log(ekor);   // [2, 3, 4, 5]

// Swap variabel tanpa variabel sementara
let p = 1, q = 2;
[p, q] = [q, p];
console.log(p, q); // 2 1
```

### 13.2 Object Destructuring

```js
const pengguna = {
  id: 1,
  nama: "Cici",
  umur: 28,
  alamat: {
    kota: "Surabaya",
    kodePos: "60111"
  }
};

// Destructuring dasar
const { nama, umur } = pengguna;
console.log(nama, umur); // "Cici" 28

// Rename saat destructuring
const { nama: namaPanggilan, umur: usia } = pengguna;
console.log(namaPanggilan, usia); // "Cici" 28

// Nilai default
const { email = "tidak ada", nama: n } = pengguna;
console.log(email); // "tidak ada"

// Nested destructuring
const { alamat: { kota, kodePos } } = pengguna;
console.log(kota, kodePos); // "Surabaya" "60111"

// Rest dalam object destructuring
const { id, ...sisaProperty } = pengguna;
console.log(id);             // 1
console.log(sisaProperty);   // { nama, umur, alamat }

// Destructuring sebagai parameter fungsi
function tampilkanProfil({ nama, umur, alamat: { kota } }) {
  return `${nama}, ${umur} tahun, tinggal di ${kota}`;
}

console.log(tampilkanProfil(pengguna));
```

---

## 14. Spread dan Rest Operator

Keduanya menggunakan simbol `...` namun di konteks berbeda.

```js
// --- SPREAD --- menyebarkan elemen

// Spread pada array
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const gabungan = [...arr1, ...arr2];     // [1, 2, 3, 4, 5, 6]
const denganTambahan = [0, ...arr1, 4]; // [0, 1, 2, 3, 4]

// Spread untuk menyalin array (shallow copy)
const salinan = [...arr1];
salinan.push(99);
console.log(arr1); // [1, 2, 3] - tidak terpengaruh

// Spread pada object
const dasar = { warna: "merah", ukuran: "L" };
const ekstra = { brand: "Nike", warna: "biru" }; // warna akan ditimpa
const baju = { ...dasar, ...ekstra };
// { warna: "biru", ukuran: "L", brand: "Nike" }

// Spread untuk menyalin object
const asli = { a: 1, b: 2 };
const kopi = { ...asli, c: 3 };

// Spread saat memanggil fungsi
function tambahTiga(x, y, z) { return x + y + z; }
const angka = [1, 2, 3];
console.log(tambahTiga(...angka)); // 6

// --- REST --- mengumpulkan elemen

// Rest parameter fungsi (sudah dibahas di bagian Fungsi)
function log(pertama, ...sisanya) {
  console.log("Pertama:", pertama);
  console.log("Sisanya:", sisanya);
}

log(1, 2, 3, 4); // Pertama: 1, Sisanya: [2, 3, 4]
```

---

## 15. Iterasi dan Looping

### 15.1 `for` Loop

```js
// for loop klasik
for (let i = 0; i < 5; i++) {
  // i dimulai dari 0, terus selama i < 5, tambah 1 setiap iterasi
  console.log(i); // 0, 1, 2, 3, 4
}

// Nested for loop
for (let baris = 1; baris <= 3; baris++) {
  for (let kolom = 1; kolom <= 3; kolom++) {
    process.stdout.write(`(${baris},${kolom}) `);
  }
  console.log();
}
```

### 15.2 `while` dan `do...while`

```js
// while - eksekusi selama kondisi true
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}

// do...while - eksekusi minimal SATU KALI, lalu periksa kondisi
let j = 10;
do {
  console.log(j); // dieksekusi meskipun j sudah 10 (lebih dari 5)
  j++;
} while (j < 5);
```

### 15.3 `for...of` (iterasi nilai)

```js
// for...of - iterasi nilai dari iterable (array, string, Map, Set, dll)
const buah = ["apel", "mangga", "jeruk"];

for (const item of buah) {
  console.log(item); // "apel", "mangga", "jeruk"
}

// Dengan index menggunakan entries()
for (const [index, nilai] of buah.entries()) {
  console.log(`${index}: ${nilai}`);
}

// Iterasi string
for (const huruf of "halo") {
  console.log(huruf); // "h", "a", "l", "o"
}
```

### 15.4 `for...in` (iterasi key)

```js
// for...in - iterasi KEY (nama properti) dari object
const orang = { nama: "Andi", umur: 25, kota: "Jakarta" };

for (const key in orang) {
  console.log(`${key}: ${orang[key]}`);
}
// nama: Andi
// umur: 25
// kota: Jakarta

// Catatan: for...in juga mengiterasi properti inherited dari prototype
// Gunakan hasOwnProperty untuk memfilter
for (const key in orang) {
  if (orang.hasOwnProperty(key)) {
    // hanya properti milik orang sendiri
  }
}
```

### 15.5 `break` dan `continue`

```js
// break - keluar dari loop sepenuhnya
for (let i = 0; i < 10; i++) {
  if (i === 5) break; // hentikan loop saat i = 5
  console.log(i); // 0, 1, 2, 3, 4
}

// continue - lompati iterasi saat ini, lanjut ke berikutnya
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) continue; // lewati angka genap
  console.log(i); // 1, 3, 5, 7, 9
}

// Label - break/continue pada loop bersarang
outer: for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    if (j === 1) continue outer; // lanjut ke iterasi outer loop
    console.log(i, j);
  }
}
```

---

## 16. Error Handling

### 16.1 `try`, `catch`, `finally`

```js
try {
  // Kode yang mungkin menghasilkan error
  const hasil = 10 / 0;           // Infinity, bukan error
  JSON.parse("ini bukan JSON");   // SyntaxError!
  console.log("Baris ini tidak dieksekusi setelah error");

} catch (error) {
  // Dieksekusi jika ada error di blok try
  // 'error' adalah object Error dengan properti:
  console.log(error.name);     // "SyntaxError"
  console.log(error.message);  // "Unexpected token..."
  console.log(error.stack);    // Stack trace

} finally {
  // SELALU dieksekusi, baik ada error maupun tidak
  // Berguna untuk cleanup (menutup koneksi, dll)
  console.log("Selesai - selalu berjalan");
}
```

### 16.2 Jenis Error Bawaan

```js
// ReferenceError - mengakses variabel yang tidak ada
try { console.log(variabelTidakAda); } catch(e) { console.log(e.name); }

// TypeError - operasi pada tipe yang salah
try { null.properti; } catch(e) { console.log(e.name); }

// SyntaxError - kode tidak valid (biasanya saat parsing JSON)
try { JSON.parse("{salah}"); } catch(e) { console.log(e.name); }

// RangeError - nilai di luar range yang valid
try { new Array(-1); } catch(e) { console.log(e.name); }
```

### 16.3 Custom Error

```js
// Membuat class Error sendiri
class ValidationError extends Error {
  constructor(message, field) {
    super(message);         // panggil constructor Error bawaan
    this.name = "ValidationError"; // override nama error
    this.field = field;     // tambah properti kustom
  }
}

function validateEmail(email) {
  if (!email.includes("@")) {
    throw new ValidationError("Email tidak valid", "email");
  }
  return true;
}

try {
  validateEmail("bukanEmail");
} catch (error) {
  if (error instanceof ValidationError) {
    console.log(`Error pada field '${error.field}': ${error.message}`);
  } else {
    throw error; // lempar ulang jika bukan error yang kita kenali
  }
}
```

---

## 17. Asynchronous JavaScript

JavaScript bersifat single-threaded, namun bisa menangani operasi yang membutuhkan waktu (seperti request jaringan atau timer) secara non-blocking menggunakan mekanisme asynchronous.

### 17.1 Callback

```js
// Cara lama - callback hell bisa terjadi jika bersarang dalam
function ambilData(callback) {
  setTimeout(() => { // simulasi operasi async (delay 1 detik)
    callback(null, { nama: "Data", nilai: 42 }); // null = tidak ada error
  }, 1000);
}

ambilData((error, data) => {
  if (error) {
    console.log("Error:", error);
  } else {
    console.log("Data diterima:", data);
  }
});
```

### 17.2 Promise

```js
// Promise merepresentasikan nilai yang mungkin tersedia sekarang, nanti, atau tidak sama sekali
// Status: pending -> fulfilled (resolved) atau rejected

function ambilDataPromise(id) {
  return new Promise((resolve, reject) => {
    // resolve dipanggil jika berhasil, reject jika gagal
    setTimeout(() => {
      if (id > 0) {
        resolve({ id, nama: "Pengguna " + id }); // berhasil
      } else {
        reject(new Error("ID tidak valid")); // gagal
      }
    }, 1000);
  });
}

// Mengonsumsi Promise
ambilDataPromise(1)
  .then(data => {           // dipanggil jika resolved
    console.log("Berhasil:", data);
    return data.id * 2;     // nilai return menjadi Promise baru
  })
  .then(idGanda => {
    console.log("ID ganda:", idGanda);
  })
  .catch(error => {         // dipanggil jika rejected (di mana saja dalam chain)
    console.log("Error:", error.message);
  })
  .finally(() => {          // selalu dipanggil
    console.log("Selesai");
  });

// Promise.all - menunggu SEMUA promise selesai (jika satu gagal, semua gagal)
Promise.all([
  ambilDataPromise(1),
  ambilDataPromise(2),
  ambilDataPromise(3)
]).then(([data1, data2, data3]) => {
  console.log("Semua selesai:", data1, data2, data3);
});

// Promise.allSettled - menunggu semua, tidak peduli berhasil atau gagal
Promise.allSettled([
  ambilDataPromise(1),
  ambilDataPromise(-1) // akan rejected
]).then(results => {
  results.forEach(result => {
    if (result.status === "fulfilled") {
      console.log("Berhasil:", result.value);
    } else {
      console.log("Gagal:", result.reason.message);
    }
  });
});

// Promise.race - mengembalikan hasil dari promise yang PERTAMA selesai
Promise.race([
  ambilDataPromise(1),
  ambilDataPromise(2)
]).then(pemenang => console.log("Pemenang:", pemenang));

// Promise.any - mengembalikan hasil dari promise yang PERTAMA berhasil
Promise.any([
  ambilDataPromise(-1), // akan gagal
  ambilDataPromise(2)   // akan berhasil
]).then(hasil => console.log("Pertama yang berhasil:", hasil));
```

### 17.3 Async/Await (ES2017)

```js
// Async/await adalah syntactic sugar di atas Promise
// Membuat kode asynchronous terlihat seperti synchronous

async function ambilDataPengguna(id) {
  try {
    // await menghentikan eksekusi fungsi ini sementara, menunggu Promise selesai
    // Fungsi lain masih bisa berjalan selama menunggu
    const pengguna = await ambilDataPromise(id);
    console.log("Pengguna:", pengguna);

    // Bisa langsung gunakan hasilnya
    const idGanda = pengguna.id * 2;
    return idGanda;

  } catch (error) {
    // Error dari await akan tertangkap di sini
    console.log("Error:", error.message);
  }
}

// Fungsi async SELALU mengembalikan Promise
ambilDataPengguna(1).then(hasil => console.log("Hasil:", hasil));

// Menjalankan beberapa request secara paralel dengan async/await
async function paralel() {
  // Cara SALAH - sequential, membuang waktu
  const a = await ambilDataPromise(1); // tunggu selesai
  const b = await ambilDataPromise(2); // baru mulai ini

  // Cara BENAR - parallel
  const [x, y] = await Promise.all([
    ambilDataPromise(1),
    ambilDataPromise(2)
  ]);
}
```

---

## 18. ES6+ Modern Syntax

### 18.1 Template Literals

```js
const nama = "Dunia";
const angka = 42;

// Multi-line string
const multiline = `Baris pertama
Baris kedua
Baris ketiga`;

// Ekspresi di dalam template
const hasil = `${nama} memiliki ${angka * 2} karakter`;

// Tagged template - template literal dengan fungsi
function highlight(strings, ...values) {
  // strings: array bagian teks biasa
  // values: array nilai ekspresi
  return strings.reduce((acc, str, i) => {
    return acc + str + (values[i] ? `<b>${values[i]}</b>` : "");
  }, "");
}

const tagged = highlight`Halo ${nama}, angka: ${angka}`;
// "Halo <b>Dunia</b>, angka: <b>42</b>"
```

### 18.2 Map dan Set

```js
// Map - object dengan key yang bisa berupa tipe apa saja
const peta = new Map();

peta.set("nama", "Andi");    // key string
peta.set(1, "satu");         // key number
peta.set(true, "benar");     // key boolean

console.log(peta.get("nama")); // "Andi"
console.log(peta.has(1));      // true
console.log(peta.size);        // 3

peta.delete(true);

// Iterasi Map
for (const [key, value] of peta) {
  console.log(key, "->", value);
}

// Map dari array
const mapDariArray = new Map([
  ["a", 1],
  ["b", 2]
]);

// WeakMap - key harus berupa object, tidak mencegah garbage collection
const wm = new WeakMap();
const objKey = {};
wm.set(objKey, "data");

// Set - koleksi nilai UNIK
const himpunan = new Set([1, 2, 3, 2, 1]); // duplikat otomatis dihapus
console.log(himpunan); // Set { 1, 2, 3 }

himpunan.add(4);
himpunan.delete(2);
console.log(himpunan.has(3)); // true
console.log(himpunan.size);   // 3

// Konversi Set ke Array
const arr = [...himpunan];
const arr2 = Array.from(himpunan);

// Menghapus duplikat dari array dengan Set
const duplikat = [1, 2, 2, 3, 3, 4];
const unik = [...new Set(duplikat)]; // [1, 2, 3, 4]
```

### 18.3 Generator Function

```js
// Generator dapat menghentikan dan melanjutkan eksekusinya
// Berguna untuk membuat iterator kustom atau mengelola alur asynchronous

function* generatorAngka() {
  yield 1;    // kembalikan 1, lalu pause
  yield 2;    // lanjut, kembalikan 2, pause lagi
  yield 3;    // lanjut, kembalikan 3
  // generator selesai
}

const gen = generatorAngka();
console.log(gen.next()); // { value: 1, done: false }
console.log(gen.next()); // { value: 2, done: false }
console.log(gen.next()); // { value: 3, done: false }
console.log(gen.next()); // { value: undefined, done: true }

// Generator sebagai iterable
for (const n of generatorAngka()) {
  console.log(n); // 1, 2, 3
}

// Generator range yang tak terbatas
function* range(start = 0, end = Infinity, step = 1) {
  for (let i = start; i < end; i += step) {
    yield i;
  }
}

const genRange = range(0, 10, 2);
console.log([...genRange]); // [0, 2, 4, 6, 8]
```

### 18.4 Proxy dan Reflect

```js
// Proxy - membungkus object dan mengintersep operasinya
const target = { nama: "Andi", umur: 25 };

const handler = {
  get(obj, prop) {
    // dieksekusi setiap kali properti diakses
    console.log(`Mengakses properti: ${prop}`);
    return prop in obj ? obj[prop] : `Properti '${prop}' tidak ada`;
  },
  set(obj, prop, value) {
    // dieksekusi setiap kali properti diubah
    if (prop === "umur" && typeof value !== "number") {
      throw new TypeError("Umur harus berupa angka");
    }
    obj[prop] = value;
    return true; // harus mengembalikan true jika berhasil
  }
};

const proxy = new Proxy(target, handler);
console.log(proxy.nama);       // "Andi" (dengan log)
console.log(proxy.tidakAda);   // "Properti 'tidakAda' tidak ada"
proxy.umur = 30;               // OK
// proxy.umur = "tiga puluh"; // TypeError!
```

---

## 19. DOM (Document Object Model)

DOM adalah representasi halaman HTML dalam bentuk struktur pohon (tree) objek yang dapat diakses dan dimanipulasi dengan JavaScript.

```
document (root)
  └── html
        ├── head
        │     ├── title
        │     └── meta
        └── body
              ├── h1
              ├── p
              └── div
                    ├── span
                    └── a
```

### 19.1 Memilih Elemen DOM (DOM Selection)

```js
// querySelector - memilih SATU elemen pertama yang cocok (CSS selector)
const judul = document.querySelector("h1");
const tombol = document.querySelector("#tombol-kirim");   // by ID
const item = document.querySelector(".item");              // by class
const link = document.querySelector("nav > a.aktif");     // selector kompleks

// querySelectorAll - memilih SEMUA elemen yang cocok (mengembalikan NodeList)
const semuaItem = document.querySelectorAll(".item");
const semuaLink = document.querySelectorAll("a[href]");

// NodeList tidak persis Array, tapi bisa diiterasi
semuaItem.forEach(el => console.log(el.textContent));

// Konversi ke Array untuk akses method Array lengkap
const arrayItem = Array.from(semuaItem);
const arrayItem2 = [...semuaItem];

// getElementById - paling cepat untuk pencarian by ID
const container = document.getElementById("container");

// getElementsByClassName - mengembalikan HTMLCollection (live collection)
const kotak = document.getElementsByClassName("kotak");

// getElementsByTagName - by tag HTML
const paragraf = document.getElementsByTagName("p");

// Traversal - navigasi dari elemen yang sudah dipilih
const el = document.querySelector(".parent");

el.parentElement          // elemen induk
el.parentNode             // node induk (bisa berupa document)
el.children               // HTMLCollection anak-anak elemen
el.childNodes             // NodeList semua node anak (termasuk text node)
el.firstElementChild      // anak pertama (element)
el.lastElementChild       // anak terakhir (element)
el.nextElementSibling     // saudara berikutnya
el.previousElementSibling // saudara sebelumnya
el.closest(".container")  // ancestor terdekat yang cocok selector

// Memeriksa apakah elemen cocok dengan selector
el.matches(".aktif")      // true/false
el.contains(anakEl)       // apakah anakEl ada di dalam el
```

### 19.2 Membaca dan Memanipulasi Konten

```js
const el = document.querySelector("#kotak");

// Membaca konten
el.textContent   // teks murni tanpa tag HTML
el.innerHTML     // konten HTML di dalamnya (termasuk tag)
el.outerHTML     // HTML dari elemen itu sendiri beserta isinya

// Mengubah konten
el.textContent = "Teks baru";           // aman - tidak mem-parse HTML
el.innerHTML = "<strong>Bold!</strong>"; // hati-hati XSS jika dari input user

// value - untuk elemen form
const input = document.querySelector("input");
const nilaiInput = input.value;
input.value = "nilai baru";
```

### 19.3 Membaca dan Memanipulasi Atribut

```js
const gambar = document.querySelector("img");

// Atribut HTML standar bisa diakses langsung
gambar.src     = "foto.jpg";
gambar.alt     = "Foto saya";
gambar.id      = "foto-profil";

// getAttribute / setAttribute - untuk atribut apa saja termasuk kustom
gambar.getAttribute("src");              // baca atribut
gambar.setAttribute("data-id", "123");   // tulis atribut
gambar.removeAttribute("title");         // hapus atribut
gambar.hasAttribute("alt");             // cek keberadaan atribut

// Data attributes - atribut kustom dengan prefix "data-"
// HTML: <div data-user-id="5" data-role="admin">
const div = document.querySelector("div");
div.dataset.userId;         // "5" (data-user-id -> userId, camelCase otomatis)
div.dataset.role;           // "admin"
div.dataset.baruTambah = "nilai"; // menambah data-baru-tambah
```

### 19.4 Membuat dan Menyisipkan Elemen

```js
// createElement - membuat elemen baru
const elBaru = document.createElement("div");
elBaru.textContent = "Elemen baru";
elBaru.id = "unik";
elBaru.className = "kotak aktif";

// appendChild - sisipkan sebagai anak terakhir
document.body.appendChild(elBaru);

// insertBefore - sisipkan sebelum elemen tertentu
const referensi = document.querySelector("#ref");
referensi.parentNode.insertBefore(elBaru, referensi);

// insertAdjacentElement - fleksibel, pilih posisi
referensi.insertAdjacentElement("beforebegin", elBaru); // sebelum referensi
referensi.insertAdjacentElement("afterbegin", elBaru);  // anak pertama referensi
referensi.insertAdjacentElement("beforeend", elBaru);   // anak terakhir referensi
referensi.insertAdjacentElement("afterend", elBaru);    // setelah referensi

// insertAdjacentHTML - sisipkan HTML string
referensi.insertAdjacentHTML("beforeend", "<p>Paragraf baru</p>");

// prepend dan append (lebih modern, bisa multi-argumen)
referensi.append(elBaru, "teks tambahan", elLain);
referensi.prepend(elPertama);

// replaceWith - ganti elemen
referensi.replaceWith(elBaru);

// Menggandakan elemen
const klon = elBaru.cloneNode(true); // true = deep clone (termasuk anak-anaknya)
const klonDangkal = elBaru.cloneNode(false); // hanya elemennya saja

// Menghapus elemen
elBaru.remove();                         // hapus diri sendiri (cara modern)
elBaru.parentNode.removeChild(elBaru);   // cara lama
```

### 19.5 Manipulasi Class

```js
const el = document.querySelector(".kotak");

// classList - cara terbaik untuk memanipulasi class
el.classList.add("aktif");               // tambah class
el.classList.remove("aktif");            // hapus class
el.classList.toggle("aktif");            // tambah jika tidak ada, hapus jika ada
el.classList.toggle("aktif", true);      // paksa tambah
el.classList.toggle("aktif", false);     // paksa hapus
el.classList.replace("lama", "baru");    // ganti class
el.classList.contains("aktif");          // cek apakah class ada: true/false

// className - seluruh string class (cara lama, hati-hati menimpa class lain)
el.className = "kotak aktif besar";      // timpa semua class

// Membaca semua class
console.log(el.classList);              // DOMTokenList
console.log([...el.classList]);         // convert ke array
```

### 19.6 Informasi Ukuran dan Posisi Elemen

```js
const el = document.querySelector(".kotak");

// Ukuran
el.offsetWidth        // lebar termasuk border, tanpa margin
el.offsetHeight       // tinggi termasuk border, tanpa margin
el.clientWidth        // lebar konten + padding (tanpa border)
el.clientHeight       // tinggi konten + padding
el.scrollWidth        // lebar total konten yang bisa di-scroll
el.scrollHeight       // tinggi total konten yang bisa di-scroll

// getBoundingClientRect - posisi relatif terhadap viewport
const rect = el.getBoundingClientRect();
console.log(rect.top);    // jarak dari atas viewport
console.log(rect.left);   // jarak dari kiri viewport
console.log(rect.width);  // lebar
console.log(rect.height); // tinggi
console.log(rect.x);      // sama dengan left
console.log(rect.y);      // sama dengan top

// Posisi scroll
window.scrollX   // atau window.pageXOffset - scroll horizontal
window.scrollY   // atau window.pageYOffset - scroll vertikal

// Scroll elemen
window.scrollTo(0, 500);            // scroll ke posisi absolut
window.scrollBy(0, 100);            // scroll relatif dari posisi sekarang
el.scrollIntoView({ behavior: "smooth" }); // scroll sampai elemen terlihat
```

### 19.7 Informasi Document dan Window

```js
// Window
window.innerWidth     // lebar viewport
window.innerHeight    // tinggi viewport
window.outerWidth     // lebar jendela browser termasuk toolbar
window.outerHeight    // tinggi jendela browser
window.location       // URL dan navigasi
window.history        // riwayat browser

// Document
document.title        = "Judul Baru"; // ubah judul tab
document.body         // akses langsung ke body
document.head         // akses langsung ke head
document.documentElement // akses ke elemen <html>
document.activeElement  // elemen yang sedang fokus
document.readyState   // "loading", "interactive", atau "complete"

// Menjalankan kode setelah DOM selesai dimuat
document.addEventListener("DOMContentLoaded", () => {
  // DOM siap, tapi gambar dan stylesheet mungkin belum
  console.log("DOM siap");
});

window.addEventListener("load", () => {
  // Semua resource termasuk gambar sudah dimuat
  console.log("Halaman sepenuhnya dimuat");
});
```

---

## 20. Event Handling

### 20.1 Menambah Event Listener

```js
const tombol = document.querySelector("#tombol");

// addEventListener - cara yang disarankan
// Argumen: (tipe event, callback, options/useCapture)
tombol.addEventListener("click", function(event) {
  // 'event' (atau biasa disingkat 'e') adalah objek Event
  console.log("Diklik!");
  console.log(event.type);   // "click"
  console.log(event.target); // elemen yang diklik
});

// Arrow function sebagai callback
tombol.addEventListener("click", (e) => {
  console.log(e.currentTarget); // elemen yang memasang listener
});

// Menghapus event listener (harus menggunakan referensi fungsi yang sama)
function handleKlik(e) {
  console.log("Klik!");
}
tombol.addEventListener("click", handleKlik);
tombol.removeEventListener("click", handleKlik);

// Options di addEventListener
tombol.addEventListener("click", handleKlik, {
  once: true,       // listener otomatis dihapus setelah dipanggil sekali
  passive: true,    // tidak akan memanggil preventDefault() - performa scroll lebih baik
  capture: true,    // listener berjalan saat capture phase, bukan bubble phase
});
```

### 20.2 Event Object

```js
document.querySelector("a").addEventListener("click", (event) => {
  event.preventDefault();       // mencegah perilaku default (misalnya: link tidak berpindah)
  event.stopPropagation();      // hentikan event bubbling ke elemen induk
  event.stopImmediatePropagation(); // hentikan listener lain pada elemen yang sama

  event.target          // elemen yang memicu event
  event.currentTarget   // elemen yang memiliki listener (sama dengan 'this' di function biasa)
  event.type            // "click", "keydown", dll
  event.timeStamp       // waktu event terjadi (milidetik)
  event.bubbles         // apakah event ini bubble? (true/false)

  // Untuk event mouse
  event.clientX    // posisi X relatif ke viewport
  event.clientY    // posisi Y relatif ke viewport
  event.pageX      // posisi X relatif ke document (termasuk scroll)
  event.pageY      // posisi Y relatif ke document
  event.button     // tombol mouse mana yang ditekan (0=kiri, 1=tengah, 2=kanan)
  event.ctrlKey    // apakah Ctrl ditekan?
  event.shiftKey   // apakah Shift ditekan?
  event.altKey     // apakah Alt ditekan?
  event.metaKey    // apakah Meta/Cmd ditekan?

  // Untuk event keyboard
  event.key        // nama key ("a", "Enter", "ArrowUp", " ", dll)
  event.code       // kode fisik tombol ("KeyA", "Enter", "Space")
  event.keyCode    // kode numerik (deprecated, gunakan event.key)
});
```

### 20.3 Daftar Event Umum

```js
// Mouse Events
element.addEventListener("click", handler);        // klik kiri
element.addEventListener("dblclick", handler);     // klik ganda
element.addEventListener("mousedown", handler);    // tombol mouse ditekan
element.addEventListener("mouseup", handler);      // tombol mouse dilepas
element.addEventListener("mousemove", handler);    // mouse bergerak di atas elemen
element.addEventListener("mouseenter", handler);   // mouse masuk ke elemen (tidak bubble)
element.addEventListener("mouseleave", handler);   // mouse keluar dari elemen (tidak bubble)
element.addEventListener("mouseover", handler);    // mouse di atas elemen atau anaknya (bubble)
element.addEventListener("mouseout", handler);     // mouse keluar dari elemen atau anaknya
element.addEventListener("contextmenu", handler);  // klik kanan

// Keyboard Events
element.addEventListener("keydown", handler);      // tombol keyboard ditekan
element.addEventListener("keyup", handler);        // tombol keyboard dilepas
element.addEventListener("keypress", handler);     // karakter diketik (deprecated)

// Form Events
input.addEventListener("input", handler);          // nilai berubah (real-time)
input.addEventListener("change", handler);         // nilai berubah dan fokus hilang
input.addEventListener("focus", handler);          // elemen mendapat fokus
input.addEventListener("blur", handler);           // elemen kehilangan fokus
form.addEventListener("submit", handler);          // form di-submit
form.addEventListener("reset", handler);           // form di-reset

// Window / Document Events
window.addEventListener("scroll", handler);        // halaman di-scroll
window.addEventListener("resize", handler);        // ukuran window berubah
window.addEventListener("load", handler);          // semua resource dimuat
document.addEventListener("DOMContentLoaded", handler); // DOM siap

// Drag Events
element.addEventListener("dragstart", handler);    // mulai drag
element.addEventListener("drag", handler);         // sedang drag
element.addEventListener("dragend", handler);      // selesai drag
element.addEventListener("dragenter", handler);    // masuk ke drop target
element.addEventListener("dragleave", handler);    // keluar dari drop target
element.addEventListener("dragover", handler);     // di atas drop target
element.addEventListener("drop", handler);         // elemen di-drop

// Touch Events (mobile)
element.addEventListener("touchstart", handler);   // jari menyentuh layar
element.addEventListener("touchmove", handler);    // jari bergerak
element.addEventListener("touchend", handler);     // jari diangkat

// Clipboard Events
element.addEventListener("copy", handler);
element.addEventListener("paste", handler);
element.addEventListener("cut", handler);

// Animation dan Transition Events
element.addEventListener("animationstart", handler);
element.addEventListener("animationend", handler);
element.addEventListener("transitionend", handler);

// Observer dan Events Lain
element.addEventListener("wheel", handler);        // scroll roda mouse
window.addEventListener("hashchange", handler);    // perubahan hash URL
window.addEventListener("popstate", handler);      // navigasi history
window.addEventListener("online", handler);        // koneksi internet kembali
window.addEventListener("offline", handler);       // koneksi internet terputus
```

### 20.4 Event Delegation

```js
// Daripada menambah listener ke setiap elemen anak,
// tambahkan satu listener ke elemen induk (lebih efisien untuk list dinamis)

const daftar = document.querySelector("#daftar");

daftar.addEventListener("click", (event) => {
  // event.target adalah elemen yang benar-benar diklik
  // event.currentTarget adalah elemen yang memiliki listener (daftar)

  // Gunakan closest() untuk menemukan elemen yang relevan
  const item = event.target.closest(".item");
  if (!item) return; // klik bukan pada .item

  const id = item.dataset.id;
  console.log("Item diklik, ID:", id);
});

// Ini juga berfungsi untuk elemen yang ditambahkan secara dinamis setelah listener dipasang
```

### 20.5 Custom Event

```js
// Membuat dan mengirim event kustom
const eventKustom = new CustomEvent("dataBaru", {
  bubbles: true,      // event akan bubble ke elemen induk
  cancelable: true,   // bisa di-cancel dengan preventDefault()
  detail: {           // data yang dikirim bersama event
    pesan: "Data baru tersedia",
    data: [1, 2, 3]
  }
});

// Kirim event dari elemen
document.getElementById("kotak").dispatchEvent(eventKustom);

// Dengarkan event kustom
document.getElementById("kotak").addEventListener("dataBaru", (e) => {
  console.log("Detail event:", e.detail);
  console.log("Pesan:", e.detail.pesan);
});
```

---

## 21. Manipulasi CSS dengan JavaScript

### 21.1 Inline Style

```js
const el = document.querySelector(".kotak");

// Membaca style
console.log(el.style.color);           // hanya membaca inline style, bukan computed
console.log(el.style.backgroundColor); // camelCase untuk properti CSS yang mengandung tanda hubung

// Mengubah style
el.style.color = "red";
el.style.backgroundColor = "#3498db";
el.style.fontSize = "18px";
el.style.display = "none";             // menyembunyikan elemen
el.style.display = "";                 // mengembalikan ke nilai default

// Menghapus style
el.style.removeProperty("color");
el.style.color = ""; // cara lain

// Mengubah banyak style sekaligus
Object.assign(el.style, {
  color: "white",
  backgroundColor: "navy",
  padding: "10px",
  borderRadius: "5px"
});

// cssText - mengubah style secara keseluruhan (menimpa semua inline style)
el.style.cssText = "color: white; background-color: navy; padding: 10px;";
```

### 21.2 Computed Style

```js
// getComputedStyle - membaca CSS yang benar-benar aktif (termasuk dari stylesheet)
const el = document.querySelector(".kotak");
const computed = window.getComputedStyle(el);

console.log(computed.color);           // nilai aktual dalam bentuk rgb()
console.log(computed.backgroundColor);
console.log(computed.fontSize);        // nilai dalam pixel, mis: "16px"
console.log(computed.display);
console.log(computed.width);           // lebar aktual

// Pseudo-element
const setelah = window.getComputedStyle(el, "::after");
console.log(setelah.content);
```

### 21.3 CSS Custom Properties (CSS Variables)

```js
// Membaca CSS variable
const el = document.querySelector(".kotak");

// getPropertyValue dengan nama variabel
const warna = getComputedStyle(el).getPropertyValue("--warna-utama");
// atau dari root
const warnaRoot = getComputedStyle(document.documentElement).getPropertyValue("--warna-utama");

// Mengubah CSS variable - perubahan berlaku ke semua elemen yang menggunakan variabel ini
document.documentElement.style.setProperty("--warna-utama", "#e74c3c");

// Mengubah pada elemen spesifik
el.style.setProperty("--ukuran-font", "24px");

// Menghapus override
el.style.removeProperty("--ukuran-font");
```

### 21.4 Menambah dan Menghapus Stylesheet Dinamis

```js
// Menambah stylesheet dari file
function tambahStylesheet(href) {
  const link = document.createElement("link");
  link.rel = "stylesheet";
  link.href = href;
  document.head.appendChild(link);
}

// Menyisipkan CSS langsung dengan tag <style>
function tambahCSS(cssString) {
  const style = document.createElement("style");
  style.textContent = cssString;
  document.head.appendChild(style);
  return style; // kembalikan agar bisa dihapus nanti
}

const styleTag = tambahCSS(`
  .sorotan {
    background-color: yellow;
    font-weight: bold;
    border: 2px solid orange;
  }
`);

// Menghapus stylesheet dinamis
styleTag.remove();
```

### 21.5 Animasi dengan JavaScript

```js
// Web Animations API - cara modern menganimasikan elemen

const el = document.querySelector(".kotak");

// animate(keyframes, options) - mengembalikan Animation object
const animasi = el.animate(
  [
    // Keyframe awal
    { transform: "translateX(0)", opacity: 1 },
    // Keyframe tengah (opsional)
    { transform: "translateX(100px)", opacity: 0.5, offset: 0.7 },
    // Keyframe akhir
    { transform: "translateX(200px)", opacity: 0 }
  ],
  {
    duration: 1000,           // milidetik
    easing: "ease-in-out",    // "linear", "ease", "ease-in", "ease-out", "ease-in-out", atau cubic-bezier
    delay: 500,               // tunda sebelum mulai (ms)
    endDelay: 200,            // tunda setelah selesai (ms)
    fill: "forwards",         // "none", "forwards", "backwards", "both" - status akhir elemen
    iterations: Infinity,     // berapa kali diulang (Infinity = terus)
    direction: "alternate",   // "normal", "reverse", "alternate", "alternate-reverse"
    iterationStart: 0.5,      // mulai dari titik mana dalam satu iterasi
  }
);

// Kontrol animasi
animasi.pause();
animasi.play();
animasi.reverse();
animasi.cancel();
animasi.finish();

// Event animasi
animasi.addEventListener("finish", () => {
  console.log("Animasi selesai");
});

// requestAnimationFrame - animasi manual berbasis frame
// Lebih efisien dari setInterval untuk animasi

let posisi = 0;

function animasiManual(timestamp) {
  // timestamp adalah waktu sejak halaman dimuat (milidetik)
  posisi += 2;
  el.style.transform = `translateX(${posisi}px)`;

  if (posisi < 300) {
    requestAnimationFrame(animasiManual); // panggil frame berikutnya
  }
}

const idAnimasi = requestAnimationFrame(animasiManual);

// Membatalkan animasi
cancelAnimationFrame(idAnimasi);
```

### 21.6 Intersection Observer

Berguna untuk mendeteksi apakah elemen terlihat di viewport (lazy loading, animasi scroll, dll).

```js
// Konfigurasi observer
const options = {
  root: null,             // null = viewport
  rootMargin: "0px",      // margin di sekitar root (positif = perluas, negatif = perkecil area observasi)
  threshold: 0.5          // callback dipanggil saat 50% elemen terlihat
                          // bisa berupa array: [0, 0.25, 0.5, 0.75, 1]
};

const observer = new IntersectionObserver((entries, obs) => {
  entries.forEach(entry => {
    // entry.isIntersecting: true jika elemen terlihat
    // entry.intersectionRatio: 0 sampai 1, seberapa banyak yang terlihat
    // entry.target: elemen yang diobservasi
    // entry.boundingClientRect: posisi dan ukuran elemen
    // entry.intersectionRect: bagian yang terlihat

    if (entry.isIntersecting) {
      entry.target.classList.add("terlihat");
      entry.target.classList.remove("tersembunyi");
      obs.unobserve(entry.target); // hentikan observasi setelah animasi berjalan
    }
  });
}, options);

// Mulai observasi
document.querySelectorAll(".elemen-animasi").forEach(el => {
  observer.observe(el);
});

// Hentikan semua observasi
observer.disconnect();
```

### 21.7 ResizeObserver dan MutationObserver

```js
// ResizeObserver - memantau perubahan ukuran elemen
const resizeObs = new ResizeObserver(entries => {
  entries.forEach(entry => {
    const { width, height } = entry.contentRect;
    console.log(`Ukuran baru: ${width}px x ${height}px`);
  });
});

resizeObs.observe(document.querySelector(".kotak"));

// MutationObserver - memantau perubahan pada DOM
const mutationObs = new MutationObserver((mutations) => {
  mutations.forEach(mutation => {
    if (mutation.type === "childList") {
      console.log("Anak elemen ditambah/dihapus");
      console.log("Ditambah:", mutation.addedNodes);
      console.log("Dihapus:", mutation.removedNodes);
    }
    if (mutation.type === "attributes") {
      console.log(`Atribut "${mutation.attributeName}" berubah`);
    }
    if (mutation.type === "characterData") {
      console.log("Konten teks berubah");
    }
  });
});

mutationObs.observe(document.body, {
  childList: true,        // pantau penambahan/penghapusan anak
  subtree: true,          // pantau semua keturunan, bukan hanya anak langsung
  attributes: true,       // pantau perubahan atribut
  attributeFilter: ["class", "style"], // hanya pantau atribut tertentu
  characterData: true,    // pantau perubahan teks
});

mutationObs.disconnect(); // hentikan observasi
```

---

## 22. Form Handling

```js
const form = document.querySelector("#form-daftar");
const inputNama = document.querySelector("#nama");
const inputEmail = document.querySelector("#email");

// Mencegah form reload halaman saat submit
form.addEventListener("submit", (e) => {
  e.preventDefault(); // sangat penting!

  // Membaca nilai input
  const nama = inputNama.value.trim();
  const email = inputEmail.value.trim();

  // Validasi
  if (!nama) {
    tampilkanError(inputNama, "Nama tidak boleh kosong");
    return;
  }

  if (!isEmailValid(email)) {
    tampilkanError(inputEmail, "Format email tidak valid");
    return;
  }

  // Proses data
  console.log("Form valid:", { nama, email });
});

function isEmailValid(email) {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
}

function tampilkanError(input, pesan) {
  const errorEl = input.nextElementSibling;
  if (errorEl && errorEl.classList.contains("pesan-error")) {
    errorEl.textContent = pesan;
  }
  input.classList.add("error");
}

// FormData API - mengumpulkan data form secara otomatis
form.addEventListener("submit", (e) => {
  e.preventDefault();
  const formData = new FormData(form);

  // Iterasi semua field
  for (const [nama, nilai] of formData.entries()) {
    console.log(`${nama}: ${nilai}`);
  }

  // Mengubah ke object biasa
  const dataObject = Object.fromEntries(formData);

  // Mengubah ke JSON untuk dikirim ke API
  const json = JSON.stringify(dataObject);
});

// Input khusus
const checkbox = document.querySelector("input[type=checkbox]");
console.log(checkbox.checked); // true/false

const radio = document.querySelector("input[type=radio]:checked");
console.log(radio?.value);

const select = document.querySelector("select");
console.log(select.value);           // nilai opsi yang dipilih
console.log(select.selectedIndex);   // index opsi yang dipilih
console.log(select.options);         // semua opsi
```

---

## 23. Local Storage dan Session Storage

```js
// localStorage - data tersimpan PERMANEN sampai dihapus manual
// sessionStorage - data hilang saat tab/browser ditutup

// Menyimpan data (hanya string)
localStorage.setItem("nama", "Andi");
localStorage.setItem("pengaturan", JSON.stringify({ tema: "gelap", bahasa: "id" }));

// Membaca data
const nama = localStorage.getItem("nama");
const pengaturan = JSON.parse(localStorage.getItem("pengaturan"));

// Menghapus satu item
localStorage.removeItem("nama");

// Menghapus semua item
localStorage.clear();

// Mendapatkan semua key
for (let i = 0; i < localStorage.length; i++) {
  const key = localStorage.key(i);
  const value = localStorage.getItem(key);
  console.log(key, value);
}

// Membuat wrapper dengan error handling
const storage = {
  simpan(key, value) {
    try {
      localStorage.setItem(key, JSON.stringify(value));
    } catch (e) {
      console.error("Gagal menyimpan:", e);
    }
  },
  baca(key, defaultValue = null) {
    try {
      const item = localStorage.getItem(key);
      return item ? JSON.parse(item) : defaultValue;
    } catch (e) {
      return defaultValue;
    }
  },
  hapus(key) {
    localStorage.removeItem(key);
  }
};
```

---

## 24. Fetch API dan HTTP Request

```js
// Fetch API - cara modern untuk membuat HTTP request

// GET request
async function ambilPengguna(id) {
  try {
    const response = await fetch(`https://api.example.com/pengguna/${id}`);

    // Periksa status HTTP
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    // Parse response body
    const data = await response.json();
    return data;

  } catch (error) {
    console.error("Gagal mengambil data:", error);
    throw error;
  }
}

// POST request - mengirim data
async function simpanPengguna(dataPengguna) {
  const response = await fetch("https://api.example.com/pengguna", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      "Authorization": "Bearer token-saya"
    },
    body: JSON.stringify(dataPengguna) // data harus dijadikan string
  });

  if (!response.ok) {
    const errorData = await response.json();
    throw new Error(errorData.message);
  }

  return await response.json();
}

// Response methods
// response.json()    - parse sebagai JSON
// response.text()    - dapatkan sebagai string
// response.blob()    - dapatkan sebagai Blob (file, gambar)
// response.arrayBuffer() - dapatkan sebagai ArrayBuffer

// Response properties
// response.status       - kode HTTP (200, 404, 500, dll)
// response.statusText   - "OK", "Not Found", dll
// response.ok           - true jika status 200-299
// response.headers      - object Headers
// response.url          - URL akhir (setelah redirect)

// Contoh penggunaan lengkap
async function kirimForm(formEl) {
  const formData = new FormData(formEl);

  const response = await fetch("/api/submit", {
    method: "POST",
    body: formData // FormData bisa langsung dikirim, tanpa JSON.stringify
    // Jangan set Content-Type secara manual saat mengirim FormData
  });

  return response.json();
}

// Abort Controller - membatalkan request
const controller = new AbortController();
const signal = controller.signal;

const fetchPromise = fetch("https://api.example.com/data", { signal });

// Batalkan setelah 5 detik
setTimeout(() => controller.abort(), 5000);

try {
  const data = await fetchPromise;
} catch (err) {
  if (err.name === "AbortError") {
    console.log("Request dibatalkan");
  }
}
```

---

## 25. Pola Umum dan Best Practice

### 25.1 Module Pattern

```js
// ES Modules (ESM) - cara standar modern

// math.js - file modul
export const PI = 3.14159;

export function tambah(a, b) {
  return a + b;
}

export function kurang(a, b) {
  return a - b;
}

// Default export - satu per file
export default class Kalkulator {
  jumlah(a, b) { return a + b; }
}

// main.js - mengimpor modul
import Kalkulator, { PI, tambah, kurang } from "./math.js";
import * as MathUtil from "./math.js"; // import semua

// Di HTML, gunakan type="module"
// <script type="module" src="main.js"></script>
```

### 25.2 Debounce dan Throttle

```js
// Debounce - tunda eksekusi hingga tidak ada pemanggilan baru selama N ms
// Berguna untuk: search autocomplete, resize handler, auto-save
function debounce(fungsi, tundaMs) {
  let timer;
  return function(...args) {
    clearTimeout(timer); // batalkan timer sebelumnya
    timer = setTimeout(() => {
      fungsi.apply(this, args); // eksekusi setelah tunda
    }, tundaMs);
  };
}

const inputPencarian = document.querySelector("#pencarian");
const pencarianDebounced = debounce((event) => {
  console.log("Mencari:", event.target.value);
  // lakukan fetch ke API di sini
}, 300);

inputPencarian.addEventListener("input", pencarianDebounced);

// Throttle - batasi eksekusi maksimal sekali per N ms
// Berguna untuk: scroll event, mouse move
function throttle(fungsi, limitMs) {
  let bolehJalan = true;
  return function(...args) {
    if (!bolehJalan) return; // abaikan jika masih dalam periode limit
    bolehJalan = false;
    fungsi.apply(this, args);
    setTimeout(() => { bolehJalan = true; }, limitMs);
  };
}

const scrollThrottled = throttle(() => {
  console.log("Scroll Y:", window.scrollY);
}, 100);

window.addEventListener("scroll", scrollThrottled);
```

### 25.3 Pola Observer (Pub/Sub)

```js
class EventEmitter {
  constructor() {
    this.listeners = {}; // { eventName: [callbacks] }
  }

  on(event, callback) {
    if (!this.listeners[event]) {
      this.listeners[event] = [];
    }
    this.listeners[event].push(callback);
    return this; // untuk chaining
  }

  off(event, callback) {
    if (this.listeners[event]) {
      this.listeners[event] = this.listeners[event].filter(cb => cb !== callback);
    }
    return this;
  }

  emit(event, data) {
    if (this.listeners[event]) {
      this.listeners[event].forEach(cb => cb(data));
    }
    return this;
  }

  once(event, callback) {
    const wrapper = (data) => {
      callback(data);
      this.off(event, wrapper); // hapus setelah dipanggil sekali
    };
    return this.on(event, wrapper);
  }
}

const emitter = new EventEmitter();

emitter.on("dataBaru", (data) => {
  console.log("Diterima:", data);
});

emitter.emit("dataBaru", { id: 1, nama: "Item" });
```

### 25.4 Singleton Pattern

```js
// Memastikan hanya ada satu instance dari sebuah class
class Konfigurasi {
  static instance = null; // properti statis - milik class, bukan instance

  constructor() {
    if (Konfigurasi.instance) {
      return Konfigurasi.instance; // kembalikan instance yang sudah ada
    }
    this.data = {};
    Konfigurasi.instance = this;
  }

  set(key, value) { this.data[key] = value; }
  get(key) { return this.data[key]; }
}

const config1 = new Konfigurasi();
const config2 = new Konfigurasi();

console.log(config1 === config2); // true - objek yang sama
```

### 25.5 Tips Performa DOM

```js
// 1. Minimalkan reflow/repaint dengan batch update

// BURUK - setiap perubahan style memicu reflow
el.style.width = "100px";
el.style.height = "100px";
el.style.margin = "10px";

// BAIK - satu kali reflow dengan cssText
el.style.cssText = "width: 100px; height: 100px; margin: 10px;";

// ATAU gunakan class
el.classList.add("kotak-besar");

// 2. DocumentFragment - batch insert elemen
const fragment = document.createDocumentFragment();

for (let i = 0; i < 100; i++) {
  const li = document.createElement("li");
  li.textContent = `Item ${i}`;
  fragment.appendChild(li); // append ke fragment, bukan ke DOM
}

document.querySelector("ul").appendChild(fragment); // satu kali operasi DOM

// 3. Simpan referensi elemen yang sering diakses
const tombol = document.querySelector("#tombol"); // cache referensi
// Jangan panggil querySelector berulang kali dalam loop

// 4. Gunakan innerHTML untuk bulk insert teks statis (lebih cepat)
// Tapi hati-hati XSS jika konten dari user!
const items = ["apel", "mangga", "jeruk"];
ul.innerHTML = items.map(item => `<li>${item}</li>`).join("");

// 5. Gunakan event delegation alih-alih banyak listener
// (sudah dibahas di bagian Event Handling)
```

### 25.6 Strict Mode

```js
"use strict"; // aktifkan di awal file atau fungsi

// Strict mode mencegah:
// - Penggunaan variabel tanpa deklarasi
// - Penghapusan variabel/fungsi
// - Parameter fungsi duplikat
// - Penggunaan kata kunci reserved di masa depan

// ES Modules dan class otomatis dalam strict mode
```

---

## Ringkasan Referensi Cepat

| Konsep | Penggunaan |
|---|---|
| `querySelector` | Pilih elemen pertama yang cocok |
| `querySelectorAll` | Pilih semua elemen yang cocok |
| `addEventListener` | Pasang event listener |
| `classList.add/remove/toggle` | Manipulasi class CSS |
| `style.property` | Manipulasi inline style |
| `textContent` | Baca/tulis teks (aman) |
| `innerHTML` | Baca/tulis HTML (hati-hati XSS) |
| `createElement` + `appendChild` | Buat dan tambahkan elemen |
| `fetch` + `async/await` | HTTP request modern |
| `localStorage` | Simpan data persisten |
| `getComputedStyle` | Baca style yang sedang aktif |
| `animate()` | Animasi via Web Animations API |
| `requestAnimationFrame` | Animasi berbasis frame |
| `IntersectionObserver` | Deteksi elemen di viewport |
| `MutationObserver` | Pantau perubahan DOM |

---

*Dokumentasi ini mencakup JavaScript versi ES2015 hingga ES2022. Selalu periksa kompatibilitas browser di MDN Web Docs atau caniuse.com sebelum menggunakan fitur terbaru di produksi.*

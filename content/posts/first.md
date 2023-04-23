---
title: "Tổng hợp tính năng javascript mới nhất kể từ ES6 đến ES11"
date: 2023-04-22T09:08:07+07:00
draft: false
tags: ["javascript", "es6"]
categories: [javascript]
author: hieupc09
---

`#javascript` `#feature_javascript` `#es6`

##### Nội dung bài viết

Những tính năng của javscript kể từ khi `ES6` ra đời cho đến chuẩn bị stage 4 của ES11. Và kết thúc năm 2019 thì chúng ta có học được những tính năng gì trong những feature javascript dưới đây.

Bạn có bao giờ tìm hiểu về các tính năng của ES6 từ khi ra đời cho đến nay, và bạn đã sử dụng hết tất cả đó chưa thì trong bài viết này, chúng ta sẽ lần lượt điểm qua những tính năng trước khi kết thúc năm 2019.

## ES6 (ECMAScript 2015)

---

### 1. Arrow functions (=>)

```javascript
const test = {
    name: "test object",
    createAnonFunction: function () {
        return function () {
            console.log(this.name);
            console.log(arguments);
        };
    },

    createArrowFunction: function () {
        return () => {
            console.log(this.name);
            console.log(arguments);
        };
    },
};
```

_Test>>_

```javascript
> const anon = test.createAnonFunction('hello', 'world');
> const arrow = test.createArrowFunction('hello', 'world');

> anon();
undefined
{}

> arrow();
test object
{ '0': 'hello', '1': 'world' }
```

### 2. Classes

```javascript
"use strict";
class Polygon {
    constructor(height, width) {
        this.h = height;
        this.w = width;
    }
    test() {
        console.log("The height of the polygon: ", this.h);
        console.log("The width of the polygon: ", this.w);
    }
}

//creating an instance
var polyObj = new Polygon(10, 20);
polyObj.test();
```

### 3. Let and Const

```javascript
// Let - variable is available only in the block of code
function calculate(x) {
    var y = 0;
    if (x > 10) {
        // let y is only available in this block of code
        let y = 30;
        return y;
    }
    return y;
}
```

### 4. Template strings

```javascript
const classes = `header ${
    isLargeScreen() ? "" : item.isCollapsed ? "icon-expander" : "icon-collapser"
}`;
```

### 5. Promises

```javascript
function getMoneyBack(money) {
    return new Promise((resolve, reject) => {
        if (typeof money !== "number") {
            reject(new Error("money is not a number"));
        } else {
            resolve(money);
        }
    });
}

getMoneyBack(1200).then((money) => {
    console.log(money);
});
```

## ES7 (ECMAScript 2016)

---

### 1. Array.prototype.includes

Before

```javascript
const numbers = [4, 8, 15, 16, 23, 42];

if (numbers.indexOf(42) !== -1) {
    // ...
}
```

After

```javascript
const numbers = [4, 8, 15, 16, 23, 42];

if (numbers.includes(42)) {
    // ...
}
```

### 2. Exponentiation Operator

```javascript
// Old way
const old = Math.pow(3, 7);
// 2187
// ✅ ES7 way
const es7 = 3 \*\* 7;
// 2187
```

## ES8 (ECMAScript 2017)

---

### 1. Object.values() and Object.entries()

Object.entries()

```javascript
Input : const obj = { 0: 'adam', 1: 'billy', 2: 'chris' };
console.log(Object.entries(obj)[1]);

Output : Array ["1", "billy"]
Object.values()

Input : var check = ['x', 'y', 'z'];
console.log(Object.values(check));
Output : Array ["x", "y", "z"] 2. String.prototype.padEnd() and String.prototype.padStart()
String.prototype.padStart()

const str1 = '5';

console.log(str1.padStart(2, '0'));
// expected output: "05"

const fullNumber = '2034399002125581';
const last4Digits = fullNumber.slice(-4);
const maskedNumber = last4Digits.padStart(fullNumber.length, '\*');

console.log(maskedNumber);
// expected output: "\*\*\*\*5581"
String.prototype.padEnd()

const str1 = 'Breaded Mushrooms';

console.log(str1.padEnd(25, '.'));
// expected output: "Breaded Mushrooms........"

const str2 = '200';

console.log(str2.padEnd(5));
// expected output: "200 "
```

### 3.Async function (async/await)

```javascript
function resolveAfter2Seconds() {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("resolved");
        }, 2000);
    });
}

async function asyncCall() {
    console.log("calling");
    var result = await resolveAfter2Seconds();
    console.log(result);
    // expected output: 'resolved'
}

asyncCall();
```

## ES9 (ECMAScript 2018)

---

### 1. Asynchronous iteration

```javascript
for await (let book of books) {
    console.log(book);
}
```

### 2. Rest operator

```javascript
const fruits = { orange: 1, apple: 10, banana: 4 };
const { orange, ...rest } = fruits;
console.log(rest); // { apple: 10, banana: 4 };

// in the function
function getFruits(apple, ...rest) {
    return rest.banana;
}
```

### 3. Promise.prototype.finally

```javascript
let isLoading = true;

fetch(myRequest)
    .then(function (response) {
        var contentType = response.headers.get("content-type");
        if (contentType && contentType.includes("application/json")) {
            return response.json();
        }
        throw new TypeError("Oops, we haven't got JSON!");
    })
    .then(function (json) {
        /_ process your JSON further _/;
    })
    .catch(function (error) {
        console.log(error);
    })
    .finally(function () {
        isLoading = false;
    });
```

## ES10 (ECMAScript 2019)

---

### 1. Optional Catch Binding

Before

```javascript
try {
    doSomethingThatMightThrow();
} catch (exception) {
    // ^^^^^^^^^
    // We must name the binding, even if we don’t use it!
    handleException();
}
```

After - In ES2019, catch can now be used without a parameter.

```javascript
try {
    doSomethingThatMightThrow();
} catch {
    // → No binding!
    handleException();
}
```

### 2. Object.fromEntries()

```javascript
const entries = new Map([
    ["foo", "bar"],
    ["baz", 42],
]);

const obj = Object.fromEntries(entries);

console.log(obj);
// expected output: Object { foo: "bar", baz: 42 } 3. Array.flat()
var arr1 = [1, 2, [3, 4]];
arr1.flat();
// [1, 2, 3, 4]

var arr2 = [1, 2, [3, 4, [5, 6]]];
arr2.flat();
// [1, 2, 3, 4, [5, 6]]

var arr3 = [1, 2, [3, 4, [5, 6]]];
arr3.flat(2);
// [1, 2, 3, 4, 5, 6]

var arr4 = [1, 2, [3, 4, [5, 6, [7, 8, [9, 10]]]]];
arr4.flat(Infinity);
// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

### 4. Array.flatMap()

```javascript
let arr1 = ["it's Sunny in", "", "California"];

arr1.map((x) => x.split(" "));
// [["it's","Sunny","in"],[""],["California"]]

arr1.flatMap((x) => x.split(" "));
// ["it's","Sunny","in", "", "California"]
```

### 5-6. String.trimStart() & String.trimEnd()

```javascript
String.trimStart();

var greeting = " Hello world! ";

console.log(greeting);
// expected output: " Hello world! ";

console.log(greeting.trimStart());
// expected output: "Hello world! ";
String.trimEnd();

var greeting = " Hello world! ";

console.log(greeting);
// expected output: " Hello world! ";

console.log(greeting.trimEnd());
// expected output: " Hello world!";
```

### 7. Dynamic Import

```javascript
// Default export
export default () => {
    console.log("Hi from the default export!");
};

// Named export `doStuff`
export const doStuff = () => {
    console.log("Doing stuff…");
};
```

Tại đây, khai báo và sử dụng ./utils.js statically:

### 8. globalThis Object

```javascript
const global = Function("return this")();

const getGlobal = function () {
    if (typeof self !== "undefined") {
        return self;
    }
    if (typeof window !== "undefined") {
        return window;
    }
    if (typeof global !== "undefined") {
        return global;
    }
    throw new Error("unable to locate global object");
};

const global = getGlobal(); // will return window object in the browser

// array usage example
const numbers = new global.Array(1, 2, 3);
console.log(numbers); // outputs [1, 2, 3];
```

## ES11 (ECMAScript 2019) - Stage 3

---

### 1 - Optional Chaining ?.

```javascript
const player = {
    details: {
        name: {
            firstName: "Quang",
            lastName: "Hai",
            age: 20,
        },
    },
    jobs: ["dev js", "dev php"],
};

const playerFirstName = player?.details?.name?.firstName;
```

### 2 - Private fields

```javascript
class Foo {
    #b = 15;
    a = 10;
    get() {
        return this.#b;
    }

    increment() {
        ++this.#b;
    }
}
const obj = new Foo();

obj["#b"]; // undefined
obj.a = 10;
obj.hasOwnProperty("#b"); // false
```

Proposal: https://github.com/tc39/proposal-class-fields

### 3 - undefined javascript - Nullish Coalescing ??

```javascript
const player = input.player || "Ronaldo Cr7";
/*Nhưng nếu input.player sẽ là một trong những falsy values thì như thế nào,
do đó sử dụng tính năng mới này Nullish Coalescing ??*/

const player = input.player ?? "Ronaldo Cr7";
```

### 4 - Top Level await

Proposal: [github](https://github.com/tc39/proposal-top-level-await) Một bài viết khá dài cho anh em, để tổng kết những tính năng từ khi es6 ra đời...

```
Chúc anh em một năm tốt đẹp ...
```

Ref: dev.to

---

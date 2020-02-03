<h1 align="center">
  Quick Tips Javascript
</h1>

<h4 align="center">
  :coffee: Code and coffee
</h4>

<p align="center">
  A simple and objective guide to good practices in javascript (in progress)
</p>

## Contents

- [Destructuring](#destructuring)
- [Conditional (ternary) operator](#conditional-ternary-operator)
- [Variable Declaration](#variable-declaration)

## Destructuring

### Objects

:poop: **BAD**

```javascript
const person = {
  name: 'Joe',
  age: 24,
  color: 'green',
  food: 'pizza'
};

function about(user) {
  return `I'm ${user.name} and my favorite food is ${user.food}`;
}

console.log(about(person));
// I'm Joe and my favorite food is pizza

const name = person.name;
const age = person.age;

console.log(name, age);
// Joe, 24
```

:heavy_check_mark: **GOOD**

```javascript
const person = {
  name: 'Joe',
  age: 24,
  color: 'green',
  food: 'pizza'
};

function about({ name, food }) {
  return `I'm ${name} and my favorite food is ${food}`;
}

console.log(about(person));
// I'm Joe and my favorite food is pizza

const { name, age } = person;

console.log(name, age);
// Joe, 24

//  OR

const { name: myName, age: myAge } = person;

console.log(myName, myAge);
// Joe, 24
```

### Arrays

:poop: **BAD**

```javascript
const names = ['Douglas', 'Thiago', 'Nill'];

console.log(names[0]); // Douglas
console.log(names[1]); // Thiago
console.log(names[2]); // Nill
```

:heavy_check_mark: **GOOD**

```javascript
const names = ['Douglas', 'Thiago', 'Nill'];

const [first, second, third] = names;

console.log(first); // Douglas
console.log(second); // Thiago
console.log(third); // Nill

//  OR

const [, , third] = names;

console.log(third); // Nill
```

---

## Conditional (ternary) operator

:poop: **BAD**

```javascript
const name = 'Douglas';
let head;

if (name === 'Douglas') {
  head = 'bald';
} else {
  head = 'hairy';
}
```

:heavy_check_mark: **GOOD**

```javascript
const name = 'Douglas';
const head = name === 'Douglas' ? 'bald' : 'hairy';
```

---

## Variable Declaration

### Let

The `let` expression allows you to limit the scope of a variable declared only for that expression.

```javascript
/*
 * Example 1
 */
function foo() {
  var a = 5;
  var b = 10;

  if (a === 5) {
    let a = 4; // let belongs to "if" scope
    var b = 1; // var belongs to "foo" scope

    console.log(a); // 4
    console.log(b); // 1
  }

  console.log(a); // 5
  console.log(b); // 1
}

/*
 * Example 2
 */
function bar() {
  for (let i = 0; i < 10; i++) {
    alert(i); // 1, 2, 3, 4 ... 9
  }

  alert(i); // ERROR: i is not defined
}
```

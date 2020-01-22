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

## Destructuring

### Objects

:poop: BAD

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

:heavy_check_mark: GOOD

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

:poop: BAD

```javascript
const names = ['Douglas', 'Thiago', 'Nill'];

console.log(names[0]); // Douglas
console.log(names[1]); // Thiago
console.log(names[2]); // Nill
```

:heavy_check_mark: GOOD

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

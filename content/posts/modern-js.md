---
title: "Modern Js"
date: 2020-12-13T21:23:31-05:00
draft: false
---


## Arrow functions
Arrow functions have this syntax:

const myFunction = () => {
  //...
}

## The spread operator
If you see

const c = [...a]

This statement copies an array.

You can add items to an array as well, using

const c = [...a, 2, 'test']

The ... is called spread operator.

## Destructuring assignments
You can extract just some properties from an object using this syntax:

const person = {
  firstName: 'Tom',
  lastName: 'Cruise',
  actor: true,
  age: 54
}

const { firstName: name, age } = person

You will now have two const values name and age.

The syntax also works on arrays:

const a = [1,2,3,4,5]
[first, second, , , fifth] = a


## Template literals
If you see strings enclosed in backticks, it’s a template literal:

const str = `test`
Inside this, you can put variables and execute javascript, using ${...} snippets:

const string = `something ${1 + 2 + 3}`

const string2 = `something ${doSomething() ? 'x' : 'y'}`

And also, you can span a string over multiple lines:

const string3 = `Hey
this

string
is awesome!`

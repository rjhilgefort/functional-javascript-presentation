# Intro To Functional Javascript
## Rob Hilgefort



---



# `whoami`

**Background**

- From Cincinnati, Ohio.
- [University of Kentucky](http://www.uky.edu/) graduate.
- Developer at [Losant, IOT](https://www.losant.com/)

**Contact**

- Github: [@rjhilgefort](https://github.com/rjhilgefort)
- Twitter: [@rjhilgefort](https://twitter.com/rjhilgefort)

{.column}

.![](https://www.losant.com/hubfs/Website/losant-icon.png?t=1514770275982)



---



# What This Is, What This Is Not

**Is**

- A "101" talk
- Enablement to read/write FP in the real world
- An advertisement for Ramda (basically)

**Is Not**

- An intro to JS (assumes modern JS knowldege)
- A deep dive into FP
- ADT Coverage

{.column}

.![](https://image.slidesharecdn.com/designersprogramadores-no-front-slide-160315170004/95/designers-developers-4-638.jpg?cb=1458061374)



---



# Functional Programming

Functional programming (FP) is a programming paradigm that is the process of building software by composing pure functions and avoiding shared state, mutable data, and side-effects.

Functional programming is declarative rather than imperative, and application state flows through pure functions. To do so, one is encouraged to follow some core tenants and guiding principles.

{.column}

Other examples of programming paradigms include procedural programming and object oriented programming.

- Procedural programming is generally what you would call a "script", where instructions are a series of computational steps to be carried out.
- Object oriented programming (OOP), encourages data where application state is usually shared and colocated with methods in objects.

<!--
# REFS
https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0
https://en.wikipedia.org/wiki/Procedural_programming
-->



---



# Why Functional Programming

- Predictability
- Testability
- Easy to reason about
- Easy to refactor
- Concurrency
- DRY

{.column}

.![](http://images.genius.com/ff26c4e75a0ef8ad88f4e7db7e63416b.1000x1000x1.jpg)

<!--
- Predictability
  - Pure functions, same output on consecutive calls
- Testability
  - Pure functions are easy to test because you don't have to "mock the world" for different cases
- Easy to reason about
  - Declarative code indicates intent from the get go
- DRY
  - FP encourages tiny composable methods (lego blocks) which are easy to reuse
- Easy to refactor
  - Tiny composable methods are easy to move around
- Concurrency
  - Because FP apps are pure and the side effects delegated to the edges of the app, concurrency is much easier to achieve
-->



---



# FP Concepts, Terms, Jargon

- Declarative (vs Imperative)
- First Class Functions
- Higher Order Functions (HOF)
- Side Effects
- Purity
- Referential Transparency
- Immutability
- Currying
- Composition (vs Inheritance)
- Point-free

{.column}

.![](http://www.bathshop321.com/blog/wp-content/uploads/2016/08/JARGON-BLOG.png)

<!--
- All still JavaScript, but baked in is some sommon language you'll hear/read when working in an FP style.
-->



---



# <span style="color:white">That's A Lot</span>

## <span style="color:black">Why should I bother?</span>

![](https://www.maxim.com/.image/t_share/MTQzODYyMzMxMjcxNTU0MTI0/home-alonejpg.jpg){.background}

<!--
- Whoa, that's a lot, do I really need to know all this stuff to write safer things.
- We're here to solve problems and put products out in the world, so why do we need to learn a new way to write code?
- Code golf or real improvements?
- Let's see through some examples
-->



---



# Declarative Programming

## Express the logic of a computation without describing its control flow.

Programming is done with expressions or declarations instead of statements. In contrast, **imperative programming** uses statements that change a program's state.

**Imperative:** I see that table located under the Gone Fishin’ sign is empty. My husband and I are going to walk over there and sit down.

**Declarative:** Table for two, please.

<!--
- Declarative Programming is like asking your friend to draw a landscape. You don’t care how they draw it, that’s up to them. Imperative Programming is like your friend listening to Bob Ross tell them how to paint a landscape. While good ole Bob Ross isn’t exactly commanding, he is giving them step by step directions to get the desired result.
- The imperative approach is concerned with HOW you’re actually going to get a seat. You need to list out the steps to be able to show HOW you’re going to get a table.The declarative approach is more concerned with WHAT you want, a table for two.
- Let's look at an example

# REFS
- https://en.wikipedia.org/wiki/Declarative_programming
- https://en.wikipedia.org/wiki/Imperative_programming
- https://codeburst.io/declarative-vs-imperative-programming-a8a7c93d9ad2
- https://tylermcginnis.com/imperative-vs-declarative-programming/
-->



---



# Declarative Programming

```javascript
// Imperative
// Double every number in list

const nums = [2, 5, 8];

for (let i = 0; i < nums.length; i++) {
  nums[i] = nums[i] ** 2
}

console.log(nums)
// [4, 10, 16]
```

{.column}

```javascript
// Declarative
// Double every number in list

const double = x => x ** 2

const nums = [2, 5, 8];
const numsDoubled = nums.map(double)

console.log(numsDoubled)
// [4, 10, 16]
```

<!--
- Code comments in imperative programs are often declarative!
-->



---



# JavaScript Enablement

## Not all languages can do that

<!--
- As a JS developer I'm not showing you anything new.
- You may write declaratively and just haven't been calling it that.
- What we saw with `map(double)` is made possible by first class functions
-->



---



# First Class Functions

## Functions are values

First class function support means we can treat functions like any other data type and there is nothing particularly special about them - they may be stored in arrays, passed around as function parameters, assigned to variables, etc.

<!--
https://stackoverflow.com/questions/10141124/any-difference-between-first-class-function-and-high-order-function
-->



---



# Higher Order Functions

## Functions take and return functions

First class function support enables **higher order functions**- functions that work on other functions, meaning that they take one or more functions as an argument and can also return a function.

<!--
https://stackoverflow.com/questions/10141124/any-difference-between-first-class-function-and-high-order-function
-->


---



# First Class Functions, Higher Order Functions

```javascript
const getServerStuff = (callback) => {
  return ajaxCall((json) => {
    return callback(json)
  })
}

// ... is the same as ...

const getServerStuff = ajaxCall;
```

{.column}

.![](https://i.kinja-img.com/gawker-media/image/upload/s--_vIgZ0km--/c_scale,f_auto,fl_progressive,q_80,w_800/yccc3f4vcwsxyj6eydy2.jpg)

<!--
https://drboolean.gitbooks.io/mostly-adequate-guide
-->



---



# <span style="color:white">Great, Thanks.</span>

## <span style="color:white">Please don't teach me JavaScript</span>

![](https://cdn-images-1.medium.com/max/1020/1*YwzjmYkrqyjkW-HzbXOEFw.jpeg){.background}

<!--
- Important to understand those terms to understand declarative programming
- Important to understand declarative programming to understand FP
-->



---



# Okay!

## Let's talk about *the* core paradigm of FP



---



# Purity

A **pure** function is a function that, given the same input, will always return the same output and does not have any observable side effect. Basic rules:

- No outside scope
- Always returns a value
- Immutability
- Doesn't have any **side effects**
- **referential trasparency**
- **function composition**

{.column}

Purity is the secret sauce of FP and everything else is an effort to preserve it. Achieving purity implies **referential transparency** and allows for **function composition**. We'll get to those, but let's make sure we grok what purity means first.

.![](http://i0.kym-cdn.com/photos/images/original/001/017/429/b8a.png)

<!--
- We'll talk about a few of those terms later
- Let's walk through what these mean

#REFS
https://drboolean.gitbooks.io/mostly-adequate-guide/content/ch3.html
-->



---



# Purity: No Outside Scope

```javascript
// Impure
const names = [
  'Michael', 'Erin', 'Dylan', 'Wes', 'Bao', 'Taron',
]
const maxNames = 5

const isValidNames =
  names => names.length <= maxNames

console.log(isValidNames(names)) // false
```

{.column}

```javascript
// Pure
const names = [
  'Michael', 'Erin', 'Dylan', 'Wes', 'Bao', 'Taron',
]

const isValidNames = names => {
  const maxNames = 5
  return names.length <= maxNames
}

console.log(isValidNames(names)) // false
```



---



# Purity: Returns A Value

```javascript
// Impure
const names = [
  'Michael', 'Erin', 'Dylan', 'Wes', 'Bao', 'Taron',
]

const count
const getNamesCount = names => {
  count = names.length
}

getNamesCount(names)
console.log(count) // 6
```

{.column}

```javascript
// Pure
const names = [
  'Michael', 'Erin', 'Dylan', 'Wes', 'Bao', 'Taron',
]

const getNamesCount =
  names => names.length

const count = getNamesCount(names)
console.log(count) // 6
```



---



# Immutability

## Objects can’t be modified after it’s created

In other words, you may not reassign properties/indexes on JS objects when you need to "update" some part of that structure. Doing so is called a **mutation** because we're modifying a piece of shared state in an application.

Immutability is a central concept of functional programming because without it, the data flow in your program is lossy. State history is abandoned, and strange bugs can creep into your software.


<!--
# REFS
- https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0
-->



---



# Mutability, Shared State :x:

```javascript
// Given the following
const foo = {
  val: 2,
}

const addOneObjVal =
  () => foo.val += 1
const doubleObjVal =
  () => foo.val *= 2
```

{.column}

```javascript
// The order of execution changes
// the output of the function

addOneObjVal() // { val: 3 }
doubleObjVal() // { val: 6 }

// `foo` is reset to original

doubleObjVal() // { val: 4 }
addOneObjVal() // { val: 5 }
```

<!--
# REFS
- https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0
-->



---



# Immutability :white_check_mark:

```javascript
// Given the following
const foo = {
  val: 2,
}

const addOneObjVal =
  x => Object.assign({}, x, { val: x.val + 1})
const doubleObjVal =
  x => Object.assign({}, x, { val: x.val * 2})
```

{.column}

```javascript
// Now it doesn't matter if we call the other
// method before any other method call that
// acts on `foo`.

addOneObjVal(foo) // { val: 3 }
addOneObjVal(foo) // { val: 3 }
addOneObjVal(foo) // { val: 3 }

doubleObjVal(foo) // { val: 4 }
doubleObjVal(foo) // { val: 4 }

// Combining as we did when mutating...

doubleObjVal(addOneObjVal(foo))
// { val: 6 }
```



---



# Mutability Is No bueno!
## Complicates debugging and reasoning about code



---



# Benefits Of Purity

![](https://cdn-images-1.medium.com/max/1600/1*lHMDe_A2Cs_4InZ-E9Da9A.png){.background}

<!--
- Seems like work, what's the pay off?
-->



---



# Referential Transparency

## An expression always evaluates to the same result in any context.

By respecting the aforementioned rules of purity when building your functions, you achieve what is called **referential transparency**. This is perhaps the biggest payoff of striving for pure functions because it allows for you to more easily reason about your functions.

A spot of code is referentially transparent when it can be substituted for its evaluated value without changing the behavior of the program.

<!--
- Most of the "good" examples from the past few slides do this
- Let's look at one more example
-->



---



# Referential Transparency

```javascript
const foo = (x, y) => {
  if (x === y) return x
  if (x < 5) return x * 2
  return y
}

const bar = foo(2, 3)
console.log(bar) // 4

// referential transparency says...

const bar = 4
console.log(bar) // 4
```

{.column}

Because our method `foo` is pure, we can use a technique called equational reasoning wherein one substitutes "equals for equals" to reason about code. It's a bit like manually evaluating the code without taking into account the quirks of programmatic evaluation.


<!--
# REFS
- https://drboolean.gitbooks.io/mostly-adequate-guide/content/ch3.html#the-case-for-purity
-->



---



# Fin

**That's it. Thanks.**

Oh, this talk was stolen! I picked code examples and some definitions here and there from other articles and books that are free on the web. Here's a list of some resources to go check out if you liked this talk and/or want to learn more.

- [Mostly Adequate Guide To Functional Programming](https://drboolean.gitbooks.io/mostly-adequate-guide/content/ch2.html)
- [Eric Elliott - What is Functional Programming?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0)
- [Anjana Vakil — Functional Programming in JS: What? Why? How?](https://youtu.be/qtsbZarFzm8)
- [Awesome FP](https://github.com/stoeffel/awesome-fp-js)

{.column}

**Feedback**

You think I missed something? Saw a silly typo? Just generally want to improve upon this talk? You can help me fix it!

I made this talk using [md2googleslides](https://github.com/googlesamples/md2googleslides) which allowed me to write the whole thing in markdown and build it to Google Slides. You can submit a PR to the repo so the next time I give the talk, it'll suck less!


---

# Extra

- fp all things https://m4n3z40.github.io/fp-intro-presentation/img/fp-all-the-things.jpg
- tweet https://m4n3z40.github.io/fp-intro-presentation/img/james-iry-about-fpers.png
- homer https://cdn-images-1.medium.com/max/1600/1*AM83LP9sGGjIul3c5hIsWg.png

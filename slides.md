---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /assets/intro.jpg
# some information about your slides (markdown enabled)
title: Software Development | Foundations
info: |
  ## Software Development | Foundations
# apply unocss classes to the current slide
class: text-left
drawings:
  persist: false
transition: slide-left
mdc: true
---

# Unit Testing
Full-Stack Development - part 6/8

- [ ] Intro to Testing
- [ ] Writing Unit Tests
- [ ] Automated Test `npm-test`

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
-->

---
transition: slide-left
---

# Intro to Unit Testing
What is testing and why it's important in software development

- Can you think of something where we test the product before we buy the product?
- Have you ever coded a new feature, only to have something that previously worked, break?
- Have you ever spent hours debugging something, only to find it was a small typo or logic error?
- Have you ever been afraid to refactor code because you weren't sure what might break?
- If your project grew 10x in size, how would you make sure everything still worked?
- What would happen if your app broke and users noticed before you did?

What is the role of a developer when we think about testing?
- [QA Job Postings](https://ca.indeed.com/jobs?q=qa+engineer&l=Remote&from=searchOnDesktopSerp&vjk=81b75ba803f6d8e7)

---
transition: slide-left
---

# Definition

- Software Testing: A process to evaluate and ensure that software works as intended
- Why?
   - Reduces bugs
   - Improves code quality
   - Supports maintainability
- Your role as a developer: Deveopers are responsible for writing reliable code, which includees creating and running tests

What are some consequences of not testing properly?

---
transition: slide-left
---

# Types of Testing

- Unit Tests: Tests the smallest parts of code (ex: functions) in isolation
   - competing tools: Jest, Mocha/Chai, Vitest
- Integration Tests: Ensures that combined parts of an app work together
   - tools: Jest, Mocha/Chai, Vitest, react-testing-library, Playwright
- End-to-End Tests: Simulates real user scenarios from start to finish
   - tools: Playwright, Cypress
- Ask ChatGPT:
   - What is the most popular testing library for node apps?
   - List developer testing tools in chronological order (ex: jest, mocha chai) 
- What do you think would change if you had a way to automatically test parts of your app every time you updated it?

---
transition: slide-left
---

# Debugging Tools

- Debugging Express Routes:
   - use of `console.log()` for basic tracing
   - use of VS Code breakpoints within Node.js
   - understanding of request/response cycle and basic status codes
- Testing Express Routes:
   - Manually testing via Postman (simulates API calls)
   - Use of browser dev tools to inspect network calls and responses

---
transition: slide-left
---

# Jest 
https://jestjs.io/ - Jest is an all-in-one test runner and assertion library

- Test Runner: a tool that finds your test files, executes the test code, reports results.  Usually includes functions like `describe`, `test` or `it`, `beforeEach` etc.
  ```js
  describe('feature name', () => {
    it('should add numbers correctly', () => {
      // put assertion code here
    });
  })
  ```
- Other competing software: Mocha, Jasmine, [Vitest](https://2024.stateofjs.com/en-US/awards/), 
- Assertion Library: a tool used to check whether your code behaves as expected.  Usually includes functions like `expect`, `assert`, `toBe`
  ```js
  it('should add numbers correctly', () => {
    expect(1 + 1).toBe(2);
  });
  ```

---
transition: slide-left
---

# Setup Jest & [supertest](https://github.com/ladjs/supertest#readme)

- `npm init -y`
- `npm i -D jest @babel/core @babel/preset-env babel-jest supertest`
- Change package.json:
   ```json
    "type": "module",
    "scripts": {
      "test": "jest --silent=false", // silent=false allows me to view console.log() output
      "test:watch": "jest --watch"
    },
   ```
   - run `git init` otherwise "watch" won't work
- Create `.babelrc`
  ```json
  {
    "presets": ["@babel/preset-env"]
  }
  ```

---
transition: slide-left
---

# Writing Unit Tests (pg.1)

  ```js
  // first.test.js
  describe('first test', () => {
      it('should work', () => {
          expect(true).toBe(true)
      });

      it('should be 4', () => {
          expect(1 + 1).toBe(2)
      })
  })
  ```
- `npm run test` or `npm run test:watch`
- try breaking a test to see what happens (ex: `expect(2 + 2).toBe(5)`)
- What does [describe](https://jestjs.io/docs/api#describename-fn) do?
- What does [it](https://jestjs.io/docs/api#testname-fn-timeout) do?
- What does [expect](https://jestjs.io/docs/expect) do?
- What does [toBe](https://jestjs.io/docs/expect#tobevalue) do? 
   - compare objects using toBe vs [toEqual](https://jestjs.io/docs/expect#toequalvalue)

---
transition: slide-left
---

# Writing Unit Tests (pg.2)
Test Driven Development (i.e. red 🔴, green 🟢, refactor 🟢) is one style of writing unit tests. 

1. Write the unit test first = `RED`
  ```js
  // math.js
  export const add = () => {}

  // /tests/math.test.js
  import { add } from '../math.js';

  describe('add', () => {
    it('should add two numbers', () => {
      expect(add(2, 3)).toBe(5);
    });
  });
  ```
- Step 1) 🔴 `RED`
- Step 2) 🟢 `GREEN` - implement function now to make it pass
- Step 3) 🟢 `REFACTOR` function (if needed) yet still pass
- Now you have a way to add/change features in your codebase and getting instant feedback

---
transition: slide-left
---

# Writing Unit Tests (pg.3)

2. Write the function then incorporate it into test so it passes = `GREEN`
    ```js
    // math.js
    export function add(a, b) {
      return ???;
    }
    ```
    ```js
    // tests/math.test.js
    import { add } from '../math.js';

    describe('add', () => {
      it('should add two numbers', () => {
        expect(add(2, 3)).toBe(5);
      });
    });
    ```
- Tip: _Your tests pass because they didn't fail. Not because your code works_ (ex: `return 4`)
1. Refactor function if needed so it's cleaner yet stays `GREEN` 
- Q: When should you write unit tests?

---
transition: slide-left
---

# Exercise: Writing Unit Tests
Practice Test Driven Development

- Tip: Install VS Code extension "Jest"
1. Make functions and unit tests for:
   - `subtract()`
   - `multiple()`
   - `divide()`

---
transition: slide-left
---

# Testing for Invalid Input (pg.1)

- What happens if your functions are called with arguments that invalid? ex: add('1', '2')

  ```js
  // math.js
  export const add = (a, b) => {
    if (typeof a === 'string') a = Number(a);
    if (typeof b === 'string') b = Number(b);
    return a + b;
  }

  // /tests/math.test.js
  it('should cast string numerals into numbers', () => {
    expect(add('1', '2')).toBe(3)
  })
  ```
  - But what happens if you call it with `(add(2, 'potato')`? 
 
---
transition: slide-left
---

# Testing for Invalid Input (pg.2)

  - What happens if you call it with `(add(2, 'potato')`?
  - How would you write the test? 
  - Would you expect it to throw an error or not? (depends on what you want to accomplish. No right answer here) 
  ```js
  // math.js
  export const add = (a, b) => {
    if (typeof a === 'string') a = Number(a);
    if (typeof b === 'string') b = Number(b);

    if (isNaN(a)) throw new Error("the first argument is not a number")
    if (isNaN(b)) throw new Error("the second argument is not a number")

    return a + b;
  }

  // /tests/math.test.js
  it('should cast string numerals into numbers', () => {
    expect(() => (add(2, 'potato').toThrow())) // note we had to wrap with expect()
  })
  ```

---
transition: slide-left
---

# Exercise: Writing Unit Tests for Edge Cases

- Refactor your unit tests to take into account some of these edge cases
- Here are some examples of invalid inputs that you may want to take into account in your unit tests:
  - `boolean`, `string`, `number`
  - `undefined`, `null`, `NaN`
  - array, object, function
  - Promise

---
layout: image-right
transition: slide-left
image: /assets/kent.png
backgroundSize: 400px 250px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:

- 🏗️ [Load Balancing](https://samwho.dev/load-balancing/)
- 💾 [Tech Documentaries](https://www.techdocumentaries.com/#2)
- 🎨 [Interactive SVG Reference](https://www.fffuel.co/sssvg/)
- 🧑‍🎨 [Toools Design Resources](https://www.toools.design/?ref=dailydev)
- ✋ [Stop Lying to Your Users](https://www.epicweb.dev/stop-lying-to-your-users)

<br>
<hr>
<br>

- 🧪 [Enter anonymous lab questions](https://docs.google.com/forms/d/e/1FAIpQLSevvGARdHQikso-uLqFCO481MABKE5HofuSrlzEPMNQ2ZLykw/viewform?usp=dialog)
- ℹ️ [Course feedback survey](https://circuitstream.typeform.com/to/ZoyYk7px#course_id=SoftwareAN&instructor=9514)

<!--
- take attendance
-->

---
transition: slide-left
---

# Unit Testing Async Functions (pg.1)

- try the following, does this pass?:
  ```js
  it('should this async code pass?', () => {
    setTimeout(() => {
      expect(false).toBe(true);
    }, 1000)
  })
  ```
  - let's put this timeout in an async function, then write a unit test

---
transition: slide-left
---

# Unit Testing Async Functions (pg.2)

  ```js
  // in math.js
  export const delayedAnswer = () => {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve(2);
      }, 1000)
    })
  }

  // in /tests/math.test.js
  import { delayedAnswer } from '../math.js';

  it('should pass even tho async', async () => {
    const answer = await delayedAnswer(2);
    expect(answer).toBe(2)
  })
  ```

---
transition: slide-left
---

# Spies 

- Spies give existing functions introspection abilities.
- 

---
transition: slide-left
---

# Mocks

- Mocks are placeholders for existing functions

---
transition: slide-left
layout: two-cols
---

# Homework

- Practice full-stack by building a [movie ratings and review application](https://courses.circuitstream.com/d2l/le/lessons/9514/topics/49843)
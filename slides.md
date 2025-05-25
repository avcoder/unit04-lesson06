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

- [ ] Intro to Unit Testing
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

- Can you think of something where we test the product before we buy the product?
- Have you ever coded a new feature, only to have something that previously worked, break?
- Have you ever spent hours debugging something, only to find it was a small typo or logic error?
- Have you ever been afraid to refactor code because you weren't sure what might break?
- If your project grew 10x in size, how would you make sure everything still worked?
- What would happen if your app broke and users noticed before you did?

What is software testing and why is it important?

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

---
transition: slide-left
---

# Debugging and Testing Routes

- Identify tools you might use to normally test a route like this:
```js
app.get('/api/trucks', (req, res) => {
  res.json({ message: 'List of food trucks' });
});
```
- What do you think would change if you had a way to automatically test parts of your app every time you updated it?
- `npm init -y`
- `npm i -D jest @babel/core @babel/preset-env babel-jest`
- Change package.json:
   ```json
    "scripts": {
      "test": "jest",
      "test:watch": "jest --watch"
    },
   ```
   - run `git init` otherwise "watch" won't work

---
transition: slide-left
---

# Exercise: Writing Unit Tests (pg.1)

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
- https://jestjs.io/docs/expect

---
transition: slide-left
---

# Exercise: Writing Unit Tests (pg.2)

- FILL IN THE BLANK
```js
// math.js
export function add(a, b) {
  return a + b;
}

// math.test.js
import { add } from '../math.js';

describe('add()', () => {
  it('should add two numbers', () => {
    expect(________).toBe(5);
  });
});
```

---
layout: image-right
transition: slide-left
image: /assets/dodds.png
backgroundSize: 400px 320px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:

- 🧼 [Background Removal Tool](https://huggingface.co/spaces/Xenova/remove-background-web)
- 🎒 [Self-hosted Apps](https://selfhosted.libhunt.com/)
- 😵‍💫 [Brutalist Report](https://brutalist.report/)
- 📝 [Markdown Notes](https://github.com/orgs/community/discussions/16925)

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

# Show a google map based off lat/lng coordinates

- We need to adjust our schema to include location etc.
- let's move our choices to truckController as a const
- adjust our addTruck form and editTruck form to include location
- add autocomplete functionality for address
- add slug page
- make static google map based off our lat/lng
- ensure slug is unique

---
transition: slide-left
---

# Create tags page

- create `getTags` route
- add `.getAllTags()` method to Truck schema
- make clicking each tag filter and display corresponding food trucks with tag

---
transition: slide-left
---

# Lab tomorrow
Do at least 1 "Getting Started" from:

  - [Socket io](https://socket.io/get-started/chat)
  - [AI LLM chat model](https://js.langchain.com/docs/tutorials/llm_chain)
  - [Snipcart](https://docs.snipcart.com/v3/)
  - [Nest JS](https://docs.nestjs.com/first-steps)
  - [Next JS](https://nextjs.org/docs/app/getting-started/installation)
  - [Netlify Serverless Functions](https://docs.netlify.com/functions/get-started/?fn-language=js)
  - [Go](https://go.dev/doc/tutorial/getting-started)
  - [PostGreSQL](https://neon.tech/postgresql/postgresql-getting-started)
  - [PHP](https://www.php.net/manual/en/tutorial.php)
  - [GraphQL](https://graphql.org/graphql-js/)
  - [Electron](https://www.electronjs.org/docs/latest/tutorial/tutorial-first-app)
  - [Astro](https://docs.astro.build/en/tutorial/0-introduction/)
---
theme: seriph
background: >-
  https://images.unsplash.com/photo-1532009877282-3340270e0529?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2000&q=80
class: text-center
highlighter: shiki
lineNumbers: false
colorSchema: dark
title: Automated testing
---

# Automated testing

How to feel safe pressing the red button

<!--
quick intro

- thank you all for coming
- what does the subtitle mean ? we'll see how automated tests may help us from having too many bugs in production and to prevent us from pushing new one when deploying a new version of a software, in our case, Jinko.
- I tried to simplify as much as I can that presentation to address every knowledge level of you all :)

-> if you never heard about automated testing, you will learn a lot
-> if you're familiar with automated testing, you'll learn how it may be done particularly on a software distributed on the web
-> if you're part of the dorayaki team, you're here to support me :)
-->

---
layout: image-right
image: >-
  https://images.unsplash.com/photo-1471520201477-47a62a269a87?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2000&q=80
---

# Summary

<v-clicks>

- <twemoji-face-with-raised-eyebrow class="inline" /> What is it? Why do we need it?
- <twemoji-bicycle class="inline" /> Unit testing
- <twemoji-articulated-lorry class="inline" /> Integration testing
- <twemoji-collision class="inline" /> Demo time
- <twemoji-question-mark class="inline" /> Q & A
  
</v-clicks>

<br />
<br />

<v-click>

#### What we won't cover/talk about

- implementation details
- existing tools overview

</v-click>
<!--
what are we going to talk about ?
-->

---
layout: center
---

# Why do we need automated testing?

---
class: text-center flex flex-col justify-center text-2xl
---

<v-clicks>

I. As developer, we write pieces of software.

II. Developers are humans.

III. Human sometimes make mistakes.

IV. As human, we (may) write bugs.

</v-clicks>

---
layout: center
---

# As developers we write bugs


---
layout: center
class: 'flex flex-col justify-center items-center text-center'
---

# So we need some bullet proof solution to automatically test our code and check if we introduce new mistakes regularly.

<br />

<v-click>
<img class="m-auto" src="https://historydaily.org/content/125768/7b40b4097346d86a4088c57db9f1887d.gif" alt="" />
<p class="text-sm">Buster Keaton chasing some bugs in production after release.</p>
</v-click>

---
layout: center
---

# How does it look like?

---
class: "flex flex-col"
---

# How does it look like?

Basically, an automated test may be reduced to 3 simple steps :

<div class="flex-1 flex flex-col justify-center items-center">
<v-clicks>

<p><twemoji-keycap-1 class="inline mr-2" /> <b>Given</b> a context</p>
<p><twemoji-keycap-2 class="inline mr-2" /> <b>When</b> I execute some action</p>
<p><twemoji-keycap-3 class="inline mr-2" /> <b>Then</b> I expect a specific result</p>

</v-clicks>
</div>

---
class: 'flex flex-col justify-center'
---

# How does it look like?

<div class="flex-1 flex items-center justify-center text-3xl font-bold">

  <v-clicks>
    <p>INPUT</p>
    <twemoji-right-arrow class="mx-6" />
    <p>OUTPUT</p>  
  </v-clicks>

</div>

---
layout: center
---

# Unit testing vs integration testing

---

# Unit testing

Write tests for specific parts of a software (method, component...), isolated from the rest.

<v-click>

```js
function add(a, b) {
  return a + b; 
}
```

</v-click>

<br />
<br />

<v-click>

```js{0|1-3|5-6|8-9|all}
// given
const a = 1;
const b = 2;

// when
const result = add(a, b);

//then
expect(result).toBe(3);
```

</v-click>

<!--
simple method, to add two numbers and return the result 

we have the three steps we saw earlier (given, when then)
-->

---

# Unit testing

<v-clicks>

- As a team, more than one developer is going to work on the same pieces of code
- Tests act as a guard to prevent them from introducing errors in a part of the software they did not write first
- Tests may act like specifications (test file are suffixed .spec sometimes) to understand what that part of the codebase in supposed to do

</v-clicks>

---
layout: center
class: text-center
---

# But testing all parts individually does not ensure you that all parts are working well together.

<br />

<img class="m-auto" src="https://www.shapeblue.com/wp-content/uploads/2018/11/1541174074683725.gif" alt="" />


---
layout: center
---

# Integration testing

---

# Integration testing

Test the whole software by letting a machine act like a normal user.

```js{none|1|3|5|7|9|11|all}
visit('/') // Attempt to visit home page without being authenticated

expect(url).toBe('/login') // check that are redirected to the login page

get('input[name="email"]').type('georges@abitbol.com') // fill email

get('input[name="password"]').type('laclasseamericaine') // fill password

get('button["type=submit"]').click() // click on submit button

expect(url).toBe('/') // check that we are on the home page
```

---

# Integration testing

Human error is still here

<v-clicks>

- Automate the test launch itself
- Trigger it on each modification made on the codebase
- Prevent new release to be done if some tests (unit or integration) are failing

</v-clicks>

---
layout: center
---

# Demo time

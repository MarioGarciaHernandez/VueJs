---
theme: vuestorefront
class: 'text-center'
highlighter: shiki
lineNumbers: true
drawings:
  persist: false
---

# Class and Style Bindings

---

# Inline Syntax

We can pass an object to v-bind:class to dynamically toggle classes

```js {all|1|3|all}
<div v-bind:class="{ active: isActive }"></div>

<div v-bind:class="{ active: isActive, 'text-danger': hasError }"></div>
```

---
layout: sfc
example: Test 
---

# Inline Syntax

---

# Object Syntax
We can also bind to a computed property that returns an object. This is a common and powerful pattern:

```js {all|1|3-8|all}
<div v-bind:class="classObject"></div>

data: {
  classObject: {
    active: true,
    'text-danger': false
  }
}
```

---
layout: sfc
example: Test2 
---

# Object Syntax


---

# Array Syntax

We can pass an array to v-bind:class to apply a list of classes:

```js {all}
<div v-bind:class="[activeClass, errorClass]"></div>

data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}
```

## Ternary expression

```js {all}
<div v-bind:class="[isActive ? activeClass : '', errorClass]"></div>
```

## Object Syntax inside Array Syntax 
```js {all}
<div v-bind:class="[{ active: isActive }, errorClass]"></div>
```

---
layout: sfc
example: Test3
---

# Array Syntax


---

# With Components

```js {all|1-3|5|7|all}
Vue.component('my-component', {
  template: '<p class="foo bar">Hi</p>'
})

<my-component class="baz boo"></my-component>

<p class="foo bar baz boo">Hi</p>
```

---

# Style Object Syntax

It is often a good idea to bind to a style object directly so that the template is cleaner:

The object syntax is often used in conjunction with computed properties that return objects.

```js {all|1|3-8|all}
<div v-bind:style="styleObject"></div>

data: {
  styleObject: {
    color: 'red',
    fontSize: '13px'
  }
}
```

---
layout: sfc
example: Test4
---

# Style Syntax

---

# Auto-prefixing

When you use a CSS property that requires a vendor prefix in :style, Vue will automatically add the appropriate prefix. Vue does this by checking at runtime to see which style properties are supported in the current browser. If the browser doesn't support a particular property then various prefixed variants will be tested to try to find one that is supported.

```js {all|1-2|3|4|5|7}
-webkit- (Chrome, Safari, newer versions of Opera, almost all iOS browsers including Firefox for iOS;
          basically, any WebKit based browser)
-moz- (Firefox)
-o- (old pre-WebKit versions of Opera)
-ms- (Internet Explorer and Microsoft Edge)

<div v-bind:style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>
```

This will only render the last value in the array which the browser supports. In this example, it will render display: flex for browsers that support the unprefixed version of flexbox.


---
layout: sfc
example: Test5
---

# Multiple Values
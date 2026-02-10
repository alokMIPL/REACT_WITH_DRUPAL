


# JSX

This document explains eight basic React examples created using **React 18 CDN** and **ReactDOM** without build tools.

These examples are useful for understanding:

- `React.createElement()`
- Components
- Rendering
- Nesting elements
- Basic React structure

---

## 📌 Common Setup (Used in All Files)

Each file includes:

```html
<script src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
```

And a root container:

```html
<div id="root"></div>
```

React renders content inside this `#root` element.

---

## ✅ Example 1 – Basic Element Rendering

### Purpose

```js
<body>
  <div id="root"></div>
  <script>
    let myElement = React.createElement("h1", null, "React Example 1"); let
    myRootElement = document.querySelector("#root"); ReactDOM.render(myElement,
    myRootElement);
  </script>
</body>
```

Render a simple heading using React.

### Key Concept

- `React.createElement()`
- `ReactDOM.render()`

### Explanation

```js
let myElement = React.createElement("h1", null, "React Example 1");
```

Creates an `<h1>` element.

```js
ReactDOM.render(myElement, myRootElement);
```

Displays it in the browser.

---

## ✅ Example 2 – Element with Props

### Purpose

```js
<body>
    <div id="root"></div>
    <script>
      let myElement = React.createElement("h1", {align: "right"}, "React Example 2");
      let myRootElement = document.querySelector("#root");
      ReactDOM.render(myElement, myRootElement);
    </script>
  </body>
```

Add attributes to elements.

### Key Concept

- Props in `createElement`

### Explanation

```js
React.createElement("h1", { align: "right" }, "React Example 2");
```

The second argument is **props (attributes)**.

⚠️ Note: `align` is deprecated in HTML. Prefer CSS.

---

## ✅ Example 3 – First Component

### Purpose

```js
<body>
    <div id="root"></div>
    <script>
      function MyApp(){
        let myElement = React.createElement("h1", null, "React Example 3.");
        return myElement;
      }
      let element = React.createElement(MyApp);
      let myRootElement = document.querySelector("#root");
      ReactDOM.render(element, myRootElement);
    </script>
  </body>
```

Learn how to create a functional component.

### Key Concept

- Components
- Returning JSX-like elements

### Explanation

```js
function MyApp() {
  return React.createElement("h1", null, "React Example 3");
}
```

A component is just a function that returns React elements.

---

## ✅ Example 4 – Direct Rendering

### Purpose

```js
<body>
    <div id="root"></div>
    <script>
      function MyApp() {
        let myElement = React.createElement("h1", null, "React Example 4.");
        return myElement;
      }
      ReactDOM.render(
        React.createElement(MyApp),
        document.querySelector("#root"),
      );
    </script>
  </body>
```

Render a component directly.

### Key Concept

- Inline rendering

### Explanation

```js
ReactDOM.render(React.createElement(MyApp), document.querySelector("#root"));
```

You don’t need to store elements in variables.

---

## ✅ Example 5 – Multiple Elements

### Purpose

```js
<body>
    <div id="root"></div>
    <script>
      function MyApp() {
        let heading = React.createElement("h1", null, "React Example 5.");
        let para = React.createElement("p", null, "This is React Example no 5.");
        let div = React.createElement("div", null, heading, para)
        return div;
      }
      ReactDOM.render(
        React.createElement(MyApp),
        document.querySelector("#root"),
      )
    </script>
  </body>
```

Create multiple child elements.

### Key Concept

- Parent wrapper
- Nested elements

### Explanation

```js
let div = React.createElement("div", null, heading, para);
```

React requires one **root element**, so we wrap children in a `<div>`.

---

## ✅ Example 6 – Inline Nested Elements

### Purpose

```js
<body>
    <div id="root"></div>
    <script>
      function MyApp() {
        let heading = React.createElement("h1", null, "React Example 5.");
        let para = React.createElement(
          "p",
          null,
          "This is React Example no 6.",
        );
        let div = React.createElement(
          "div",
          null,
          React.createElement("h1", null, "React Example 6."),
          React.createElement("p", null, "This is React Example no 6."),
        );
        return div;
      }
      ReactDOM.render(
        React.createElement(MyApp),
        document.querySelector("#root"),
      );
    </script>
  </body>
```

Create nested elements directly.

### Key Concept

- Nested `createElement` calls

### Explanation

```js
React.createElement(
  "div",
  null,
  React.createElement("h1"),
  React.createElement("p"),
);
```

This is how JSX works internally.

---

## ✅ Example 7 – Mixing Text and Elements

### Purpose

```js
<body>
    <div id="root"></div>
    <script>
      function MyApp() {
        let para = React.createElement(
          "p",
          null,
          "React is a Component Based JS Library",
        );
        let div = React.createElement("div", null, "React Example no 7. What is React?", para);
        return div
      }
      ReactDOM.render(
        React.createElement(MyApp),
        document.querySelector("#root"),
      );
    </script>
  </body>
```

Combine text and elements.

### Key Concept

- Multiple children

### Explanation

```js
React.createElement("div", null, "Text", para);
```

React allows mixing strings and elements as children.

---

## ⚠️ Example 8 – Return Expression Style

### Purpose

```js
<body>
    <div id="root"></div>
    <script>
      function MyApp() {
        return (div = React.createElement(
          "div",
          null,
          "What is React?",
          React.createElement(
            "p",
            null,
          "React is React Component Based JS Library"),
        ));
      }
      ReactDOM.render(
        React.createElement(MyApp),
        document.querySelector("#root"),
      );
    </script>
  </body>
```

Return element directly.

### Key Concept

- Returning expressions

### Explanation

```js
return React.createElement("div", ...);
```

Your version:

```js
return (div = React.createElement(...));
```

⚠️ This works, but assigning to `div` is unnecessary.

Better:

```js
return React.createElement(...);
```

---

## 🧠 Important Concepts Learned

### 1️⃣ React.createElement()

Syntax:

```js
React.createElement(type, props, ...children);
```

Example:

```js
React.createElement("h1", null, "Hello");
```

---

### 2️⃣ Components

A component is:

```js
function MyComponent() {
  return React.createElement(...);
}
```

Components must:

- Start with Capital Letter
- Return React element

---

### 3️⃣ Rendering

Legacy method (used here):

```js
ReactDOM.render(element, container);
```

Modern React 18 method:

```js
const root = ReactDOM.createRoot(container);
root.render(element);
```

---

### 4️⃣ One Root Element Rule

Every component must return **one parent element**.

❌ Invalid:

```js
return (h1, p);
```

✅ Valid:

```js
return div(h1, p);
```

---

## 🚀 How This Connects to JSX

Your code:

```js
React.createElement("h1", null, "Hello");
```

JSX Version:

```jsx
<h1>Hello</h1>
```

JSX is just a shortcut for `createElement`.

---

## 📈 Recommended Next Step

Now that you understand `createElement`, move to:

✔ JSX
✔ Babel
✔ Vite / CRA / Next.js
✔ Hooks
✔ State & Props

Example (JSX):

```jsx
function App() {
  return <h1>Hello React</h1>;
}
```

---

## 📝 Summary Table

| Example | Topic             |
| ------- | ----------------- |
| 1       | Basic Element     |
| 2       | Props             |
| 3       | Component         |
| 4       | Direct Render     |
| 5       | Multiple Elements |
| 6       | Nested Elements   |
| 7       | Text + Elements   |
| 8       | Return Expression |

---

## ✅ Final Advice

These examples are excellent for learning React fundamentals.

Use them to understand:

- How React works internally
- Before learning JSX
- Before frameworks (Next.js)

---

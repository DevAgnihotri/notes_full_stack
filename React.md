

# ⭐ **(1) React Fundamentals**

---

## **1.1 What is React?**

**React is a JavaScript Library** used for building **User Interfaces (UI)** for web applications.
The word **library** is important because React does not control your full project, it only helps you build the **view layer** (what users see).
React organizes UI into small reusable blocks called **components**.

**Examples of components:** Button, Navbar, Card, Form, Sidebar.

**Important technical points:**

- React is created and maintained by **Meta (Facebook)**.
- React follows a **Component-Based Architecture**.
- React works with something called the **Virtual DOM** to update screens fast.

---

## **1.2 Why React?**

React became popular because it solves front-end problems better than plain JavaScript.

**Key technical benefits:**

1. **Reusable Components** → Write once, use many times.
2. **Virtual DOM** → Faster screen updates.
3. **Unidirectional Data Flow** → Data travels in one direction (top → down) which makes apps easier to manage.
4. **Rich Ecosystem** → Many tools and libraries for routing, state, styling, server-rendering.

**Real usage examples:**

- Facebook Web
- Instagram Web
- Netflix
- Amazon UI parts

---

## **1.3 SPA vs MPA**

### **SPA (Single Page Application)**

An SPA loads **one HTML page** and updates the screen using **JavaScript** without full page reloads.
React is mostly used to build SPAs.

**Technical features:**

- Uses **client-side routing**
- Faster navigation
- Feels like a desktop app

**Example SPAs:** Gmail, Twitter Web, Facebook Web

---

### **MPA (Multi Page Application)**

MPAs load a **new HTML page** from the server for each route.

**Technical features:**

- Uses **server-side routing**
- Full page reload for each navigation

**Example MPAs:** Government portals, old banking sites.

---

## **1.4 Library vs Framework**

### **Library**

A **library** gives tools, and **the developer decides** how to use them.
**Control = Developer**

**Examples of libraries:**

- **React** (UI Library)
- **Lodash** (Utility functions)
- **D3.js** (Data visualization)

### **Framework**

A **framework** gives a full structure and controls the flow.
**Control = Framework**

**Examples of frameworks:**

- **Angular** (Front-end framework)
- **Django** (Backend framework)
- **Spring** (Java framework)

So React = **Library**, Angular = **Framework**.

---

## **1.5 React Ecosystem**

The **React Ecosystem** means all tools that work with React to build full applications.

**Main ecosystem parts:**

1. **UI Library:** React
2. **Routing:** React Router
3. **State Management:** Redux, Zustand, Recoil, Jotai
4. **Server Frameworks:** Next.js, Remix
5. **Build Tools:** Vite, Webpack, CRA
6. **Styling:** Tailwind CSS, Styled Components, CSS Modules

This ecosystem makes React powerful and flexible for many project types.

---

## **1.6 JSX Overview (What JSX is)**

**JSX (JavaScript XML)** is a syntax that lets you write **HTML-like code** inside **JavaScript**.
Browsers cannot run JSX directly; tools like **Babel** convert JSX into normal JavaScript.

**Example JSX:**

```jsx
const element = <h1>Hello World</h1>;
```

So JSX is not HTML, but it **looks like HTML** and **behaves like JavaScript**.

---

## **1.7 Virtual DOM**

The **Virtual DOM** is a **lightweight copy** of the **Real DOM** stored in memory.

**Why it exists:**
Updating the real DOM directly is slow.
React updates the **Virtual DOM first**, compares changes, and only updates the parts that changed in the **Real DOM**.
This process is called **Reconciliation**.

**Result:** Faster rendering and smoother UI.

---

## **1.8 Rendering Flow (How React updates the screen)**

React follows this flow:

1. User action or data changes.
2. React updates **State**.
3. Virtual DOM gets updated.
4. Virtual DOM compares old vs new (diffing).
5. Only changed nodes update in Real DOM.
6. Screen updates.

This process avoids full page refresh and improves performance.

---

# ⭐ **(2) React Project Setup**

---

## **2.1 CRA vs Vite vs Next.js**

### **CRA (Create React App)**

- Old tool for React setup
- Slow development build
- Used mostly for older tutorials

### **Vite**

- Modern build tool
- Very fast dev server (uses ES modules)
- Recommended for new React projects

### **Next.js**

- Full React Framework
- Provides routing, server-side rendering, API routes
- Used for production-level apps

Summary:

- Simple & fast → **Vite**
- Full-stack features → **Next.js**

---

## **2.2 Vite + React Setup**

Commands:

```bash
npm create vite@latest my-app --template react
cd my-app
npm install
npm run dev
```

After `npm run dev`, the development server runs and shows your project in the browser.

---

## **2.3 Project Structure in Vite**

Common folders:

```
src/
  App.jsx
  main.jsx
  assets/
index.html
package.json
```

**Technical meaning:**

- **App.jsx:** Root React component
- **main.jsx:** Entry point that connects React to browser DOM
- **index.html:** Base HTML skeleton
- **assets/:** Images or static files

---

## **2.4 Entry Point**

An **entry point** is where the application starts execution.

In Vite, the entry point is **main.jsx**:

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

ReactDOM.createRoot(document.getElementById("root")).render(<App />);
```

This code mounts the **App** component inside the `<div id="root">` inside `index.html`.

---

# ⭐ **(3) JSX (Deep)**

---

## **3.1 What is JSX?**

JSX is a **syntax extension for JavaScript** that allows writing **HTML-like markup** inside JavaScript.
Jes syntax allows React to describe UI elements more easily.

The browser cannot run JSX directly, so **Babel** converts it into `React.createElement()` calls.

---

## **3.2 JSX Syntax Rules**

Some important rules:

1. Tags must be closed (`<img />`)
2. Components must return **one parent element**
3. JavaScript expressions go inside `{ }`
4. Attributes use **camelCase**

---

## **3.3 Expressions in JSX**

Expressions let you insert JavaScript values inside JSX using `{}`.

Example:

```jsx
const name = "Alice";
return <h1>Hello {name}</h1>;
```

Expressions can be:

- Variables
- Functions
- Math
- Strings
- Boolean outputs

---

## **3.4 Attributes in JSX**

Attributes look like HTML but follow JavaScript rules.

Example:

```jsx
<img src="logo.png" width="200" />
```

---

## **3.5 className**

HTML uses `class`, but JSX uses `className` because `class` is a reserved word in JavaScript.

Example:

```jsx
<div className="box"></div>
```

---

## **3.6 Fragments**

Fragments allow returning multiple elements **without adding extra `<div>`**.

Example:

```jsx
<>
  <p>Line 1</p>
  <p>Line 2</p>
</>
```

---

## **3.7 Conditional JSX**

React can show or hide UI based on conditions.

**Ternary example:**

```jsx
{
  loggedIn ? <p>Welcome</p> : <p>Login</p>;
}
```

**Logical AND example:**

```jsx
{
  isAdmin && <p>Admin Panel</p>;
}
```

---

## **3.8 Lists in JSX**

Lists are rendered using `array.map()`.

Example:

```jsx
const items = ["A", "B", "C"];
return items.map((item) => <p>{item}</p>);
```

---

## **3.9 Keys (Intro)**

Keys help React identify list items during updates.

Example:

```jsx
items.map((item, index) => <p key={index}>{item}</p>);
```

---

# ⭐ **(4) Components**

---

## **4.1 What are Components?**

In React, a **Component** is a small, independent, reusable block of UI.
React applications are built by combining many components together.
Each component returns some **JSX** that describes what should appear on the screen.

React has two main types historically:

- Class Components (older)
- **Functional Components (modern and recommended)**

Today, almost all modern React code uses **Functional Components**, so we focus on them.

---

## **4.2 Functional Components**

A **Functional Component** is a JavaScript function that returns JSX.
It can receive data through **props** and can store internal data using **state**.

Example of a functional component:

```jsx
function Hello() {
  return <h1>Hello World</h1>;
}
```

Functional components are:

- Easier to read
- Easier to test
- Work well with **React Hooks** (like `useState`)

---

## **4.3 Component Rules**

React components follow important rules:

1. **Component names must start with a capital letter**
   Example: `Header`, `Navbar`, not `header` or `navbar`.
2. **Components must return one parent element**
3. **Components must be pure functions**
   This means:

   - They should not change inputs directly.
   - They should always return the same output for the same inputs.

Example of improper component (wrong):

```jsx
function header() { ... }
```

Proper component (correct):

```jsx
function Header() { ... }
```

---

## **4.4 Reusability**

Components are designed to be **reusable**.
This means a single component can be used many times in different places.

Example:

```jsx
<Button text="Login" />
<Button text="Sign Up" />
<Button text="Logout" />
```

Here we reused the same `Button` component with different **props**.

Reusability makes:

- Code cleaner
- Code shorter
- UI consistent
- Maintenance easier

---

## **4.5 Composition**

**Composition** means building big UI by combining smaller components together.
This idea comes from **Component-Based Architecture**.

Example:

```
App
 ┣ Header
 ┣ Main
 ┗ Footer
```

`Header`, `Main`, and `Footer` are small components that together form a complete **App** component.

This approach makes large applications easier to manage and understand.

---

# ⭐ **(5) Props**

---

## **5.1 What are Props?**

**Props (Properties)** are a way to pass **data** from a **parent component** to a **child component**.
Props are **read-only**, meaning the child cannot change the prop it receives.

Example of passing a name prop:

```jsx
<Hello name="Alice" />
```

Inside the component:

```jsx
function Hello(props) {
  return <h1>Hello {props.name}</h1>;
}
```

---

## **5.2 Passing Props**

Props are passed like attributes in HTML.

Example:

```jsx
<User age={20} city="London" />
```

`age` and `city` are props passed from the parent to the `User` component.

---

## **5.3 Destructuring Props**

**Destructuring** makes props easier to use.

Without destructuring:

```jsx
function User(props) {
  return <p>{props.name}</p>;
}
```

With destructuring:

```jsx
function User({ name }) {
  return <p>{name}</p>;
}
```

Both do the same thing, but destructuring is cleaner.

---

## **5.4 Default Props**

Sometimes we want props to have a **default value** if none is provided.

Example:

```jsx
function Greeting({ name = "Guest" }) {
  return <h1>Hello {name}</h1>;
}
```

If we call:

```jsx
<Greeting />
```

It will display: `Hello Guest`

---

## **5.5 children Prop**

The `children` prop allows components to wrap other components or elements inside.

Example:

```jsx
<Card>
  <p>This is inside the card.</p>
</Card>
```

Inside `Card` component:

```jsx
function Card({ children }) {
  return <div className="card">{children}</div>;
}
```

This allows flexible layouts and reusability.

---

## **5.6 Props vs State**

| Feature    | Props              | State                |
| ---------- | ------------------ | -------------------- |
| Source     | Parent component   | Inside the component |
| Read/Write | Read-only          | Can be changed       |
| Purpose    | Send data to child | Store internal data  |
| Changes UI | No                 | Yes                  |

**Conclusion:**
Props are for **input data**, State is for **dynamic data** that can change with time.

---

# ⭐ **(6) State**

---

## **6.1 State Concept**

**State** is internal data stored inside a component.
When state changes, React **re-renders the component** to update the UI.

State is used for:

- Counters
- Form inputs
- Toggles
- Fetching and storing API data
- Showing and hiding elements

---

## **6.2 useState**

`useState` is a React **Hook** that allows functional components to use state.

Example:

```jsx
const [count, setCount] = useState(0);
```

Explanation:

- `count` = current value
- `setCount` = function to update value
- `0` = initial value of state

---

## **6.3 Updating State**

State must be updated using its **setter function**, not directly.

Correct:

```jsx
setCount(count + 1);
```

Wrong:

```jsx
count = count + 1;
```

Direct changes do not re-render UI, but setter functions do.

---

## **6.4 Functional Updates**

When new state depends on old state, we use **functional updates**.

Example:

```jsx
setCount((prevCount) => prevCount + 1);
```

This avoids bugs when updates happen quickly or multiple times.

---

## **6.5 Multiple States**

A component can hold multiple pieces of state.

Example:

```jsx
const [name, setName] = useState("");
const [age, setAge] = useState(0);
const [isOnline, setIsOnline] = useState(false);
```

React handles them independently.

---

## **6.6 Lifting State Up**

Sometimes two child components need to share the same data.
In that case, we move the state to the **closest common parent**.
This is called **Lifting State Up**.

Example structure:

```
Parent
 ┣ ChildA
 ┗ ChildB
```

The parent stores the shared state and passes it to both children through props.

---

## **6.7 Derived State**

**Derived state** means values that can be **computed** from existing state instead of storing them as separate states.

Example:
If we have a `firstName` and `lastName`, the `fullName` can be derived:

```jsx
const fullName = firstName + " " + lastName;
```

We do **not** store `fullName` as another state because it can be calculated.

---

# ⭐ **(7) Event Handling**

---

## **7.1 What is Event Handling in React?**

**Event handling** means responding to user actions such as clicking a button, typing in input, submitting a form, etc.
React uses **camelCase event names** and **functions** as event handlers.

Example:

```jsx
<button onClick={handleClick}>Click</button>
```

React events work similar to DOM events but follow React’s own synthetic event system for performance and cross-browser compatibility.

---

## **7.2 onClick**

`onClick` is used to capture click events from elements like buttons, divs, etc.

Example:

```jsx
function App() {
  function handleClick() {
    alert("Button clicked!");
  }
  return <button onClick={handleClick}>Click Me</button>;
}
```

Here, when the button is clicked, `handleClick()` runs.

---

## **7.3 onChange**

`onChange` is mostly used for input fields.
It runs when the value in the input changes.

Example:

```jsx
function App() {
  function handleChange(event) {
    console.log(event.target.value);
  }
  return <input onChange={handleChange} />;
}
```

This is useful for form inputs, search bars, etc.

---

## **7.4 onSubmit**

`onSubmit` is used on forms to handle submission.

Example:

```jsx
function App() {
  function handleSubmit(event) {
    event.preventDefault(); // stops page refresh
    alert("Form submitted!");
  }
  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```

React uses `event.preventDefault()` to stop the default browser behavior of refreshing the page.

---

## **7.5 Event Object**

React passes an **event object** to event handlers.
This object contains event info such as:

- what element triggered it
- value entered
- mouse position
- key pressed, etc.

Example:

```jsx
function handleChange(event) {
  console.log(event.target.value);
}
```

`event.target` refers to the element that triggered the event.

---

## **7.6 Passing Arguments in Event Handlers**

If you need to pass data to the event handler, you wrap it in an arrow function.

Example:

```jsx
function App() {
  function greet(name) {
    alert("Hello " + name);
  }

  return <button onClick={() => greet("Alice")}>Greet</button>;
}
```

If you write `onClick={greet("Alice")}`, it would execute immediately, so we use an arrow function to delay execution until click.

---

# ⭐ **(8) Conditional Rendering**

---

## **8.1 What is Conditional Rendering?**

Conditional rendering means showing UI elements **only if certain conditions are true**.
React uses JavaScript logic to decide what to display.

---

## **8.2 if-else Statement**

Used for longer multi-line conditions.

Example:

```jsx
if (isLoggedIn) {
  return <h1>Welcome</h1>;
}
else {
  return <h1>Please Login</h1>;
}
```

---

## **8.3 Ternary Operator**

Useful for short conditions inside JSX.

Syntax:

```jsx
condition ? truePart : falsePart;
```

Example:

```jsx
<p>{age >= 18 ? "Adult" : "Minor"}</p>
```

---

## **8.4 Logical AND (&&)**

Used when we **only** want to show something for the true case and nothing for the false case.

Syntax:

```jsx
condition && partToShow;
```

Example:

```jsx
{
  isAdmin && <button>Admin Panel</button>;
}
```

If `isAdmin` is `true`, the button shows. If false, nothing shows.

---

## **8.5 Early Return**

Used inside components to exit early if a condition fails.

Example:

```jsx
function Dashboard({ user }) {
  if (!user) {
    return <p>Loading...</p>;
  }
  return <p>Welcome {user.name}</p>;
}
```

This makes components cleaner and avoids nested conditions.

---

# ⭐ **(9) Lists & Keys**

---

## **9.1 What are Lists in React?**

Lists are multiple UI elements created from arrays.
React uses the JavaScript `map()` method for rendering lists.

Example:

```jsx
const items = ["A", "B", "C"];

return items.map((item) => <p>{item}</p>);
```

---

## **9.2 map Rendering**

React does **not** loop like a template engine. It uses `array.map()` to convert data into JSX elements.

Example with JSX:

```jsx
const users = ["Alice", "Bob", "Charlie"];

return (
  <ul>
    {users.map((user) => (
      <li>{user}</li>
    ))}
  </ul>
);
```

---

## **9.3 Keys Importance**

**Keys** help React identify which items changed, were added, or removed.
This makes list updates efficient during the Virtual DOM diffing process.

Example:

```jsx
{
  users.map((user) => <li key={user.id}>{user.name}</li>);
}
```

Without keys, React cannot match elements properly, which can cause incorrect UI updates or warnings.

---

## **9.4 Index as Key**

If the data has **no unique ID**, developers sometimes use the array index:

```jsx
items.map((item, index) => <li key={index}>{item}</li>);
```

But using index as a key is **not recommended** when:

- Items can be reordered
- Items can be deleted
- Items can be inserted in between

Because it can cause incorrect state mapping.

Use index only when:

- List is static
- List will never reorder
- No unique IDs exist

---

## **9.5 Nested Lists**

Lists can be nested inside other lists.

Example:

```jsx
const data = [
  { name: "Group A", items: ["x", "y"] },
  { name: "Group B", items: ["p", "q"] },
];

return (
  <>
    {data.map((group) => (
      <div key={group.name}>
        <h3>{group.name}</h3>
        <ul>
          {group.items.map((item) => (
            <li key={item}>{item}</li>
          ))}
        </ul>
      </div>
    ))}
  </>
);
```

Nested lists are useful for rendering grouped data, categories, menus, comments with replies, etc.

---

# **10. Forms**

### **What are Forms in React?**

Forms are UI elements that allow users to **enter data** (like text, email, password, selections). React controls forms using **state**, so UI and data stay in sync.

---

## **1) Controlled Inputs**

**Meaning:**
A controlled input is an input element whose **value is controlled by React state**.

**Why?**
So React always knows the **current value**, can **validate**, and can **update UI** correctly.

**Example:**

```jsx
function Form() {
  const [name, setName] = useState("");

  return (
    <input
      value={name}
      onChange={(e) => setName(e.target.value)}
    />
  );
}
```

Here:

* `value={name}` → React controls the input
* `onChange` → updates state

---

## **2) Multiple Inputs**

Often forms need **many fields** (name, email, age). We can store them in **one state object**.

**Example:**

```jsx
const [form, setForm] = useState({ name: "", email: "" });

<input
  name="name"
  value={form.name}
  onChange={(e) => setForm({...form, [e.target.name]: e.target.value})}
/>

<input
  name="email"
  value={form.email}
  onChange={(e) => setForm({...form, [e.target.name]: e.target.value})}
/>
```

---

## **3) Checkbox & Radio**

### **Checkbox**

Stores **true/false** values.

```jsx
<input
  type="checkbox"
  checked={agree}
  onChange={(e) => setAgree(e.target.checked)}
/>
```

→ `checked` is used instead of `value`.

### **Radio**

Used for **single choice among multiple options**.

```jsx
<input
  type="radio"
  value="male"
  checked={gender === "male"}
  onChange={(e) => setGender(e.target.value)}
/>
```

---

## **4) Select Dropdown**

Allows choosing a value from a **list**.

```jsx
<select value={city} onChange={(e) => setCity(e.target.value)}>
  <option value="delhi">Delhi</option>
  <option value="mumbai">Mumbai</option>
</select>
```

---

## **5) Validation**

Validation means **checking user input** (example: email must be valid).

Types:

✔ **Required field check**
✔ **Format check** (email, phone)
✔ **Length check** (password min length)

**Example:**

```jsx
if (!email.includes("@")) {
  setError("Invalid email");
}
```

---

## **6) Submission Flow**

Form submission involves:

1. User fills data
2. On submit, `event.preventDefault()` stops page refresh
3. Validate data
4. Send data to backend / show result

**Example:**

```jsx
function handleSubmit(e) {
  e.preventDefault();
  console.log(form);
}
<form onSubmit={handleSubmit}>...</form>
```

---

# **11. Hooks**

### **What are Hooks?**

Hooks are **special functions** in React that let functional components use:

* **State**
* **Lifecycle**
* **Context**
* **Performance features**

Example hook: `useState()`

---

## **A) Basic Hooks**

---

### **1) Rules of Hooks**

Hooks follow **strict rules**:

✔ Only call **at top level**, not inside loops, conditions, or functions.
✔ Only call **inside React components or custom hooks**.

Wrong:

```jsx
if (show) {
  const [x, setX] = useState(); // ❌ not allowed
}
```

---

### **2) useState**

Used to **store and update state** in functional components.

Syntax:

```jsx
const [count, setCount] = useState(0);
```

---

### **3) useEffect**

useEffect lets you **run side effects** like:

* API calls
* Event listeners
* Timers
* Updating document title

Example:

```jsx
useEffect(() => {
  console.log("Component rendered");
});
```

Runs after **every render** by default.

---

## **B) useEffect Deep**

---

### **1) Dependency Array**

Controls **when** the effect runs.

Types:

| Dependency | Behavior                  |
| ---------- | ------------------------- |
| `[]`       | Runs only once (on mount) |
| `[value]`  | Runs when `value` changes |
| none       | Runs on every render      |

Example:

```jsx
useEffect(() => {
  console.log("Runs only once");
}, []);
```

---

### **2) Cleanup**

Used for removing old listeners, intervals, or subscriptions.

Example:

```jsx
useEffect(() => {
  const id = setInterval(() => {}, 1000);
  return () => clearInterval(id);
}, []);
```

---

### **3) Multiple Effects**

You can write **many useEffects** for different logic.

```jsx
useEffect(() => {...}, []);
useEffect(() => {...}, [count]);
```

---

### **4) Infinite Loops**

Happens when:

* You update state **inside** useEffect **without dependency** handling

Example bad:

```jsx
useEffect(() => {
  setCount(count + 1);
});
```

→ runs forever

---

## **C) Intermediate Hooks**

---

### **1) useContext**

Lets you **share data** without passing props manually.

Example use case:

* Theme
* Language
* Auth user

---

### **Context API workflow**

Steps:

1. Create Context
2. Provide Context
3. Consume Context

Example:

```jsx
const ThemeContext = createContext();
```

Provider:

```jsx
<ThemeContext.Provider value="dark">...</ThemeContext.Provider>
```

Consumer:

```jsx
const theme = useContext(ThemeContext);
```

---

## **D) Performance Hooks**

Used to **optimize performance** when components re-render too much.

---

### **1) useMemo**

Caches **calculated values** so they don’t recalc every render.

Example:

```jsx
const result = useMemo(() => heavyCalc(num), [num]);
```

---

### **2) useCallback**

Caches **functions** so children don’t re-render.

```jsx
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);
```

---

### **3) React.memo**

Prevents component from re-rendering if **props don't change**.

```jsx
export default React.memo(Button);
```

---

## **E) Advanced Hooks**

---

### **1) useRef**

Stores **mutable values**, also used to **access DOM elements**.

Example:

```jsx
const inputRef = useRef();
<input ref={inputRef} />
```

---

### **2) useReducer**

Alternative to `useState` for **complex state logic**.

Uses:

* state object
* actions
* reducer function

---

### **3) useLayoutEffect**

Same as useEffect but runs **before screen paint**, used for **layout measurements**.

---

### **4) useImperativeHandle**

Used with `forwardRef` to **control what is exposed to parent ref**.

---

### **5) useDebugValue**

Used inside **custom hooks** for debugging values.

---

## **F) Custom Hooks**

### **What are Custom Hooks?**

A custom hook is a **function that uses other hooks** and contains **reusable logic**.

Example naming rule:
✔ Must start with `"use"` (like `useFetch()`)

### **Benefits:**

* Reusability
* Cleaner components
* Shared logic

Example:

```jsx
function useCounter(){
  const [count, setCount] = useState(0);
  return { count, setCount };
}
```

---

# **12. Lifecycle (Conceptual)**

### **What is Component Lifecycle?**

Component Lifecycle means the **phases a React component goes through** while it exists in the UI.

React components have **3 main lifecycle stages**:

---

## **1) Mounting**

### **Meaning:**

Mounting is when a component is **created and added to the UI for the first time**.

### **What happens here?**

* State & props are set
* UI gets rendered for the first time

### **Functional Component equivalent:**

You simulate mounting using:

```jsx
useEffect(() => {
  console.log("Mounted");
}, []);
```

`[]` ensures it runs **only once**, like mounting.

---

## **2) Updating**

### **Meaning:**

Updating is when a component **re-renders** because:

* state changes
* props change
* parent re-renders

### **What happens here?**

* UI updates with new data
* Some logic re-runs

### **Functional component equivalent:**

```jsx
useEffect(() => {
  console.log("Updated");
}, [value]);
```

Runs whenever `value` changes.

---

## **3) Unmounting**

### **Meaning:**

Unmounting is when a component is **removed from the UI**.

Example:

* User navigates to another page
* List item removed
* Popup closed

### **Cleanup before unmount**

Used to:
✔ remove event listeners
✔ clear timers
✔ stop API subscriptions

### **useEffect cleanup example:**

```jsx
useEffect(() => {
  const id = setInterval(() => {}, 1000);

  return () => clearInterval(id);
}, []);
```

`return()` part runs during **unmount**.

---

# **13. Styling**

### **What is Styling in React?**

Styling means applying **visual design** to UI elements like color, size, layout, fonts, etc.

React supports **multiple styling methods**.

---

## **1) CSS Files**

Traditional styling method using **.css files**.

Example `App.css`:

```css
.title {
  color: blue;
}
```

Use it in component:

```jsx
import "./App.css";
<h1 className="title">Hello</h1>
```

✔ Simple
❌ Classes may conflict if names are same

---

## **2) Inline Styles**

Styles written directly inside JSX using **objects**.

Example:

```jsx
<h1 style={{ color: "red", fontSize: "20px" }}>
  Hello
</h1>
```

Key rules:

* Use **camelCase** (ex: `fontSize`)
* Values are usually **strings**

✔ Good for dynamic styles
❌ No pseudo classes (`:hover`) or media queries

---

## **3) CSS Modules**

CSS Modules allow **scoped CSS**, meaning class names are **component-only**.

File: `Button.module.css`

```css
.btn {
  color: green;
}
```

Use:

```jsx
import styles from "./Button.module.css";

<button className={styles.btn}>Click</button>
```

✔ No class name conflicts
✔ Cleaner styling for components

---

## **4) Styled-components**

Styled-components use **CSS-in-JS** + **tagged template literals**.

Install:

```
npm install styled-components
```

Example:

```jsx
import styled from "styled-components";

const Btn = styled.button`
  background: blue;
  color: white;
`;

<Btn>Click</Btn>
```

✔ Supports theming
✔ Dynamic styles
❌ Extra library needed

---

## **5) Tailwind CSS**

Tailwind is a **utility-first CSS framework**.

You apply classes directly in JSX.

Example:

```jsx
<h1 className="text-2xl font-bold text-red-500">Hello</h1>
```

✔ Fast development
✔ Responsive utilities
❌ Classes can look long (visual noise)

---

# **14. Assets**

### **What are Assets?**

Assets are **non-code files** used by the UI such as:

* images
* icons
* fonts
* animations
* audio/video

React stores assets differently based on usage.

---

## **1) Images**

There are **two ways** to use images:

### **A) Imported from `src`**

Good for component-level usage.

Example:

```jsx
import pic from "./logo.png";

<img src={pic} />
```

✔ Tree-shaking support
✔ Bundled with code

---

### **B) From `public` folder**

Access directly with a URL.

Example:

```jsx
<img src="/logo.png" />
```

✔ Good for static images
✔ Direct browser access
❌ Not optimized by bundler

---

## **2) SVGs**

SVGs can be used **as images** or **as React components**.

### **A) As image**

```jsx
<img src="/icon.svg" />
```

### **B) As React component**

```jsx
import {ReactComponent as Icon} from "./icon.svg";

<Icon width={20} />
```

✔ Vector graphics = no quality loss
✔ Color + styling via CSS

---

## **3) Fonts**

Fonts are usually placed in `public` or `src/assets/fonts`.

Example via CSS:

```css
@font-face {
  font-family: "Roboto";
  src: url("/fonts/Roboto.ttf");
}
```

Use:

```css
body {
  font-family: "Roboto";
}
```

---

## **4) Public vs Src**

### **Public Folder**

* Files are not processed by bundler
* Access with direct paths (`/file.png`)
* Good for:
  ✔ favicon
  ✔ static images
  ✔ robots.txt
  ✔ fonts

### **Src Folder**

* Bundled and optimized
* Imported in JavaScript
* Good for:
  ✔ component-specific images
  ✔ svg components
  ✔ modules

**Quick Difference Table:**

| Feature           | public/ | src/  |
| ----------------- | ------- | ----- |
| Bundled?          | ❌ No    | ✔ Yes |
| Direct URL access | ✔ Yes   | ❌ No  |
| Tree-shaking      | ❌       | ✔     |
| Use in import     | ❌       | ✔     |

---

# **15. Routing (React Router)**

### **What is Routing?**

Routing means changing **pages/views** inside a web app without reloading the whole browser page.

React apps are **SPA (Single Page Applications)** — they load **one HTML page** and update UI **dynamically**.

---

## **1) SPA Routing**

### **Meaning:**

SPA routing changes content using **JavaScript**, not full page reload.

✔ Faster
✔ Saves network
✔ Better user experience

Examples:

* `/` → Home
* `/about` → About
* `/profile/123` → Profile with ID

---

## **2) react-router-dom**

This is the **official routing library** for React in the browser.

Install:

```bash
npm install react-router-dom
```

---

## **3) Routes & Route**

These define which component should show on which path.

**Setup Example:**

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";

<BrowserRouter>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
  </Routes>
</BrowserRouter>
```

Key items:

* `BrowserRouter` → enables routing
* `Routes` → wraps all routes
* `Route` → path + component mapping

---

## **4) Link & NavLink**

### **Link**

Used to change routes **without page reload**.

```jsx
<Link to="/about">About</Link>
```

### **NavLink**

Same as Link but adds **active styling** when route is selected.

```jsx
<NavLink to="/home" className={({isActive}) => isActive ? "active" : ""}>
  Home
</NavLink>
```

---

## **5) useParams**

Used to get **dynamic URL values** (route variables).

Example route:

```jsx
<Route path="/user/:id" element={<User />} />
```

Access in component:

```jsx
const { id } = useParams();
```

If user goes to `/user/50` → `id = "50"`

---

## **6) useNavigate**

Used for **programmatic navigation** (navigate using code).

Example:

```jsx
const navigate = useNavigate();
navigate("/login");
```

Useful after **submit**, **login**, or **action**.

---

## **7) Nested Routes**

Used for pages with **layout sections**, for example:

* Dashboard with sidebar
* User profile tabs

Example:

```jsx
<Route path="/dashboard" element={<Dashboard />}>
  <Route path="profile" element={<Profile />} />
  <Route path="settings" element={<Settings />} />
</Route>
```

URL examples:

* `/dashboard/profile`
* `/dashboard/settings`

---

## **8) Protected Routes**

Used to **block pages** unless user is **logged in**.

Basic example:

```jsx
function Protected({children}) {
  const loggedIn = false;
  return loggedIn ? children : <Navigate to="/login" />;
}
```

Usage:

```jsx
<Route path="/admin" element={<Protected><Admin /></Protected>} />
```

If not logged in → redirect to `/login`.

---

# **16. Data Fetching**

### **What is Data Fetching?**

Data fetching means getting data from a **backend server or API**.

Example APIs:

* REST API
* GraphQL API

Common formats: **JSON**

---

## **1) fetch**

Built-in JS function for requests.

Example:

```jsx
fetch("https://api.example.com/users")
  .then(res => res.json())
  .then(data => console.log(data));
```

---

## **2) axios**

Third-party library for easier HTTP requests.

Install:

```
npm install axios
```

Example:

```jsx
const res = await axios.get("/users");
console.log(res.data);
```

✔ auto JSON parsing
✔ better error handling

---

## **3) Loading State**

We show loading while waiting for data.

Example with React:

```jsx
const [loading, setLoading] = useState(true);
const [data, setData] = useState([]);

useEffect(() => {
  fetchAPI();
}, []);

async function fetchAPI() {
  const res = await fetch(url);
  const json = await res.json();
  setData(json);
  setLoading(false);
}
```

UI:

```jsx
return loading ? <p>Loading...</p> : <DataList data={data} />;
```

---

## **4) Error Handling**

Network errors must be handled.

Example:

```jsx
try {
  const res = await fetch(url);
  if (!res.ok) throw new Error("Server error");
} catch (err) {
  setError(err.message);
}
```

UI:

```jsx
{error && <p>Error: {error}</p>}
```

---

## **5) Pagination**

Fetching data in **pages** instead of all at once.

Example API:
`/users?page=1&limit=10`

Benefits:
✔ Faster load
✔ Saves bandwidth

---

## **6) Infinite Scroll**

Load more data when user reaches **bottom of the page** (like Instagram feed).

Steps:

1. Detect scroll
2. Fetch more data
3. Append to existing list

Libraries exist like `react-infinite-scroll-component`.

---

## **7) Debouncing**

Debouncing delays processing **until user stops typing**.

Use case:
✔ Search boxes
✔ Auto-suggestions

Example idea:

* Wait 500ms after typing before calling API

Prevents **too many API requests**.

---

# **17. State Management (Advanced)**

### **What is State Management?**

State Management means controlling and sharing **application data** across components.

When app grows → state becomes complex → need advanced tools.

---

## **1) Context API Deep**

Context is used to **share state globally** without passing props down manually.

### **When to use Context:**

* Theme (dark/light)
* Auth user
* Language
* Cart data

### **Flow:**

1. Create Context
2. Provide value
3. Consume value

Example:

```jsx
const AuthContext = createContext();

<AuthContext.Provider value={user}>
  <App />
</AuthContext.Provider>
```

Consume:

```jsx
const user = useContext(AuthContext);
```

---

## **2) Redux Concepts**

Redux is a **state container** for predictable state changes.

### **Core Concepts:**

✔ **Store** → holds global state
✔ **Actions** → describe events
✔ **Reducers** → update state based on actions
✔ **Dispatch** → send actions
✔ **Selectors** → read state

Example Action:

```js
{ type: "ADD_TODO", payload: "Learn Redux" }
```

Reducer:

```js
function todoReducer(state, action) {
  if (action.type === "ADD_TODO") {
    return [...state, action.payload];
  }
}
```

---

## **3) Redux Toolkit**

Redux Toolkit (RTK) makes Redux **simpler**.

Install:

```
npm install @reduxjs/toolkit react-redux
```

Benefits:
✔ less boilerplate
✔ built-in async support
✔ createSlice concept

Example:

```js
const todoSlice = createSlice({
  name: "todo",
  initialState: [],
  reducers: {
    addTodo: (state, action) => { state.push(action.payload); }
  }
});
```

---

## **4) Async Thunk**

Used for **async tasks** like API calls.

Example:

```js
export const fetchUsers = createAsyncThunk(
  "users/fetch",
  async () => {
    const res = await fetch("/users");
    return res.json();
  }
);
```

Thunk handles:
✔ loading
✔ success
✔ error states

---

## **5) Zustand Intro**

Zustand is a small **state-management library** for React.

Benefits:
✔ simple
✔ minimal code
✔ good performance

Example:

```js
import create from "zustand";

const useStore = create((set) => ({
  count: 0,
  inc: () => set((state) => ({ count: state.count + 1 }))
}));
```

Use in component:

```jsx
const { count, inc } = useStore();
```

---

# **18. Performance**

### **What is Performance Optimization?**

Performance means how **fast, smooth, and efficient** a React app feels.
Goal: **avoid unnecessary work** and **render only what is needed**.

---

## **1) Re-rendering**

### **Meaning:**

Re-render happens when a component **updates its UI** because:
✔ state changes
✔ props change
✔ parent re-renders

Too many re-renders = **slow UI**

Typical problems:

* Large lists re-rendering
* Re-rendering children unnecessarily
* Creating new functions every render

Example re-render cause:

```jsx
const [count, setCount] = useState(0);
```

Calling `setCount()` → triggers re-render.

---

## **2) Memoization**

### **Meaning:**

Memoization = **saving** expensive values/functions so they don’t re-calculate or re-create every time.

In React, three tools:

### **A) React.memo**

Stops child re-renders if props don't change.

```jsx
export default React.memo(Button);
```

### **B) useMemo**

Caches computed values.

```jsx
const total = useMemo(() => heavyCalc(data), [data]);
```

### **C) useCallback**

Caches functions.

```jsx
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);
```

**When to use memoization?**
✔ heavy calculations
✔ child components
✔ stable function references needed

---

## **3) Lazy Loading**

### **Meaning:**

Lazy loading delays loading a component until it's needed.

Why?
✔ smaller initial bundle
✔ faster initial load

Example:

```jsx
const Profile = React.lazy(() => import('./Profile'));
```

Component loaded only when rendered.

---

## **4) Code Splitting**

### **Meaning:**

Code splitting breaks app bundle into **smaller chunks** instead of one big file.

Tools:
✔ React.lazy
✔ dynamic import
✔ bundlers (Vite, Webpack)

Example:

```jsx
import("./Chart").then(...)
```

Benefits:
✔ faster initial load
✔ better performance

---

## **5) Suspense**

### **Meaning:**

Suspense shows a **loading state** while waiting for lazy-loaded components.

Example:

```jsx
<Suspense fallback={<p>Loading...</p>}>
  <Profile />
</Suspense>
```

Suspense works well with:

* Lazy loading components
* Server-side data fetching (in React 18)

---

# **19. Error Handling**

### **What is Error Handling?**

Error handling prevents app crashes and shows **friendly UI** instead of breaking.

React has different error types:
✔ Runtime errors
✔ Rendering errors
✔ Logical errors
✔ Async errors (API calls)

---

## **1) Error Boundaries**

### **Meaning:**

Error Boundaries catch **render-time errors** in child components.

Only class-based right now.

Example:

```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  render() {
    return this.state.hasError ? <h1>Error!</h1> : this.props.children;
  }
}
```

Usage:

```jsx
<ErrorBoundary>
  <Dashboard />
</ErrorBoundary>
```

**Note:**
CANNOT catch async errors or event handler errors.

---

## **2) Async try-catch**

Used for errors in:
✔ fetch
✔ axios
✔ async functions

Example:

```jsx
try {
  const res = await fetch(url);
  if (!res.ok) throw new Error("Failed");
} catch (err) {
  console.error(err.message);
}
```

---

## **3) Fallback UI**

Showing a **safe UI** instead of crash.

Example:

```jsx
{error ? <p>Something went wrong</p> : <UserList />}
```

Fallback UI is used in:
✔ error boundaries
✔ API failures
✔ Suspense fallbacks

---

# **20. Testing (Intro)**

### **What is Testing?**

Testing checks if code **works correctly** and avoids bugs.

Types of tests:
✔ Unit tests
✔ Integration tests
✔ E2E tests

---

## **1) Unit Testing**

### **Meaning:**

Unit testing tests **small pieces** of code like:

* functions
* components
* reducers

Goal: ensure individual units behave correctly.

Example logic test:

```jsx
expect(sum(2, 3)).toBe(5);
```

---

## **2) Jest**

### **What is Jest?**

Jest is a **JavaScript testing framework** used for:
✔ unit tests
✔ mocks
✔ timers

Features:

* snapshot testing
* built-in assertion functions
* works with React + JS

Example Jest test:

```jsx
test("adds numbers", () => {
  expect(2 + 3).toBe(5);
});
```

---

## **3) React Testing Library**

### **Meaning:**

React Testing Library (RTL) tests React components by:
✔ rendering UI
✔ interacting like a real user
✔ checking DOM output

Goal: **test behavior, not implementation.**

Example:

```jsx
render(<Button text="Click" />);
expect(screen.getByText("Click")).toBeInTheDocument();
```

RTL uses:

* `render`
* `screen`
* `fireEvent` or `userEvent`

---

# **21. Build & Production**

### **What is Build?**

Build means converting development code into **optimized production-ready code**.

During build:
✔ JSX → JS
✔ CSS optimized
✔ code minified
✔ dead code removed
✔ chunks created

---

## **1) Build Process**

Commands:

* CRA / Vite: `npm run build`
* Next.js: `next build`

Build output includes:
✔ JS bundles
✔ CSS files
✔ assets
✔ HTML templates

---

## **2) Env Variables**

### **Meaning:**

Environment variables store **config values** that change between environments:

* development
* testing
* production

Example:

```
REACT_APP_API_URL=https://api.example.com
```

Usage:

```jsx
fetch(process.env.REACT_APP_API_URL + "/users");
```

Benefits:
✔ hide secrets
✔ different servers per environment

---

## **3) Production Optimizations**

Optimizations include:

✔ **Minification** → remove spaces & shorten code
✔ **Tree Shaking** → remove unused code
✔ **Gzip/Brotli** → compress files
✔ **Caching** → store assets in browser
✔ **CDN hosting** → faster global delivery
✔ **Image optimization** (webp, lazy image loading)
✔ **Preloading** important assets

Framework tools:

* Vite
* Webpack
* Next.js
* Parcel

**Result:**
App loads faster + better performance in real devices.

---
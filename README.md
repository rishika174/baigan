
# ✅ **SET C – ANSWERS**
--------------------------------------------------------------------------------------------------------------------------------------------
Question 1
(a) Create a React application that allows a user to enter personal and academic details such as name, age, city, country, email ID, course,
and college name using the useState hook.Provide input fields for each detail, update the state dynamically as the user types, and display
the entered information in real time below the inputs.
Initialize each field with default values (e.g., Name: “Ahmed Saraf”, Age: 25, City: “Delhi”, Country: “India”, Email: “abc123@gmail.com
”, Course: “B.Tech”, College: “ABC”).

(b) Input fields should update the context/state dynamically using the onChange event.

(c) The entered details must be displayed in real time below the input fields in descriptive sentence format.

## **1. useState Form with Real-time Display**
--------------------------------------------------------------------------------------------------------------------------------------------
import React, { useState } from "react";

function UserDetails() {
  const [details, setDetails] = useState({
    name: "Ahmed Saraf",
    age: 25,
    city: "Delhi",
    country: "India",
    email: "abc123@gmail.com",
    course: "B.Tech",
    college: "ABC"
  });

  const handleChange = (e) => {
    setDetails({ ...details, [e.target.name]: e.target.value });
  };

  return (
    <div>
      <input name="name" value={details.name} onChange={handleChange} />
      <input name="age" value={details.age} onChange={handleChange} />
      <input name="city" value={details.city} onChange={handleChange} />
      <input name="country" value={details.country} onChange={handleChange} />
      <input name="email" value={details.email} onChange={handleChange} />
      <input name="course" value={details.course} onChange={handleChange} />
      <input name="college" value={details.college} onChange={handleChange} />

      <p>
        My name is {details.name}, I am {details.age} years old from{" "}
        {details.city}, {details.country}. I am pursuing {details.course} at{" "}
        {details.college}. My email ID is {details.email}.
      </p>
    </div>
  );
}

export default UserDetails;

---------------------------------------------------------------------------------------------------------------
Question 2

(a) Create a React functional component to demonstrate the use of the useMemo hook for performance optimization.
The component should include:
a number state initialized to 101,
a text state initialized to an empty string, and
a todo array state to store a list of tasks.
(b) Implement an expensive computation function based on the number value and memoize it using useMemo so that
it recomputes only when the number changes.

(c) Render the current number, the computed value, a button to increment the number, an input field to add todos,
display the todo list, and show the typed text below the text input.

## **2. useMemo Performance Optimization**
---------------------------------------------------------------------------------------------------------------

import React, { useState, useMemo } from "react";

function UseMemoDemo() {
  const [number, setNumber] = useState(101);
  const [text, setText] = useState("");
  const [todos, setTodos] = useState([]);

  const expensiveCalculation = (num) => {
    console.log("Calculating...");
    return num * 2;
  };

  const computedValue = useMemo(() => expensiveCalculation(number), [number]);

  return (
    <div>
      <h3>Number: {number}</h3>
      <h3>Computed Value: {computedValue}</h3>
      <button onClick={() => setNumber(number + 1)}>Increment</button>

      <input
        type="text"
        value={text}
        onChange={(e) => setText(e.target.value)}
        placeholder="Enter todo"
      />
      <button onClick={() => setTodos([...todos, text])}>Add Todo</button>

      <p>Typed Text: {text}</p>

      <ul>
        {todos.map((todo, index) => (
          <li key={index}>{todo}</li>
        ))}
      </ul>
    </div>
  );
}

export default UseMemoDemo;

----------------------------------------------------------------------------------------------------------------------------------
Question 3

(a) Develop a React Native application that demonstrates efficient rendering of a dynamic list of academic subjects using the
FlatList component.

(b) The program should initialize an array of subject objects containing unique IDs and subject names, manage the data using state,
and render each subject with a custom-styled list item component.

## **3. React Native FlatList**
----------------------------------------------------------------------------------------------------------------------------------
npx create-expo-app SubjectApp
cd SubjectApp

import React, { useState } from "react";
import { View, Text, FlatList, StyleSheet } from "react-native";

export default function SubjectList() {
  const [subjects] = useState([
    { id: "1", name: "Maths" },
    { id: "2", name: "Physics" },
    { id: "3", name: "Computer Science" }
  ]);

  return (
    <FlatList
      data={subjects}
      keyExtractor={(item) => item.id}
      renderItem={({ item }) => (
        <View style={styles.item}>
          <Text>{item.name}</Text>
        </View>
      )}
    />
  );
}

const styles = StyleSheet.create({
  item: {
    padding: 15,
    backgroundColor: "#ddd",
    margin: 5
  }
});


------------------------------------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------------------------------------------------------------------------
# ✅ **SET D – ANSWERS**

1>Question 1
(a) Create a ShoppingList.tsx component that manages a simple grocery shopping list with three initial items: “Milk”, “Bread”, and “Eggs”.

(b) Use the useState hook to store an array of shopping items, where each item includes properties such as id and itemName, and display
each item with a Remove button. Implement the remove functionality using the filter() method to delete an item from the list when clicked.

(c) Add an input field with an “Add Item” button to allow users to insert new grocery items.

------------------------------------------------------------------------------------------------------------------------------------------

npx create-expo-app SubjectApp
cd SubjectApp
npx expo start


## **1. ShoppingList.tsx**

import React, { useState } from "react";

const ShoppingList = () => {
  const [items, setItems] = useState([
    { id: 1, itemName: "Milk" },
    { id: 2, itemName: "Bread" },
    { id: 3, itemName: "Eggs" }
  ]);

  const [newItem, setNewItem] = useState("");

  const removeItem = (id: number) => {
    setItems(items.filter(item => item.id !== id));
  };

  const addItem = () => {
    setItems([...items, { id: Date.now(), itemName: newItem }]);
    setNewItem("");
  };

  return (
    <div>
      <input value={newItem} onChange={(e) => setNewItem(e.target.value)} />
      <button onClick={addItem}>Add Item</button>

      <ul>
        {items.map(item => (
          <li key={item.id}>
            {item.itemName}
            <button onClick={() => removeItem(item.id)}>Remove</button>
          </li>
        ))}
      </ul>
    </div>
  );
};

export default ShoppingList;

------------------------------------------------------------------------------------------------------------------------------------
Question 2

(a) Design a React application that mounts to a root DOM node and showcases JSX rendering
of multiple HTML elements with Synthetic Event handling.

(b) The program should manage user interactions such as input changes and button clicks
while displaying structured content including an unordered list and a dropdown.

## **2. JSX & Synthetic Events**
-----------------------------------------------------------------------------------------------------------------------------------

import React, { useState } from "react";
import ReactDOM from "react-dom/client";

function App() {
  const [text, setText] = useState("");

  return (
    <div>
      <input onChange={(e) => setText(e.target.value)} />
      <button onClick={() => alert("Button Clicked")}>Click</button>

      <p>{text}</p>

      <ul>
        <li>Apple</li>
        <li>Banana</li>
      </ul>

      <select>
        <option>India</option>
        <option>USA</option>
      </select>
    </div>
  );
}

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);

-----------------------------------------------------------------------------------------------------------------------------
Question 3

(a) Create a LanguageContext.tsx using TypeScript to manage global language settings (“English” and “Spanish”) with useState.

(b) Implement a toggleLanguage function to switch languages and provide the state via a LanguageProvider.

(c) Create a LanguageButton.tsx component that consumes the context using useContext and updates its text or style based on
the current language. Render multiple buttons to demonstrate the shared global state across the app.

## **3. Language Context (TypeScript)**
-----------------------------------------------------------------------------------------------------------------------------

npx create-react-app myapp --template typescript
cd myapp
npm start

### **LanguageContext.tsx**
-----------------------------------------------------------------------------------------------------------------------------

import React, { createContext, useState } from "react";

export const LanguageContext = createContext<any>(null);

export const LanguageProvider = ({ children }: any) => {
  const [language, setLanguage] = useState("English");

  const toggleLanguage = () => {
    setLanguage(language === "English" ? "Spanish" : "English");
  };

  return (
    <LanguageContext.Provider value={{ language, toggleLanguage }}>
      {children}
    </LanguageContext.Provider>
  );
};

### **LanguageButton.tsx**

import React, { useContext } from "react";
import { LanguageContext } from "./LanguageContext";

const LanguageButton = () => {
  const { language, toggleLanguage } = useContext(LanguageContext);

  return (
    <button onClick={toggleLanguage}>
      Current Language: {language}
    </button>
  );
};

export default LanguageButton;


---

### **App.tsx**

import React from "react";
import { LanguageProvider } from "./LanguageContext";
import LanguageButton from "./LanguageButton";

function App() {
  return (
    <LanguageProvider>
      <LanguageButton />
      <LanguageButton />
    </LanguageProvider>
  );
}

export default App;



---------------------------------------------------------------------------------------

------------------------ASSIGNMENT 3---------------------------------------------------

## **1. Responsive Grid Layout using Material UI Grid**

import { Grid, Paper, Typography } from "@mui/material";

function ResponsiveGrid() {
  return (
    <Grid container spacing={2}>
      <Grid item xs={12}>
        <Paper><Typography>Header</Typography></Paper>
      </Grid>

      <Grid item xs={12} md={3}>
        <Paper><Typography>Navigation</Typography></Paper>
      </Grid>

      <Grid item xs={12} md={9}>
        <Paper><Typography>Main Content</Typography></Paper>
      </Grid>

      <Grid item xs={12}>
        <Paper><Typography>Footer</Typography></Paper>
      </Grid>
    </Grid>
  );
}

export default ResponsiveGrid;


------------------------------------------------------------------------------------------

## **2. Tabs Navigation using Material UI with React Router**

import { Tabs, Tab } from "@mui/material";
import { Link, useLocation } from "react-router-dom";

function NavigationTabs() {
  const location = useLocation();

  return (
    <Tabs value={location.pathname}>
      <Tab label="Page 1" value="/page1" component={Link} to="/page1" />
      <Tab label="Page 2" value="/page2" component={Link} to="/page2" />
    </Tabs>
  );
}

export default NavigationTabs;


------------------------------------------------------------------------------------------

## **3(a). Batch Asynchronous State Updates (React 18)**

import React, { useState, startTransition } from "react";

function App() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState("Initial");

  const handleClick = () => {
    startTransition(() => {
      setCount(c => c + 1);
      setText("Updated");
    });
  };

  return (
    <div>
      <p>{text}</p>
      <p>Count: {count}</p>
      <button onClick={handleClick}>Update</button>
    </div>
  );
}

export default App;


------------------------------------------------------------------------------------------

## **3(b). Filter Input with Prioritized Updates**

import { useState, startTransition } from "react";

const ITEMS = ["Apple", "Banana", "Cherry", "Date", "Elderberry"];

function FilterList() {
  const [input, setInput] = useState("");
  const [list, setList] = useState(ITEMS);

  const handleChange = (e) => {
    const value = e.target.value;
    setInput(value);

    startTransition(() => {
      setList(ITEMS.filter(i =>
        i.toLowerCase().includes(value.toLowerCase())
      ));
    });
  };

  return (
    <div>
      <input value={input} onChange={handleChange} />
      <ul>{list.map(i => <li key={i}>{i}</li>)}</ul>
    </div>
  );
}

export default FilterList;


------------------------------------------------------------------------------------------

## **3(c). Fetch GitHub User using Fetch API**

import { useEffect, useState } from "react";

function GitHubUser() {
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetch("https://api.github.com/users/octocat")
      .then(res => res.json())
      .then(data => setUser(data));
  }, []);

  return user ? <p>{user.name}</p> : <p>Loading...</p>;
}

export default GitHubUser;


------------------------------------------------------------------------------------------

## **4(a). Data Fetching with TanStack Query**

import { QueryClient, QueryClientProvider, useQuery } from "@tanstack/react-query";

const queryClient = new QueryClient();

function GitHubUser() {
  const { data, isLoading } = useQuery({
    queryKey: ["githubUser"],
    queryFn: () =>
      fetch("https://api.github.com/users/octocat").then(res => res.json())
  });

  if (isLoading) return <p>Loading...</p>;
  return <p>{data.name}</p>;
}

export default function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <GitHubUser />
    </QueryClientProvider>
  );
}


------------------------------------------------------------------------------------------

## **4(b). Global Theme using Context API**

import { createContext, useContext } from "react";

const ThemeContext = createContext("light");

function ThemedComponent() {
  const theme = useContext(ThemeContext);
  return <div>Theme: {theme}</div>;
}

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedComponent />
    </ThemeContext.Provider>
  );
}

export default App;


------------------------------------------------------------------------------------------

## **5(a). Simple Counter using Redux**

import { createStore } from "redux";
import { Provider, useDispatch, useSelector } from "react-redux";

function reducer(state = { count: 0 }, action) {
  switch (action.type) {
    case "INCREMENT":
      return { count: state.count + 1 };
    default:
      return state;
  }
}

const store = createStore(reducer);

function Counter() {
  const count = useSelector(s => s.count);
  const dispatch = useDispatch();

  return (
    <button onClick={() => dispatch({ type: "INCREMENT" })}>
      Count: {count}
    </button>
  );
}

export default function App() {
  return (
    <Provider store={store}>
      <Counter />
    </Provider>
  );
}


------------------------------------------------------------------------------------------

## **5(b). SSR using getServerSideProps (Next.js)**

export async function getServerSideProps() {
  const res = await fetch("https://jsonplaceholder.typicode.com/todos/1");
  const data = await res.json();

  return { props: { data } };
}

export default function Page({ data }) {
  return <p>{data.title}</p>;
}

------------------------------------------------------------------------------------------

## **5(c). Dynamic Post Page with SSG (Next.js)**

export async function getStaticPaths() {
  return {
    paths: [{ params: { id: "1" } }],
    fallback: false
  };
}

export async function getStaticProps({ params }) {
  const res = await fetch(
    `https://jsonplaceholder.typicode.com/posts/${params.id}`
  );
  const post = await res.json();

  return { props: { post } };
}

export default function Post({ post }) {
  return <h1>{post.title}</h1>;
}
------------------------------------------------------------------------------------------

## **5(d). Unit Test using Vitest**

**Component**

```jsx
export default function Component() {
  return <p>Hello Test</p>;
}
```

**Test File**

```js
import { render, screen } from "@testing-library/react";
import { describe, it, expect } from "vitest";
import Component from "./Component";

describe("Component test", () => {
  it("renders text", () => {
    render(<Component />);
    expect(screen.getByText("Hello Test")).toBeInTheDocument();
  });
});

---------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------


ASSIGNMENT2
Q1 

import React, { useState } from "react";

function UserDetails() {
  const [details, setDetails] = useState({
    name: "Ahmed Saraf",
    age: 25,
    city: "Delhi",
    country: "India",
    email: "abc123@gmail.com",
    course: "B.Tech",
    college: "ABC"
  });

  const handleChange = (e) => {
    setDetails({ ...details, [e.target.name]: e.target.value });
  };

  return (
    <div>
      <input name="name" value={details.name} onChange={handleChange} />
      <input name="age" value={details.age} onChange={handleChange} />
      <input name="city" value={details.city} onChange={handleChange} />
      <input name="country" value={details.country} onChange={handleChange} />
      <input name="email" value={details.email} onChange={handleChange} />
      <input name="course" value={details.course} onChange={handleChange} />
      <input name="college" value={details.college} onChange={handleChange} />

      <p>
        My name is {details.name}, I am {details.age} years old from{" "}
        {details.city}, {details.country}. I am pursuing {details.course} at{" "}
        {details.college}. My email ID is {details.email}.
      </p>
    </div>
  );
}

export default UserDetails;

------------------------------------------------------------------------------------------

Q2
function App() {
  const students = [
    { name: "arush", marks: 90 },
    { name: "jojo", marks: 93 },
    { name: "diaa", marks: 94 },
  ];

  return (
    <div>
      <h2>Student Marks</h2>
      <ul>
        {students.map((student, index) => (
          <li key={index}>
            {student.name}: {student.marks}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;

------------------------------------------------------------------------------------------

Q3
import { useMemo, useState } from "react";

function computeExpensiveValue(num) {
  let res = 0;
  for (let i = 0; i < 1000; i++) {
    res += num * 2;
  }
  return res;
}

function Component() {
  const [number, setNumber] = useState(1);
  const [text, setText] = useState("");

  const expRes = useMemo(() => {
    return computeExpensiveValue(number);
  }, [number]);

  return (
    <div>
      <h1>useMemo Example</h1>

      <p>Number: {number}</p>
      <p>Expensive result: {expRes}</p>

      <button onClick={() => setNumber(number + 1)}>
        Increment Number
      </button>

      <br /><br />

      <input
        type="text"
        value={text}
        placeholder="Type something"
        onChange={(e) => setText(e.target.value)}
      />

      <p>Typed text: {text}</p>
    </div>
  );
}

export default Component;


------------------------------------------------------------------------------------------
Q4
import React, { useState, useCallback } from "react";

const MyButton = React.memo(({ onClick, label }) => {
  console.log("Button rendered:", label);
  return <button onClick={onClick}>{label}</button>;
});
function App() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState("");
  const increment = useCallback(() => {
    setCount((prev) => prev + 1);
  }, []);
  return (
    <div>
      <h1>useCallback Example</h1>
      <p>Count: {count}</p>
      <MyButton onClick={increment} label="Increment Count" />
      <br /><br />
      <input
        type="text"
        placeholder="Type something"
        value={text}
        onChange={(e) => setText(e.target.value)}
      />
      <p>Typed text: {text}</p>
    </div>
  );
}

export default App;


------------------------------------------------------------------------------------------
Q5

import { useState, useEffect } from "react";

function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Effect ran, count:", count);

    return () => {
      console.log("Cleanup before next effect / unmount, count:", count);
    };
  }, [count]);

  return (
    <div>
      <h2>useEffect Hook</h2>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </div>
  );
}

export default App;
------------------------------------------------------------------------------------------
Q6

import {useContext, useState} from "react";
const usercontext=createContext();
function App(){
    const[user,setUser]=useState({name:'Rishika', theme:'light'});
    const toggleTheme=()=>{
        setUser(prev=>({..prev,theme:prev.theme==='light'?'dark':'light'}));
    }
    return(
        <usercontext.Provider value={{user,toggleTheme}}>
        <Dashboard/>
        </usercontext.Provider>
    )
}
function Dashboard(){
    const{user,toggleTheme}=useContext(usercontext);
    const styles={
        backgroundColor:user.theme==='light'?'#fff':'#333',
        color:user.theme==='light'?'#000':'#fff'};

    return(
        <div style={styles}>
            <h2>Welcome:{user.name}</h2>
            <button onClick={toggleTheme}>Toggle Theme</button>
        </div>
    )
}
------------------------------------------------------------------------------------------
Q7
import React, { useRef, useState } from "react";

function App() {
  const inputRef = useRef();
  const handleClick = () => {
    inputRef.current.focus();
  };

  const renderCount = useRef(0);
  renderCount.current += 1;

  const [text, setText] = useState("");

  return (
    <div>
      <input
        type="text"
        ref={inputRef}
        placeholder="Focus me on button click"
        value={text}
        onChange={(e) => setText(e.target.value)}
      />
      <button onClick={handleClick}>Focus Input</button>
      <p>Input value: {text}</p>
      <p>Render count: {renderCount.current}</p>
    </div>
  );
}

export default App;
----------------------------------------------------------------------
Q8
import React from 'react';
function eventHandling(){
    const handleClick = () => { alert('Button clicked!'); };
    return(
        <div>
            <h2>Event handling</h2>
            <button onClick={handleClick}>Click Me</button>
        </div>
    )
}
-----------------------------------------------------------------------
Q9
import React, { useState } from "react";

function EventHandling() {
  const [message, setMessage] = useState("Hello");

  const handleClick = () => {
    setMessage("Button clicked!");
  };

  const handleChange = (e) => {
    setMessage(e.target.value);
  };

  const handleMouseOver = () => {
    setMessage("Mouse Over Event");
  };

  return (
    <div>
      <h2>Event handling</h2>
      <button onClick={handleClick}>Click Me</button>
      <input type="text" onChange={handleChange} placeholder="Type something" />
      <div
        onMouseOver={handleMouseOver}
        style={{ border: "1px solid black", padding: "10px", marginTop: "10px" }}
    >
        Hover over this box
      </div>
      <p>{message}</p>
    </div>
  );
}

export default EventHandling;

-----------------------------------------------------------------------
Q10
import React from "react";

function EventHandler() {
  const handleClick = () => {
    alert("Button was clicked!");
  };

  return (
    <div>
      <button onClick={() => alert("Button was clicked!")}>
        Inline
      </button>
      <button onClick={handleClick}>
        Non-inline
      </button>
    </div>
  );
}

export default EventHandler;
-----------------------------------------------------------------------

Q11
import React from "react";

function EventHandler() {
  const handleClick = (e) => {
    console.log("Synthetic Event Type:", e.type);
    console.log("Button Text:", e.target.textContent);

    setTimeout(() => {
      console.log("After Timeout:", e.target?.textContent);
    }, 1000);
  };

  return (
    <>
      <h2>Synthetic and Event Pooling</h2>
      <button onClick={handleClick}>Click Me</button>
    </>
  );
}

export default EventHandler;
-----------------------------------------------------------------------
Q12

import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h2>Counter: {count}</h2>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
  );
}

export default Counter;

-----------------------------------------------------------------------
Q13
import React, { useState } from "react";

function App() {
  const [title, setTitle] = useState("");
  const [summary, setSummary] = useState("");
  const [articles, setArticles] = useState([]);

  const addArticle = () => {
    if (!title.trim()) return;

    setArticles((prev) => [
      ...prev,
      {
        id: Date.now(),
        title: title.trim(),
        summary: summary.trim(),
        visible: false,
      },
    ]);

    setTitle("");
    setSummary("");
  };

  const toggleSummary = (id) => {
    setArticles((prev) =>
      prev.map((article) =>
        article.id === id
          ? { ...article, visible: !article.visible }
          : article
      )
    );
  };

  const deleteArticle = (id) => {
    setArticles((prev) => prev.filter((article) => article.id !== id));
  };

  return (
    <div>
      <h1>Article Manager</h1>

      <input
        placeholder="Title"
        value={title}
        onChange={(e) => setTitle(e.target.value)}
      />

      <input
        placeholder="Summary"
        value={summary}
        onChange={(e) => setSummary(e.target.value)}
      />

      <button onClick={addArticle}>Add Article</button>

      <ul>
        {articles.map(({ id, title, summary, visible }) => (
          <li key={id}>
            <a href="#" onClick={() => toggleSummary(id)}>
              {title}
            </a>

            <div style={{ display: visible ? "block" : "none" }}>
              {summary}
            </div>

            <button onClick={() => deleteArticle(id)}>Remove</button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;
-----------------------------------------------------------------------
-----------------------------------------------------------------------

ASSIGNMENT 1

Q1
App.js


import './App.css';
import {useState} from 'react';
export default function App(){
    const[highlight,setHighlight]=useState(false);
    const handleClick=()=>{
        setHighlight(true);
    }
    return(
        <div>
            <button onClick={handleClick}>highlight paragraph</button>
            <p className={highlight?'highlight':''}>This is the same text</p>
        </div>
    )
}

App.css
.highlight{
  background-color: black;
  color: wheat;
  font-weight: bold;
}




------------------------------------------------------------------------------------------




Q2
App.js

export default function App() {
  const person = {
    name: "ARIF",
    age: 15,
    branch: "CSIT",
    college: "ITER",
    professionType: "Engineer",
    salary: 10000000000,
    professionDetails: "Software developer",
    hobbies: "Reading, Coding, Music"
  };
  return (
    <div>
      <h1>Biography</h1>
      <p><strong>Name:</strong> {person.name}</p>
      <p><strong>Age:</strong> {person.age}</p>
      <p><strong>Branch:</strong> {person.branch}</p>
      <p><strong>College:</strong> {person.college}</p>
      <p><strong>Profession Type:</strong> {person.professionType}</p>
      <p><strong>Salary:</strong> {person.salary}</p>
      <p><strong>Profession Details:</strong> {person.professionDetails}</p>
      <p><strong>Hobbies:</strong> {person.hobbies}</p>
    </div>
  );
}
------------------------------------------------------------------------------------------


Q3
index.js

import React from "react";
import { createRoot } from "react-dom/client";
const root = createRoot(document.getElementById("root"));
const element = React.createElement(
  "div",
  null,
  React.createElement("p", null, "Hello"),
  React.createElement("p", null, "JSX")
);
root.render(element);
------------------------------------------------------------------------------------------


Q4
index.js
import React from "react";
import ReactDOM from "react-dom/client";

function App() {
  return (
    <div>
      <button>Click Me</button>

      <code>console.log("Hello World");</code>

      <br />

      <label>Name: </label>
      <input type="text" placeholder="Enter something" />

      <p>This is a sample paragraph.</p>

      <pre>
This is
preformatted
text
      </pre>

      <select>
        <option>Option 1</option>
        <option>Option 2</option>
      </select>

      <table border="1">
        <tr>
          <th>Sl No</th>
          <th>Item</th>
        </tr>
        <tr>
          <td>1</td>
          <td>Apple</td>
        </tr>
        <tr>
          <td>2</td>
          <td>Mango</td>
        </tr>
      </table>
    </div>
  );
}

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);

------------------------------------------------------------------------------------------

Q5
import React from "react";
import ReactDOM from "react-dom/client";

function App() {
  return (
    <section>
      <header>
        <h1>A Header</h1>
      </header>

      <nav>
        <a href="#">Nav Item</a>
      </nav>

      <main>
        <p>The main content...</p>
      </main>

      <footer>
        <small>© 2024</small>
      </footer>
    </section>
  );
}

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);

------------------------------------------------------------------------------------------


Q6
app.js

import "./App.css";
function MyComponent({ title, description }) {
  return (
    <div>
      <h1>{title}</h1>
      <p>{description}</p>
    </div>
  );
}
function App() {
  return (
    <MyComponent
      title="Hello World"
      description="This is a sample description"
    />
  );
}
export default App;

------------------------------------------------------------------------------------------

Q7
import "./App.css";

function MyButton({ disabled, text }) {
  return (
    <button disabled={disabled}>
      {text}
    </button>
  );
}
function App() {
  return (
    <div>
      <MyButton disabled={true} text="Disabled Button" />
      <MyButton disabled={false} text="Enabled Button" />
    </div>
  );
}

export default App;
------------------------------------------------------------------------------------------

Q8
import { useState, useEffect } from "react";

function MyButton({ disabled, text }) {
  return (
    <button disabled={disabled}>
      {text}
    </button>
  );
}

function MyComponent({ title, description }) {
  return (
    <div>
      <h1>{title}</h1>
      <p>{description}</p>
    </div>
  );
}

function MyList() {
  return (
    <ul>
      <li>Item 1</li>
      <li>Item 2</li>
    </ul>
  );
}

function App() {
  const [show, setShow] = useState(false);

  useEffect(() => {
    setTimeout(() => {
      setShow(true);
    }, 2000);
  }, []);

  return (
    <div>
      {show && (
        <>
          <MyComponent
            title="Hello World"
            description="This is a sample description"
          />
          <MyButton disabled={true} text="Disabled Button" />
          <MyList />
        </>
      )}
    </div>
  );
}

export default App;
------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------

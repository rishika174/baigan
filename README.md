
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
1. Write a Program to create a responsive grid layout using Material UI's Grid
component.
Use the Grid component with container and item roles.

## **1. Responsive Grid Layout using Material UI Grid**
npm install @mui/material @emotion/react @emotion/styled


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
2. Write code to implement tabs for navigation in Material UI with React Router
## **2. Tabs Navigation using Material UI with React Router**
npm install react-router-dom
npm install @mui/material @emotion/react @emotion/styled


import React from "react";
import { BrowserRouter, Routes, Route, Link, useLocation } from "react-router-dom";
import { Tabs, Tab, Box, Container } from "@mui/material";
function NavigationTabs() {
  const location = useLocation();
  const cur = location.pathname;
  return (
    <Box sx={{ borderBottom: 1, borderColor: "divider" }}>
      <Tabs value={cur} aria-label="navigation tabs">
        <Tab label="Home" value="/" component={Link} to="/" />
        <Tab label="Page1" value="/page1" component={Link} to="/page1" />
        <Tab label="Page2" value="/page2" component={Link} to="/page2" />
      </Tabs>
    </Box>
  );
}

function Home() {
  return <h2>Home Page</h2>;
}

function Page1() {
  return <h2>Page 1</h2>;
}

function Page2() {
  return <h2>Page 2</h2>;
}

function App() {
  return (
    <BrowserRouter>
      <Container>
        <NavigationTabs />
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/page1" element={<Page1 />} />
          <Route path="/page2" element={<Page2 />} />
        </Routes>
      </Container>
    </BrowserRouter>
  );
}

export default App;



------------------------------------------------------------------------------------------

**3(a). Batch Asynchronous State Updates (React 18)**

3. (a) Write a Program to batch asynchronous state updates in React 18.
(b) Implement a filter input with prioritized updates for a large list.
(c) Write a program to fetch GitHub user data using the Fetch API in a React
component.


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

const Items = [
  { id: 1, name: "Item 1" },
  { id: 2, name: "Item 2" },
  { id: 3, name: "Item 3" },
  { id: 4, name: "Item 4" },
  { id: 5, name: "Item 5" },
];

function filterList(inputValue) {
  return Items.filter(item =>
    item.name.toLowerCase().includes(inputValue.toLowerCase())
  );
}

function FilterList() {
  const [filter, setFilter] = useState("");
  const [items, setItems] = useState(Items);

  const onChange = (e) => {
    const value = e.target.value;
    setFilter(value);

    startTransition(() => {
      setItems(filterList(value));
    });
  };

  return (
    <div>
      <input value={filter} onChange={onChange} />
      <ul>
        {items.map(item => (
          <li key={item.id}>{item.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default FilterList;



------------------------------------------------------------------------------------------

## **3(c). Fetch GitHub User using Fetch API**

import React,{useState,useEffect, use} from 'react';
function GitHubUser(){
    const[user,setUser]=useState(null);
    const[loading,setLoading]=useState(true);
    useEffect(()=>{
        fetch('https://api.github.com/users/octocat')
        .then(res=>res.json())
        .then(data=>setUser(data))
        .finally(()=>setLoading(false));
    },[]);
    return(loading ? <p>Loading...</p> :<p>{user.name}</p>);
}
function App(){
    return(
        <div>
            <h1>Github user info</h1>
            <GitHubUser/>
        </div>
    )
}
export default App;


------------------------------------------------------------------------------------------
4.(a) Write a program to Implement data fetching with TanStack Query for a GitHub user.
(b) Write a program to create a global theme using React Context API?**

**4(a). Data Fetching with TanStack Query**
npm install @tanstack/react-query

import React from "react";
import { useQuery, QueryClient, QueryClientProvider } from "@tanstack/react-query";

const queryClient = new QueryClient();

function GithubUser() {
  const { data, isLoading, isError } = useQuery({
    queryKey: ["user"],
    queryFn: () =>
      fetch("https://api.github.com/users/octocat").then((res) => res.json()),
  });

  if (isLoading) return <p>Loading...</p>;
  if (isError) return <p>Error fetching</p>;

  return <p>{data.name}</p>;
}

function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <div>
        <h1>Github User Info</h1>
        <GithubUser />
      </div>
    </QueryClientProvider>
  );
}

export default App;



------------------------------------------------------------------------------------------

## **4(b). Global Theme using Context API**

import React, { createContext, useContext } from "react";

const ThemeContext = createContext("light");

function ThemeProvider({ children }) {
  const themeValue = "dark";

  return (
    <ThemeContext.Provider value={themeValue}>
      {children}
    </ThemeContext.Provider>
  );
}

function Component() {
  const theme = useContext(ThemeContext);

  return (
    <div style={{ background: theme === "dark" ? "#333" : "#fff", padding: "10px", color: "#fff" }}>
      Theme: {theme}
    </div>
  );
}

function App() {
  return (
    <ThemeProvider>
      <Component />
    </ThemeProvider>
  );
}

export default App;


------------------------------------------------------------------------------------------
5.(a) Implement a simple counter using Redux in React.
(b) implement SSR in Next.js using getServerSideProps?
(c) Create a dynamic post page with SSG in Next.js.
(d) Write a program to set up a basic unit test for a React component using Vitest.

5(a). Simple Counter using Redux
npm install redux react-redux


import React from "react";
import { createStore } from "redux";
import { Provider, useDispatch, useSelector } from "react-redux";

function reducer(state = { count: 0 }, action) {
  switch (action.type) {
    case "INCREMENT":
      return { count: state.count + 1 };

    case "SET_INITIAL_COUNT": {
      const safeCount = parseInt(action.payload, 10);
      return { count: isNaN(safeCount) ? 0 : safeCount };
    }

    default:
      return state;
  }
}

const store = createStore(reducer);

function Counter() {
  const count = useSelector((state) => state.count);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>Redux Counter</h1>
      <button onClick={() => dispatch({ type: "INCREMENT" })}>
        {count}
      </button>
    </div>
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
npx create-next-app

export async function getServerSideProps() {
  const res = await fetch("https://api.github.com/users/torvalds");
  const data = await res.json();

  return {
    props: { data },
  };
}

function Page({ data }) {
  return (
    <div>
      <h1>Server side rendered page</h1>
      <p>Name: {data.name}</p>
      <p>UserName: {data.login}</p>
      <p>Location: {data.location}</p>
    </div>
  );
}

export default Page;


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
npm install -D vitest @testing-library/react @testing-library/jest-dom jsdom

App.js
import React from "react";
import Component from "./Component";

function App() {
  return (
    <div>
      <h1>My react app</h1>
      <Component />
    </div>
  );
}

export default App;

✅  App.test.js
import { render, screen } from "@testing-library/react";
import App from "./App";

test("renders app heading", () => {
  render(<App />);
  const heading = screen.getByText("My react app");
  expect(heading).toBeInTheDocument();
});


✅ Component.js
function Component() {
  return <div>Hello</div>;
}
export default Component;


✅ Component.test.js
import { render, screen } from "@testing-library/react";
import Component from "./Component";

test("renders text", () => {
  render(<Component />);
  expect(screen.getByText("Hello")).toBeInTheDocument();
});

---------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------


ASSIGNMENT2
Q1
Create a React program that lets user to input his/her name, age, city, country, course,
college name and email id and display the entered values on the screen.
Tips:
(a) Use React's useState hook to manage the state for the user's name and age.
(b) Provide an input field for the name with a default value of "Ahmed Saraf" and an
input field for age with a default value of 25.
Other Default Vaalues: "Delhi" for city , "India" for country, “abc123@gmail.com
for email id, course: “B. Tech”, College name: “ABC”.
(c) Use the onChange event to update the state when the user types in the input fields.
(d) Below each input field, display the entered name, age, etc, dynamically as the user
types.
(e) The program should display the following text below the inputs:
"My name is [entered name]"
"My age is [entered age]"
"My city is [entered city]"
"My country is [entered country]"
"My email id is [entered email id]"
"My course is [entered B. Tech]"
"My college name is [entered ABC]"


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

Q2 Create a React program that displays a list of student names and their marks using the
map() function.

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

Q3 Create a React program that demonstrates the use of useMemo to optimize performance
for expensive computations as follows:
(i) Create a functional component called Component. Add a state variable number
with an initial value of 1. Add a state variable text with an initial value of an
empty string "".
(ii) Create a function computeExpensiveValue(num) that simulates a heavy
computation (e.g., a large loop) and returns a result based on num.
(iii) Use React.useMemo to compute the expensive value based on number. The
computation should only rerun when number changes.
a. Render the following in the component: display the current number, display
the result of the expensive computation, a button to increment number by 1,
an input field bound to text that updates as the user types, display the typed
text below the input.



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
Q4 Create a React program that demonstrates the use of useCallback to prevent
unnecessary re-renders of a memoized child component.


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
Q5 Write a program in React to implement the concept of the useEffect hook.
(a) Create a functional component that demonstrates the use of the useEffect hook.
(b) The component should perform an operation such as:displaying a message in
the console or on the screen whenever the component mounts or updates.
Optionally, implement a cleanup function to demonstrate how useEffect handles
unmounting.
(c) Use appropriate state management with the useState hook to trigger rerendering and observe how useEffect behaves in response to state changes.
(d) Include clear comments explaining the purpose of useEffect, its dependency
array, and the flow of execution.


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
Q6 Create a React application that demonstrates data sharing between components using
the Context API and the useContext hook. Define a context (e.g., UserContext) in a
parent component and provide a value such as a user’s name, theme, or language
preference. Consume the context value in one or more child components using the
useContext hook, and display the data on the screen. Optionally, include a mechanism
(such as a button) to update the context value dynamically and reflect

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
Q7 Write a program in React to implement the concept of the useRef hook as follows:
(a) Create a functional React component that demonstrates the use of the useRef hook.
(b) Use useRef to access and manipulate a DOM element directly — for example,
setting focus on an input field when a button is clicked.
(c) Optionally, demonstrate how useRef can be used to store mutable values that
persist across renders without causing re-renders.
(d) Include appropriate comments explaining the purpose of useRef, its difference
from useState, and its practical use cases in React applications.


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
---------------------------------------------------------------------------------
Q8. Write a Simple program in react to implement the event handling used in react.
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
---------------------------------------------------------------------------------
Q9.  Write a React program to demonstrate the handling of multiple events.
• Create a functional React component that includes different user interface elements
such as buttons, input fields, or divs.
• Implement multiple event handlers (for example, onClick, onChange,
onMouseOver, etc.) to respond to various user actions.
• Display appropriate messages or perform specific actions when each event is
triggered.
• Include comments explaining the purpose of each event handler and how React’s
event system (Synthetic Events) manages them.


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
Q10 Write a program in react to implement the concept of inline and non-inline event
handlers.

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

Q11 Write a program in react to demonstrate the concept of synthetic events and event
pooling used in react environment.


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
Q12 Write a React component that uses the useState hook to create a counter with
Increment, Decrement, and Reset buttons.

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
Q13 Design and implement a React application utilizing the useState hook to manage and
display a list of articles. The application should meet the following specifications:
• The interface must contain two input fields for entering an article’s Title and
Summary.
• Upon clicking the “Add” button, the entered article should be appended to a
displayed list of articles.
• Each article entry in the list must include: the Title, displayed as a clickable link.
Clicking this link should toggle the visibility of the corresponding Summary
(i.e., show or hide it).
• A Remove ( ) button that allows the user to delete the respective article from
the list. The visibility of each article’s summary should be controlled using
inline CSS styling (e.g., by modifying the display property between "none" and
"block").



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

Q1. Create a React component to do the following operations:
i) A button labelled "Highlight Paragraph".
ii) A paragraph with the text "This is some text."
iii) When the button is clicked, the paragraph should: Have a yellow background
color and becomes bold
iv) Use React state (useState) and conditional CSS class to implement this
behavior.

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




Q2 Write a react program that prints the biography of a person having the following details:
Name, age, profession type, salary, profession details, etc.

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
Q3 Write a React program (without using JSX) that:
i) imports React and ReactDOM.
ii) Creates a root container by selecting the <div id="root"></div> element in the
HTML file.
iii) Uses React.createElement() to render the following output inside the root
element:
iv) Hello, JSX
v) The word "JSX" should appear in bold.
vi) Do not use JSX syntax (<p>...</p>). Use only React.createElement()
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


Q4 Write a React program that demonstrates the use of built-in HTML tags in React.
Your program should:
i) Import React and ReactDOM.
ii) Create a root container that mounts the React app to a <div id="root"></div>
in index.html.
iii) Render the following HTML tags inside React:
a. A button with the text Click Me.
b. A code block showing console.log("Hello World");.
c. An input field with a placeholder "Enter something".
d. A label for the input field with text "Name:".
e. A paragraph with any sample text.
f. A preformatted text block.
g. A select dropdown with two options (Option 1 and Option 2).
h. A table with two rows (Sl No, Item → Apple, Mango).


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
Write a React program that demonstrates the use of semantic HTML5 tags inside
React.
Your program should:
(i) Import ReactDOM and create a root container that renders into <div
id="root"></div>.
(ii) Render a <section> element that contains the following:
(iii) A <header> with an <h1> heading: "A Header".
(iv) A <nav> element with a navigation link labeled "Nav Item".
(v) A <main> section with a paragraph containing the text: "The main content...".
(vi) A <footer> with a <small> tag showing: © 2024.
(Ensure that all tags are properly nested and follow React’s JSX syntax)



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
Write a React program that defines a component called MyComponent which
accepts title and description as props and displays them inside an <h1> and <p>
element respectively. Then, create an App component that renders MyComponent
with the following values:
title = "Hello World"
description = "This is a sample description"

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
Write a React component named MyButton that accepts two props as follows:
disabled – a boolean value that determines whether the button should be disabled or
enabled.
text – a string that represents the button’s label.
The component should return a <button> element that displays the text prop and applies
the disabled state based on the disabled prop. Finally, export the component as default.


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
Write a complete React program with MyButton, MyList, and MyComponent, and
then update the UI dynamically after setTimeout().

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

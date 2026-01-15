
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


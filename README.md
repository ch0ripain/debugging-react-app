# 🐛 Debugging React App

## Debugging Methods

### 1. Using the Browser Console 🖥️

The first method is to check the browser's error console. Here, you can find the type of error, the exact line of code, and other useful information that helps you locate and fix the issue.

> [!TIP]
> The console is your first go-to for quick details on any unexpected error.

if we input a duration less than 1 (e.g., 0, -1), the app crashes and shows the following error in the console:
```javascript
Uncaught TypeError: Cannot read properties of undefined (reading 'valueEndOfYear') at Results (Results.jsx:12:16)
```
This error tells us exactly where to look in our code. On line 12 of Results.jsx, we have a constant that retrieves data from another function:
```javascript
const initialInvestment = 
    results[0].valueEndOfYear - 
    results[0].interest - 
    results[0].annualInvestment;
```
The results variable is populated by calling:
```javascript
const results = [];
calculateInvestmentResults(input, results);
```
When we take a look on calculateInvestmentResults, we see it contains a for loop that relies on duration as the iteration count:
```javascript
for (let i = 0; i < duration; i++) {
    //some logic
}
```
Since duration is 0, this loop never executes, leaving results empty, which leads to the error.
Solution 🛠️
To handle this, we have a couple of options:

- Add validation in calculateInvestmentResults to check if duration is valid. If it isn’t, we could return a default value or a specific error message. However, this would add extra logic to the function, so it may not be the best approach.
- Show a user-friendly message in the UI when duration is invalid. This approach informs the user about the error and suggests how to correct it, making it a better option.
To implement this, we’ll add a condition in Results to catch the error and display a helpful message to guide the user:
```javascript
if (results.length === 0) {
    return <p className="center">Invalid input data provided</p>;
}
```

### 2. Browser Developer Tools 🧰

Another way is to leverage the browser’s developer tools, especially the **Source** tab. Here, you can see your entire project structure and navigate between files. 
With **breakpoints**, you can monitor values and follow the flow of your code, checking if data is correctly passed between components for example.

> [!TIP]
>  Place breakpoints strategically to track data flow and better understand your app’s behavior.

### 3. React Extensions 🔍

Use extensions like **React Developer Tools**. This tool allows you to see your entire component structure. 
By clicking on a component, you can inspect its state, props, and functions, and even modify values in real-time to observe your app’s response.

> [!TIP]
>  The **Components** view in React DevTools is ideal for analyzing each component's state and props throughout your app.

### 4. Strict Mode 🚨
Another tool is Strict Mode, a component provided by the React library that helps identify potential issues in your app's logic. 
To use it, you simply need to wrap your application (or specific parts of it) with <React.StrictMode>. 
This mode highlights unexpected behaviors, unsafe lifecycle methods, and deprecated features, making it easier to detect logic-related issues that could affect your app's stability.
```javascript
import React from 'react';

function App() {
  return (
    <React.StrictMode>
      {/* Your App Components */}
    </React.StrictMode>
  );
}
```
> [!TIP]
> Enabling Strict Mode is especially useful in development, as it helps catch subtle bugs and ensures that your code follows React's best practices.

---
<p align="center">🌟 This project is a practice exercise I learned from the <a href='https://www.udemy.com/course/react-the-complete-guide-incl-redux/?couponCode=ST7MT110524'>Academind's React Course</a> 🌟</p>
<p align="center">🐸 I hope this README helps you in some way! 🐸</p>


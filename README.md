# 🐛 Debugging React App

## Debugging Methods

### 1. Using the Browser Console 🖥️

The first method is to check the browser's error console. Here, you can find the type of error, the exact line of code, and other useful information that helps you locate and fix the issue.

> [!TIP]
> The console is your first go-to for quick details on any unexpected error.

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

<p align="center">I hope this helps u 🐸</p>
---


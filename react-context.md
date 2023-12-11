# React Context Explained

## Introduction

React Context provides a way to share values like themes, user authentication status, or any global state across the entire React component tree without the need to pass props manually at every level. It helps in simplifying state management and avoids prop drilling.

## When to Use React Context

React Context is useful in the following scenarios:

- **Theme Switching:** When you want to apply different themes to your application.
- **User Authentication:** Managing user authentication state across components.
- **Localization:** Providing language preferences throughout the app.

## How to Use React Context

### 1. Create a Context

```jsx
// MyContext.js

import { createContext } from 'react';

const MyContext = createContext();

export default MyContext;

```

### 2. Create a Provider

Wrap your application or a section of it with the context provider.

```jsx
// MyProvider.js

import React, { useState } from 'react';
import MyContext from './MyContext';

const MyProvider = ({ children }) => {
  const [value, setValue] = useState('Default Value');

  const updateValue = (newValue) => {
    setValue(newValue);
  };

  return (
    <MyContext.Provider value={{ value, updateValue }}>
      {children}
    </MyContext.Provider>
  );
};

export default MyProvider;
```

### 3. Consume the Context

In any component, you can access the context values using the useContext hook.

```jsx
// MyComponent.js

import React, { useContext } from 'react';
import MyContext from './MyContext';

const MyComponent = () => {
  const { value, updateValue } = useContext(MyContext);

  return (
    <div>
      <p>Current Value: {value}</p>
      <button onClick={() => updateValue('New Value')}>Update Value</button>
    </div>
  );
};

export default MyComponent;

```

### 4. Wrap Your App with the Provider

Wrap your main application component with the context provider.

```jsx
// App.js

import React from 'react';
import MyProvider from './MyProvider';
import MyComponent from './MyComponent';

const App = () => {
  return (
    <MyProvider>
      <MyComponent />
    </MyProvider>
  );
};

export default App;

```


### Conclusion

React Context is a powerful tool for managing global state in your React applications, providing a cleaner and more efficient alternative to prop drilling.


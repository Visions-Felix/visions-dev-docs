# Using Context & Providers

Context and providers are powerful tools in React that allow you to share data and functionality across components without passing props manually. In the context of the VisionsTrust app, understanding how to properly use context and providers is crucial for building scalable and maintainable code.

## What is Context?

Context in React provides a way to pass data through the component tree without having to pass props down manually at every level. It allows you to share data between components that are not directly connected in the component hierarchy.

## Creating a Context & Provider

To create a context in the VisionsTrust app, you can use the `createContext` function from the `react` package.

A provider is a component that allows consuming components to subscribe to the context changes. It provides the context value to all its descendants. In the VisionsTrust app, you can create a provider component to wrap the relevant parts of the component tree.

Here's an example for a Theme Context Provider. It sets the type of the context value, creates the type, creates the provider and assigns the value of the correct type to the Provider.

```tsx
// File: ThemeProvider.tsx

import { createContext, PropsWithChildren, useContext, useState } from 'react';

interface ThemeContextValue {
    theme: string;
    handleThemeChange: (theme: string) => void;
}

const ThemeContext = createContext<ThemeContextValue>({} as ThemeContextValue);

export const ThemeProvider = ({ children }: PropsWithChildren) => {
    const [theme, setTheme] = useState('light');

    const handleThemeChange = (newTheme: string) => {
        setTheme(newTheme);
    };

    return <ThemeContext.Provider value={{ theme, handleThemeChange }}>{children}</ThemeContext.Provider>;
};
```

## Consuming the Context

To consume the context in a component, the `useContext()` hook should be encapsulated in a custom hook with the name of the provider.

The context consumption should always check if it called from within the bounds of his Provider, thus the custom hook should verify or throw an Error if not the case in order to catch the issues as soon as possible during development.

Here's an example from our theme provider.

```tsx
// File: ThemeProvider.tsx

export const useTheme = () => {
    const context = useContext(ThemeContext);

    if (!context) throw new Error('useTheme should be used within a ThemeProvider');

    return context;
};
```

Once the hook exists in the code, any component can consume the context by calling the hook.

```tsx
const MyComponent = () => {
    const { theme, handleThemeChange } = useTheme();

    return (
        <div>
            <button onClick={() => handleThemeChange('dark')}>Change Theme</button>
            <p>Current Theme: {theme}</p>
        </div>
    );
};
```

## Using the Provider

To use the provider in the VisionsTrust app, you need to wrap the relevant parts of the component tree with the provider component created earlier. Here's an example:

```jsx
const App = () => {
    return <ThemeProvider>{/* Component tree */}</ThemeProvider>;
};
```

## Documenting Complex Methods

When working with complex methods in a provider, it is important to provide clear and concise documentation. This helps other developers understand the purpose, inputs, and outputs of the method, making it easier to maintain and debug the codebase.

Here are some best practices for documenting complex methods in a provider:

1. Use descriptive function names: Choose function names that accurately describe what the method does. Avoid generic names that can be ambiguous or misleading.

2. Add comments: Include comments within the method to explain the logic and any important details. This can help other developers understand the implementation and make modifications if needed.

3. Document parameters and return values: Clearly specify the parameters that the method expects and the type of value it returns. This helps other developers understand how to use the method correctly and what to expect as a result.

4. Provide examples: ***(If necessary)*** Include examples of how to use the method in different scenarios. This can help other developers understand the intended usage and provide guidance on how to handle edge cases.

5. Update documentation as needed: If the method undergoes changes or improvements, make sure to update the documentation accordingly. This ensures that the documentation remains accurate and up-to-date.

## Avoid Over-Complexifying Providers

While providers are powerful tools for sharing data and functionality, it is important to avoid over-complexifying them. A provider should have a clear and specific purpose, focusing on a single responsibility. This helps maintain a clean and maintainable codebase.

Here are some tips to avoid over-complexifying a provider:

1. Single responsibility principle: Ensure that the provider is responsible for a specific set of data or functionality. Avoid adding unrelated features or functionalities that can make the provider bloated and harder to understand.

2. Modularize functionality: If the provider becomes too large or complex, consider breaking it down into smaller, more manageable pieces. This can improve code organization and make it easier to maintain and test.

3. Separate concerns: Keep the provider focused on managing state and providing data or functionality. Avoid mixing business logic or UI-related code within the provider. Instead, delegate those responsibilities to separate modules or components.

4. Use [composition](https://www.digitalocean.com/community/tutorials/composition-vs-inheritance): Instead of adding more complexity to a single provider, consider using composition to combine multiple providers with specific responsibilities. This can help maintain a clear separation of concerns and make the codebase more modular.

By following these practices, you can ensure that your provider remains focused, maintainable, and easy to understand, while effectively sharing data and functionality across components.


## Summary

In the VisionsTrust app, context and providers are essential for sharing data and functionality across components. By creating a context, defining a provider, and consuming the context using the `useContext` hook, you can effectively manage and share state and methods throughout your app.

Remember to use context and providers judiciously, as excessive use can lead to a complex and hard-to-maintain codebase. Use them when it makes sense to share data or functionality across multiple components that are not directly connected in the component hierarchy.

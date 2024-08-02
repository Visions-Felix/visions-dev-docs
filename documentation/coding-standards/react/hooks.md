# Using Hooks
Hooks are a powerful feature in React that allow you to use state and other React features without writing a class. In the context of the VisionsTrust app, understanding how to properly use hooks is crucial for avoiding un-necessary complexity in components.

## What are Hooks?

Hooks are functions that let you "hook into" React state and lifecycle features from function components. They provide a way to use stateful logic and other React functionalities in function components.

## Custom Hooks

Custom hooks are a mechanism to reuse stateful logic between components. They are a great way to extract and share logic that involves hooks.

### Creating a Custom Hook

Here's an example of a custom hook that uses a certain query from TanStack Query.

```tsx
import { useQuery } from '@tanstack/react-query';
import { fetchProjects } from './api/projects';

const useCatalogQuery = (queryKey: string) => {
    const projectsQuery = useQuery({
        queryKey: ['projects'],
        queryFn: fetchProjects;
    })

    return { data, loading: isLoading };
};
```

### Using a Custom Hook

You can use the custom hook in any component just like built-in hooks.

```tsx
import useCustomQuery from './useCustomQuery';

const MyComponent = () => {
    const { data, loading } = useCustomQuery('myQueryKey');

    if (loading) return <p>Loading...</p>;

    return <div>Data: {data}</div>;
};
```

## Best Practices for Using Hooks

1. **Keep hooks at the top level:** Always call hooks at the top level of your React function. Don’t call hooks inside loops, conditions, or nested functions.

2. **Custom hook naming convention:** Start the name of your custom hooks with "use" to follow the convention and let React know that this function follows the rules of hooks.

3. **Avoid overusing hooks:** While hooks are powerful, overusing them or using them unnecessarily can make your code complex. Use hooks when they simplify your code or add value.

4. **Encapsulate logic:** Use custom hooks to encapsulate and reuse logic. This makes your components cleaner and more maintainable.

5. **Dependency arrays:** When using `useEffect`, `useMemo`, or `useCallback`, always specify dependencies correctly to avoid unexpected behaviors or performance issues.

## Summary

In the VisionsTrust app, hooks are essential for managing state and lifecycle methods in function components. By understanding and utilizing hooks such as `useState`, `useEffect`, and custom hooks, you can build more maintainable and scalable React applications. Always follow best practices to ensure your hooks are used correctly and effectively.

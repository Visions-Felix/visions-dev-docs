# Commenting Guide

Comments play a crucial role in making code more understandable and maintainable. They provide context and explanations for complex logic, helping current and future developers comprehend the codebase. This guide outlines best practices for adding comments to your code, with a focus on using JSDoc for documentation.

## General Principles

1. **Use JSDoc:** When possible, use JSDoc to provide structured documentation for your code.
2. **Be Descriptive:** Ensure comments are clear and descriptive, explaining the "why" behind the code, not just the "what."
3. **Keep Comments Updated:** Always update comments to reflect any changes in the code.
4. **Don't Comment Just To Comment:** Be smart about whether or not something needs commenting. Sometimes a good function, component or variable name is more than enough.

## Comments for Components

For React components, add comments especially when the component is complex or involves intricate logic.

### Example

```tsx
/**
 * UserProfile component displays the user's profile information.
 *
 * @component
 * @example
 * const user = {
 *   name: 'John Doe',
 *   age: 30,
 *   email: 'john.doe@example.com'
 * }
 * return <UserProfile user={user} />
 */
const UserProfile = ({ user }: { user: User }) => {
  // Display user's profile information
  return (
    <div>
      <h1>{user.name}</h1>
      <p>Age: {user.age}</p>
      <p>Email: {user.email}</p>
    </div>
  );
};
```

## Comments for Hooks

For custom hooks, document the props (if any) and the methods returned by the hook. Define a TypeScript type for the return value and use JSDoc to document the type.

### Example

```tsx
/**
 * Return type for useAuth hook, containing the authentication state and methods.
 */
type UseAuthReturnType = {
  /**
   * Indicates if the user is authenticated.
   */
  isAuthenticated: boolean;

  /**
   * Function to log in the user.
   *
   * @param {User} userInfo - The user's information.
   */
  login: (userInfo: User) => void;

  /**
   * Function to log out the user.
   */
  logout: () => void;

  /**
   * The authenticated user's information.
   */
  user: User | null;
};

/**
 * useAuth is a custom hook that manages authentication state.
 *
 * @returns {UseAuthReturnType} The authentication state and methods.
 *
 * @example
 * const { isAuthenticated, login, logout, user } = useAuth();
 */
const useAuth = (): UseAuthReturnType => {
  const [isAuthenticated, setIsAuthenticated] = useState(false);
  const [user, setUser] = useState<User | null>(null);

  const login = (userInfo: User) => {
    setIsAuthenticated(true);
    setUser(userInfo);
  };

  const logout = () => {
    setIsAuthenticated(false);
    setUser(null);
  };

  return { isAuthenticated, login, logout, user };
};
```

## Comments for Providers

For context providers, document everything the context provides, the methods used within it, and add comments detailing the functionality for complex logic. Define a TypeScript type for the context value and use JSDoc to document the type.

### Example

```tsx
/**
 * Context value type for AuthProvider, providing authentication state and methods.
 */
type AuthContextType = {
  /**
   * Indicates if the user is authenticated.
   */
  isAuthenticated: boolean;

  /**
   * Function to log in the user.
   *
   * @param {User} userInfo - The user's information.
   */
  login: (userInfo: User) => void;

  /**
   * Function to log out the user.
   */
  logout: () => void;

  /**
   * The authenticated user's information.
   */
  user: User | null;
};

const AuthContext = createContext<AuthContextType | undefined>(undefined);

/**
 * AuthProvider component that provides authentication state and methods.
 *
 * @example
 * <AuthProvider>
 *   <App />
 * </AuthProvider>
 */
const AuthProvider = ({ children }: { children: React.ReactNode }): JSX.Element => {
  const [isAuthenticated, setIsAuthenticated] = useState(false);
  const [user, setUser] = useState<User | null>(null);

  /**
   * Logs in the user and updates the authentication state.
   *
   * @param {User} userInfo - The user's information.
   */
  const login = (userInfo: User) => {
    setIsAuthenticated(true);
    setUser(userInfo);
  };

  /**
   * Logs out the user and clears the authentication state.
   */
  const logout = () => {
    setIsAuthenticated(false);
    setUser(null);
  };

  return (
    <AuthContext.Provider value={{ isAuthenticated, login, logout, user }}>
      {children}
    </AuthContext.Provider>
  );
};
```

### Complex Logic Example

```tsx
/**
 * Context value type for DataProvider, providing fetched data and loading state.
 */
type DataContextType = {
  /**
   * The fetched data.
   */
  data: any[];

  /**
   * Indicates if data is currently being loaded.
   */
  isLoading: boolean;
};

const DataContext = createContext<DataContextType | undefined>(undefined);

type Props = {
    /**
     * Defines whether or not to activate this provider on page load (example definition)
     */
    active: string;
}

/**
 * DataProvider component that fetches and provides data to its children.
 *
 * @example
 * <DataProvider>
 *   <App />
 * </DataProvider>
 */
const DataProvider = (props: PropsWithChildren<Props>): JSX.Element => {
  const [data, setData] = useState<any[]>([]);
  const [isLoading, setIsLoading] = useState(true);

  useEffect(() => {
    /**
     * Fetches data from the API.
     *
     * @async
     * @function fetchData
     * @returns {Promise<void>}
     */
    const fetchData = async () => {
      try {
        const response = await fetch('/api/data');
        const result = await response.json();
        setData(result);
        setIsLoading(false);
      } catch (error) {
        console.error('Failed to fetch data:', error);
        setIsLoading(false);
      }
    };

    fetchData();
  }, []);

  return (
    <DataContext.Provider value={{ data, isLoading }}>
      {children}
    </DataContext.Provider>
  );
};
```

## Summary

- **Components:** Add comments for complex components using JSDoc to document props and provide examples.
- **Hooks:** Use JSDoc to document the props, methods, and returned values of custom hooks. Define and document a TypeScript type for the return value.
- **Providers:** Thoroughly document everything the context provides, methods within the provider, and add comments for complex logic. Define and document a TypeScript type for the context value.

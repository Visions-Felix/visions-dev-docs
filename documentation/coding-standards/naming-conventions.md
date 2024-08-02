# General Coding Standards Guide

Adhering to consistent coding standards across a codebase ensures readability, maintainability, and collaboration efficiency. This guide outlines best practices for naming things, functions, files, and variables.

## Naming Conventions

### General Principles

1. **Be Descriptive:** Names should clearly describe what the item represents.
2. **Use Consistent Style:** Follow a consistent style for naming similar items.
3. **Avoid Abbreviations:** Use full words unless the abbreviation is well-known and widely accepted.

### Variables

1. **Use CamelCase for Variables:**
    - Example: `userName`, `totalAmount`
2. **Boolean Variables Should Start with 'is', 'has', or 'should':**
    - Example: `isActive`, `hasPermission`, `shouldUpdate`
3. **Avoid Single-letter Variable Names:**
    - Exception: Loop variables like `i`, `j`, `k`

```javascript
let userName = 'JohnDoe';
let isUserActive = true;
```

### Functions

1. **Use CamelCase for Function Names:**
    - Example: `calculateTotal`, `fetchUserData`
2. **Start Function Names with a Verb:**
    - Example: `getUser`, `setName`, `isValid`
3. **Use `handle` as a Prefix for Event Handlers:**
    - Example: `handleClick`, `handleSubmit`, `handleChange`
4. **Avoid Long Function Names:** Keep them concise yet descriptive.

```javascript
function calculateTotal(price, tax) {
    return price + tax;
}

function fetchUserData(userId) {
    // fetch data logic
}

function handleClick(event) {
    // handle click event logic
}
```

### Classes and Interfaces

1. **Use PascalCase for Class and Interface Names:**
    - Example: `UserManager`, `HttpClient`
2. **Use Nouns for Class Names:** Class names should represent objects or concepts.
    - Example: `User`, `Invoice`
3. **Prefix Interfaces with 'I':**
    - Example: `IUser`, `IInvoice`

```typescript
class UserManager {
    constructor() {
        // initialization logic
    }
}

interface IUser {
    id: number;
    name: string;
}
```

### Constants

1. **Use UPPER_CASE for Constants:**
    - Example: `MAX_RETRIES`, `DEFAULT_TIMEOUT`
2. **Separate Words with Underscores:**
    - Example: `API_BASE_URL`

```javascript
const MAX_RETRIES = 5;
const API_BASE_URL = 'https://api.example.com';
```

### Files

1. **React Component Files:** Use PascalCase format for file names.

    - Example: `UserProfile.tsx`, `InvoiceDetails.tsx`

2. **SCSS Module Files:** Use PascalCase format, matching the corresponding React component name with `.module.scss` suffix.

    - Example: `UserProfile.module.scss`, `InvoiceDetails.module.scss`

3. **Other Scripts:** Use camelCase format for file names.
    - Example: `userService.js`, `authMiddleware.ts`

```bash
# Correct
UserProfile.tsx
UserProfile.module.scss
invoiceDetails.tsx
invoiceDetails.module.scss
userService.ts
authMiddleware.ts

# Incorrect
user-profile.tsx
user-profile.module.scss
invoice-details.tsx
invoice-details.module.scss
UserService.ts
AuthMiddleware.ts
```

### Naming Conventions for Specific Scenarios

1. **Event Handlers:** Use 'handle' as a prefix for the function names responding to events.
    - Example: `handleClick`, `handleUserLogin`
2. **Props Passing Event Handlers:** Use 'on' as a prefix.
    - Example: `onClick`, `onUserLogin`
3. **Test Files:** Mirror the file name of the tested module and suffix with `.test`.
    - Example: `user-manager.test.ts`
4. **Configuration Files:** Use descriptive names indicating their purpose.
    - Example: `webpack.config.js`, `tsconfig.json`

```javascript
function handleClickButton() {
    // event handling logic
}
```

## Best Practices

1. **Consistency Over Preference:** Stick to the established conventions even if personal preferences differ.
2. **Refactor for Clarity:** Rename variables, functions, or files if a better name becomes apparent.
3. **Review and Enforce Standards:** Regularly review code and ensure adherence to naming conventions.

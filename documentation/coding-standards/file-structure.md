# File Structure Guide

Maintaining a well-organized file structure is crucial for the scalability and maintainability of a project. Below is the guide to the file structure used in our project, detailing the purpose and conventions for each directory.

## Root Directory: `src/`

The `src/` directory is the root directory for all source code and assets of the project.

### 1. **assets/**

Contains static assets such as fonts, images, and videos.

- **fonts/**: Custom fonts used in the project.
- **img/**: Image files used throughout the application.
- **videos/**: Video files used in the application.

### 2. **components/**

Contains all React components organized by their atomic design principles.

- **Atoms/**: Basic, indivisible components (e.g., buttons, inputs).
- **Molecules/**: Compound components built from atoms (e.g., form groups, cards).
- **Organisms/**: Complex components built from atoms and molecules (e.g., headers, footers).

### 3. **constants/**

Contains files that define shared constants used across the application. This could include things like API endpoints, configuration values, and other static values.

### 4. **context/**

Contains context providers for React Context API, facilitating state management and sharing state across different parts of the application.

### 5. **data/**

Contains files that store fixed data not stored in a database. This could include static JSON data, mock data for development, or other non-dynamic data sources.

### 6. **hooks/**

Contains custom React hooks used in the application. These are reusable pieces of logic that encapsulate common behaviors and state management.

### 7. **layouts/**

Contains components used as layouts. These components define the structure of pages and can include headers, footers, and other layout elements.

### 8. **libs/**

Contains modules and libraries on certain subjects. This could include third-party integrations, utility libraries, and other modular code that can be reused across the application.

### 9. **pages/**

Contains components that represent a full page in the application. These are the top-level components that correspond to routes in the application.

### 10. **shared/**

Contains shared content such as SCSS stylesheets, variables, mixins, and other styling resources that are used across multiple components.

### 11. **types/**

Contains custom TypeScript types used throughout the project. This helps in maintaining type safety and consistency.

### 12. **utils/**

Contains utility function files. These are helper functions that perform common tasks and operations used across the application that are not directly React-related.

## Example File Structure

Here is an example of how the file structure might look in practice:

```bash
src/
├── assets/
│   ├── fonts/
│   │   └── custom-font.woff
│   ├── img/
│   │   └── logo.png
│   └── videos/
│       └── intro.mp4
├── components/
│   ├── Atoms/
│   │   └── Button.tsx
│   ├── Molecules/
│   │   └── Card.tsx
│   └── Organisms/
│       └── Header.tsx
├── constants/
│   └── appBreakpoints.ts
├── context/
│   └── AuthProvider.tsx
├── data/
│   └── countries.json
├── hooks/
│   └── useAuth.ts
├── layouts/
│   └── MainLayout.tsx
├── libs/
│   └── analytics.ts
├── pages/
│   └── HomePage.tsx
├── shared/
│   ├── styles/
│   │   ├── variables.scss
│   │   └── mixins.scss
│   └── components/
│       └── SharedButton.module.scss
├── types/
│   └── index.ts
└── utils/
    └── formatDate.ts
```

## The `api` directory

The `api` directory contains everything that is needed to perform API operations with as much re-usability as possible.

Since the project uses an APIClient that is required by our application in order to centralize API calls and centrally handle error scenarios, we need the API calls to be encapsulated in React hooks that would be used in children of an ClientProvider.

### File structure

The file structure for the `api` directory is organized by resource available on the API.

We group hooks and utilitaries together instead of placing them directly in a separate hooks or utils directory to avoid having files that work on the same resource in different locations of the application.

The following is an example for using the `projects` resource.

```bash
src/
└── api/
    └── projects/
        └── projectsMethods.ts
        └── useProjectsAPI.tsx
        └── useProjectsQuery.tsx
```

#### `useProjectsAPI.tsx`
The first file `useProjectsAPI.tsx` contains all of the API calls wrapped around the client provided by the ClientProvider. 

This enables any react component that is a child of the ClientProvider to use this api call.

> *Note: In practice, we are currently using tanstack-query, so the APIs from this file are rarely used directly by components. Continue reading to understand why in the `useProjectsQuery.tsx` section.*

#### `useProjectsQuery.tsx`
This file is where all the tanstack-query queries are defined for the `projects` resource.
It consumes the APIs provided by `useProjectsAPI.tsx` in order to use them as the queryFn of a useQuery.

## Best Practices

1. **Modularity:** Keep components and modules small and focused. Each file should have a single responsibility.
2. **Reusability:** Organize files to promote reuse. Shared components, hooks, and utilities should be easily accessible.
3. **Scalability:** As the project grows, the file structure should accommodate new files and directories without major refactoring.
4. **Consistency:** Follow consistent naming conventions and directory structures throughout the project.

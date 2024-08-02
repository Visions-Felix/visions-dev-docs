# Branch Naming Guide

Consistent and descriptive branch naming conventions help streamline collaboration and make it easier to understand the purpose and scope of each branch at a glance. Follow these conventions to maintain a clean and organized Git repository.

## General Conventions

1. **Use Lowercase and Hyphen-Separated Names:**

    - Stick to lowercase letters and use hyphens (`-`) to separate words.
    - Avoid using underscores (`_`), camel case, or any non-alphanumeric character.

2. **Include a Prefix for Context:**
    - Prefixes help to quickly identify the purpose of a branch.

## Prefix Categories

### Feature Branches

Use for new features or enhancements.

Format: `feature/brief-description`

Examples:

-   `feature/add-user-authentication`
-   `feature/update-dashboard-ui`

### Bug Fix Branches

Use for bug fixes.

Format: `bugfix/brief-description`

Examples:

-   `bugfix/fix-login-issue`
-   `bugfix/correct-header-styling`

### Hotfix Branches

Use for urgent fixes in the production environment.

Format: `hotfix/brief-description`

Examples:

-   `hotfix/patch-security-vulnerability`
-   `hotfix/resolve-payment-error`

### Release Branches

Use for preparing a new production release.

Format: `release/version-number`

Examples:

-   `release/1.2.0`
-   `release/2.0.1`

### Chore Branches

Use for routine tasks and maintenance that do not affect the product's functionality (e.g., updating dependencies, refactoring code).

Format: `chore/brief-description`

Examples:

-   `chore/update-dependencies`
-   `chore/refactor-user-service`

### Documentation Branches

Use for documentation updates and changes.

Format: `docs/brief-description`

Examples:

-   `docs/update-readme`
-   `docs/add-api-documentation`

## Examples and Best Practices

1. **Be Descriptive but Concise:**
    - Clearly describe the branch's purpose in a few words.
    - Avoid overly long names.
2. **Use Consistent Tense and Style:**
    - Maintain a uniform style throughout the branch names.
    - Typically use imperative mood (e.g., `add`, `fix`, `update`).
3. **Avoid Using Personal Names:**
    - Do not include personal names or identifiers in branch names.

### Example Workflow

1. **Creating a New Feature:**
    - Branch name: `feature/add-comment-section`
2. **Fixing a Bug:**
    - Branch name: `bugfix/fix-404-error`
3. **Making an Urgent Fix:**
    - Branch name: `hotfix/repair-crash-on-login`
4. **Preparing for a Release:**
    - Branch name: `release/1.3.0`
5. **Updating Documentation:**
    - Branch name: `docs/add-setup-guide`

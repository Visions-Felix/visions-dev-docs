# Conventional Commits Guide

Using Conventional Commits provides a standard way to structure commit messages, making it easier to read and understand the history of changes in a project. This guide outlines the rules for writing commit messages according to the Conventional Commits specification.

## Commit Message Format

A commit message consists of a **header**, **optional body**, and **optional footer**. The header is mandatory and must conform to the format below:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Header

The header is mandatory and includes:

- **type**: A keyword indicating the type of change (see below for types).
- **optional scope**: A noun describing a section of the codebase enclosed in parentheses, e.g., `(parser)`, `(login)`. This is optional.
- **description**: A brief description of the change in present tense, not capitalized, and no period at the end.

### Body

The body is optional and should include additional information about the commit. Use it to explain the motivation for the change and contrast it with previous behavior.

### Footer

The footer is optional and can include information about breaking changes and issues that the commit closes. Breaking changes must start with `BREAKING CHANGE:` followed by an explanation.

## Types

### Commonly Used Types

- **feat**: A new feature.
- **fix**: A bug fix.
- **docs**: Documentation-only changes.
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
- **refactor**: A code change that neither fixes a bug nor adds a feature.
- **perf**: A code change that improves performance.
- **test**: Adding missing or correcting existing tests.
- **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm).
- **ci**: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs).
- **chore**: Other changes that don't modify src or test files.
- **revert**: Reverts a previous commit.

## Examples

### Feature Commit

```
feat(parser): add ability to parse arrays

Add support for parsing arrays. This change introduces a new method
to the parser module that allows it to handle arrays in input data.
```

### Bug Fix Commit

```
fix(login): resolve login issue on iOS devices

Fixed a bug that caused the login process to fail on iOS devices due
to incorrect handling of touch events.
```

### Documentation Commit

```
docs: update API usage section in README

Clarified the usage of the API with examples and detailed parameter descriptions.
```

### Breaking Change Commit

```
feat(auth): update authentication method

BREAKING CHANGE: The authentication method has been updated to use JWT tokens
instead of session-based authentication. This requires all clients to update
their authentication logic.
```

### Commit Closing an Issue

```
fix(router): handle unknown routes properly

Ensure that unknown routes return a 404 status code and render the NotFound component.

Closes #123.
```

## Best Practices

1. **Be Consistent**: Always follow the Conventional Commits format to ensure a consistent and understandable commit history.
2. **Use the Right Type**: Choose the appropriate type for your commit to clearly convey the nature of the change.
3. **Write Clear Descriptions**: Make your descriptions concise yet informative. Use the body to provide additional context if needed.
4. **Reference Issues**: When applicable, reference issues in the footer to provide traceability.

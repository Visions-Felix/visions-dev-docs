# Pull Request Guide

Pull requests (PRs) are essential for code review, ensuring code quality, and facilitating collaboration among team members. This guide outlines the best practices and process for creating, submitting, and reviewing pull requests.

## Creating a Pull Request

### 1. Branching

Before starting work on a new feature or bug fix, create a new branch from the `dev` branch. Follow the [branch naming conventions](./branch-naming.md).

### 2. Commit Messages

Ensure your commit messages follow the [Conventional Commits](./conventional-commits.md) format. This provides a clear and understandable history of changes.

### 3. Write Clear and Concise Description

When creating a pull request, provide a clear and concise description. Include the following:

- **What**: A brief summary of what the PR does.
- **Why**: The reason for the change, including any relevant context.
- **How**: A brief description of how the changes were made.
- **Testing**: Details of how the changes were tested.

### 4. Reference Issues

If your pull request addresses or closes an issue, reference it in the description. This provides traceability and context for reviewers.

```
Closes #123
```

### 5. Request Reviewers

Assign relevant team members as reviewers who have the expertise or context to review the changes effectively.

### 6. Include Screenshots/Logs

If applicable, include screenshots or logs to provide additional context, especially for UI changes or bugs that are visually identifiable.

## Submitting a Pull Request

### 1. Ensure Code Completeness

Before submitting a PR, ensure that your code is complete, functional, and meets the project's requirements. Do not submit PRs with unfinished code.

### 2. Run Tests

Run all relevant tests locally to ensure that your changes do not introduce any new issues. Include new tests if your changes introduce new functionality or fix bugs.

### 3. Linting and Formatting

Ensure that your code follows the project's coding standards and style guidelines. Run any linters or formatters to clean up your code.

## Reviewing a Pull Request

### 1. Understand the Context

Before reviewing, understand the context of the changes by reading the description, related issues, and any linked documentation.

### 2. Review Code Thoroughly

- **Correctness**: Verify that the code functions as expected and does not introduce bugs.
- **Readability**: Ensure the code is readable and follows the project's style guidelines.
- **Design**: Assess the design and structure of the code for maintainability and scalability.
- **Testing**: Check that adequate tests are included and that they pass.

### 3. Provide Constructive Feedback

- **Be Specific**: Point out specific lines or sections of code with suggestions for improvements.
- **Be Respectful**: Provide feedback respectfully and constructively.
- **Ask Questions**: If something is unclear, ask questions to understand the changes better.

### 4. Approve or Request Changes

After reviewing, either approve the PR or request changes. If requesting changes, provide clear instructions on what needs to be addressed.

### 5. Re-Review if Necessary

If changes are made after your review, re-review the updated code to ensure that all issues have been addressed.

## Merging a Pull Request

### 1. Verify Approvals

Ensure that the PR has received the necessary approvals from the required reviewers.

### 2. Resolve Conflicts

If there are merge conflicts, resolve them before merging the PR. Ensure that the resolved code is still functional and passes all tests.

### 3. Squash Commits

If applicable, squash commits to clean up the commit history. This is particularly useful for PRs with many small commits.

### 4. Merge Strategy

Use the appropriate merge strategy (merge, squash, rebase) based on the project's guidelines.

### 5. Post-Merge Actions

- **Close Related Issues**: Ensure that any related issues are closed.
- **Notify Stakeholders**: Notify relevant team members or stakeholders about the merged changes if necessary.

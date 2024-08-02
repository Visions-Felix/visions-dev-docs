# Version Management Guide

Version management is crucial for maintaining a clear and organized development process, ensuring that changes are tracked accurately and that releases are well-documented. This guide outlines best practices for updating software versions, including when and how to update versions, and the process to follow.

## Semantic Versioning

We follow [Semantic Versioning](https://semver.org/) (SemVer) for our versioning strategy. Semantic Versioning uses a three-part version number: `MAJOR.MINOR.PATCH`.

-   **MAJOR** version when you make incompatible API changes.
-   **MINOR** version when you add functionality in a backwards-compatible manner.
-   **PATCH** version when you make backwards-compatible bug fixes.

## When to Update the Version

### Major Version (MAJOR)

Update the major version when there are significant changes that break backward compatibility. Examples include:

-   Removing or renaming public APIs.
-   Significant changes in functionality that require users to modify their code to accommodate the changes.

### Minor Version (MINOR)

Update the minor version when new features are added in a backward-compatible manner. Examples include:

-   Adding new functionalities that do not break existing APIs.
-   Deprecating existing features without removing them.

### Patch Version (PATCH)

Update the patch version for backward-compatible bug fixes. Examples include:

-   Fixing bugs.
-   Minor performance improvements.

## Version Update Process

### Feature Branches

1. **Do Not Update Version Numbers:**
    - Version numbers should not be updated directly within feature branches. This avoids conflicts and ensures a smooth integration process.

### Pull Requests

1. **Do Not Update Version Numbers in PRs:**
    - When submitting a pull request, do not include version number updates. Focus on implementing and testing the feature or fix.

### After Merging

1. **Update the Version Number:**
    - After merging a pull request into the `main` branch, the version number should be updated as part of the release process.

### Release Process

1. **Determine the Version Increment:**

    - Decide whether the changes require a major, minor, or patch version increment based on the guidelines above.

2. **Update the Version Number:**

    - Update the version number in the appropriate configuration files (package.json).
    - Ensure the version number follows the SemVer format.

3. **Commit the Version Update:**

    - Create a commit with a message that clearly indicates the version update. Example:
        ```
        chore: bump version to 1.2.0
        ```

4. **Tag the Commit:**

    - If applicable, Tag the commit with the new version number. Example:
        ```
        git tag -a v1.2.0 -m "Release version 1.2.0"
        ```

5. **Push the Tag:**

    - If applicable, Push the commit and tag to the repository.
        ```
        git push origin main --tags
        ```

6. **Create a Release:**
    - If applicable, create a release in the repository and include release notes that summarize the changes.

## Best Practices

1. **Automate Versioning:**
    - Use tools or scripts to automate the versioning process where possible. This reduces the risk of human error and ensures consistency.
2. **Consistent Release Notes:**
    - Maintain consistent and clear release notes that provide a summary of changes, including new features, bug fixes, and any breaking changes.
3. **Communicate Changes:**
    - Ensure that all stakeholders are aware of the version changes, especially for major versions that may require changes on their part.
4. **Testing Before Release:**
    - Thoroughly test the software before updating the version and creating a release. This includes automated tests, manual tests, and any other relevant testing processes.
5. **Continuous Integration:**
    - Integrate version management into the CI/CD pipeline to ensure that version updates are part of the deployment process.

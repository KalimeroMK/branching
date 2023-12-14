
# Project Git Workflow Guide

## Main Branches

### Master Branch
- **Purpose**: Represents the production-ready state.
- **Best Practices**: 
  - Only merge code that is thoroughly tested and stable.
  - Regularly update with developed features to keep production current.
- **Usage**:
  - Represents the "source of truth" for production code.
  - Used for deploying code to production environments.

### Develop Branch
- **Purpose**: Contains the latest development changes for the next release.
- **Best Practices**: 
  - Frequently commit and merge new features and fixes to keep it updated.
  - Regularly sync with the master branch to stay aligned with production.
- **Usage**:
  - Serves as a base for creating feature, bugfix, and hotfix branches.
  - Acts as a staging area for the next release.

#### Release Process
- **When to Release**: Once the `develop` branch is stable and ready.
- **Steps**:
  1. Merge `develop` into `master`.
  2. Tag the commit in `master` with a release number.
  3. Deploy from `master` to production.

## Supporting Branches

### Feature Branches
- **Purpose**: Develop new features independently.
- **Creation**: `git checkout -b feature/my-feat develop`.
- **Merging**: After completion, merge back into `develop`.
- **Best Practices**:
  - Keep the branch updated with `develop` to avoid conflicts.
  - Write unit tests for new features.
  - Review code before merging.

### Bugfix Branches
- **Purpose**: Address bugs in the current development state.
- **Creation**: `git checkout -b bugfix/my-issue develop`.
- **Merging**: Merge back into `develop` after fixing the issue.
- **Best Practices**:
  - Add regression tests to ensure the bug does not recur.
  - Keep the branch small and focused on a specific issue.

### Hotfix Branches
- **Purpose**: Quickly fix critical bugs in production.
- **Creation**: `git checkout -b hotfix/1.2.1 master`.
- **Merging**: Merge into both `master` and `develop`.
- **Process**:
  1. Bump version number (`./bump-version.sh 1.2.1`).
  2. Commit the changes.
  3. Merge into `master`, tag the release.
  4. Merge the changes back into `develop`.
- **Best Practices**:
  - Act quickly to resolve production issues.
  - Ensure minimal changes to fix the issue effectively.
```

####Ideal Commit Tree:

<p align="center">
  <img src="https://wac-cdn.atlassian.com/dam/jcr:34c86360-8dea-4be4-92f7-6597d4d5bfae/02%20Feature%20branches.svg?cdnVersion=69">
  <span>fig: Git Flow Commit Tree</span>
</p>

# Git Strategy for New Developers

Welcome to the MakerStudio development team! To ensure a smooth and consistent workflow, we follow a specific Git strategy. This guide will walk you through the process step-by-step. Let's get started!

## Branch Structure

We have two main branches:

1. **main**: This is our production branch. Only stable and approved code is merged here.
2. **development**: This is our main working branch. All new features, bug fixes, and other changes are first merged here.

### Feature Branches

When working on a new feature, bug fix, or documentation update, you will create a new branch off the `development` branch. These branches should follow specific naming conventions:

- **Feature**: `feat/your-feature-name`
- **Bug Fix**: `bug/your-bug-fix`
- **Documentation**: `docs/your-docs-update`
- **Other Fixes**: `fix/your-fix`
- **Code Refactoring**: `refactor/your-refactor`

## Workflow Steps

### 1. Clone the Repository

First, clone the repository to your local machine if you haven't already:

```bash
git clone https://github.com/MakerStudio-io/your-repo-name.git
cd your-repo-name
```

Replace `your-repo-name` with the actual name of the repository you are working on.

### 2. Create a New Branch

Always start by pulling the latest changes from the `development` branch:

```bash
git checkout development
git pull origin development
```

Create a new branch for your work from the `development` branch:

```bash
git checkout -b feat/your-feature-name development
```

Replace `feat/your-feature-name` with the appropriate prefix and name based on what you are working on.

### 3. Make Atomic Commits

An [atomic commit](https://www.aleksandrhovhannisyan.com/blog/atomic-git-commits/) means a single commit should only contain related changes. For example, if you are working on a new feature, each commit should be a logical step towards completing that feature.

Add and commit your changes:

```bash
git add .
git commit -m "Your descriptive commit message"
```

Refer to [this link](https://www.aleksandrhovhannisyan.com/blog/atomic-git-commits/) for more details if required.

### 4. Push Your Branch to the Repository

Push your new branch to the remote repository at the end of each day.

```bash
git push origin feat/your-feature-name
```

### 5. Create a Pull Request (PR)

Go to the repository on GitHub and create a new Pull Request from your branch to the `development` branch. Ensure your PR description is clear and provides context about the changes.

### 6. Review and Approval

Your PR will be reviewed by the assigned reviewer for your project. Address any feedback and make necessary changes. Once approved, your PR will be merged into the `development` branch.

**Important**: Changes should never be merged directly into the `development` or `main` branches. All changes must be made through a Pull Request (PR). Each PR needs to be reviewed and approved by the assigned reviewer before it is merged. This ensures that all code is properly reviewed and maintains the integrity of our codebase.

### 7. Merging Development to Main

Periodically, once all features and fixes in the `development` branch are tested and approved, the `development` branch will be merged into the `main` branch. This step is usually performed by a team lead or a designated developer:

```bash
git checkout main
git pull origin main
git merge development
git push origin main
```

## Rebasing and Squashing Commits

### Rebasing

If you need to incorporate changes from another branch into your current branch, use rebase instead of merge to maintain a clean history:

```bash
git checkout your-branch
git pull --rebase origin development
```

This will replay your changes on top of the latest `development` branch.

### Squashing Commits

If there are duplicate commits or too many small commits, squash them before merging. This can be done using interactive rebase:

```bash
git checkout your-branch
git rebase -i HEAD~n
```

Replace `n` with the number of commits you want to squash. Mark the commits you want to squash with `s` or `squash`.

## Summary of Commands

Here's a quick summary of the commands you will use:

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-repo-name.git
   cd your-repo-name
   ```

2. **Create a new branch:**

   ```bash
   git checkout development
   git pull origin development
   git checkout -b feat/your-feature-name
   ```

3. **Add and commit changes:**

   ```bash
   git add .
   git commit -m "Your descriptive commit message"
   ```

4. **Push your branch:**

   ```bash
   git push origin feat/your-feature-name
   ```

5. **Create a Pull Request on GitHub.**

6. **Rebase with the latest development branch:**

   ```bash
   git pull --rebase origin development
   ```

7. **Squash commits if necessary:**

   ```bash
   git rebase -i HEAD~n
   ```

8. **Merge development to main (for team leads):**

   ```bash
   git checkout main
   git pull origin main
   git merge development
   git push origin main
   ```

## Naming Conventions

- **Feature branches:** `feat/your-feature-name`
- **Bug fix branches:** `bug/your-bug-fix`
- **Documentation branches:** `docs/your-docs-update`
- **Other fixes:** `fix/your-fix`
- **Code refactoring:** `refactor/your-refactor`

## Best Practices

- **Keep commits atomic:** Ensure each commit is a small, logical change.
- **Write clear commit messages:** Describe what the commit does and why.
- **Stay updated:** Regularly pull changes from `development` to avoid conflicts.
- **Use rebase for incorporating changes:** Rebase instead of merge to maintain a clean history.
- **Squash commits if necessary:** Squash duplicate or small commits for a cleaner history.
- **Review and test thoroughly:** Ensure your changes are reviewed and approved before merging.

By following this strategy, we maintain a clean, organized, and efficient workflow. If you have any questions, feel free to ask your team lead. Happy coding!

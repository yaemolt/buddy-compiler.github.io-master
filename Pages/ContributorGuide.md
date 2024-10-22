---
layout: default
title: Contributor Guide
nav_order: 3
---

# Contributor Guide

If you wish to contribute a new feature or a bug fix, please follow the workflow explained in this document.

## Table of Content

- [Prerequisites](#prerequisites)
- [Getting Started for New Contributors](#getting-started-for-new-contributors)
- [Pull Requests](#pull-requests)
- [Submitting a Pull Request](#submitting-a-pull-request-)
- [Submitting an Issue/Feature Request](#submitting-an-issuefeature-request-)
- [Contributor Guidelines](#contributor-guidelines-)
- [Troubleshooting and Help](#troubleshooting-and-help)
- [Additional Information for Beginners](#additional-information-for-beginners)

## Prerequisites

- Experience with `git` command line basics.
- Familiarity with build toolset and development environment of your choice.

If you are new to Git or any of these tools, don't worry! We have provided a beginner's guide below to help you get started.

## Getting Started for New Contributors

### Step 1: Fork the Repository

To begin contributing, you need to create a copy of the project, known as "forking". Forking allows you to make changes without affecting the original project.

- Click the "Fork" button at the top right of the project page.

### Step 2: Clone the Project to Your Local Machine

Once you have forked the repository, you need to clone it to your local machine to start making changes.

```bash
git clone https://github.com/your-username/project-name.git
```

### Step 3: Create a New Branch

It is recommended to create a new branch for your changes. This keeps the `main` branch clean and helps organize your contributions.

```bash
git checkout -b my-feature-branch
```

### Step 4: Make Changes

Now, you can make changes to the code. After making your changes, add them to your branch.

```bash
git add .
git commit -m "Describe your changes here"
```

### Step 5: Push Changes to GitHub

After committing your changes, push them to your forked repository on GitHub.

```bash
git push origin my-feature-branch
```

### Step 6: Create a Pull Request

Go to your forked repository on GitHub. Click "Compare & pull request" to propose your changes to the main project. Fill out the description with details about your changes.

## Pull Requests

- **DO** base your work against the `main` branch.
- **DO** submit all major changes to code via pull requests (PRs) rather than through
  a direct commit. Contributors with commit access may submit trivial patches or changes to the project
  infrastructure configuration via direct commits (CAUTION!)
- **DO NOT** mix independent, unrelated changes in one PR.
  Separate unrelated fixes into separate PRs, especially if they are in different components of the project.
- **DO** give PRs short-but-descriptive names (e.g. "[subsection_tag] Add test for algorithm XXX", 
  not "Fix #1234").
- **DO** name your PR in a meaningful manner and start with a relevant tag for the targeted 
  subsection of the project (Ex. [DIP] Develop support for Fast Fourier Transform, [DIP] replace 
  C-style variadic function with std::vector, etc.). 
- **DO** provide a description summarising the proposed changes in your PR. This is a good place to 
  cite related issues and other PRs in context of your work as well. 
- **DO** [refer](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/autolinked-references-and-urls) to any 
  relevant issues, and include the [keywords](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue) 
  that automatically close issues when the PR is merged.
- **DO** [mention](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#mentioning-people-and-teams) 
  any users that should know about and/or review the change.
- **DO** ensure any new features or changes to existing behaviours are covered with test cases.
- **DO** address PR feedback in an additional commit(s) rather than amending the existing commits.
  This makes it easier for reviewers to track changes.
- **DO** assume that the [Squash and Merge] will be used to merge your commit unless you
  request otherwise in the PR.

### Merging Pull Requests (for maintainers with write access)

- **DO** use [Squash and Merge] by default for individual contributions unless requested
  by the PR author. Do so, even if the PR contains only one commit. It creates a simpler
  history than [Create a Merge Commit]. Reasons that PR authors may request the true
  merge recording a merge commit may include (but are not limited to):
  - The change is easier to understand as a series of focused commits.
    Each commit in the series must be buildable so as not to break git bisect.

## Submitting a Pull Request : 

1. Follow [Forking Projects](https://docs.github.com/en/get-started/quickstart/contributing-to-projects) guide to get personal copy of 
   [buddy-mlir](https://github.com/buddy-compiler/buddy-mlir) repository from where you will be able to submit new contributions as 
   [pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

2. Clone your fork in your local system.

3. Create a new branch based on `main` and start working on your code inside this branch. Relevant git commands are : 

   ```shell
   git branch foo
   git checkout foo
   ```

4. Follow the [Getting started](#getting-started-with-git-workflow) workflow to set up the project on your system.

5. Make changes in your branch and push them to the upstream copy of your fork. Relevant git commands are : 

   ```shell
   git add .
   git commit -m "Add feature foo1"
   git push origin
   ```

6. You should update your local pull request branch with upstream main branch and your local llvm submodule with upstream specified llvm submodule before
   submitting a Pull request. Relevant git commands are : 

   ```shell
   cd buddy-mlir
   git pull https://github.com/buddy-compiler/buddy-mlir.git main
   git submodule update --init --recursive
   ```
    And then build llvm and buddy-mlir to make sure your commits are based on the latest buddy-mlir.

    Note : You should build your changes against updated `buddy-mlir` and `llvm` submodule before opening a PR (Pull Request).

7. Follow [this](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)
   for opening a pull request using GitHub GUI.

## Submitting an Issue/Feature Request

If you encounter a bug or have an idea for a new feature, please submit an issue:

1. Go to the repository's "Issues" tab.
2. Click "New issue".
3. Describe the issue or feature request, including as much relevant detail as possible.

We welcome relevant and descriptive issues/feature requests for this project. Deafault templates are provided for creating both of them. Although it is recommended to use provided templates while creating an issue/feature request, it is not a compulsion and you can choose not to use them. Please ensure that your request/issue is self-explanable and provides sufficient technical info in latter case.

## Contributor Guidelines

- **Code Style**: Follow the coding style used in the project. Consistent style helps readability and maintainability.
- **Testing**: Make sure that your changes are thoroughly tested. If you're fixing a bug, add a test that ensures the bug is fixed.
- **Documentation**: Update the documentation to reflect your changes, including comments in the code and any relevant Markdown files.

- Name files in a meaningful way.
- Put copyright and license information in every relevant file.
- All non-public definitions should reside in scope enclosed by `namespace detail {...}`.
- Use the provided `clang-format` file for applying appropriate formatting.
- It is advisable to apply `clang-format` in a separate commit after making changes to the code.
- Indent with 2 spaces while using a new line.
- Remove any trailing whitespace at the end of each line.
- Leave one single blank line at the end of each file.
- Group variable declaration(s) and loops separately in files containing code.
- Leave space after commas in .mlir files.
- Leave space before and after '->', ':' and '=' in .mlir files.

## Troubleshooting and Help

### Git Configuration Issues

If you encounter issues with Git configuration, please refer to the [Git Configuration Help Document](https://example.com/git-config-help).

### Common Problems

- **Pull Request Not Reviewed**: If your Pull Request has not been reviewed in a few days, feel free to leave a polite comment to remind the maintainers.
- **Authentication Errors**: Ensure that your Git credentials are correctly set up. You can follow this [GitHub Authentication Guide](https://example.com/github-auth-guide) for more help.

### More Resources

- [GitHub Beginner's Guide](https://example.com/github-guide)
- [Markdown Basics](https://example.com/markdown-intro)

## Additional Information for Beginners

### Introduction to Key Terms

- **Fork**: Creating your own copy of a repository, which allows you to make changes independently from the original project.
- **Branch**: A separate line of development in your Git repository. Creating a new branch allows you to work on features without affecting the main project.
- **Pull Request (PR)**: A request to merge your changes from your fork or branch into the main project repository.

### Step-by-Step Guide with Examples

If you are not familiar with the steps provided above, here is a more detailed guide with additional resources:

1. **Forking the Repository**: Forking allows you to create a copy of the project under your GitHub account. This way, you can work on it without impacting the original repository.
   - [GitHub Guide to Forking](https://example.com/github-fork-guide)

2. **Cloning Your Fork**: Cloning brings the repository to your local machine, so you can work on it directly from your computer.
   - Example command:
   ```bash
   git clone https://github.com/your-username/project-name.git
   ```

3. **Creating a New Branch**: Always create a branch to organize your work. For example:
   ```bash
   git checkout -b new-feature-branch
   ```
   This ensures the `main` branch stays clean and only contains stable code.

4. **Making Your Changes**: Edit the code or documentation. Once you're happy with your changes, you need to save and commit them.
   ```bash
   git add .
   git commit -m "Added a new feature to improve user experience"
   ```

5. **Pushing Your Changes**: Push your branch to GitHub so that it can be merged later.
   ```bash
   git push origin new-feature-branch
   ```

6. **Creating a Pull Request**: A Pull Request allows maintainers to review your changes. Describe your changes clearly and explain why they are beneficial.
   - [How to Create a Pull Request](https://example.com/github-pull-request-guide)

### Helpful Tips for Beginners

- **Stay Updated**: Always keep your fork in sync with the original repository by pulling the latest changes.
- **Ask Questions**: If you are unsure about something, feel free to ask in the comments section of an issue or pull request.
- **Learn by Doing**: Don't hesitate to make contributions, even if they are small. Updating documentation or fixing minor bugs is a great way to start.

Thank you for contributing! Every contribution helps improve the project for everyone.

# GitHub Documentation Workflow Guide

## Overview

This guide explains how to create, manage, review, and publish documentation changes using GitHub's web interface.

It is designed for technical writers who are new to GitHub and need to understand not only which steps to follow, but why each step is part of the documentation workflow.

The guide covers:

- Understanding repositories, branches, files, and commits
- Creating a branch for documentation changes
- Creating and editing Markdown files
- Writing useful commit messages
- Understanding the difference between committing and publishing changes
- Creating and reviewing pull requests
- Merging documentation changes into the main branch
- Cleaning up branches after a merge
- Understanding Ahead and Behind indicators
- Recovering from common mistakes

---

## Understanding the GitHub Structure

Before making changes in GitHub, it is important to understand how the major components relate to one another.

A simplified GitHub project can be thought of as:

    GitHub account
        ↓
    Repository
        ↓
    Branch
        ↓
    Files
        ↓
    Commits

### Repository

A **repository**, often called a **repo**, is the container for an entire project.

A repository can contain:

- Documentation files
- Folders
- Images
- Source code
- Project configuration files
- The history of changes made to those files

For a documentation project, think of the repository as the project's main workspace.

For example:

`github-documentation-workflow`

is a repository containing the files associated with this documentation project.

> **Important:** A repository and a branch are not the same thing. A repository contains the project. Branches exist inside the repository.

---

### Branch

A **branch** is an independent line of work within a repository.

Most repositories have a primary branch named:

`main`

The `main` branch generally represents the current accepted version of the project.

Instead of making every change directly to `main`, a writer can create a separate branch for a specific documentation change.

For example:

`develop-workflow-guide`

This branch can be used to create and revise the guide without immediately changing the version stored on `main`.

The relationship looks like this:

    Repository: github-documentation-workflow
    │
    ├── main
    │
    └── develop-workflow-guide

When `develop-workflow-guide` was first created from `main`, both branches contained the same files and history.

Changes made afterward on `develop-workflow-guide` remain on that branch until they are merged into `main`.

### Why Use a Branch?

Branches allow documentation changes to be developed separately from the accepted version of the project.

This provides an opportunity to:

- Make multiple related changes
- Review work before publishing it
- Compare proposed changes with the current version
- Collaborate with reviewers
- Correct mistakes without immediately changing `main`
- Maintain a record of how a documentation change was developed

In a professional documentation environment, this workflow can allow writers, developers, subject matter experts, and reviewers to collaborate on proposed changes before they become part of the main project.

---

## Repository vs. Branch

One of the easiest concepts to confuse when learning GitHub is the difference between creating a new repository and creating a new branch.

Use a **new repository** when the work represents a separate project.

Use a **new branch** when the work represents a change to an existing project.

For example:

| Goal | Appropriate Action |
| --- | --- |
| Create a separate GitHub workflow documentation project | Create a new repository |
| Add a new guide to that project | Create a branch in the existing repository |
| Revise an existing procedure | Create a branch |
| Start an unrelated portfolio project | Create a new repository |

A useful way to remember the distinction is:

> **Repository = What project am I working on?**  
> **Branch = What change am I making to that project?**

---

## Check Your Location Before Making Changes

Before creating or editing a file, verify both the **repository** and **branch**.

This prevents changes from accidentally being made in the wrong project.

At the top of the repository page, confirm the repository name.

Then check the branch selector above the file list.

For example:

**Repository:** `github-documentation-workflow`

**Branch:** `develop-workflow-guide`

If either value is incorrect, navigate to the correct repository or switch branches before making the change.

> **Tip:** Make checking the repository and branch part of your normal workflow before creating, editing, or deleting anything.

---

## Creating a Branch for Documentation Work

Before making documentation changes, create a branch from `main` when the work should be reviewed before becoming part of the accepted project.

### Before Creating the Branch

Verify that you are:

1. In the correct repository.
2. On the `main` branch.
3. Starting from the current version of the project.

Creating a branch from `main` establishes the current state of `main` as the starting point for the new work.

### Create a Branch in the GitHub Web Interface

1. Open the repository.
2. Locate the branch selector above the file list. It typically displays `main`.
3. Select the branch selector.
4. Enter a descriptive name for the new branch.
5. Select the option to create the branch from `main`.

For example:

`develop-workflow-guide`

After the branch is created, verify that the branch selector displays the new branch name before making changes.

### Choose a Useful Branch Name

A branch name should communicate the purpose of the work.

Examples include:

- `update-installation-guide`
- `revise-password-reset-procedure`
- `add-troubleshooting-section`
- `develop-workflow-guide`

Avoid vague names such as:

- `changes`
- `new`
- `test`
- `update`

A descriptive branch name makes it easier for writers and reviewers to understand what work is being performed.

---

## Creating and Editing Documentation Files

After switching to the appropriate branch, documentation files can be created or edited without immediately changing the version on `main`.

### Create a New File

1. Verify that the correct repository and branch are displayed.
2. Select **Add file** or the **+** button near the file list.
3. Select **Create new file**.
4. Enter the file name, including the appropriate file extension.
5. Add the document content in the editor.

For Markdown documentation, use the `.md` file extension.

For example:

`GITHUB-DOCUMENTATION-WORKFLOW.md`

### Create a File Inside a Folder

GitHub also allows a file path to be entered when creating a file.

For example:

`guides/creating-a-branch.md`

creates the Markdown file inside a `guides` folder.

Use folders to group related content rather than placing unrelated files together.

For example:

    repository/
    │
    ├── README.md
    ├── guides/
    │   ├── getting-started.md
    │   └── troubleshooting.md
    └── images/
        └── example.png

### Decide Where a File Belongs

File organization should reflect the purpose of the content.

For example, a folder named `original` might contain source documentation preserved for comparison:

    original/
        employee-pto-policy-procedure.md

A redesigned document should not automatically be placed in the `original` folder simply because it is related to that file. If `original` means "content before redesign," placing the final version there would make the folder structure misleading.

A clearer structure would be:

    repository/
    │
    ├── original/
    │   └── employee-pto-policy-procedure.md
    │
    ├── employee-pto-policy-procedure.md
    └── CASE-STUDY.md

The folder structure itself communicates information about the project.

---

## Previewing Markdown Before Committing

Before committing a Markdown document, use GitHub's **Preview** option to review how the content will appear when rendered.

Check for:

- Correct heading levels
- Working lists
- Proper spacing
- Correct tables
- Readable code or examples
- Correct blockquotes
- Working links
- Consistent formatting

Previewing does not commit or publish the change. It provides an opportunity to catch formatting problems before saving the change to the branch history.

A useful documentation workflow is:

    Author
      ↓
    Preview
      ↓
    Review
      ↓
    Commit

---

## Understanding Commits

A **commit** records a saved change in the history of a branch.

A commit can be thought of as a checkpoint that answers three basic questions:

- What changed?
- Who made the change?
- When was the change made?

The commit message provides a short explanation of the purpose of the change.

### A Commit Does Not Mean a Merge

Committing a change to a feature branch does **not** automatically update `main`.

For example:

    main
      │
      └── create develop-workflow-guide
                    │
                    └── add documentation
                              │
                              └── commit

At this point, the committed documentation exists on `develop-workflow-guide`, but `main` has not received the change.

The work must later be merged into `main`.

### Write Meaningful Commit Messages

Commit messages should briefly describe the change that was made.

Good examples:

- `Add GitHub workflow guide foundation`
- `Add branch creation procedure`
- `Clarify PTO approval requirements`
- `Add troubleshooting guidance`
- `Fix broken documentation links`

Avoid messages such as:

- `stuff`
- `changes`
- `update`
- `fixed it`

A reviewer should be able to look at the commit history and understand how the documentation evolved.

### Make Logical Commits

A project does not need to be completed in one commit.

Instead, commits can represent meaningful units of work.

For example:

    Add GitHub workflow guide foundation
                ↓
    Add branch and file creation procedures
                ↓
    Add commit and pull request procedures
                ↓
    Add merge and cleanup guidance
                ↓
    Add troubleshooting guidance

This creates a useful history of the documentation project and makes individual changes easier to understand and review.

---

## Understanding Ahead and Behind

GitHub compares branches and may display **Ahead** and **Behind** values.

These values describe differences in commit history between the selected branch and the branch being used for comparison, typically `main`.

### Ahead

If a branch is **1 commit ahead of `main`**, the branch contains one commit that `main` does not contain.

For example:

    main
      │
      A
      │
      └──────── feature branch
                     │
                     B

The feature branch contains commit `B`, but `main` does not.

The branch is therefore:

**1 ahead**

This is what happens after making a commit on a feature branch before merging it into `main`.

### Behind

If a branch is **2 commits behind `main`**, `main` contains two commits that the branch does not contain.

For example:

    feature branch
          │
          A

    main
      │
      A
      │
      B
      │
      C

The feature branch does not contain commits `B` or `C`.

It is therefore:

**2 behind**

### Ahead 0 / Behind 2

A branch showing:

**Ahead: 0**  
**Behind: 2**

contains no commits that are missing from `main`, while `main` contains two newer commits that are missing from the branch.

This commonly occurs when an old branch has already served its purpose and `main` has continued to change.

> **Important:** Ahead and Behind describe commit history. Always understand the status of a branch before deleting or attempting to merge it.

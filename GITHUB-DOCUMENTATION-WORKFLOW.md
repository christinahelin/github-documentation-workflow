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

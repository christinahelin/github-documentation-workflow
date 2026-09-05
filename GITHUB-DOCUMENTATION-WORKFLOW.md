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

---

## Commit Messages and Extended Descriptions

GitHub may ask for both a **commit message** and an **extended description** when saving a change.

These fields serve different purposes.

### Commit Message

The commit message is the short summary of the change.

It should usually:

- Begin with an action verb
- Describe what changed
- Be specific enough to understand later
- Stay concise

Good examples:

- `Add GitHub workflow guide foundation`
- `Add branch and file creation guidance`
- `Update README with portfolio overview`
- `Fix broken documentation links`
- `Clarify PTO approval requirements`

Avoid vague messages such as:

- `Update`
- `Changes`
- `Stuff`
- `Fix`
- `Done`

A useful pattern is:

> **Action + what changed**

Examples:

`Add troubleshooting section`

`Update task status procedure`

`Remove outdated screenshots`

---

### Extended Description

The extended description is optional.

Use it when the short commit message does not provide enough context.

The extended description can explain:

- Why the change was needed
- What sections were added or revised
- Important context for reviewers
- Multiple related changes included in one commit

Example:

**Commit message**

`Add branch, file, and commit guidance`

**Extended description**

`Document branch creation, file organization, Markdown previewing, commit practices, and Ahead/Behind branch status.`

This provides more context without making the commit message itself too long.

### When to Leave the Extended Description Blank

Leave the extended description blank when the commit message already explains the change clearly.

For example:

**Commit message**

`Fix broken link in README`

No extended description is needed because the change is simple and specific.

Another example:

**Commit message**

`Add TaskFlow project to portfolio`

If the commit only adds that one project to the profile README, the short message is usually sufficient.

A good rule is:

> If someone can understand the change from the commit message alone, the extended description is optional.

---

## When GitHub Generates a Commit Message

GitHub sometimes generates commit text automatically.

This often happens when merging a pull request.

For example, GitHub may generate:

`Merge pull request #3 from username/update-task-status`

and use the pull request title as the extended description.

In this situation, the generated message is usually appropriate and can be left unchanged.

The auto-generated merge message records:

- The pull request number
- The source branch
- The fact that the change was merged

This creates a useful historical record.

### When to Keep the Auto-Generated Merge Message

Keep GitHub's auto-generated merge message when:

- The pull request title is already clear
- The branch name is descriptive
- The merge represents a normal completed change
- There is no additional context that future reviewers need

Example:

`Merge pull request #1 from christinahelin/redesign-pto-document`

Extended description:

`Redesign PTO policy and procedure`

This is clear and provides useful history.

### When You Might Change It

Consider changing auto-generated text only when:

- The generated wording is unclear
- The pull request title is too vague
- The branch name does not explain the change
- Important context would otherwise be lost

For example, if the pull request title were:

`Updates`

that would not be very useful in the project history.

A clearer merge description might be:

`Update onboarding documentation and correct broken navigation links`

However, it is generally better to write a clear pull request title before merging rather than rewriting the merge message afterward.

---

## Commit Message vs. Pull Request Title

Commit messages and pull request titles are related, but they are not always the same thing.

A **commit message** describes one saved unit of work.

A **pull request title** describes the overall change being proposed for merge.

For example, one branch might contain several commits:

- `Add workflow guide foundation`
- `Add branch and commit guidance`
- `Add troubleshooting section`

The pull request title could summarize the entire body of work:

`Add GitHub documentation workflow guide`

This means:

    Branch
      │
      ├── Commit 1
      ├── Commit 2
      └── Commit 3
              ↓
        Pull Request
              ↓
          Merge to main

The commit history shows how the work developed.

The pull request title summarizes the overall change being reviewed and merged.

| Field | Purpose | Usually Change It? |
| --- | --- | --- |
| Commit message | Short summary of one saved change | Yes |
| Extended description | Optional extra context for the commit | Only when useful |
| Pull request title | Summary of the overall proposed change | Yes |
| Pull request description | Explains scope and key changes | Usually yes |
| Auto-generated merge message | Records the merge event | Usually leave as generated |

## Pull Requests

A pull request (PR) is a request to merge changes from one branch into another branch.

In a documentation workflow, you will commonly:

1. Create a branch from `main`.
2. Make documentation changes on the branch.
3. Commit those changes.
4. Create a pull request.
5. Review the changes.
6. Merge the pull request into `main`.
7. Delete the completed branch.

A pull request creates a review point before changes become part of the main version of the documentation.

### When Should I Create a Pull Request?

Create a pull request when you have completed the changes you intended to make on your branch and are ready for those changes to be reviewed and added to `main`.

For example, suppose you create a branch named:

`update-pto-procedure`

You might make several changes on that branch, such as:

- Reorganizing the PTO procedure
- Adding numbered instructions
- Correcting terminology
- Updating the README
- Adding screenshots

You can make multiple commits while completing this work. You do not need to create a pull request after every commit.

Instead, create the pull request when the branch represents a complete or reviewable unit of work.

---

## Creating a Pull Request

After committing changes to a branch, return to the repository's **Code** page.

GitHub may display a banner stating that your branch had recent pushes.

Select **Compare & pull request**.

If the banner is not displayed:

1. Select **Pull requests** from the repository navigation.
2. Select **New pull request**.
3. Confirm that the branches are correct.

You will typically see something similar to:

**base: main ← compare: your-branch-name**

For example:

**base: main ← compare: update-pto-procedure**

This means:

> Take the changes from `update-pto-procedure` and propose adding them to `main`.

### Important: Check the Branch Direction

Before creating the pull request, verify:

- **Base** = the branch receiving the changes
- **Compare** = the branch containing your changes

In this workflow, `main` will usually be the base branch.

Your working branch will usually be the compare branch.

If these are reversed, the pull request may attempt to merge changes in the wrong direction.

---

## Writing a Pull Request Title

The pull request title should briefly describe the overall change.

Good examples include:

- `Add GitHub documentation workflow guide`
- `Redesign PTO policy and procedure`
- `Add task management user documentation`
- `Update onboarding documentation`
- `Improve PTO request instructions`

Avoid vague titles such as:

- `Changes`
- `Updates`
- `New stuff`
- `Fix`
- `Documentation`

The title should help another person understand the purpose of the pull request without opening it.

### Pull Request Title vs. Commit Message

A pull request title and a commit message may look similar, but they describe different things.

A **commit message** describes a specific saved change.

A **pull request title** describes the overall body of work being proposed for merging.

For example, a branch might contain these commits:

- `Add GitHub workflow guide foundation`
- `Add commit message guidance`
- `Add pull request instructions`
- `Add troubleshooting section`

The pull request containing all four commits could be titled:

`Add GitHub documentation workflow guide`

The pull request title summarizes the entire change rather than repeating one individual commit.

---

## Writing a Pull Request Description

Use the pull request description to provide additional context about the change.

A useful description may explain:

- What was changed
- Why the change was needed
- Which files were affected
- Anything a reviewer should pay particular attention to

For example:

### Summary

Adds a comprehensive GitHub documentation workflow guide covering branches, commits, pull requests, merging, and common documentation workflows.

### Changes

- Added branch creation guidance
- Added commit message and extended description guidance
- Added pull request instructions
- Added examples for documentation workflows
- Added troubleshooting information for common mistakes

For a small personal portfolio project, the description does not need to be extremely detailed. However, practicing clear pull request descriptions demonstrates a professional documentation workflow.

---

## Reviewing a Pull Request Before Merging

Do not immediately select **Merge pull request** simply because GitHub allows you to.

First, review the pull request.

Check the following areas:

### Commits

Review the commits included in the pull request.

Ask:

- Do these commits belong in this project?
- Did I accidentally include unrelated work?
- Do the commit messages make sense?

### Files Changed

Select **Files changed**.

This view shows exactly what the pull request will add, remove, or modify.

Lines added to a file are typically displayed as additions.

Lines removed from a file are typically displayed as deletions.

Review the changes and ask:

- Did I modify the correct file?
- Did I accidentally delete anything?
- Is the Markdown formatted correctly?
- Are headings and lists structured correctly?
- Are links correct?
- Did I leave temporary notes or placeholder text?
- Does the rendered documentation look the way I intended?

This review step is particularly important for technical writers because it functions as a final quality-control check before publication.

---

## Merging a Pull Request

Once you are satisfied with the changes, you can merge the pull request.

Select:

**Merge pull request**

GitHub will display a confirmation screen containing a commit message and, in some cases, an extended description.

### Should I Change GitHub's Automatically Generated Merge Commit Message?

Not always.

GitHub may generate something similar to:

`Merge pull request #1 from username/update-pto-procedure`

This message is technically correct and provides traceability to the pull request and branch.

For ordinary merges, it is perfectly acceptable to leave this automatically generated message.

You may change it when a clearer description would make the repository history easier to understand.

For example:

`Merge PTO policy and procedure redesign`

You might use the extended description for additional context:

`Adds the redesigned PTO document and supporting case study.`

### When to Leave the Automatically Generated Message

Consider leaving GitHub's generated merge message when:

- The pull request title already clearly explains the work.
- You want the pull request number and branch name preserved in the commit history.
- The repository follows GitHub's default merge conventions.
- There is no meaningful additional context to add.

### When to Customize the Merge Message

Consider customizing the message when:

- The automatically generated text is difficult to understand.
- The branch name does not clearly describe the completed work.
- A clearer message would improve the repository history.
- Your team or organization follows a specific commit-message convention.

The goal is not to customize every field simply because GitHub allows you to edit it.

The goal is to create useful documentation history.

---

## Confirming the Merge

After reviewing the merge information, select:

**Confirm merge**

The changes from your branch are now incorporated into `main`.

Return to the repository's **Code** page and select the `main` branch.

Confirm that the new or updated files appear there.

At this point:

- Your working branch contains the changes.
- `main` now also contains those changes.
- The pull request records the review and merge history.

---

## Deleting a Branch After a Merge

After successfully merging a pull request, GitHub may display a **Delete branch** button.

In most cases, you should delete the completed working branch.

Deleting the branch does **not** delete the work you just merged.

The changes are already part of `main`.

Think of the branch as a temporary workspace.

Before the merge:

`main → working branch → changes`

After the merge:

`working branch → merged into main`

Once the work exists in `main`, the temporary branch is usually no longer necessary.

### When Should I Delete a Branch?

Delete a branch when:

- Its work has been successfully merged.
- You have confirmed that the changes appear in `main`.
- You do not plan to continue using that branch for additional work.

### When Should I Keep a Branch?

You may keep a branch temporarily when:

- The pull request has not been merged.
- Work on the branch is still in progress.
- You need to make additional changes requested during review.
- The branch represents ongoing work that is not ready for `main`.

Do not keep old branches simply because deleting them feels dangerous.

Once the work is safely merged into `main`, deleting the working branch is normal repository maintenance.

---

## Understanding Ahead and Behind

GitHub may display numbers showing that a branch is **ahead** or **behind** another branch.

These numbers describe differences between the histories of the branches.

### Ahead

If a branch is:

**1 ahead**

the branch contains one commit that `main` does not currently contain.

For example:

`main: A → B`

`feature branch: A → B → C`

The feature branch is one commit ahead because commit `C` has not yet been merged into `main`.

### Behind

If a branch is:

**2 behind**

`main` contains two commits that the branch does not contain.

For example:

`main: A → B → C → D`

`feature branch: A → B`

The feature branch is two commits behind because it does not contain commits `C` and `D`.

### 0 Ahead / 0 Behind

If a branch displays:

**0 ahead / 0 behind**

the branch and `main` currently contain the same commit history.

This often happens immediately after creating a new branch before making any changes.

---

## A Complete Example

Suppose you need to add a new troubleshooting section to this guide.

### 1. Start from `main`

Make sure you are viewing the current `main` branch.

### 2. Create a branch

Create:

`add-troubleshooting-guide`

This gives you a separate workspace for the change.

### 3. Edit the documentation

Open:

`GITHUB-DOCUMENTATION-WORKFLOW.md`

Add the troubleshooting content.

### 4. Commit the change

Use a descriptive commit message:

`Add GitHub workflow troubleshooting guidance`

If useful, add an extended description:

`Documents common branch, commit, pull request, and merge mistakes and explains how to recover from them.`

### 5. Create a pull request

Set:

**base: main**

**compare: add-troubleshooting-guide**

Use a pull request title such as:

`Add GitHub workflow troubleshooting guide`

### 6. Review the pull request

Check:

- Commits
- Files changed
- Markdown formatting
- Links
- Content accuracy

### 7. Merge

Select **Merge pull request** and then **Confirm merge**.

### 8. Verify `main`

Return to the `main` branch and confirm that the troubleshooting section appears in the guide.

### 9. Delete the branch

Once the change is safely in `main`, delete:

`add-troubleshooting-guide`

The feature branch is no longer needed.

---

## Quick Reference: What Am I Actually Doing?

| Action | What It Means | Why You Do It |
|---|---|---|
| Create a branch | Create a separate workspace based on the current repository | Keeps unfinished work away from `main` |
| Edit a file | Change the documentation | Produces the actual content update |
| Commit | Save a recorded version of your changes | Creates documentation history |
| Push | Send local commits to GitHub | Makes locally created work available in the remote repository |
| Pull request | Propose merging one branch into another | Creates an opportunity to review the change |
| Review Files changed | Inspect exactly what will be modified | Helps catch errors before merging |
| Merge | Incorporate the branch's changes into the target branch | Publishes the approved work into `main` |
| Delete branch | Remove the completed temporary workspace | Keeps the repository organized |

> **Note:** When working entirely in GitHub's website, GitHub handles much of the remote repository interaction for you. You may therefore not manually perform a separate `push` step. When using Git locally, `commit` and `push` are separate actions.

---

# Troubleshooting and Recovering from Common Mistakes

Mistakes in GitHub do not always mean that work has been lost or damaged. Before deleting, reverting, or recreating anything, identify:

1. Which repository you are in.
2. Which branch you are on.
3. Whether the change has been committed.
4. Whether the change has been merged into `main`.

Understanding where the change exists determines the appropriate recovery action.

---

## I Created a Branch in the Wrong Repository

### What Happened?

A branch belongs to the repository in which it was created.

For example, suppose you intend to create a new repository named:

`github-documentation-workflow`

but you are currently inside:

`username/profile-repository`

If you enter `github-documentation-workflow` in the **branch selector**, GitHub creates a branch with that name inside the existing profile repository.

It does **not** create a new repository.

You would have:

    username/profile-repository
    │
    ├── main
    └── github-documentation-workflow  ← accidental branch

instead of:

    username/github-documentation-workflow
    │
    └── main

### How to Fix It

If no work on the accidental branch needs to be preserved:

1. Open the repository containing the accidental branch.
2. Open the branch selector.
3. Select **View all branches**.
4. Locate the accidental branch.
5. Verify that you are selecting the correct branch.
6. Select the **Delete branch** or trash-can option.
7. Create or navigate to the correct repository.

Deleting the accidental branch does not delete a separate repository with the same name.

> **Prevention:** Before creating a branch, check the repository name displayed near the upper-left area of the page.

---

## I Created a File in the Wrong Folder

### What Happened?

When creating a file, GitHub uses the path shown in the filename area to determine where the file will be stored.

For example:

`original/employee-pto-policy.md`

places the file inside the `original` folder.

If you intended the file to be at the repository root, that location would be incorrect.

### If You Have Not Committed Yet

The easiest solution is usually:

1. Select **Cancel changes**.
2. Return to the correct repository location.
3. Create the file again in the intended location.

If you are creating a root-level file, make sure the path does not include an unwanted folder.

### If You Already Committed the File

Do not panic or delete the entire branch.

You can correct the file location in another commit by moving or recreating the file in the appropriate location and removing the incorrectly located version.

Use a commit message that explains the correction, such as:

`Move PTO procedure to repository root`

A correction commit is a normal part of version-controlled work.

---

## I Started Editing the Wrong File

If the change has **not been committed**, cancel the edit and open the correct file.

If the change **has been committed**, first determine whether the incorrect changes need to be preserved.

Do not begin deleting files or branches until you understand where the committed work exists.

For a simple correction, restore the incorrect file to the appropriate content and commit the correction.

Example:

`Restore original PTO source document`

---

## I Made Changes on `main` Instead of Creating a Branch

First determine whether the change has been committed.

### If You Have Not Committed

Cancel the edit.

Then:

1. Return to the repository.
2. Make sure `main` is selected.
3. Create the appropriate working branch.
4. Make the change on that branch.

### If You Already Committed to `main`

The change is now part of `main`.

Do not attempt to fix the mistake by randomly deleting files, branches, or commits.

For a personal documentation repository, a small intentional change committed directly to `main` may not require correction at all.

For a professional repository, follow the team's established process for correcting or reverting changes to `main`.

> **Important:** Whether a direct commit to `main` is allowed depends on repository permissions and team practices. Some repositories protect `main` and require all changes to go through pull requests.

---

## When Is It Okay to Commit Directly to `main`?

For a small personal repository, direct commits to `main` may be reasonable for minor changes such as:

- Correcting a typo
- Fixing a broken link
- Making a small README update
- Correcting simple formatting

A branch and pull request are more appropriate when:

- Adding a new document
- Making substantial revisions
- Changing multiple files
- Creating work that should be reviewed
- Collaborating with other contributors
- Working in a repository that requires pull requests

When in doubt, using a branch is generally the safer workflow because it creates an opportunity to review the change before it reaches `main`.

---

## I Committed Too Early

A commit does not have to represent the finished project.

If you committed a change and then realized additional work is needed, continue editing on the same branch and create another commit.

For example:

    Commit 1: Add task status guide
            ↓
    Notice missing troubleshooting information
            ↓
    Commit 2: Add task status troubleshooting

You do not need to delete the first commit simply because the document was not completely finished.

Multiple logical commits on one branch are normal.

---

## I Used a Bad Commit Message

A vague commit message such as:

`changes`

does not automatically damage the documentation.

If the commit has already been created, avoid rewriting repository history solely to make a minor cosmetic improvement unless your team's workflow specifically requires it.

Instead, use clearer messages for future commits.

For example:

Instead of:

`update`

use:

`Clarify branch deletion instructions`

Good version-control habits are developed over time. Not every imperfect message requires a recovery operation.

---

## I Do Not See My Changes on `main`

This is often normal.

Ask:

**Did I commit the change on a feature branch?**

If yes, the change is saved on that branch.

Next ask:

**Did I create and merge a pull request into `main`?**

If not, the change has not reached `main` yet.

The workflow may currently be:

    main
      │
      └── feature branch
              │
              └── committed changes

You still need:

    committed changes
          ↓
    pull request
          ↓
        review
          ↓
         merge
          ↓
         main

Switching back to `main` before merging may therefore make it appear that the new file or content has disappeared.

It has not disappeared. It remains on the feature branch.

---

## I Created a Pull Request but Found Another Problem

You do not necessarily need to close the pull request.

If the pull request is still open:

1. Return to the branch associated with the pull request.
2. Make the necessary correction.
3. Commit the correction to the same branch.
4. Return to the pull request.

GitHub updates the open pull request to include the new commit.

This allows review feedback and corrections to remain part of the same proposed change.

---

## I Opened a Pull Request but Do Not Want to Merge It

A pull request does not have to be merged.

If the proposed change should not be added to `main`, close the pull request without merging it.

Closing a pull request means:

> Do not incorporate these proposed branch changes into the target branch.

Closing the pull request does not automatically mean that the branch itself must be deleted.

Decide separately whether the branch should be preserved or removed.

---

## I Am Afraid to Delete a Branch

Before deleting a completed branch, confirm:

1. The pull request was successfully merged.
2. The desired changes appear on `main`.
3. The branch does not contain additional work that still needs to be preserved.

Once committed work has been merged into `main`, deleting the feature branch does not remove those merged changes from `main`.

For example:

Before merge:

    main: A
    feature: A → B

After merge:

    main: A → B
    feature: A → B

After deleting the feature branch:

    main: A → B

Commit `B` remains in `main`.

The temporary branch name is removed; the merged work is not.

---

## I See an Old Branch That Is 0 Ahead and 2 Behind

Suppose GitHub displays:

**Ahead: 0**  
**Behind: 2**

This means:

- The old branch contains no commits that `main` is missing.
- `main` contains two commits that the old branch does not contain.

If the branch's work was already merged and no additional work is needed, this is a strong indication that the old branch may simply be stale and can be cleaned up.

Before deleting it, still confirm that the branch does not contain work you intend to keep.

---

## I Deleted the Wrong Branch

First, determine whether the branch had been merged.

If the work was already merged into `main`, the merged changes remain on `main`.

Deleting the branch does not undo the merge.

If the branch contained unmerged work, recovery may require restoring the branch or locating its commits. The available recovery options depend on the repository state and GitHub interface.

> **Important:** If you are uncertain whether an unmerged branch contains work you need, do not delete it until you have verified its contents.

---

## Repository or Branch? Quick Decision Guide

Ask:

**Am I starting an entirely separate project?**

→ Create a **repository**.

**Am I making a change to an existing project?**

→ Create a **branch** in that repository.

**Am I making another related change as part of the work already underway on my current branch?**

→ Continue using the **current branch** and make another logical commit.

**Has my work been merged and the branch is finished?**

→ Verify the work on `main`, then **delete the branch**.

---

## Before You Click Delete, Merge, or Commit

When uncertain, stop and check:

| Question | What to Verify |
| --- | --- |
| Where am I? | Repository name |
| What version am I changing? | Branch name |
| Has this been saved? | Commit history |
| Is it already in the accepted version? | Check `main` |
| Has it been proposed for merge? | Pull requests |
| Has the pull request been completed? | Merged status |
| Is this branch still unique? | Ahead/Behind status |

Taking a few seconds to identify the repository, branch, and state of the change is usually safer than immediately trying to undo something.

---

# Markdown Quick Reference

GitHub uses **Markdown** to format text in files with the `.md` extension.

Markdown allows writers to create structured documentation using plain-text characters rather than a traditional word processor.

For example, while editing a Markdown file, you type:

```markdown
## Request Paid Time Off
```

When you select **Preview**, GitHub renders it as a second-level heading.

Use the following reference when creating or editing documentation in GitHub.

---

## Headings

Use `#` characters to create headings.

### What You Type

```markdown
# Document Title

## Major Section

### Subsection

#### Smaller Subsection
```

The number of `#` characters determines the heading level.

| Markdown | Heading Level | Typical Use |
| --- | --- | --- |
| `#` | Heading 1 | Document title |
| `##` | Heading 2 | Major section |
| `###` | Heading 3 | Subsection |
| `####` | Heading 4 | Section within a subsection |

For most documentation, use only one Heading 1 for the document title and organize the remaining content hierarchically underneath it.

---

## Bold Text

Use two asterisks on each side of text to make it bold.

### What You Type

```markdown
Select **Commit changes**.
```

### How It Renders

Select **Commit changes**.

Bold formatting is useful for interface elements such as button names, menu options, tabs, and fields.

---

## Italic Text

Use one asterisk on each side of text.

### What You Type

```markdown
*Optional*
```

### How It Renders

*Optional*

Use italics sparingly when emphasis is necessary.

---

## Bulleted Lists

Use a hyphen followed by a space for each list item.

### What You Type

```markdown
- Create a branch
- Edit the documentation
- Preview the changes
- Commit the changes
```

### How It Renders

- Create a branch
- Edit the documentation
- Preview the changes
- Commit the changes

Use bulleted lists when the order of the items does not matter.

---

## Numbered Lists

Use numbers when the reader must perform steps in a particular order.

### What You Type

```markdown
1. Open the repository.
2. Create a branch.
3. Edit the documentation.
4. Preview the changes.
5. Commit the changes.
```

### How It Renders

1. Open the repository.
2. Create a branch.
3. Edit the documentation.
4. Preview the changes.
5. Commit the changes.

For procedures, numbered lists help communicate that the actions should be completed sequentially.

---

## Links

Use square brackets for the text the reader sees and parentheses for the destination.

### What You Type

```markdown
[View the TaskFlow documentation](https://github.com/example/taskflow-documentation)
```

The structure is:

```text
[Visible link text](destination)
```

For files within the same repository, a relative link can be used.

Example:

```markdown
[Read the case study](CASE-STUDY.md)
```

A relative link points to another file based on its location within the repository rather than requiring the full web address.

---

## Tables

Tables use vertical bars (`|`) to separate columns.

### What You Type

```markdown
| Status | Description |
| --- | --- |
| Pending | Awaiting review |
| Approved | Request approved |
| Denied | Request not approved |
```

### How It Renders

| Status | Description |
| --- | --- |
| Pending | Awaiting review |
| Approved | Request approved |
| Denied | Request not approved |

The second row:

```text
| --- | --- |
```

defines the table columns and separates the header from the table content.

---

## Blockquotes

Use `>` at the beginning of a line to create a blockquote.

### What You Type

```markdown
> **Tip:** Preview your Markdown before committing the change.
```

### How It Renders

> **Tip:** Preview your Markdown before committing the change.

Blockquotes can be useful for notes, tips, warnings, or other information that should stand apart from the surrounding text.

---

## Inline Code

Use a single backtick on each side of text to identify commands, file names, branch names, paths, or other technical values.

### What You Type

```markdown
Create a branch named `update-task-status`.
```

### How It Renders

Create a branch named `update-task-status`.

Other examples include:

`main`

`README.md`

`docs/getting-started.md`

`.md`

---

## Code Blocks

Use three backticks before and after a block of code or preformatted text.

### What You Type

    ```text
    main
      ↓
    feature branch
      ↓
    commit
    ```

Code blocks preserve formatting and are useful for examples where spacing matters.

---

## Horizontal Lines

Use three hyphens to create a horizontal divider.

### What You Type

```markdown
---
```

Horizontal lines can visually separate major portions of a long document.

Avoid using them so frequently that the document becomes visually fragmented.

---

## File Names and Paths

A Markdown filename typically ends in:

`.md`

Examples:

`README.md`

`getting-started.md`

`GITHUB-DOCUMENTATION-WORKFLOW.md`

A forward slash indicates that a file is inside a folder.

For example:

`docs/getting-started.md`

means:

```text
repository
└── docs
    └── getting-started.md
```

When creating a new file in GitHub, entering the folder and filename together can create the file at that location.

---

## Common Markdown Mistakes

### Missing Space After a Heading Symbol

Incorrect:

```markdown
##Heading
```

Correct:

```markdown
## Heading
```

### Forgetting to Close Bold Formatting

Incorrect:

```markdown
Select **Commit changes.
```

Correct:

```markdown
Select **Commit changes**.
```

### Incorrect Link Structure

Incorrect:

```markdown
[Read the guide] GITHUB-DOCUMENTATION-WORKFLOW.md
```

Correct:

```markdown
[Read the guide](GITHUB-DOCUMENTATION-WORKFLOW.md)
```

### Forgetting the Table Separator Row

A Markdown table requires the separator underneath the header:

```markdown
| Action | Purpose |
| --- | --- |
| Commit | Save a change |
```

---

## Markdown Writing Checklist

Before committing a Markdown document, check:

- [ ] The document has a clear title.
- [ ] Heading levels follow a logical hierarchy.
- [ ] Sequential procedures use numbered steps.
- [ ] Nonsequential information uses bullets where appropriate.
- [ ] UI elements are formatted consistently.
- [ ] File names, paths, and branch names are easy to distinguish.
- [ ] Tables render correctly.
- [ ] Links point to the intended destination.
- [ ] Notes and tips are visually distinct.
- [ ] The document has been reviewed in **Preview**.

> **Tip:** If you cannot remember the Markdown syntax, open an existing `.md` file that contains the formatting you want and select **Edit** to see how it was written.

---

# What Should I Type Here?

GitHub frequently asks you to name or describe something. The following reference explains what information belongs in each field and provides examples for documentation projects.

## Repository Name

The repository name identifies the overall project.

Use a name that describes the project rather than an individual change.

**Examples:**

`taskflow-documentation`

`pto-policy-procedure-redesign`

`github-documentation-workflow`

**Ask yourself:** What is this entire project?

---

## Repository Description

The repository description is a short explanation of what the project contains or accomplishes.

**Example:**

`A practical guide to creating, reviewing, and publishing documentation changes in GitHub`

Keep the description concise enough to understand at a glance.

---

## Branch Name

The branch name identifies the specific change you are making within a repository.

A useful pattern is:

`action-topic`

**Examples:**

`update-task-status`

`redesign-pto-document`

`develop-workflow-guide`

`add-troubleshooting-section`

**Ask yourself:** What change am I making to this project?

Do not use the name of an entirely separate project as a branch name when what you actually need is a new repository.

---

## File Name

The filename should identify the content of the document.

Markdown files use the `.md` extension.

**Examples:**

`getting-started.md`

`update-task-status.md`

`employee-pto-policy-procedure.md`

`GITHUB-DOCUMENTATION-WORKFLOW.md`

If the file belongs in a folder, include the path when creating it:

`docs/getting-started.md`

Before creating the file, ask:

1. What does this document contain?
2. Which folder should contain it?
3. Am I creating it from the correct location?

---

## Commit Message

The commit message summarizes one saved change.

Use:

**Action + what changed**

**Examples:**

`Add Markdown quick reference`

`Add task status guide`

`Update README with portfolio overview`

`Clarify branch deletion instructions`

`Fix broken documentation links`

Keep the message short and specific.

---

## Extended Commit Description

The extended description provides optional additional context.

Use it when the commit message alone does not adequately explain the change.

**Example**

Commit message:

`Add troubleshooting and recovery guidance`

Extended description:

`Document common GitHub workflow mistakes, recovery options, branch cleanup, direct commits to main, and how to verify where changes are stored.`

For a simple change such as:

`Fix typo in README`

the extended description can usually be left blank.

---

## Pull Request Title

The pull request title summarizes the **entire body of work** you are proposing to merge.

A branch may contain several commits, so the pull request title does not need to match the most recent commit.

For example:

**Commits:**

- `Add workflow guide foundation`
- `Add commit message guidance`
- `Add troubleshooting guidance`
- `Add Markdown quick reference`

**Pull request title:**

`Add GitHub documentation workflow guide`

**Ask yourself:** What does this entire branch accomplish?

---

## Pull Request Description

The pull request description gives the reviewer an overview of the proposed changes.

A simple documentation template is:

```markdown
## Summary

- Adds [new content]
- Updates [existing content]
- Clarifies [topic or process]
- Adds [supporting reference or troubleshooting information]
```

For example:

```markdown
## Summary

- Adds a comprehensive GitHub documentation workflow guide
- Explains repositories, branches, commits, pull requests, and merges
- Adds troubleshooting guidance for common workflow mistakes
- Includes a Markdown quick reference and workflow checklist
```

The description should help a reviewer understand the scope without having to inspect every changed line first.

---

## Merge Commit Message

When merging a pull request, GitHub may automatically create a message such as:

`Merge pull request #4 from username/develop-workflow-guide`

In most cases, this can remain unchanged.

The generated message preserves information about the pull request and source branch.

Customize it only when doing so provides meaningful clarity or when your team's standards require a particular format.

---

## Quick Decision Table

| GitHub Is Asking For | Ask Yourself | Example |
| --- | --- | --- |
| Repository name | What is the whole project? | `github-documentation-workflow` |
| Repository description | What does this project provide? | `A practical guide to...` |
| Branch name | What change am I making? | `add-troubleshooting-section` |
| Filename | What does this document contain? | `troubleshooting.md` |
| Commit message | What did I just save? | `Add troubleshooting guidance` |
| Extended description | Does this commit need more context? | Explain the scope |
| PR title | What does this entire branch accomplish? | `Add GitHub workflow guide` |
| PR description | What should the reviewer know? | Summarize major changes |
| Merge message | Does GitHub's generated text adequately record the merge? | Usually leave it |
---

# Where Am I in the Workflow?

When you are unsure what to do next, identify the current state of your work.

| What You See | What It Usually Means | Typical Next Step |
| --- | --- | --- |
| `main` selected and no work started | You are viewing the accepted version | Create a branch for substantial new work |
| New branch is `0 ahead / 0 behind` | The branch was created but has no unique commits | Begin editing |
| Working branch is ahead of `main` | You have committed work not yet in `main` | Continue working or create a pull request |
| **Compare & pull request** appears | GitHub recognizes branch changes that can be proposed for merge | Create the pull request when the work is ready |
| Pull request is open | Changes have been proposed but not merged | Review and make corrections if needed |
| **Files changed** shows the expected edits | The proposed changes are ready for final review | Merge when satisfied |
| Pull request says **Merged** | The branch changes have been incorporated into the target branch | Verify the changes on `main` |
| Merged work appears on `main` | The change is safely incorporated | Delete the completed branch |
| File appears on your branch but not `main` | The work has not been merged | Check the pull request/merge status |

---

# Start-to-Finish Documentation Checklist

Use this checklist when making a substantial documentation change.

## Before Starting

- [ ] Open the correct repository.
- [ ] Confirm that `main` is selected.
- [ ] Confirm that you are starting from the current project.
- [ ] Decide what change you are making.
- [ ] Create a descriptive branch from `main`.

## While Working

- [ ] Confirm the working branch is selected.
- [ ] Create or edit the correct file.
- [ ] Confirm that the file is in the correct folder.
- [ ] Use appropriate Markdown formatting.
- [ ] Preview the document.
- [ ] Review the rendered content for errors.
- [ ] Commit a meaningful unit of work.
- [ ] Write a descriptive commit message.
- [ ] Add an extended description when additional context is useful.
- [ ] Continue making logical commits on the same branch as needed.

## When the Work Is Ready

- [ ] Create a pull request.
- [ ] Confirm **base: main**.
- [ ] Confirm **compare: your working branch**.
- [ ] Write a clear pull request title.
- [ ] Add a useful pull request description.
- [ ] Review the included commits.
- [ ] Review **Files changed**.
- [ ] Correct any problems before merging.

## After Review

- [ ] Select **Merge pull request**.
- [ ] Review the merge message.
- [ ] Keep the generated merge message unless changing it adds meaningful value.
- [ ] Select **Confirm merge**.
- [ ] Return to `main`.
- [ ] Verify that the expected changes appear on `main`.
- [ ] Delete the completed working branch.

## The Short Version

> **Main → Branch → Write → Preview → Commit → Pull Request → Review → Merge → Verify → Delete**

If you lose track of the process, return to this sequence and determine which step you completed most recently.

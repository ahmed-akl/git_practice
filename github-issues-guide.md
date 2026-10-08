# GitHub Issues: A Student Guide

## 1. What is an issue?

A **GitHub issue** is a tracked item inside a repository. It is used to report a bug, request a feature, ask a question, or record a task that needs to be done. Think of it as a to-do item with a built-in discussion thread.

Each issue has:

| Part | Purpose |
|------|---------|
| **Title** | A short summary of the problem or task |
| **Description** | Details: what is wrong, what you expected, how to reproduce it |
| **Number** | A unique ID such as `#12`, used to reference the issue anywhere in the repo |
| **Labels** | Tags such as `bug`, `enhancement`, `documentation`, `question` |
| **Assignees** | The person (or people) responsible for solving it |
| **Milestone / Project** | Optional grouping, such as "Week 5 Lab" or "Sprint 1" |
| **Comments** | The discussion between team members |
| **Status** | **Open** or **Closed** |

**Why use issues?**
- Everyone can see what needs to be done and who is working on it.
- Discussions stay in one place instead of being scattered across chats and emails.
- Every fix can be linked back to the problem it solves, which keeps a clear history.

---

## 2. How to create an issue

1. Open the repository on GitHub.
2. Click the **Issues** tab at the top. (If you do not see it, the repository owner may have disabled issues.)
3. Click the green **New issue** button.
4. Fill in the form:
   - **Title:** Be short and specific.
     - Good: `Login page crashes when the password field is empty`
     - Bad: `It doesn't work`
   - **Description:** Explain clearly. A useful template for bugs:
     ```
     **What happened:**
     The app crashes when I click Login with an empty password.

     **What I expected:**
     An error message such as "Password is required".

     **Steps to reproduce:**
     1. Run the app
     2. Leave the password field empty
     3. Click Login

     **Environment:** Windows 11, Python 3.12
     ```
   - You can add screenshots by dragging and dropping images into the description box.
5. (Optional) On the right-hand side, set **Assignees**, **Labels**, **Projects**, and **Milestone**.
6. Click **Submit new issue**.

**Tips for writing a good issue**
- One problem per issue.
- Search existing issues first to avoid duplicates.
- Include error messages (copy and paste the text).
- Mention a teammate with `@username` to get their attention.
- Link to another issue by typing `#` followed by its number (for example, `#7`).

---

## 3. Steps to solve an issue

### Step 1: Pick the issue and assign it to yourself
Open the issue and click **Assignees > assign yourself**. Add a comment such as "I'm working on this" so others do not duplicate your work.

### Step 2: Get the latest code
```bash
git checkout main
git pull
```

### Step 3: Create a branch for the issue
Never fix issues directly on `main`. Name the branch after the issue number:
```bash
git checkout -b fix-12-empty-password-crash
```

### Step 4: Fix the problem
Edit the code, then test that the problem is gone and nothing else broke.

### Step 5: Commit your changes and reference the issue
```bash
git add .
git commit -m "Show error when password is empty (fixes #12)"
```
Using a keyword followed by the issue number (`fixes #12`, `closes #12`, or `resolves #12`) links the commit to the issue.

### Step 6: Push your branch
```bash
git push -u origin fix-12-empty-password-crash
```

### Step 7: Open a pull request (PR)
1. On GitHub, click **Compare & pull request** (the banner shown after pushing).
2. Write a short description of what you changed.
3. In the description, add `Closes #12`. This links the PR to the issue and **closes the issue automatically** when the PR is merged.
4. Click **Create pull request**.

### Step 8: Review and merge
- A teammate or instructor reviews your PR and may ask for changes. Make them on the same branch, commit, and push again. The PR updates automatically.
- Once approved, click **Merge pull request**.

### Step 9: Confirm the issue is closed
After the merge, the issue closes automatically. If it does not, open the issue and click **Close issue**, adding a comment about how it was solved.

### Step 10: Clean up
```bash
git checkout main
git pull
git branch -d fix-12-empty-password-crash
```

---

## Issue lifecycle at a glance

```
Create issue  ->  Assign  ->  Create branch  ->  Fix + commit  ->  Push
      ->  Open pull request ("Closes #12")  ->  Review  ->  Merge  ->  Issue closed
```

## Quick reference

| Task | How |
|------|-----|
| Create an issue | Repo > **Issues** > **New issue** |
| Reference an issue | Type `#<number>` in a comment, commit, or PR |
| Auto-close an issue | Write `Closes #<number>` in the PR description or commit message |
| Assign someone | Right sidebar > **Assignees** |
| Add a label | Right sidebar > **Labels** |
| Close manually | Open the issue > **Close issue** |
| Reopen | Open the closed issue > **Reopen issue** |

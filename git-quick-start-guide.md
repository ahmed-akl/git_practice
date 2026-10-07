# Git Quick Start Guide for Students

This guide covers three things: installing Git, setting up VS Code and PyCharm to work with Git, and cloning a repository to your laptop.

---

## 1. Install and set up Git

### Windows
1. Download the installer from **https://git-scm.com/downloads** and run it.
2. Keep the default options and click **Next** through the wizard. (Make sure "Git from the command line and also from 3rd-party software" is selected. It is the default.)
3. Click **Install**, then **Finish**.

### macOS
1. Open **Terminal**.
2. Run `git --version`. If Git is not installed, macOS will offer to install the Command Line Tools. Click **Install**.
   (Alternative: `brew install git` if you use Homebrew.)

### Linux (Ubuntu/Debian)
```bash
sudo apt update && sudo apt install git
```

### Verify the installation
Open a terminal (Git Bash on Windows) and run:
```bash
git --version
```
You should see something like `git version 2.x.x`.

### Tell Git who you are (one time only)
Use the same email as your GitHub/GitLab account:
```bash
git config --global user.name "Your Full Name"
git config --global user.email "your.email@example.com"
git config --global init.defaultBranch main
```
Check your settings with:
```bash
git config --list
```

---

## 2. Configure your IDE
Chose your refered IDE to use Git. Here we are recommending to use VScode or PyCharm as they are free editors.
You can also use Git command prompt, which give yu a full control on Git capabilities. Moreover, it allows you to work on any device that has Git without sticking to a specific IDE.
Install one of the following IDEs:

### a) Configure VS Code for Git

1. Install VS Code from **https://code.visualstudio.com** (Git must already be installed).
2. Open VS Code. Git support is built in. No extension is required.
3. Check that VS Code found Git: open **File > Preferences > Settings** (macOS: **Code > Settings > Settings**), search for `git.path`. Leave it empty unless VS Code shows a "Git not found" message. If it does, restart VS Code after installing Git.
4. Sign in to your account (for pushing and pulling):
   - The first time you clone, push, or pull, VS Code will open a browser window asking you to sign in to GitHub. Click **Authorize**.
   - Optional: install the **GitHub Pull Requests** extension (Extensions icon, search "GitHub Pull Requests") for easier GitHub integration.
5. Learn the Source Control panel (the branch icon in the left sidebar, or `Ctrl+Shift+G`):
   - **Changes** lists the files you edited.
   - Click **+** next to a file to stage it.
   - Type a message in the box and click **Commit**.
   - Click **Sync Changes** (or the `...` menu > **Push** / **Pull**) to send or receive updates.


### b) Configure PyCharm for Git

1. Install PyCharm (Community or Professional) from **https://www.jetbrains.com/pycharm/download**.
2. Open **File > Settings** (macOS: **PyCharm > Settings**) and go to **Version Control > Git**.
3. In **Path to Git executable**:
   - PyCharm usually detects Git automatically.
   - If not, click the folder icon and select it manually.
     - Windows: `C:\Program Files\Git\bin\git.exe`
     - macOS/Linux: run `which git` in a terminal to find the path.
4. Click **Test**. You should see "Git executable version is ...". Click **OK**.
5. Sign in to GitHub: go to **Settings > Version Control > GitHub**, click **+** (Add Account) and choose **Log In via GitHub**. A browser window opens. Click **Authorize**.
6. Everyday use:
   - **Commit:** `Ctrl+K` (macOS: `Cmd+K`)
   - **Push:** `Ctrl+Shift+K` (macOS: `Cmd+Shift+K`)
   - **Pull / Update:** `Ctrl+T` (macOS: `Cmd+T`)
   - The **Git** menu at the top has all other options (branches, log, etc.).

---

## 4. Clone an existing repository

You will need the repository URL. On GitHub, open the repo, click the green **Code** button, select **HTTPS**, and click the copy icon.
Example: `https://github.com/your-instructor/course-repo.git`

### Option A: Command line (works everywhere)
```bash
cd path/to/the/folder/where/you/want/the/project
git clone https://github.com/your-instructor/course-repo.git
cd course-repo
```

### Option B: VS Code
1. Open VS Code and press `Ctrl+Shift+P` (macOS: `Cmd+Shift+P`).
2. Type **Git: Clone** and press Enter.
3. Paste the repository URL and press Enter.
4. Choose a folder on your laptop to save it in.
5. Click **Open** when VS Code asks "Would you like to open the cloned repository?"

### Option C: PyCharm
1. On the Welcome screen click **Get from VCS** (or go to **Git > Clone**, or **File > New > Project from Version Control**).
2. Select **Git** as the version control system.
3. Paste the URL and choose the **Directory** where it should be saved.
4. Click **Clone**. Trust the project when asked.

---

## 5. Daily workflow cheat sheet

| Task | Command |
|------|---------|
| Get the latest changes | `git pull` |
| See what you changed | `git status` |
| Stage all changes | `git add .` |
| Save a snapshot | `git commit -m "Describe your change"` |
| Send to GitHub | `git push` |

Always **pull before you start working**, and **commit + push when you finish**.

---

## 6. Common problems

- **`git` is not recognized:** Close and reopen your terminal or IDE. If it still fails, reinstall Git and make sure it is added to PATH.
- **Authentication failed when pushing or cloning:** GitHub no longer accepts account passwords on the command line. Sign in through the browser prompt in VS Code/PyCharm, or create a **Personal Access Token** (GitHub > Settings > Developer settings > Personal access tokens) and use it as your password.
- **"Please tell me who you are":** Repeat the `git config --global user.name` and `user.email` steps in Section 1.
- **Merge conflicts after a pull:** Do not panic. Both VS Code and PyCharm show the conflicting lines and let you choose which version to keep. Ask your instructor if unsure.
- **Cloned into the wrong folder:** Simply delete the folder and clone again.

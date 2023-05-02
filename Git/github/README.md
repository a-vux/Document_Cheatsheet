# **What is Git?**
- A Version Control System (VCS) for ***tracking changes*** in files, or codes to be specific
- To be specific, Git is a ***distributed/decentralized*** VCS (devs can work on a same project without having to be in the same network)
- Link download: https://git-scm.com/downloads
(or `sudo apt-get install git` for Linux OS)

# **Some terms:**
- *Central repository* : a repository where all participants add their changes to. It is known as the "final working version" of the project
- *Forked repository* : a personal working copy of the central repository stored in your Github account (also called a ***fork***)
- *Local/Cloned repository* : a local version of your fork on your computer

# **To fork a repo in Github:**
<p align="center">
    <img src="./src/fork.png" style="width: 1000px">
</p>
<p align="center">
    <img src="./src/fork2.png" style="width: 600px">
</p>

- Note that the name of the forked repo ***can be changed and still connected*** to the central repo
- Forked repo is useful as a backup of the central repo, and also allows you to edit/update changes without modifying the original one

# **To clone a repo:**
- Use `git clone <URL>` to make a copy of the forked repo to your local computer
<p align="center">
    <img src="./src/clone.png" style="width: 600px">
</p>

# **Some commands:**
## *First-time Git setup:*
- Set username and email address:
    * `git config --global user.name = <username>`
    * `git config --global user.email = <email>`
- Using `--global` let Git always use the given information for anything you do on the system. If you want to set them for ***just the current repo***, use the command without `--global`
- `git config --list`: to check your ***configuration lists***
## *Common commands:*
- `git --version`: to check ***which version*** of Git is installed
- `git init`: to initialize Git on the current folder. Since then, Git will watch the folder by creating a ***hidden folder*** (`.git`) to ***keep track of changes***
- `git pull <URL>`: to pull changes in the forked repo on Github to your computer to ensure both repos are in sync
- `git status`: to ***check if any changes occured*** in the current repo
<p align="center">
    <img src="./src/status.png" style="width: 600px">
</p>

- `git add`
- `git commit`
- `git push`

# **To add changes from your repo to the central repo:**
- Use `pull request`
- Head fork: the repo from which changes come
- Base fork: the repo that to which changes will be added
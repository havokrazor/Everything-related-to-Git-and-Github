# Git #   
is a distributed version control system that tracks changes in source code during software development. 
It allows multiple developers to work on the same project simultaneously without overwriting each other's work

Before Git, the tech industry primarily used **Centralized Version Control Systems (CVCS)** and, before that, Local Version Control Systems (LVCS).
For example - Subversion (SVN): The most popular centralized system before Git, still used in some legacy corporate systems.
              Concurrent Versions System (CVS): An early, popular centralized system from the 1980s that SVN eventually replaced.

### Git and Type of Branches ###

 - Main Branch (Production)
 
 What it is: The primary branch containing the stable, production-ready code.
 
 How strategies use it: In GitHub Flow, code is deployed directly to production the second it hits `main`. In GitFlow, code only hits main during an official, scheduled release.

 - Feature Branch (Development)

What it is: A temporary branch used to develop a single feature or fix a bug without messing up the working code.

How strategies use it: In GitHub Flow, feature branches are created directly from main and merged right back into `main`.

In GitFlow, feature branches are created from and merged back into a develop branch, completely isolated from `main`

- Release Branch (Preparation)

What it is: A buffer branch used to polish, test, and bug-fix a version of the software before it goes live.

How strategies use it: GitFlow heavily relies on release branches to freeze features while QA tests the build. 

GitHub Flow does not use release branches at all, as testing is fully automated before merging to main

### Git Branching Strategy ###

**Git branching** is the practice of creating isolated copies of a codebase to develop features, fix bugs, or test ideas without affecting the main production code.

**4 Essential Git Branching Techniques**

**GitFlow**: A strict, structured model featuring two long-lived branches (**main** for production, **develop** for pre-production) and temporary branches (**feature, release, hotfix**). Ideal for traditional enterprise software with scheduled release cycles.

**GitHub Flow**: A lightweight, agile model where all development happens on short-lived feature branches created directly off **main**. Features are continuously integrated and deployed to production immediately after merging. Ideal for web apps and Continuous Deployment (CD).

**GitLab Flow**: A variant that adds environment-driven branches (e.g., **production, pre-production**) or release-driven branches to GitHub Flow. Ideal for teams that need to deploy to distinct staging and production environments at different times.

**Trunk-Based Development**: Developers merge small, frequent updates directly into a single central branch (**trunk or main**) multiple times a day. It eliminates long-lived branches and heavily relies on automated testing and "feature flags" to hide unfinished code. Ideal for high-velocity teams practicing true Continuous Integration (CI).

Here are the essential commands organized by the order you will use them.1. Starting a Repositorygit init: Turns your current local folder into a brand-new Git repository.git clone <url>: Copies an existing remote repository (like from GitHub) down to your computer.2. The Daily Workflow (Save Your Work)git status: Shows you the current state of your folder (which files are modified or unsaved).git add <file_name>: Prepares a specific file to be saved. (Think of this as putting an item into a moving box).git add .: Prepares all modified and new files in your folder at once.git commit -m "your message": Permanently saves your prepared changes to your local history with a descriptive note. (Think of this as taping the moving box shut and labeling it).3. Sharing & Syncing Codegit push origin main: Sends your locally committed changes up to your remote repository (like GitHub) so others can see them.git pull: Downloads and merges the newest changes from the remote repository down to your computer.4. Branching Basics (Working Safely)git branch: Lists all the branches in your project.git checkout -b <branch_name>: Creates a brand-new branch and switches you into it immediately so you can experiment safely.git checkout <branch_name>: Switches your workspace back to an existing branch.5. Checking Your Historygit log: Shows a chronological list of all the commits (saves) made in the project so far.

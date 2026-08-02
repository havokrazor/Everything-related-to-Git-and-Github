1) **How to initialize or create a git repo?**
   
   -That can be done using the `git init` command that turns that specific directory you're in a local git repository.

2) **How to track a file in git through CLI? and see the difference someone has made in that file?**
   
   -Using the `git add filename` you can add the file to be tracked, and if someone made changes in it you can use `git diff` to see the change done.
    you can also use `git status` so see any overall changes as well.

3) **What is the first command you run whenever you make any changes in the file?**

   -You run the command called as `git add filename` to save any changes in the file , if you do just `git add` without the file name , all the change for
    all files will be saved.

**Note - `git add` only prepares the file and temporarily saves it in a stating area of sort, but `git commit` permanently saves those prepared files into 
your official project history with a descriptive message. _The staging area acts as a safety net. Once you use `git add`, you can run `git diff --cached` 
to see exactly what you are about to save before you commit it._**

4) **How to push the changes done in your local repo to Github or any other distributed file system?**
   
   -You can do that by doing `git push` to push the changes done in the local repo to Github or any other distributed file system.

5) **What is the git workflow you use in your organization?**
   
   -So the answer to that question is `git add && git commit -m && git push` or
    When answering this in an interview, use this structure instead:
   
    -**Branching Strategy**: "We use GitHub Flow, where main is always deployable.
    -**Feature Management**: "We create a new branch for every task or bug fix.
    -**Code Quality**: "Once complete, we open a Pull Request (PR) for peer review and CI/CD testing.
    -**Deployment**: "After approval, we merge the PR into main for deployment."

6) **What can you do if you create a local repo and the `git push` does not work?**
   
   -You can use the command called `git remote add "remote-repo-name"`

7) **How to pull code from Github? or how cloning is done?**
   
   - `git clone repo-link` helpes you pull the code from github and also created a link between the local and remote repo so you don't need to run
     `git remote add`.
   - You can also do this via SSH by generating a public/private key using the `ssh keygen -t rsa` and then adding this ssh key in your github profile.

8) **What is the difference between `git clone` vs `git fork`?**

   -In simple words fork is used to create a copy of the repository and clone is used to download the repository.
   
   -**Git Fork:**
            -Location: Happens entirely on the remote hosting service (GitHub, GitLab, Bitbucket).
   
            -Ownership: Creates a personal copy of someone else's project under your own account.
   
            -Purpose: Used to propose changes to an open-source project via a Pull Request (PR).Command: None. You click a "Fork" button on the website interface.
   
   -**Git Clone:**
            -Location: Downloads a repository from a remote server to your local machine.
   
            -Ownership: Links directly back to the source repository you copied it from.
   
            -Purpose: Used to actually start working on the code, compile it, and run it locally.Command: Run via terminal: git clone <repository-url>.
   
   -In practice, you often use them together:
   
            -Fork a project on GitHub to get your own remote copy.
   
            -Clone your forked repository to your laptop to write code.
   
            -Push changes back to your fork.
   
            -Open a Pull Request to merge your changes into the original project.
   

9) **What is the best way to create a branch? with `git branch` or `git checkout -b`?**
       
       -The best way for most developers is `git checkout -b <branch-name>` (or the modern equivalent `git switch -c <branch-name>`).
      
       -`git checkout -b` Creates the new branch and immediately switches you to it, Saves a step and Prevents you from accidentally making commits on your main branch.
         `git checkout branch-name` is also used to switch branches.
      
       -`git branch` Creates the new branch but leaves you sitting on your current branch. It is Good if you want to create multiple branches ahead of time without moving.

10) **What is `git log`?**
       -talk about git log or git log branch-name and git checkout branch-name && git log , gitlog --oneline
       - `gitlog` : When run on its own without arguments, git log shows the commit history for your currently checked-out branch (where your HEAD is pointing).
       - `git log branch-name` :This allows you to peek into another branch's history without switching branches.
         
Behavior: Git prints the commit history starting from the tip of branch-name down through its parent commits.
Why use it? You save time and context-switching overhead. If you are currently on main and want to check what your teammate committed on feature-login, you don't need to leave main

       - `git checkout branch-name && git log` : This is a two-step sequence using the && operator (which only runs the second command if the first succeeds):
git checkout branch-name: Changes your active branch (updates HEAD and replaces the files in your working directory to match branch-name).
git log: Displays the log for that newly checked-out branch.

11) **Which one is better to merge the branches together? `git merge` or `git rebase` or `git cherry-pick`?**

   -**`git merge` (The Safest & Easiest):**
       -How it works: Combines the target branch into your current branch by creating a brand-new "merge commit".
       
       -Best for: Finalizing a feature and bringing it into the main or production branch.
       
       -Pros: Preserves the true, chronological history of exactly when and how code was written. It is non-destructive.
       
       -Cons: Can make your Git history look messy and chaotic (a "train track" effect) if many developers merge at once.

   -**`git rebase` (The Cleanest History):**
       -How it works: Lifts your local commits, temporarily sets them aside, catches up to the latest target branch, and then reapplies your commits on top.
       
       -Best for: Keeping your own local feature branch up-to-date with main before you merge.
       
       -Pros: Creates a perfectly straight, linear project history that is incredibly easy to read.
       
       -Cons: Rewrites Git history. Never use this on public branches shared with other developers, as it can cause massive sync conflicts for your team.

   -**`git cherry-pick` (The Surgical Strike):**
       -How it works: Grabs a single, specific commit from any branch and copies it onto your current branch.
       
       -Best for: Hotfixes or undoing a mistake (e.g., you accidentally committed a bug fix to the wrong branch and want to pull just that fix over).
       
       -Pros: Highly precise. You don't have to bring over an entire branch just to get one piece of code. You can use `git log` copy the commit ID and merge with the               desired branch.
       
       -Cons: Creates duplicate commits, which can confuse Git later if you eventually try to merge the full branches.

*__Note - Choose `git merge` if you are ready to merge a completed feature into the main team branch.Choose `git rebase` if you want to update your solo feature branch with the latest team changes.Choose `git cherry-pick` if you only need one specific fix out of a long list of commits.__*
   
12) **How to handle merge conflits?**
    
    -Find Conflicted Files using `git status` , Look for files listed under "Both modified".
    
    -Open and Fix the Files marked "Both modified" in your code editor. Edit the code to keep what you want and delete these Git markers:
    
    `<<<<<<< HEAD`
    `=======`
    `>>>>>>>`

    Talk to your teammate if you are unsure whose code is correct.Delete the lines of code you want to discard.Keep the lines of code you want to save.Delete the Git            markers (<<<<<<<, =======, >>>>>>>).

    -Stage the Fixed Files by running `git add <file-name>`.

    -Finish the Process If you were merging: `git commit -m "Fix merge conflict"` or If you were rebasing: `git rebase --continue`

    -Emergency Abort (Undo Everything) - To cancel a merge: `git merge --abort` or To cancel a rebase: `git rebase --abort`

13) **Is Git a distributed or Centralised version control system? and what is the difference between them?**
    
    -Git is a distributed version control system (DVCS).
    
    -The difference between them is that Centralised Version Control (e.g., SVN) Contains the only full history of the project. Developers only download a single snapshot        of the files.
    
    -You cannot commit, view history, or branch without connectivity and If the central server crashes, you lose the historical data.
    
    -In Distributed Version Control (e.g., Git) Every developer clones a full copy of the entire repository history locally. You can commit, create branches, and view logs       completely offline and there is no single point of failure due to it being a distributed system.

15) **What are the Git commands that you use to commit changes to your remote repository?**
    
    -I use the command such as `git status` to check which files are modified , then `git add filename` , then `git commit -m` and then `git push`.

16) **What is the difference between `git fetch` and `git pull`?**
    
    - `git fetch` can only get the information or changes done to the remote repository it does not merge it into your local repository, whereas `git pull` does two commands
      by doing `git fetch` and `git merge` by default. It downloads data from the remote repository and merges it into the local branch.

17) **What is .git and .gitignore?**
    
    - `.git` is a hidden folder created when you run `git init`. It tracks and store everything including history, metadata, config files and more. If this folder is deleted
      then you lose everything in your local repository.
      
    -`.gitignore` is a file that you can manually create in the root directory and it can contain list , files, keys that you can git to ignore and do not track and               prevents it from being committed or staged.

18) **What are pre-commit hooks and post-commit hooks?**
    
    -Git hooks are automated scripts that run before or after specific actions in the Git lifecycle. They live in the `.git/hooks/` directory.
    
    -The difference between these 2 are as follows,
    
     -**Pre-commit Hooks**
    
      -When they run: Right before you type a commit message, before the commit is actually created.
    
      -Purpose: Code quality and security checks.Common
    
      -Uses: Running linters, executing unit tests, formatting code, or checking files for accidentally exposed AWS secret keys.
    
      -Behavior: If the script fails (returns a non-zero exit code), Git aborts the commit.
    
     -**Post-commit Hooks**
    
      -When they run: Immediately after the commit is successfully created.
    
      -Purpose: Notification and automation triggering.
    
      -Common Uses: Sending a Slack notification to the team, triggering a local build, or logging information.
    
      -Behavior: It cannot affect the outcome of the commit because the commit has already happened.

19) **What is webhook?**
    
    -A github webhook automated workflows by letting other applications know the instant something changes on your GitHub repository.
    
    -It sends real-time HTTP POST notifications from GitHub to an external server whenever a specific repository event occurs.
    
    -For example :  specific action happens on GitHub (e.g., a code push, a new pull request, or an issue comment).
    GitHub packages the details of that event into a JSON payload. It instantly sends an HTTP POST request to an external URL you configure.
     Your external system (like a CI/CD tool) receives the payload and immediately triggers an automated task.
    
    -Another example would you that you run git push, GitHub tells Jenkins or AWS CodePipeline, and your automated build starts immediately.

19)**How to push and pull changes to git?**

    - To push changes you do `git push` and to pull changes to local you do `git pull`

20) **What is git stash and talk about it's use case?**

    -`git stash` temporarily saves any changes you have done to the file, so you can work on something else and then use `git stash pop` to remove the latest stashed changes from the stack and reapplies them to your current branch you can continue working.
    
    -For example : You are halfway through writing a feature on a feature branch, and your code is broken/incomplete. Suddenly, an urgent bug hits production. You cannot         commit your incomplete work, but you need to switch branches immediately to fix the bug. Then you can run `git stash` to clear your workplace, switch to main, fix and       deploy the bug, switch back to your feature branch, and run `git stash pop` to resume exactly where you left off.
    
    -Other exmaples : You want to pull the latest code from GitHub using `git pull`, but Git blocks you with an error because your local, uncommitted changes conflict with the incoming remote changes. Solution: You run git stash to safely save your work, run `git pull` to successfully update your branch, and then run `git stash pop` to reapply your work on top of the fresh code.
    
    -You accidentally start writing code directly on the main branch instead of a dedicated feature branch. You realise your mistake before committing. Solution: You run `git stash`, checkout to a new branch `(git checkout -b feature-xyz)`, and run `git stash pop`. Your work is now safely on the correct branch.

22) **What is the difference between `git clone` and `git fork`?**
    
    -The core difference is that `git fork` creates a complete copy of someone else's GitHub repository under your own GitHub account.
    
    -Whereas `git clone` downloads an existing Git repository (whether it is yours, a team repo, or a forked repo) from a remote server down to your local machine.

    -How devops use it : You **fork** the original repository on GitHub to your own account. You **clone** your forked repository down to your laptop to write code. You          commit and push back up to your fork. You open a **pull request** from your fork to the original repository.

23) **How to amend a commit in git?**
    
    -Amending is nothing but to you want to add something to an existing commit you made or fix a typo. To amend your most recent commit in Git, you use the `--amend` flag.

    -If your code is fine but you made a typo in the last commit message, run this command: `git commit --amend -m "Your new and corrected commit message"`.
    
    -If you already committed but realized you forgot to stage a file or missed a line of code: `git add forgotten-file.txt` and `git commit --amend --no-edit` 


      



   
   

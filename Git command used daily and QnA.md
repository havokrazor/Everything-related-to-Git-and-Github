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

8) What is the difference between `git clone` vs `git fork`?

   -In simple words fork is used to create a copy of the repository and clone is used to download the repository.
   
   -Git Fork:
            -Location: Happens entirely on the remote hosting service (GitHub, GitLab, Bitbucket).
   
            -Ownership: Creates a personal copy of someone else's project under your own account.
   
            -Purpose: Used to propose changes to an open-source project via a Pull Request (PR).Command: None. You click a "Fork" button on the website interface.
   
   -Git Clone:
            -Location: Downloads a repository from a remote server to your local machine.
   
            -Ownership: Links directly back to the source repository you copied it from.
   
            -Purpose: Used to actually start working on the code, compile it, and run it locally.Command: Run via terminal: git clone <repository-url>.
   
   -In practice, you often use them together:
   
            -Fork a project on GitHub to get your own remote copy.
   
            -Clone your forked repository to your laptop to write code.
   
            -Push changes back to your fork.
   
            -Open a Pull Request to merge your changes into the original project.
   

   9) What is the best way to create a branch? with `git branch` or `git checkout -b`?
       
       -The best way for most developers is `git checkout -b <branch-name>` (or the modern equivalent `git switch -c <branch-name>`).
      
       -`git checkout -b` Creates the new branch and immediately switches you to it, Saves a step and Prevents you from accidentally making commits on your main branch.
      
       -`git branch` Creates the new branch but leaves you sitting on your current branch. It is Good if you want to create multiple branches ahead of time without moving.
      



   
   

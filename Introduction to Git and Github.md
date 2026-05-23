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

GitFlow: A strict, structured model featuring two long-lived branches (**main** for production, **develop** for pre-production) and temporary branches (**feature, release, hotfix**). Ideal for traditional enterprise software with scheduled release cycles.

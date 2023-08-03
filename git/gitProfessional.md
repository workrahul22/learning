
#### The Perfect Commit
```bash
    git add css/general.css
    git diff index.html
    git add -p index.html # to select a chunk inside a file and add it to staging area
```

#### The perfect commit message
1. subject = concise summary of what happend
2. body = more detailed explanation
    - what is now different than before
    - what's the reason for the change
    - Is there anything to watch out for / anything particularly remarkable

```bash
    git commit # after running this command a file will get opened
    # in this file the first line will be considered as the subject of the commit
    # after the first line put a blan line and that will seperate the subject from the body of the commit message
```

#### Branching Strategies
##### Agree on a branching workflow in your team
1. git allows you to create branches - but it doesn't tell you how to use them!
2. you need a written best practice of how work is ideally structured in your team - to avoid mistakes & collisions.
3. It highly depends on your team / team size, on your project, and how you handle releases.
4. It helps to onboard new team members ("this is how we work here").

Type of branches.
1. feature branch
2. develop/producttion/staging branch
3. release branch

Long Running branches
1. exist through the complete lifetime of the project.
2. often, they mirron "stages" in your dev life cycle.
3. common convention: no direct commits!

Short Lived Branches.
1. for new features, bug fixes, refactoring, experiments.
2. will be deleted after integration (merge/rebase)

Example of Branching Strategies
1. Github Flow
    - very simple, very lean: only one long-running branch ("main") + feature branches.
2. Gitflow
    - more structure, more rules
    - long-running: "main" + "develop"
    - short-lived: features, releases, hotfixes

The Best branching model
    - consider your project, release cycle, and team
    - take inspiration from existing models (gitflow, github flow)
    - and create your own model!

#### Pull Request
- Communicating About and Reviewing Code
- A pull request invites reviewers to provide feedback before merging
- Contributing code to other Repositories
    - creating a Fork of the original repository, where you can make changes
    - and suggest those changes to be included via a pull request

#### Merge Conflicts
How and when conflicts occur
    - when integrating commits from different sources
        - git merge
        - git rebase
        - git pull
        - git cherry-pick
        - git stash apply
    - when contradictory changes happen
How to know when a conflict has occurred
    - Don't worry: Git will tell you

```bash
    git merge <branch-name>
    git merge --abort # undo merge conflict
    git rebase --abort # undo rebase
```

### Merge vs Rebase
How a merge works
    - common ancestor
    - last commit of branch A
    - last commit of branch B
    - the merge will combine these three commits
    - a special case of this will be fast-forward merge
    - merge commit gets created automatically by git

How Rebase works
    - a straight line of commits
    - git rebase branch-B
    - it will remove all the commit from branch A and saved it temproraly somewhere
    - now git apply branch b 
    - now the temproary changes from branch a will be added on top of branch b changes
    - it rewrites commit history

Warning notice
- do not use rebase on commits that you've already pushed/shared on a remote repository!
- instead, use it for cleaning up your local commit history before merging it into a shared team branch





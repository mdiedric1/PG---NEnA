- [How to contribute (developer guide)](#how-to-contribute-developer-guide)
  - [Branching scheme](#branching-scheme)
  - [Example workflow with git bash](#example-workflow-with-git-bash)

# How to contribute (developer guide)

## Branching scheme
A general minimal branching scheme is shown below:

```mermaid
%%{init: { 'logLevel': 'debug', 'theme': 'dark', 'themeVariables': {
              'commitLabelColor': '#ffffff'} } }%%
gitGraph
    commit id: "Initial Commit" type: HIGHLIGHT tag: "v0.1.0"
    branch continuous_development
    checkout continuous_development
    commit
    branch feature/task_1
    commit
    commit
    checkout continuous_development
    branch chore/task_2
    checkout chore/task_2
    commit
    commit
    checkout continuous_development
    merge feature/task_1 id: "v1.0.0"
    merge chore/task_2 id: "v1.1.0"
    checkout main
    merge continuous_development type: HIGHLIGHT tag: "v1.1.0"
    checkout continuous_development
    branch hotfix/task_3
    checkout hotfix/task_3
    commit
    checkout continuous_development
    merge hotfix/task_3 id: "v1.1.1"
    checkout main
    merge continuous_development type: HIGHLIGHT tag: "v1.1.1"

```

'main' receives increments/releases (direct commits are prohibited).
'continuous_development' receives continuous feature updates.
Branches like 'feature/task_n' as well as 'hotfix/task_m' are the work task branches. 
Users will adapt/update their code and commit their changes here.
In order to update 'main' with the content of the task based branches, a review process is engaged via a
'Pull Request' in Github.

## Example workflow with git bash

**Target:** Create a *feature* branch from *main*
```bash
git checkout main
git pull origin main
git checkout -b feature/<small_content_description>
```

**Target:** Commit your changes

At first you need to add your changes. In case that you don't want to commit your whole workspace of changes,
you can manually stage your files and commit them to your local repository afterwards.
```bash
git add ./path/to/your/file
git commit -m "This is a meaningful commit message"
```

In case that you just want to add and commit all changes you can go with
```bash
git commit -a -m "This is a even more meaningful commit message"
```
instead.

Now you committed your changes to your local repository. In order to sync that with the remote repository,
you need to push your changes to the remote server
```bash
git push origin feature/<small_content_description>
```

This process is repeated until you close your branch e.g. via a merge to the main branch.
Then you create another branch for the next feature.



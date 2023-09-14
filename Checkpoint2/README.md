# CSP451-Azure-Project

# Checkpoint 2 Submission

- **COURSE INFORMATION: CSP451NIA**
- **STUDENT’S NAME: Kenneth Chu**
- **STUDENT'S NUMBER: 158945204**
- **GITHUB USER_ID: 158945204-myseneca**
- **TEACHER’S NAME: Atoosa Nasiri**

---
### Table of Contents
1. [Part A - Adding Files - Local Repo Workflow](#part-a---adding-files---local-repo-workflow)
2. [Part B - Inspecting Local Repo with `git status` and `git log`](#part-b---inspecting-local-repo-with-git-status-and-git-log)
3. [Part C - Creating & Merging Branches](#part-c---creating--merging-branches)
4. [Part D - Git Branching Strategy Review Question](#part-d---git-branching-strategy-review-questions)

---

### Part A - Adding Files - Local Repo Workflow
Make sure to use the exact names and follow the exact steps as this assignment will be automatically marked and if your work deviates from the instructions you will receive no marks.

Work from local VS Code. Clone you repo CSP451-Azure-Project in your laptop or any other code development environment you use. You are not allowed to work from remote though browser or from local. You must use local repo in your laptop and azure.You can use any IDE of your choice, though the preferred option in this course is Microsoft VS Code.
In your CSP451-Azure-Projectfolder run command ls -la and make sure you can see the .git hidden folder that contains all the git workflow information.
Make a directory Checkpoint2. In this directory create a file README.me. Add below lines to README.md and update with your details:

### Checkpoint2 Submission

- **COURSE INFORMATION: xxx**
- **STUDENT’S NAME: xxx**
- **STUDENT'S NUMBER: xxx**
- **GITHUB USER ID: xxx**
- **TEACHER’S NAME: xxx**

Save your changes in the working directory and run git status. If it shows that you have un-tracked files then copy the output into git_status_untracked.txt by running the command git status > git_status_untracked.txt You will need content of this file as part of your submission.

The [git_status_untracked.txt](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/9d7b4de1c7ddf26858b260bc2c0cf13018d83d97/Checkpoint2/git_status_untracked.txt) file can be found here.

Add your files to staging area and run git status. If it shows that you have files to be committed then copy the output into git_status_uncommitted.txt by running the command git status > git_status_uncommitted.txt You will need content of this file as part of your submission

The [git_status_uncommitted.txt](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/9d7b4de1c7ddf26858b260bc2c0cf13018d83d97/Checkpoint2/git_status_uncommitted.txt) file can be found here.

Commit your work to local repository work with comment "adds Checkpoint2/README.md" and run git status. If it shows that your local repo is one commit ahead of origin/main then copy the output into git_status_committed.txt by running the command git status > git_status_committed.txt You will need content of this file as part of your submission

The [git_status_committed.txt](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/9d7b4de1c7ddf26858b260bc2c0cf13018d83d97/Checkpoint2/git_status_committed.txt) file can be found here.

Push your changes to remote and run git status. Make sure the output is "Everything is up to date". Run git log -n 5 to get the details of your last commit.

The README.md file that contains the output of `log -n 5` can be found [here](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/9d7b4de1c7ddf26858b260bc2c0cf13018d83d97/Checkpoint2/emojis/README.md)

---

## Part B - Inspecting Local Repo with `git status` and `git log`

You can use `git status` command to understand the status of the files in your working directory, staging area and local repo. You can use `git log` command to get list of your commit history. How do these two commands differ?

### The difference between git status and git log is that

**git status** - helps users understand the current state of their working directory in relation to their local repository.

Indicates which files have been staged for the next commit


**git log** - provides a detailed history of commits in the repository.

```
commit b3181d606a1d9efba3845ecc2fd2c1c09d5ded87 Author: Ken Chu kchu29@myseneca.ca Date: Wed Sep 13 13:29:23 2023 -0400

Adds emojis to feat-emojis branch
```

---

## Part C - Creating & Merging Branches

1. Work from local VS Code. Make sure you are working in the folder specific to this assignment.
2. Create a sub-folder called `footnotes`
3. Copy the files [rendered-footnote.png](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/895d70821972e79e48aefa1eda43c006044efbb4/Checkpoint2/footnotes/rendered-footnote.png) and [tips-footnote.md](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/895d70821972e79e48aefa1eda43c006044efbb4/Checkpoint2/footnotes/tips-footnote.md) to your `footnotes` folder
4. Navigate through the files and understand what it does, you might need it in future assignments
5. Push your changes to remote: `add`, `commit`, `push` your work with comment _"adds footnotes folder"_
6. Work from local VS Code. Make sure you are working in the folder specific to this assignment.
7. Create a branch using command `git branch feat-emojis`
8. Start working in your branch by `git checkout feat-emojis`
9. Confirm you are working in you recently created branch by `git branch`. There would be a `*` beside active branch.
10. Create a folder called `emojis`
11. Copy the files [emojis-rendered.png](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/895d70821972e79e48aefa1eda43c006044efbb4/Checkpoint2/emojis/emoji-rendered.png) and [tips-emojis.md](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/895d70821972e79e48aefa1eda43c006044efbb4/Checkpoint2/emojis/tips-emojis.md) to `emojis` folder
12. Navigate through the files and understand what it does, you might need it in future assignments
13. Push your changes to remote: `add`, `commit`, `push` your work with comment _"adds emojis to feat-emojis branch"_
14. Go to GitHub web page and look into `feat-emojis` branch and compare it with `main`. You should see the `emojis` folder and its content in `feat-emojis` branch but not in `main`
15. Merge `feat-emojis` to `main`. For this, you need to first `git checkout main` and then `git merge feat-emojis`. Run `git log -n 5`, you will need this for your submission.

### The output of the `git log -n 5` can be found [here](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/4917a69218033ad384279949cd600118dea463bf/Checkpoint2/emojis/README.md) ###

---

## Part D - Git Branching Strategy Review Questions

<img src="https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/08a6f3f8615894d46b7893c0b43a9b9dd5757c04/Checkpoint2/images/branching-conventions.png"
     alt="Branching Conventions"
     style="left; margin-right: 10px;" height="500"/>

It is important to understand the naming conventions in branching when you are part of a large team. Conventional color coding and naming help tracking changes easier. In some cases, if you do not follow the syntax, your features can never find their way to release branch.

Read though [Git Branching Strategy](./GitStrategies/README.md). Answer below questions in your `README.md`. Your answers can be one-two paragraphs. Try to elaborate but remain brief and to the point. **If you copy answers from internet or other students your mark for this assignment would be zero.**

### 1. What are the differences between `develop` branch and `main` branch?

We can consider the 'main' branch as the production or release-ready branch. It contains stable production-ready code that is redy for deployment. The 'develop' branch resembles a development area where individuals can work with one another to create ideas and address issues as a team before moving it towards the 'main' branch.

In simple terms, the 'main' branch serves as the finished product whereas the 'develop' branch is where experimentation and adjustments occur before being brought forth to the 'main' branch.


### 2. What are the three supporting branches? Briefly describe the function of each of these supporting branches.

Three supporting branches may include:

Feature branches
Created for specific new features or bug fixes. Each feature branch focuses on a specific piece of work, making it easier to manage and collaborate on new features without disrupting the 'develop' branch. These branches are merged back into 'develop' after the feature is complete.

Release branches
Release branches are used to prepare for a new production release. The code in the release branch is tested and fine-tuned before it is ready for deployment. When the release branch is complete, it is merged into both'main' to establish a new production release and 'develop' to include any final-minute adjustments.

Hotfix branches
Hotfix branches are created to address critical issues or bugs in the production code found after a release. These branches allow for immediate fixes to be made without interfering with ongoing development in 'develop.' Once the hotfix is complete, it's merged into both 'main' and 'develop' to ensure that the issue is resolved in both places.

### 3. What are the best practices in working with `release` branches?

When handling 'release' branches, keeping things organized will help any software releases go smoothly. In order to do so, one can provide `release` branches with clear names such as `release/1.0.0,` and create them from the latest `develop` code. When working on the `release` branch, it is important that we focus on fixing bugs, ensuring that everything works, avoiding adding any new features. It is then recommended that we test the heck out of it, including unit tests, integrations, and user checks. It is also important that we keep the version numbers updated to match the release, and to keep any documentation and release notes up to date. After it's all set, merge it into both main for the new release and develop for ongoing work, by using the pull feature. Once you're done, it's a good idea to clean up and delete that release branch to keep things tidy. Keeping the team in the loop and automating where possible helps to smoothen the process as well.

This information is based on this [GitStrategies](https://github.com/158945204-myseneca/CSP451-Azure-Project/tree/2a222080d8e14aa9318b100f02806ae9d9bdaac9/Checkpoint2/GitStrategies) and this [link](https://learn.microsoft.com/en-us/azure/devops/repos/git/git-branching-guidance?view=azure-devops)
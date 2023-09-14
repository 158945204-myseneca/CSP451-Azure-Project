# Git Branching Strategy

# Acknowledgements
This page is a cope from [Git branching Strategies GitHub Repo](https://gist.github.com/jpolete/aa31b9043e8e90f8a47c7738669555fa#file-git-branching-strategy-md)

## Quick Legend

| Branch | Name | Notes |
|---|---|---|
| Stable | master | Accepts merges from Release and Hotfix branches only.|
| Development | develop | Accepts merges from Feature/Bugfix, Release and Hotfix | 
| Features/Bugfix | feat-* / bug-* | Always branch off HEAD of develop |
| Hotfix | hotfix-* | Always branch off master. Merges back into master and develop.|
| Release | release-* | Always branches off develop. Last minute  changes for release.|

## Main Branches

The main repository will always hold two evergreen branches:

* `master`
* `develop`

Consider `origin/master` the source for shippable, production code. The HEAD of this branch is always the latest code deployed to production, tagged with a version number. Only hotfix branches are ever cut from this. 

Consider `develop` as the active development branch. As a developer, your work will entail creating feature and bugfix branches off of `develop`, working on the issue, and finally merging back into develop. The HEAD of `origin/develop` will always be the latest state of development destined for the next release.

## Supporting Branches

Supporting branches are used to aid parallel development between team members, ease tracking of features/bugs, and to assist in quickly fixing live production problems. Unlike the main branches, these branches have a limited life span, and will be removed eventually.

The different types of supporting branches are:

* Feature/Bugfix branches
* Hotfix branches
* Release branches

Each of these branches has a specific purpose and is bound to strict rules as to which branches may be their originating branch and which branches must be their merge targets. Each branch and its usage is explained below.

*Note: When merging supporting branches always use the —no-ff flag to force the merge to create a new commit object. This keeps the historical information from your feature/bugfix branch. Alternatively use pull requests over simple merging to enable discussion and code review*

### Feature Branches

Feature branches are used when developing a new feature or enhancement. When starting development, the deployment in which this feature will be released may not be known. No matter when the feature branch will be finished, it will always be merged back into the develop branch.

During the lifespan of the feature development, the lead should watch the `develop` branch (network tool or branch tool in GitHub) to see if commits have been made since the feature was branched. Changes to `develop` should be merged into the feature before merging back to `develop`; this can be done at various times during feature branch work or at the end, right before merging into develop. Regardless time to handle merge conflicts should be accounted for and those conflicts should be handled in the feature branch before merging into develop.

* Must branch from: `develop`
* Must merge back into: `develop`
* Branch naming convention: `feat-issue-<id>`

Example: `feat-issue-27`

#### Working with a feature branch

If the branch does not exist yet (check with the Lead), create the branch locally and then push to GitHub. A feature branch should always be 'publicly' available. That is, development should never exist in just one developer's local branch.

```
// create a local branch for the new feature
$ git checkout -b feature-branch develop  

// push to remote and set local branch to track it
$ git push -u origin feature-branch       
```

Periodically, changes made to `develop` (if any) should be merged back into your feature branch.

```
// merges changes from develop into feature branch
$ git merge develop    
```

For longer running feature branches you should periodically push your changes to make them available to everyone. Push active work at the end of each day at least. 

```
// make sure you're on feature branch
$ git checkout feature-branch

// push to origin
$ git push  
```

When development on the feature is complete, [the Lead] should merge changes into develop and delete the feature branch. 

```
// checkout the feature branch locally
$ git checkout --track origin/feature-branch  

// change to the develop branch
$ git checkout develop         
                 
// merge, making sure to create a commit object during merge
$ git merge --no-ff feature-branch 

// push merge changes    
$ git push origin develop

// deletes the remote branch
$ git push origin :feature-branch             
```

*As an alternative to manually merging like this, the developer can make a pull request in Github to enable discussion and code review before merging.*

### Bugfix Branches

Bug branches differ from feature branches only semantically. Bug branches will be created when there is a bug that should be fixed and merged into the next deployment. For that reason, a bug branch typically will not last longer than one deployment cycle. Additionally, bug branches are used to explicitly track the difference between bug development and feature development. No matter when the bug branch will be finished, it will always be merged back into `develop`.

* Must branch from: `develop`
* Must merge back into: `develop`
* Branch naming convention: `bug-issue-<id>`

Example: `bug-issue-34`

#### Working with a bugfix branch

See “Working with a feature branch” above. Bugfix and feature branches work identically and only differ semantically.

### Hotfix Branches

A hotfix branch comes from the need to act immediately upon an undesired state of a live production version. Additionally, because of the urgency, a hotfix is not required to be pushed during a scheduled deployment. Due to these requirements, a hotfix branch is always branched from a tagged `master` branch. This is done for two reasons:

* Development on the `develop` branch can continue while the hotfix is being addressed.
* A tagged `master` branch still represents what is in production. At the point in time where a hotfix is needed, there could have been multiple commits to `develop` which would then no longer represent production.

* Must branch from: tagged `master`
* Must merge back into: `master` and `develop`
* Branch naming convention: `hotfix-issue-<id>`

#### Working with a hotfix branch

If the branch does not exist yet (check with the Lead), create the branch locally and then push to GitHub. A hotfix branch should always be 'publicly' available. That is, development should never exist in just one developer's local branch.

```
// creates a local branch for the new hotfix
$ git checkout -b hotfix-branch master  

// makes the new hotfix remotely available
$ git push -u origin hotfix-branch      
```

When development on the hotfix is complete, [the Lead] should merge changes into `master` and then update the tag.

```
// Pull down hotfix branch
$ git checkout origin/hotfix-branch 

// Change to master
$ git checkout master               

// Ensure it's up to date
$ git pull                          

// Merge w/commit object
$ git merge --no-ff hotfix-branch   

// tags the fix
$ git tag -a v0.0.0                 

// push changes w/tag
$ git push origin master --tags     
```

Merge changes into `develop` so not to lose the hotfix and then delete the remote hotfix branch.

```
// change to develop branch
$ git checkout develop             

// Ensure it's up to date
$ git pull              
           
// Merge w/commit object
$ git merge --no-ff hotfix-branch  

// push merge changes
$ git push origin develop          

// delete the remote branch
$ git push origin :hotfix-branch   
```

### Release Branches
Release branches are short-lived branches strictly used to prepare for a release. A release branch should be created when all of the feature and bugfix branches planned for this release have been merged into the develop branch and it’s almost ready for release. Use the release branch to bump the version number and do any last minute housekeeping.

Once the release branch is ready, merge into `master` and tag the version, then merge back into `develop` so that your working copy is up to date with the latest release. Version numbering should use [semantic versioning](http://semver.org/)

* Must branch from: tagged `develop`
* Must merge back into: `master` and `develop`
* Branch naming convention: `release-<semver>`

Example: `release-1.0.0`

#### Working with a release branch
If the branch does not exist yet (check with the Lead), create the branch locally and then push to GitHub. A release branch should always be ‘publicly’ available. That is, development should never exist in just one developer’s local branch.

```
// creates a local branch for the new release
$ git checkout -b release-branch develop   

// makes the new hotfix remotely available             
$ git push -u origin release-branch        
```

When final changes to the release branch are complete, [the Lead] should merge changes into `master` and tag the release.

```
// pull down release branch
$ git checkout origin/release-<semver>

// change to master
$ git checkout master                

// ensure it's up to date
$ git pull                           

// merge w/commit object
$ git merge --no-ff release-branch   

// tag the release
$ git tag -a v1.0.0                 

// push changes w/tag
$ git push origin master --tags      
```

## Workflow Diagram

![Git Branching Model](http://nvie.com/img/git-model@2x.png)  
Methodology and image from [Vincent Driessen’s Gitflow](http://nvie.com/posts/a-successful-git-branching-model/)

## Resources and Further Reading

-  [Vincent Driessen’s Gitflow model](http://nvie.com/posts/a-successful-git-branching-model/)
-  [Atlassian’s Git Workflow Comparison](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) (covers feature branch and Gitflow)
-  [Branching standards and conventions (digitaljhelms)](https://gist.github.com/digitaljhelms/4287848) (Similar to Gitflow)
-  [Github Flow](https://guides.github.com/introduction/flow/)

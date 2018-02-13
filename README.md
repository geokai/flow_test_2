## manual flow use

This repo is a test-bed for the use of a manual flow implementation and
evaluation of its use methods.

The work-flow is taken from [A successful Git branching
model](http://nvie.com/posts/a-successful-git-branching-model/) by Vincent
Driessen.

The branches:
- master - maintains released verions, infinite branch
- develop - continual in-development branch, infinite branch
- feature - development of featured code, short life span branch
- release - preparation of release version, short life span branch
- hot-fix - bug fixing, short life span branch

The following command groups are used in support of the the main
constant branches, master and develop.

### Creating a Feature Branch
Feature branches are short-lived, existing only as long as their development\
$ git checkout -b feature/myFeature develop\
_Switched to a new branch 'feature/myFeature'_\
(development of feature branch)

### Incorporating a finished feature on develop
$ git checkout develop\
_Switched to branch develop_\
$ git merge --no-ff feature/myFeature\
(merges feature branch into develop using recursion method)\
$ git branch -d feature/myFeature\
(feature branch deleted)\
$ git push origin develop


### Creating a release branch
Release branches are short-lived, existing only during the release preparation time.\
The use of a dedicated release branch removes the _release responsibility_ from the develop\
branch, allowing it to be continally developed.\
$ git checkout -b release-1.2 'develop'\
_Switched to a new branch 'release-1.2'_\
$ ./bump-version.sh 1.2\
(files modified to reflect release version and any minor amends/bug-fixes made)\
$ got commit -a -m "Bumped version number to 1.2, fixes, clean-up"

### Finishing a release branch
$ git checkout master\
_Switched to branch 'master'_\
$ git merge --no-ff release-1.2\
_Merge made by recursive_\
$ git tag -a release-1.2\
_Annotated tag to mark release_\
$ git checkout develop\
_Switched to branch 'develop'_\
$ git merge \__no-ff release-1.2\
_Merge made by recursive_\
$ git branch -d release-1.2\
_Deleted branch 'release-1.2'_

Graph log mode can be used to display branching.\
The recursive merge mode is used to maintain a historical record of feature and release branches.


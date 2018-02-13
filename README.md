## manual flow use

This repo is a test-bed for the use of a manual flow implementation and
evaluation of its use methods.

The various work-flow commands are taken from [A successful Git branching
model](http://nvie.com/posts/a-successful-git-branching-model/) by Vincent
Driessen

The following command groups are used in suupport of the the main
constant branches, master and develop.

### Creating a Feature Branch
$ git checkout -b feature/myFeature develop
_Switched to a new branch 'feature/myFeature'_
(development of feature branch)
### Incorporating a finished feature on develop
$ git checkout develop
_Switched to branch develop_
$ git merge --no-ff feature/myFeature_
(merges feature branch into develop using recursion method)
$ git branch -d feature/myFeature_
(feature branch deleted)
$ git push origin develop


### Creating a release branch
$ git checkout -b release-1.2 'develop'
_Switched to a new branch 'release-1.2'_
$ ./bump-version.sh 1.2
(files modified to release version and any minor amends/bug-fixes)
$ got commit -a -m "Bumped version number to 1.2, fixes, clean-up"
### Finishing a release branch
$ git checkout master
_Switched to branch 'master'_
$ git merge --no-ff release-1.2
_Merge made by recursive_
git tag -a release-1.2
_Annotated tag to mark release_
$ git checkout develop
_Switched to branch 'develop'_
$ git merge __no-ff release-1.2
_Merge made by recursive_
$ git branch -d release-1.2
_Deleted branch 'release-1.2'_

- run graph log mode to see branching


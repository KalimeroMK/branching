### Main branches

At the core, the development model is greatly inspired by existing models out there, especially gitflow. The central
repo holds two main branches with an infinite lifetime with **develop being the default branch:**

- `master` - Always reflects a production-ready state.

- `develop`- Always reflects a state with the latest delivered development changes for the next release.

When the source code in the develop branch reaches a stable point and is ready to be released, all of the changes should
be merged back into master and then **tagged with a release number.**

### Supporting branches

Our development model uses a variety of supporting branches to aid parallel development between team members, ease
tracking of features, prepare for production releases and to assist in quickly fixing live production problems. **These
branches should be short lived to ensure the best development experience.**

The different types of branches we may use are:

- Feature branches
- Bugfix branches
- Hotfix branches

**FEATURES:**

Use to develop new features starting from the `develop` branch. Merge back into `develop` branch waiting for a
reasonable amount of features to be there before declaring it a release.

```
Create Branch:
$ git checkout -b feature/my-feat develop

Merge Changes:
$ git checkout develop
$ git merge --no-ff feature/my-feat
$ git branch -d feature/my-feat
$ git push origin develop
```

**BUGFIXES:**

Use to work on bugfixes starting from the `develop` branch. Merge back into `develop` branch waiting for a reasonable
amount of bugs to be there before declaring it a minor release.

```
Create branch:
$ git checkout -b bugfix/my-issue develop

Merge Changes:
$ git checkout develop
$ git merge --no-ff bugfix/my-issue
$ git branch -d bugfix/my-issue
$ git push origin develop
```

**HOTFIXES:**

The `hotfix` branch starts off `master` to avoid involuntary send to production of unwanted features that my be present
in branches. The `hotfix` must be used when an important bug arises in production which must be fixed and can't wait for
other features to be ready. It merges back to `master` and `develop`.

```
Create Branch:
$ git checkout -b hotfix/1.2.1 master
$ ./bump-version.sh 1.2.1
$ git commit -a -m "Bumped version number to 1.2.1"

Merge Changes:
$ git checkout master
$ git merge --no-ff release-1.2
$ git tag -a 1.2

Also:
$ git checkout develop
$ git merge --no-ff hotfix-1.2.1
```

####Ideal Commit Tree:

<p align="center">
  <img src="https://wac-cdn.atlassian.com/dam/jcr:34c86360-8dea-4be4-92f7-6597d4d5bfae/02%20Feature%20branches.svg?cdnVersion=69">
  <span>fig: Git Flow Commit Tree</span>
</p>

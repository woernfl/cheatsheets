# Git

## Basic actions

Clone a remote repo:

```bash
git clone $REMOTE_REPO_URL
```

Get the status of your repo:

```bash
git status
```

Get the status of your repo listing all the files:

```bash
git status -u
```

Stage a change:

```bash
git add $FILE_PATH
```

Choose chunks of code you want to stage:

```bash
git add -p $FILE_PATH
```

Commit a change and sign it:

```bash
git commit -s -m "$COMMIT_MESSAGE"
```

Add new changes to the last commit:

```bash
git commit --amend
```

Push your change to a remote repo:

```bash
git push -u origin $BRANCH_NAME
```

Create a branch:

```bash
git checkout -b $BRANCH_NAME
```

Search some code in the git history:

```bash
git rev-list --all | xargs git grep -F ‘$STRING_TO_SEARCH’
```

## Standardise commit messages

Using [Commitizen](https://github.com/commitizen/cz-cli) to have a common format.

Install `commitizen` globally:

```bash
npm install -g commitizen
```

Install the commitizen adapter globally:

```bash
npm install -g cz-conventional-changelog
```

Create a `.czrc` file in the home directory, with the path referring to the preferred, globally-installed, `commitizen` adapter:

```bash
echo "{ \"path\": \"$(npm root -g)/cz-conventional-changelog\" }" > ~/.czrc
```

Now, use `git cz`to handle the commit.

Here is are the type of changes that you can commit:

- `feat:` A new feature
- `fix:` A bug fix
- `docs:` Documentation only changes
- `style:` Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
- `refactor:` A code change that neither fixes a bug nor adds a feature
- `perf:` A code change that improves performance
- `test:` Adding missing or correcting existing tests
- `chore:` Changes to the build process or auxiliary tools and libraries such as documentation generation

## Check differences

Check all changes since last commit:

```bash
git diff --color-words
```

Check changes since last commit for a specific file:

```bash
git diff --color-words HEAD $PATH_TO_FILE
```

Check changes between two commits:

```bash
git diff --color-words $COMMIT_NUMBER $COMMIT_NUMBER
```

Check changes between two commits for a specific file:

```bash
git diff --color-words $COMMIT_NUMBER $COMMIT_NUMBER $PATH_TO_FILE
```

Check changes between two branches:

```bash
git diff --color-words $BRANCH_NAME $BRANCH_NAME
```

Check changes between two branches for a specific file:

```bash
git diff --color-words $BRANCH_NAME $BRANCH_NAME $PATH_TO_FILE
```

Check stages changes:

```bash
git diff --staged
```

## Commit history managment

Check commit history:

```bash
git log --oneline --graph --color
```

Better git log:

```bash
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

Check commit history with changes:

```bash
git log -p
```

Add file change to the last commit:

```bash
git commit --am -s -m "$COMMIT_MESSAGE"
```

Count the number of commits on a specific branch:

```bash
git rev-list --count $BRANCH_NAME
```

## Branch managment

Delete local branch:

```bash
git branch -d $BRANCH_NAME
```

Delete remote branch:

```bash
git push origin --delete $BRANCH_NAME
```

Pulls the changes from the remote branch to the local branch and makes a merge:

```bash
git pull origin $BRANCH_NAME
```

Rebase a base branch in current branch:

```bash
git rebase $BASE_BRANCH
```

Rebase a remote branch in current branch:

```bash
git pull --rebase --autostash origin master
```

Rename a branch:

```bash
git branch -m $BRANCH_OLD_NAME $BRANCH_NEW_NAME
git push origin :$BRANCH_OLD_NAME $BRANCH_NEW_NAME
git push origin -u $BRANCH_NEW_NAME
```

Copy a file from a branch to the current one:

```bash
git checkout $BRANCH_TO_COPY_FROM $PATH_OF_THE_FILE_TO_COPY
```

Delete local branch that has been deleted remotely:

```bash
git branch --merged master | grep -E -v "master|main" | xargs -n 1 git branch -d
```

Delete local branch that are not `master`:

```bash
git branch | grep -E -v "master|main" | xargs -n 1 git branch -d
```

## Start a new git repository

```bash
git init
git add .
git commit -m "First commit"
git remote add origin $REPO_URL
git push -u origin master
```

## Config managment

To set the default config to be used, used `git config --global --edit`:

```bash
[color]
     ui = true
[alias]
     lop = log --pretty=format:"%C(yellow)%h %Cred%ad %Cblue%an%Cgreen%d %Creset%s" --date=short
     lod = log --graph --decorate --pretty=oneline --abbrev-commit --all
     ls = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate
     lsp = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate -p
     ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
```

Check current config:

```bash
git config -l
```

Set username for the repo:

```bash
git config user.name "$NAME"
```

Set username globally:

```bash
git config --global user.name "$NAME"
```

Set email for the repo:

```bash
git config user.email "$EMAIL"
```

Set email globally:

```bash
git config --global user.email "$EMAIL"
```

Set a GPG key to be used to sing commits:

```bash
gpg --list-secret-keys --keyid-format LONG
# Copy the GPG key ID that starts with sec
git config user.signingkey 30F2B65B9246B6CA
# Automatically sign commits
git config commit.gpgsign true
```

Set GPG program to use (usefull to solve `gpg: signing failed: secret key not available`):

```bash
git config --global gpg.program gpg2
```

Enable credential helper to not have to retype your password each time you want to do something:

```
git config credential.helper store 
```

## Submodules

Clone repo with submodules (5 submodules at once):

```
git clone --recursive --jobs 5 $GIT_SUBMODULE_REPO_URL
```

Pull all the submodules updates:

```
git pull --recurse-submodules
```

Create a submodule:

```
git submodule add -b master --name $SUBMODULE_NAME $GIT_SUBMODULE_REPO_URL $SUBMODULE_PATH
```

Delete a submodule:

```
# Delete the relevant section from the .gitmodules file
git add .gitmodules
git submodule deinit $PATH_TO_SUBMODULE
git rm $PATH_TO_SUBMODULE
git commit -m "Removed submodule"
rm -rf .git/modules/$PATH_TO_SUBMODULE
```

## Tips and tricks

I committed and immediately realized I need to make one small change:

```bash
# make your change
git add . # or add individual files
git commit --amend --no-edit
```

I accidentally committed something to master that should have been on a new branch:

```bash
# create a new branch from the current state of master
git branch $SOME_NEW_BRANCH
# remove the last commit from the master branch
git reset HEAD~ --hard
git checkout $SOME_NEW_BRANCH
# your commit lives in this branch now
```

I accidentally committed to the wrong branch:

```bash
# undo the last commit, but leave the changes available
git reset HEAD~ --soft
git stash
# move to the correct branch
git checkout $NAME_OF_THE_CORRECT_BRANCH
git stash pop
git add . # or add individual files
git commit -m "your message here";
# now your changes are on the correct branch
```

I need to undo the last commit:

```bash
git revert --no-edit HEAD
# git will create a new commit that undoes the last commit
```

I need to undo a commit from like 5 commits ago:

```bash
# find the commit you need to undo
git log
# use the arrow keys to scroll up and down in history
# once you've found your commit, save the hash
git revert --edit [saved hash]
# git will create a new commit that undoes that commit with the message you will have specified
```

I need to undo a commit from like 5 commits ago:

```bash
# find the commit you need to undo
git log
# use the arrow keys to scroll up and down in history
# once you've found your commit, save the hash
git revert --no-edit [saved hash]
# git will create a new commit that undoes that commit
```

I need to undo a commit from like 5 commit ago, and I want to review the changes made by the revert statement before committing them:

```bash
# find the commit you need to undo
git log
# use the arrow keys to scroll up and down in history
# once you've found your commit, save the hash
git revert --no-commit [saved hash]
# git will not create a new commit that undoes that commit
```

I need to undo my changes to a file:

```bash
# find a hash for a commit before the file was changed
git log
# use the arrow keys to scroll up and down in history
# once you've found your commit, save the hash
git checkout [saved hash] -- path/to/file
# the old version of the file will be in your index
git commit -m "Wow, you don't have to copy-paste to undo"
```

Thanks to Frumusanu Razvan for this [tricks](https://medium.com/faun/stop-headaches-from-git-3829210d2a31)

Trigger the CI without making changes to the code base:

```bash
git commit --allow-empty -s -m "Trigger CI"
```


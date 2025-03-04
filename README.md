# Git Recipes

## Table of Contents

* [Move a Repo from one Host to Another](#move-a-repo-from-one-host-to-another)

## Move a Repo from one Host to Another

* We have a repo on Gitlab and we want to move that repo to Github.
* We want to preserve all tags and branches.

```shell
# Clone the gitlab repo with the mirror argument.
# Note that we are creating a bare repo, ie. no working directory, just the .git directory.
git clone --mirror git@gitlab.com:owner/directory/repo.git local-repo/.git

cd local-repo
git config --unset core.bare

# Create a working directory and check out the files.
git checkout main

# Create a new repo on github website.
# Add the github repo as another remote.
git remote add github git@github.com:owner/directory/repo.git
git push github

# Alternatively, we can also just replace origin with a new url.
git remote set-url origin git@github.com:owner/directory/repo.git
```




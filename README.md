The aim of this tutorial is to help you understand the *git cherry-pick* command.

### Introduction

The _cherry-pick_ command can be used when you are using different versions of documentation and/or software. In order to help you imagine a use case for the command, here is a real example. Say that you have just released version 1.2 of a piece of software and you patch a bug but this bug is also present in 1.1. You can cherry-pick the commits you made in 1.2 and put them also on the 1.1 branch.

### Typical workflow

Commit changes, make a PR and merge to master. Note that your the project you are working on may have a different workflow.
1. On master branch, run `git pull` to ensure the changes that have merged to master.
2. On master, run `git log` in Terminal. Verify that changes that you want are there.
3. Check which commit hash/hashes are relevant and you want to have on the previous version of software as well.
4. Move to the branch, where the older version of the software is located i.e. `git checkout 1.1`.
5. Make sure you have the last commit on this branch. Run the command: `git pull`.

#### One commit
Run the following command in Terminal:
> git cherry-pick _hash_of_desired_commit_

#### Multiple commits
This is slightly more complex you need to specify a range.
> git cherry-pick _hash_of_commit_before_your_first_desired_commit_.._your_last_desired_commit_

#### After cherry-pick

1. At this point, you might have a conflict to deal with, in which case run `git status`, find out if there are any merge conflicts and choose which version you would like to keep.
2. You will also need to do `git add` and `git commit`. It might also be necessary to run: `git cherry-pick --continue`.
3. Finally verify that the right commits are in the branch you have specified by running the command `git log`. Now you can push your changes: `git push`.

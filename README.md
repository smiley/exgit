# exgit
**Ex**tends the functionality of **Git** with some useful commands &amp; shortcuts.

## Description
This is a collection of custom commands &amp; aliases for common Git workflow actions. They either add new functionality to the git command line (e.g.: GitHub-integrated features) or ease use of some common, yet tedious commands (like updating another branch).

### The problem
Git has a lot of functionality, some of which isn't even in use by most users. Worse, some commands are *very* useful for that same group of people, but aren't accessible or overly-daunting.

For example, when most people want to merge with/rebase against `master`, they switch to it (`git checkout`), update it (`git pull`), switch back (`git checkout`) and `merge`/`rebase`. This gets worse if they have any uncommited changes that clash with `master`, and they can't really afford to commit them now because they're half-baked. So they `git stash` them, do the thing, and `git stash pop` them.

Those are a lot of commands, and the sheer amount tends to discourage people from using the CLI. Except, there's an *easier* option -- calling `git fetch origin master:master`. But it's not easily-accessible, nor is it obvious. To compensate, `exgit` offers the aptly-named alias, [`git update [remote] <branch>`](/docs/README.md#git-update).

Another issue is force-pushing a branch. You force-push a branch by manually-specifying the source branch, destination branch & remote. (The branch name is specified to ensure only *that* branch is force-pushed, no matter the config) Even if the branch names are identical and it's for `origin`, you still have to run `git push --force origin feature/add-very-important-functionality:feature/add-very-important-functionality`. If your organization leads a policy of squashing or clean, semantic commits, this gets tedious -- fast.

Instead, `exgit` offers [`git pushf`](/docs/README.md#git-pushf). This force-pushes the current branch to `origin` and also asks for confirmation before. (manually-specifying remotes will be supported later)

### The solution
`exgit` aims to solve this problem with semantic, clear, obvious aliases for these actions. Like `git update`, or `git pushf`. As a bonus, it also comes with some workflow-supporting commands that aren't part of git, like [`git pull-request`](/docs/README.md#git-pull-request).

## Requirements & OS Support
Every command is made to be cross-platform by being written as a shell script (for simple ones) or as a Python script (for more complicated, "enhanced" commands). However, PR-searching for [`git pull-request`](/docs/README.md#git-pull-request) is currently only supported on Windows, due to making use of Windows' saved credential system (where querying for credentials doesn't require a username). This will later be supported on Mac & Linux.

**tl;dr:**
- Git 2.0+
- Python 2.7
  - `GitPython` for all Python-based commands
  - `keyring` for `git-pull-request`
- Any OS that runs git
  - **Temporary:** Windows-only for PR searches in `git-pull-request` (you can still create PRs, though)

## Help
- [Documentation](docs/README.md)

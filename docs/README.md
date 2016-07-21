# `exgit` documentation

You've reached the documentation for `exgit` (short for **Ex**tended **Git**). This is where help text & command descriptions are saved. (and soon available via `--help` as well)

## Commands

### [`git pull-request`](git-pull-request)
#### `$ git pull-request`
Open the pull request creation screen right from your command line. If a PR already exists, (and you have GitHub credentials saved via the Git Credentials Helper) *it* is opened instead.

### [`git pushf`](git-pushf)
#### `$ git pushf [-y]`
Force-update the current branch, and only it. Asks for confirmation before actually running the `push` command, unless the `-y` option is used.

You can also [configure this command](#user-content-exgitpushfassertusernameinbranch) to validate your "ownership" of the branch before pushing it. Currently, this means having the branch stored "in" your branch folder. (ex: `johndoe/fix-bugs`) Later, this will be adjusted to account for GitHub forks. (Though that'd require making sure your forced-update will not rewrite commits originating from the fork's parent)

### [`git update`](git-update)
#### `$ git update [<options>] [[<remote>] <local_branch>]`
Fast-forward a branch without checking it out first. Essentially, an alias for `git fetch <REMOTE> <REMOTE_BRANCH>:<LOCAL_BRANCH>`.

## General configuration
### `git config` variables
#### `exgit.username`
**Type:** String

Your GitHub username (or semantic username; e.g.: your in-company username), used to enhance some commands. For example, branch ownership validation in `git-pushf` uses this to ensure you're force-pushing only into branches you "own".

#### `exgit.pushf.assertUsernameInBranch`
**Type:** Boolean

Asserts that the branch name starts with your username before `push --force`ing into it. Requires [`exgit.username`](#user-content-exgitusername).

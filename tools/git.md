# Git

Git is an open source version control system, which supports your development tasks, especially in distributed code projects.

## Installation

### MacOS

On MacOS, Git can be installed by using the [Homebrew](https://brew.sh/) package manager:

```sh
brew install git
```

Or by installing the XCode command line tools. This can be done by executing the following command:

```sh
xcode-select --install
```

### Linux

On Linux, Git can be easily installed on Linux systems with the available package managers.

E.g. for Debian based systems:

```sh
apt install git
```

### Windows

On Windows, Git can be installed by downloading the installer from the [download page of Git](https://git-scm.com/downloads).

Or by using the winget package manager:

```pwsh
winget install git
```

### Others

For more information, see [download page of Git](https://git-scm.com/downloads).

## Configuration

Git can be configured by the CLI using the `git config` command. For first configuration it is necessary to configure at least the parameters `user.name` and `user.email`. This
can be done by the following commands:

```bash
git config --global user.name "MyFancyUser"
```

```bash
git config --global user.email "developer@mydomain.com"
```

## Using Git

The following commands can be helpful for working with `git`.

### Basic commands

| Git Command | Comment |
| --- | --- |
| `git init` | Initialize a directory as git managed repository |
| `git clone <url>` | Clone a remote repository to your local client |
| `git status` | Shows uncommited changes, new files etc. |
| `git add <file>` | Stage an updated / new file to the next commit |
| `git rm <file>` | Remove a file and stage the removal for the next commit |
| `git commit -m "message"` | Commit staged changes under a new commit |
| `git commit` | Will open an editor to write more descriptive commit messages. See [here](https://cbea.ms/git-commit/) for a guide on good commit messages |
| `git log` | Shows a list of commits in the current branch |
| `git log --pretty=oneline` | Shows a list of commits in the current branch in one line |
| `git log --patch` | Shows a list of commits in the current branch with the changes |
| `git reset <commit>` | Reset the current branch to the given commit |
| `git reset --hard <commit>` | Reset the current branch to the given commit and discard all changes |
| `git reset --soft <commit>` | Reset the current branch to the given commit and keep all changes staged |
| `git checkout <branch>` | Switch to another branch |
| `git branch` | Shows a list of existing branches |
| `git branch <branch>` | Creates a new branch (from the currently checked out branch) |
| `git merge <branch>` | Merge changes from `branch` to the currently checked out branch |
| `git push` | Push commited changes to the remote repository |
| `git pull` | Pull current state from the remote repository to your local repo |

### Working with git-flow

Git-flow assists you by combining multiple steps of `git` commands to one `git-flow` command
which will do a workflow of steps. Although `git-flow` makes live easier in some cases,
it makes it also more complex sometimes and you need to execute some steps before or after using
a `git-flow` command as regular `git` command. (See below)

As an example, here is the comparison between the regular `git` commands and the appropriate
`git-flow` command for creating a release.

| git-flow command                                    | git command                                           |
| --------------------------------------------------- | ----------------------------------------------------- |
| `git-flow feature start <feature_name>`             | `git checkout -b feature/<feature_name> develop`      |
| `git-flow feature finish <feature_name> [--squash]` | `git checkout develop`                                |
|                                                     | `git merge [--squash] --no-ff feature/<feature_name>` |
|                                                     | `git branch -d feature/<feature_name>`                |

Another `git-flow` cheat sheet can be found [here](https://danielkummer.github.io/git-flow-cheatsheet/).

## Using git-crypt

Having secret or sensitive information in your git repository is never a good choice. But
sometimes it's necessary. Never push unencrypted data to your remote repository.

Git-crypt is a transparent encryption tool that works seamless with your Git repository. All sensitive
information is encrypted before pushed to the remote repository. Once you've unlocked the
repository locally, all data will be decrypted automatically when pulling from the remote
repo. This makes development with encrypted data effortless.

To install git-crypt, you can use your package manager of choice (e.g. `apt`):

```bash
sudo apt install git-crypt
```

To initialize a new repository with git-crypt, you can use `git-crypt init` when located in the
repository directory. An already encrypted git repository can be unlocked by `git-crypt unlock`.
This requires you to have either the repository encryption key in your GPG keychain, or that
your private GPG key has been added to the allowed keys in the repository. For more details,
see the links below.

For more information, check out the official Github repository [here](https://github.com/AGWA/git-crypt).
A tutorial on git-crypt can be found [here](https://thedatabaseme.de/2022/04/13/lets-keep-this-our-secret-transparent-git-encryption-using-git-crypt/).
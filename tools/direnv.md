# Direnv

Direnv is an extension for your shell. It augments existing shells with a new feature that can load and unload [environment variables](linux/environment-variables-in-linux.md) depending on the current directory.

---
## Installation

Install Direnv on Mac OS, Windows or Linux, by following the [official direnv installation docs](https://direnv.net/docs/installation.html).

**Example on Mac OS**:
```zsh
brew install direnv
```

For direnv to work properly it needs to be hooked into the shell. Each shell has its own extension mechanism. Follow the [official direnv hook docs](https://direnv.net/docs/hook.html).

**Example on zsh**:
```zsh
eval "$(direnv hook zsh)"
```

---
## Getting started

Create a new `.envrc` file with your environment variables.

**Example `.envrc` file**:
```zsh
export ENVVAR="test"
export ENVVAR2="test2"
```

Allow the current directory in **direnv**.

```zsh
direnv allow .
```


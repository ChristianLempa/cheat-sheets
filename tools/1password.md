# 1Password

1Password is a password manager that provides ability to store various passwords, important documents, secure notes and more.
It supports user-friendly Web interface, as well as macOS, Windows, Linux, iOS, and Android applications.
But also it has *command line interface*, so it can be in use for any application and system to store secure information.

**Note:** 1Password is not free to use, but it provides various pricing plans for personal, family, and business usage.

## Installation

To install 1Password on your device, please follow the [installation link](https://1password.com/downloads/).

## 1Password-CLI

With 1Password CLI, you can automate administrative tasks and load secrets straight from your command line and in your scripts.

### CLI Installation

Install 1Password-CLI on macOS, Windows or Linux, by following the [official 1password-cli installation docs](https://developer.1password.com/docs/cli/get-started#install).

**Example on Mac OS**:
```zsh
brew install --cask 1password/tap/1password-cli
```

### Sign In

To sign in to 1Password CLI with the accounts you've added to the 1Password desktop app, navigate to Developer settings in the app and select "Connect with 1Password CLI". You'll need to add new accounts to the app to use them on the command line if this option is enabled. Follow the [official 1password-cli installation docs](https://developer.1password.com/docs/cli/get-started#sign-in).

If you don't want to connect 1Password CLI and the 1Password app, you'll need to add each account to 1Password CLI manually before you can sign in to it.

```zsh
op account add
```

1Password CLI will prompt you to enter your account details.

After you've added your account, you can sign in to it.

```zsh
eval $(op signin)
```

### Basic Usage

Most useful commands:

| op command                         | Comment                                      |
| ---------------------------------- | -------------------------------------------- |
| `op --help`                        | Get list of all possible commands and flags  |
| `op account get`                   | Get details about your account               |
| `op user list`                     | Get list of users                            |
| `op vault list`                    | Get details for all vaults                   |
| `op item get <itemName>`           | Get details about an item                    |


### Environment Variables

It is possible to load secrets from 1Password directly to environment variables.
It can be done by using 1Password CLI, which provides options to load secret values either to environment variable directly, or to `.env` file.
For detailed instruction on how to set up process to load secrets from 1passwords, use to [the official documentation]([1Password-CLI](https://developer.1password.com/docs/cli/secrets-environment-variables/#step-1-create-secret-references)).

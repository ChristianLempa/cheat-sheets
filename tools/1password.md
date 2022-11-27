# 1Password
WIP

## Installation
WIP


---
## 1Password-CLI

With 1Password CLI, you can automate administrative tasks and load secrets straight from your command line and in your scripts.

### Installation

Install 1Password-CLI on Mac OS, Windows or Linux, by following the [official 1password-cli installation docs](https://developer.1password.com/docs/cli/get-started#install).

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
WIP

### Environment Variables
WIP

---

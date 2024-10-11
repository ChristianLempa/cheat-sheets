# Environment Variables in Linux

| Variable | Description |
| --- | --- |
| `$HOME` | Home directory of the current user |
| `$PWD` | Present working directory |
| `$USER` | Current user |
| `$SHELL` | Current shell |
| `$PATH` | List of directories to search for executable files |
| `$EDITOR` | Default text editor |
| `$LANG` | Default language |
| `$HOSTNAME` | Hostname of the computer |

## Setting Environment Variables

| Command | Description |
| --- | --- |
| `export VAR=value` | Set an environment variable |
| `export VAR=value1:value2` | Set an environment variable with multiple values |
| `export VAR=$VAR:value` | Append a value to an environment variable |
| `unset VAR` | Remove an environment variable |
| `env` | Display all environment variables |
| `printenv` | Display all environment variables |
| `echo $VAR` | Display the value of an environment variable |

## Parameter Expansion

| Command | Description |
| --- | --- |
| `${VAR}` | Value of the variable `VAR` |
| `${VAR:-value}` | Value of `VAR` if set, otherwise `value` |
| `${VAR:=value}` | Value of `VAR` if set, otherwise `value` and set `VAR` to `value` |
| `${VAR:?message}` | Value of `VAR` if set, otherwise print `message` and exit |
| `${VAR:+value}` | Value of `value` if `VAR` is set, otherwise nothing |

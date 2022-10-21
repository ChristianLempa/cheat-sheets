# LogCLI

Go [here](../README.md) to setup Loki

## Install

Install the binary:

```
$ wget https://github.com/grafana/loki/releases/download/v1.6.1/logcli-darwin-amd64.zip
$ unzip logcli-darwin-amd64.zip
$ sudo mv logcli-darwin-amd64 /usr/local/bin/logcli
```

Configure the environment:

```
$ export LOKI_ADDR=https://loki.domain.com
$ export LOKI_USERNAME=x
$ export LOKI_PASSWORD=x
```

## Discover Labels

```
$ logcli labels
__name__
cluster_name
container_name
environment
job
```

Vew all the job labels:

```
$ logcli labels job
dev/dockerlogs
prod/dockerlogs
```

## Analyze Labels

```
$ logcli series '{job="dev/dockerlogs"}' --analyze-labels
Total Streams:  5
Unique Labels:  4

Label Name      Unique Values  Found In Streams
container_name  5              5
cluster_name    1              5
environment     1              5
job             1              5
```

## Query

Query by label value:

```
$ logcli query '{job="dev/dockerlogs"}'
```

Query by label value and match filter expression:

```
$ logcli query '{job="dev/dockerlogs"} |= "this string"'
```

Query by label value and dont match filter expression:

```
$ logcli query '{job="dev/dockerlogs"} != "this string"'
```

Query by label value and regex match filter expression:

```
$ logcli query '{job="dev/dockerlogs"} |~ "this string: (true|false)"'
```

Query by label value and dont match regex filter expression:

```
$ logcli query '{job="dev/dockerlogs"} !~ "this string and .+"'
```

Tail:

```
$ logcli query '{job="dev/dockerlogs"}' --tail
```

Since 4h ago:

```
$ logcli query '{job="dev/dockerlogs"}' --since 4h
```

Last 10 lines:

```
$ logcli query '{job="dev/dockerlogs"}' --last 10
```

Piping:

```
$ logcli query '{job="dev/dockerlogs"} |= "error"' | grep -i message
```

Suppress log labels:

```
$ logcli query -q '{job="dev/dockerlogs"}'
```

Change output:

```
$ logcli query -o raw '{job="dev/dockerlogs"}'
```

## More

For more detailed tutorials have a look at my blog at [blog.ruanbekker.com](https://blog.ruanbekker.com/blog/archives/)

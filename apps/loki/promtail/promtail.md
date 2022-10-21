## Examples
- https://gist.github.com/ruanbekker/c6fa9bc6882e6f324b4319c5e3622460
- https://sbcode.net/grafana/install-promtail-service/
- https://www.bookstack.cn/read/loki/clients-promtail-pipelines.md
- https://github.com/grafana/loki/issues/333#issuecomment-570651075 (parsing labels from log tag)
- https://docs.docker.com/config/containers/logging/configure/      (^ related) 
- https://github.com/grafana/loki/issues/775#issuecomment-568814165 (create labels from filename)
- https://www.gitmemory.com/issue/grafana/loki/748/534945463 (drop logs from something)
- https://github.com/cyriltovena/loki/blob/master/docs/clients/promtail/stages/match.md#example (drop logs from match)
- https://www.youtube.com/watch?v=bIAC0uQee0k (using promtail with loki)
- https://grafana.com/docs/loki/latest/clients/promtail/scraping/
- https://grafana.com/blog/2020/07/13/loki-tutorial-how-to-set-up-promtail-on-aws-ec2-to-find-and-analyze-your-logs/

## Current Issues

- https://github.com/grafana/loki/issues/74 (multi-line)
- https://github.com/grafana/loki/issues/1880 (malformed logs with slashes)

## LogQL
- https://github.com/grafana/loki/blob/master/docs/logql.md

## Pipelines

More Info: 
  - https://github.com/grafana/loki/blob/master/docs/clients/promtail/pipelines.md
  - https://github.com/grafana/loki/blob/master/docs/clients/promtail/stages/template.md

### Transform

> The pipeline example below, takes the current value of level from the extracted map and converts its value to be all lowercase. For example, if the extracted map contained level with a value of INFO, this pipeline would change its value to info"

Pipeline Transform example, change uppercase values to lowercase (INFO to info):

```
scrape_configs:
  - job_name: app1
    static_configs:
    - targets:
        - localhost
      labels:
        job: app1
        environment: production
        host: app1.mydomain.com
        service: app1
        __path__: /var/log/app1_*.log
    pipeline_stages:
    - match:
        selector: '{service="app1"}'
        stages:
        - regex:
            expression: "(?P<level>(INFO|WARNING|ERROR))(.*)"
        - template:
            source: level
            template: '{{ ToLower .Value }}'
        - labels:
            level:
```

Convert from stdout to info, stderr to error:

```
  pipeline_stages:
  - regex:
      expression: '(?P<level>(stdout|stderr))'

  - template:
      source: level
      template: '{{ if eq .Value "stdout" }}{{ Replace .Value "stdout" "info" -1 }}{{ else if eq .Value "stderr" }}{{ Replace .Value "stderr" "error" -1 }}{{ .Value }}{{ end }}'
```

### Drop

In this scenario, we want to drop specific logs to not appear in loki

Ref: https://github.com/cyriltovena/loki/blob/master/docs/clients/promtail/stages/match.md#example

```
- job_name: qa/docker
  entry_parser: raw
  static_configs:
  - targets:
      - localhost
    labels:
      job: preprod/docker
      service: app1
      __path__: /var/lib/docker/containers/*/*-json.log

scrape_configs:
  pipeline_stages:
  - match:
      pipeline_name: 'drop_elb_healthchecks'
      selector: '{service="app1"} |= "ELB-HealthChecker"'
      action: drop

  - match:
      pipeline_name: 'drop_ecs_agent_logs'
      selector: '{service="app1"} |~ ".*(Managed task|Task engine).*" |~ "arn:aws:ecs:eu-west-1:000000000000:task"'
      #selector: '{service="app1"} |~ ".*Managed task.*" |= "eu-west-1:000000000000:task"'
      action: drop

  - match:
      pipeline_name: 'drop_blackbox_exporter_checks'
      selector: '{service="app1"} |~ ".*Go-http-client.*" |= "GET /login"'
      action: drop
```

### Docker log opt tag

```
scrape_configs:

- job_name: system
  static_configs:
  - targets:
      - localhost
    labels:
      job: varlogs
      __path__: /var/log/*log

- job_name: containers
  entry_parser: raw

  static_configs:
  - targets:
      - localhost
    labels:
      job: containerlogs
      __path__: /var/lib/docker/containers/*/*log

  # --log-opt tag="{{.ImageName}}|{{.Name}}|{{.ImageFullID}}|{{.FullID}}"
  pipeline_stages:

  - json:
      expressions:
        stream: stream
        attrs: attrs
        tag: attrs.tag

  - regex:
      expression: (?P<image_name>(?:[^|]*[^|])).(?P<container_name>(?:[^|]*[^|])).(?P<image_id>(?:[^|]*[^|])).(?P<container_id>(?:[^|]*[^|]))
      source: "tag"

  - labels:
      tag:
      stream:
      image_name:
      container_name:
      image_id:
      container_id:
```

### Containers with File Workaround

Taken from [here](https://github.com/grafana/loki/issues/333#issuecomment-637401983)

```
docker ps --format '- targets: ["{{.ID}}"]\n  labels:\n    container_name: "{{.Names}}"' > /etc/promtail/promtail-targets.yaml
```

```
scrape_configs:
- job_name: containers
  entry_parser: docker
  file_sd_configs:
  - files:
    - /etc/promtail/promtail-targets.yaml
  relabel_configs:
  - source_labels: [__address__]
    target_label: container_id
  - source_labels: [container_id]
    target_label: __path__
    replacement: /var/lib/docker/containers/$1*/*.log
```

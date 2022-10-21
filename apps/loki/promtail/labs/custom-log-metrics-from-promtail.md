Setup promtail config:

```
$ cat /etc/promtail/promtail-config.yml
server:
  http_listen_port: 9080
  grpc_listen_port: 0

positions:
  filename: /var/lib/promtail/positions.yaml

clients:
  - url: https://x:x@loki.domain.com/loki/api/v1/push

scrape_configs:
  - job_name: prod/logs
    static_configs:
    - targets:
        - localhost
      labels:
        job: prod/logs
        service: nginx-test
        logtype: info
        __path__: /var/log/nginx/access.log
    pipeline_stages:
    - match:
        selector: '{job="prod/logs", service="nginx-test"}'
        stages:
        - regex:
            expression: '.*(?P<hits>GET /.*)'
        - metrics:
            nginx_get_hits:
              type: Counter
              description: "Total GET requests"
              source: hits
              config:
                action: inc

```

Verify that you can access the metrics endpoint:

```
$ curl http://localhost:9080/metrics
# HELP promtail_custom_nginx_get_hits Total GET requests
# TYPE promtail_custom_nginx_get_hits counter
promtail_custom_nginx_get_hits{filename="/var/log/nginx/access.log",job="prod/logs",logtype="info",service="nginx-test"} 801
```

Now we can configure prometheus to scrape this endpoint, I am using [ec2_sd_config](https://prometheus.io/docs/prometheus/latest/configuration/configuration/#ec2_sd_config):

```
scrape_configs:
  # promtail-exporter
  - job_name: promtail-exporter
    scrape_interval: 15s
    ec2_sd_configs:
    - region: eu-west-1
      port: 9100
      filters:
        - name: tag:PromtailScrape
          values:
            - Enabled
    relabel_configs:
    - source_labels: [__meta_ec2_private_ip]
      replacement: '${1}:9080'
      target_label: __address__
    - source_labels: [__meta_ec2_tag_Name]
      target_label: instance
```

Tag the EC2 instance as `PromtailScrape` => `Enabled` and verify that prometheus is scraping promtail with the following in prometheus:

```
up{job="promtail-exporter"}
```

You can also view all the metrics from that exporter with:

```
{__name__=~".+", job="promtail-exporter"}
```

Now we can query our exported metric:

```
increase(promtail_custom_nginx_get_hits{service="nginx-test"}[5m])
```

Let’s say for some reason you want to alert if that value goes over 5000:

```
  - name: loki-metric-alert
    groups:
      - name: loki_metric_alert
        rules:
        - alert: nginx_get_hits
          expr: sum(increase(promtail_custom_nginx_get_hits{service="nginx-test"}[5m])) > 5000
          for: 2m
```

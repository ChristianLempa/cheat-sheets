# Loki

Loki is a horizontally scalable, highly available, multi-tenant log aggregation system inspired by Prometheus. It is designed to be very cost effective and easy to operate. It does not index the contents of the logs, but rather a set of labels for each log stream.

The Loki project was started at [Grafana](../grafana.md) Labs in 2018, and announced at KubeCon Seattle. Loki is released under the AGPLv3 license.

## Blogposts about Loki

- https://rtfm.co.ua/en/grafana-labs-loki-logs-collector-and-monitoring-system/
- [Using Fluentd and Loki on Docker](https://dev.to/thakkaryash94/docker-container-logs-using-fluentd-and-grafana-loki-a15)
- [Log Monitoring and Alerting with Loki](https://www.infracloud.io/blogs/grafana-loki-log-monitoring-alerting/)

## Dashboards for Grafana

- https://grafana.com/grafana/dashboards/12019

## Get Started

You can refer to the following to get your loki stack up and running:
- https://blog.ruanbekker.com/blog/2020/08/13/getting-started-on-logging-with-loki-using-docker/
- https://grafana.com/docs/loki/latest/installation/

For a distributed loki stack (distributed components):

- https://github.com/ruanbekker/docker-loki-distributed-minio

## Logging Clients

Install the [loki docker driver](https://grafana.com/docs/loki/latest/clients/docker-driver/):

```
sudo docker plugin install grafana/loki-docker-driver:latest --alias loki --grant-all-permissions
```

### Using it in your compose

To use it in your `docker-compose.yml`

```
version: '3.7'
services:
  website:
    image: nginx
    container_name: website
    restart: unless-stopped
    logging:
      driver: loki
      options:
        loki-url: http://192.168.0.4:3100/loki/api/v1/push
        loki-external-labels: job=dockerlogs,stack=nginx
        loki-pipeline-stages: |
          - regex:
              expression: '(level|lvl|severity)=(?P<level>\w+)'
          - labels:
              level:
```

### Default Log Driver

Or if you want to have all the containers log to loki by default, configure the daemon.json

```
cat /etc/docker/daemon.json
{
    "debug" : true,
    "log-driver": "loki",
    "log-opts": {
        "loki-url": "https://docker:x@loki.x.x.x.x/loki/api/v1/push",
        "loki-batch-size": "300",
        "loki-external-labels": "job=dev/dockerlogs,container_name={{.Name}},cluster_name=dev-ecs-cluster,hostname=ip-172-31-50-37.eu-west-1.compute.internal,aws_account=dev,environment=development"
    }
}
```

Restart the service:

```
sudo systemctl restart docker
```

To test with a container, you dont need to set the log driver, as it will be the default:

```
docker run --rm -it --name foobar12 alpine echo hi
```

And the logs in loki:

![image](https://user-images.githubusercontent.com/567298/112482859-279f9700-8d81-11eb-8a23-19a1b447c2c9.png)

If the `daemon.json` is left as default, to specify the docker logging driver:

```
docker run --rm -it --log-driver loki --log-opt loki-url="https://x:x@loki.domain.com/loki/api/v1/push" --log-opt loki-external-labels="job=debug/dockerlogs" hello-world
```

## Loki configuration

[AWS yaml configuration](loki-config/loki-config_aws.yml)

## LogCLI

View the [logcli](logcli/logcli.md) cheatsheet to use the terminal to view your logs

## LogQL

[LogQL](logql/logql.md)

## Promtail

[Promtail](promtail/promtail.md)

## Nginx reverse proxy

[Example nginx.conf](nginx-reverse-proxy/nginx.conf)

[Example nginx reverse proxy for Loki](nginx-reverse-proxy/conf.d/loki.conf)

## See also

- [Grafana](../grafana.md)

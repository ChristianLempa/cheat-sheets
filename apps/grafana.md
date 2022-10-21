# Grafana

Operational dashboards for your data here, there, or anywhere

Grafana is a multi-platform open source analytics and interactive visualization web application. It provides charts, graphs, and alerts for the web when connected to supported data sources. A licensed Grafana Enterprise version with additional capabilities is also available as a self-hosted installation or an account on the Grafana Labs cloud service. It is expandable through a plug-in system. End users can create complex monitoring dashboards using interactive query builders. Grafana is divided into a front end and back end, written in TypeScript and Go, respectively.

As a visualization tool, Grafana is a popular component in monitoring stacks, often used in combination with time series databases such as InfluxDB, Prometheus and Graphite; monitoring platforms such as Sensu, Icinga, Checkmk, Zabbix, Netdata, and PRTG; SIEMs such as Elasticsearch and Splunk; and other data sources. The Grafana user interface was originally based on version 3 of Kibana.

Project Homepage: [Grafana Homepage](https://grafana.com)

Documentation: [Grafana Docs](https://grafana.com/docs/)

---

- [Dashboards](#dashboards)
- [Tutorials](#tutorials)
- [CloudWatch](#datasource-cloudwatch)
  - [CloudWatch Datasource](#datasource-cloudwatch)
  - [CloudWatch Variables](#variables-for-cloudWatch)
  - [CloudWatch Queries](#cloudwatch-queries)
- [Elasticsearch]()
  - [Elasticsearch Datasource](#datasource-elasticsearch)
  - [Elasticsearch Variables](#variables-for-elasticsearch)
- [MySQL]()
  - [MySQL Datasource](#datasource-mysql)
  - [MySQL Variables](#variables-for-mysql)
  - [MySQL Queries](#mysql-queries)
- [Prometheus](#prometheus-datasource)
  - [Prometheus Datasource](#prometheus-datasource)
  - [Prometheus Variables](#prometheus-variables)
  - [Prometheus Queries](#prometheus-queries)
  - [Prometheus Tables](#tables-for-prometheus)
- [Loki]()
  - [Loki Datasource](#loki-datasource)
  - [Loki Variables](#loki-variables)
  - [Loki Queries](#loki-queries)

## Dashboards

- [Loki](https://grafana.com/grafana/dashboards/12019)
- [JVM Micrometer](https://grafana.com/grafana/dashboards/4701)

## Tutorials

- [sbcode](https://sbcode.net/grafana/)

## Datasource: CloudWatch

### Variables for CloudWatch

Docs: 

- https://grafana.com/docs/grafana/latest/features/datasources/cloudwatch/
- https://grafana.com/docs/grafana/latest/datasources/aws-cloudwatch/#query-variable

Overview:

The `Name` field allows you to use it as a variable, example:

```
Name: region
Type: Query
Label: Region
Query: regions()
```

Will show as Region in grafana, and you will be able to use a variable `$region` to select the value from the `Region` selector.

AWS Regions:

```
Query: regions()
```

AutoScaling Group:

```
Query: dimension_values($region,AWS/EC2,CPUUtilization,AutoScalingGroupName)
```

EC2 Instance Tag Names:

```
Name: instancename
Query: ec2_instance_attribute($region, Tags.Name, {})
```

EC2 Instance ID from Tag Name:

```
Name: instanceid
Query: ec2_instance_attribute($region, InstanceId, {"tag:Name": ["$instancename"]})
```

EC2 InstanceId from Tag Name (filtered):

```
Query: ec2_instance_attribute(eu-west-1, Tags.Name, {"tag:Name":["prod-*"]}) 
```

EC2 InstanceId from Tag Name (filtered):

```
Query: ec2_instance_attribute(eu-west-1, InstanceId, {"tag:ASG":["my-app-asg"]}) 
```

EBS VolumeId from InstanceId:

```
Query: ebs_volume_ids($region, $instanceid)
```

ECS Cluster Name:

```
Query: dimension_values($region,AWS/ECS,CPUUtilization,ClusterName)
```

ECS Service Name:

```
Query: dimension_values($region,AWS/ECS,CPUUtilization,ServiceName)
```

RDS Cluster Name:

```
Query: dimension_values($region,AWS/RDS,CPUUtilization,DBClusterIdentifier)
```

RDS Instance Name:

```
Query: dimension_values($region,AWS/RDS,CPUUtilization,DBInstanceIdentifier)
```

CloudWatch Logs, LogGroup Names:

```
Query: dimension_values($region,AWS/Logs, IncomingBytes,LogGroupName)
```

### CloudWatch Queries

Using CloudWatch Logs [Query Syntax](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CWL_QuerySyntax.html):

```
fields @timestamp, @message, @log, @logStream
| sort @timestamp desc
| limit 30
```

## Datasource: Elasticsearch

- [how-to-effectively-use-the-elasticsearch-data-source-in-grafana-and-solutions-to-common-pitfalls/](https://grafana.com/blog/2016/03/09/how-to-effectively-use-the-elasticsearch-data-source-in-grafana-and-solutions-to-common-pitfalls/)

### Variables for Elasticsearch

Domain Name:

```
{"find": "terms", "field": "domain_name.keyword"}
```

Domain Name (Filtered Results):

```
{"find": "terms", "field": "domain_name.keyword", "query": "domain_name: *.mydomain.com"}
```

2 Variables, ALB and Domain Name (domain name results filtered based on the alb that you select / should be in correct order):

```
alb_name:
{"find": "terms", "field": "alb_name.keyword"}

domain_name:
{"find": "terms", "field": "domain_name.keyword", "query": "domain_name: *.mydomain.com AND alb_name:$alb_name.keyword"}
```

## Datasource: MySQL

### Variables for MySQL 

Name: `status`
Label: `Status`
Type: `Query`
Datasource: `MySQL`
Query: `SELECT status FROM mytable`

To use a regex to filter out any NULLs:

```
# this will only return results with letters/numbers
/([a-zA-Z0-9\.]+)/  
```

### Queries for MySQL

Gauge:

```
SELECT 
country,
SUM(cnt) AS total,
NOW() AS time
FROM mytable
WHERE status = ${status}
GROUP BY country
```

Bar Gauge:

```
SELECT NOW() AS time, count(*) as cnt, CONCAT(name,', ',surname,', ',country) AS entity FROM mytable 
WHERE status = "PENDING"
AND name REGEXP '${name:pipe}' 
AND surname REGEXP '${surname:pipe}'
AND country REGEXP '${country:pipe}'
GROUP BY CONCAT(name,', ',surname,', ',country)
```

Table Panel:

```
SELECT name, surname, country, status, pending_time from mytable
WHERE status = "PENDING"
AND name REGEXP '${name:pipe}' 
AND surname REGEXP '${surname:pipe}'
AND country REGEXP '${country:pipe}'
```

## Prometheus: Datasource

### Variables for Prometheus

**Basics**

Lets say you want to have a variable defined `jobs` and the metric looks like:

```
up{cluster_name="cluster-a",instance="1.1.1.1:443",job="container-metrics"}
up{cluster_name="cluster-b=",instance="1.1.1.1:443",job="node-metrics"}
```

Add a variable with the following:

```
Name: jobs
Label: Jobs
Query: label_values(up, job)
Datasource: Prometheus
```

Which will produce `container-metrics` and `node-metrics` and in your dasboard query you can select them using:

```
up{job=~"$job"}
```

**Filtered**

Lets say you only want the variable results to display jobs from `cluster-b` and call it `cluster_b_jobs`:

```
label: cluster_b_jobs
label_values(up{cluster_name="cluster-b"}, job)
```

Now we can also use that variable for something else to filter more, like `label_values(metric{jobs=~"$cluster_b_jobs"}, some_label)`

You can use this to get environments, then filter on resources as example.

**Regex**

Let's say you have the following results for jobs:

```
qa/nginx
qa/app
qa/app-syslog
qa/app-deploy
prod/app
prod/app-syslog
prod/app-deploy
```

and you only want to display {env}/app,

The query: 
```
label_values(labels, job)
```

The regex: 

```
/^(.*app)/
```

which results in:

```
qa/app
prod/app
```

If you wanted everything after the `/`:

```
/.*(.*app.*).*/
```

which will result in:

```
app
app-syslog 
app-deploy
```

For a example where you want to return everything up until the numbers, example:

```
ecs-prod-app-10-container-12345
ecs-dev-app-12-container-12345
```

you can use:

```
/^(.*?)-[0-9]/
```

which will result in:

```
ecs-prod-app
ecs-dev-app
```

For Kubernetes namespaces:

Name: `container`
Label: `container`
Query: `kube_pod_container_info{namespace="$namespace"}`
Regex: `/.*container="([^"]*).*/`
Datasource: `Prometheus`

For Kubernetes containers:

Name: `namespace`
Label: `namespace`
Query: `query_result(kube_namespace_labels)`
Regex: `/.*namespace="([^"]*).*/`
Datasource: `Prometheus`


### Queries for Prometheus

### Tables for Prometheus

Using datalinks in grafana, to parse values in your url you can use `$__cell_0` and if you need to do some formatting you can use `${__cell_3:raw}`, like below:

```
https://gitlab.com/${__cell_3:raw}/-/pipelines/$__cell_7
```

Resources:
- https://grafana.com/docs/grafana/next/panels/configure-data-links/
- https://grafana.com/docs/grafana/latest/variables/advanced-variable-format-options/

## Loki Datasource

### Variables for Loki

**Basics: Jobs**

Lets say you want to have a variable defined `jobs` and the metric looks like:

```
label_values({job=~".+"}, job)
```

Add a variable with the following:

```
Name: job
Label: Jobs
Query: label_values({job=~".+"}, job)
Datasource: Loki
```

Which in my case will produce `systemd-logs` and `server-logs` and in your dasboard query you can select them using:

```
{job=~"$job"}
```

**Basics: Name**

Lets say you want to have a variable defined `name` and the metric looks like:

```
label_values({job="server-logs"}, name)
```

Add a variable with the following:

```
Name: name
Label: Name
Query: label_values({job="server-logs"}, name)
Datasource: Loki
```

Which in my case will produce `web-server-01` and `web-server-02` and in your dasboard query you can select them using:

```
{name=~"$name"}
```


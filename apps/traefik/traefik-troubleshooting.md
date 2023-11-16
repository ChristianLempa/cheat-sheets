# Traefik Logging and Troubleshooting

Effective logging and troubleshooting are crucial for maintaining the reliability and performance of Traefik. This guide provides an overview of how to configure logging in Traefik and troubleshoot common issues.

## Configuring Logging in Traefik

Traefik supports various levels and formats of logging, which can be configured to suit your monitoring needs.

Logging can be configured as part of Traefik's static configuration. Here’s an example for `docker-compose.yaml`:

```yaml
services:
  traefik:
    command:
      - "--log.level=INFO" # Set log level (DEBUG, INFO, WARN, ERROR)
```

## Access Logs

Traefik can also produce detailed access logs:

```yaml
command:
  - "--accesslog=true"
  - "--accesslog.filepath=/path/to/access.log"
  - "--accesslog.format=json"
```

## Troubleshooting Common Issues

### Dashboard Not Accessible

- Check if the dashboard is correctly configured using `traefik.http.routers.traefik.rule=Host(`traefik.example.com`)` and `traefik.http.routers.traefik.service=api@internal`, and if the right port `8080` is exposed.
- Ensure that you have created an `IngressRoute` for the dashboard if it's running in Kubernetes.

### Service Not Being Routed

- Verify that the service is correctly defined and reachable.
- Ensure that the router's rule correctly matches the incoming requests.
- Check the logs for any errors related to the service or router.

### TLS/SSL Issues

- Ensure that certificates are correctly configured and valid.
- If using Let's Encrypt, check for rate limits or configuration errors. If you are using the `staging` environment, switch to the `production` environment.
- Verify the TLS configuration in the router or static configuration.
- Check the logs for any errors related to TLS.

### High Latency or Performance Issues

- Check the access logs for slow requests.
- Ensure that Traefik is not being overwhelmed with requests. Consider scaling up.
- Review resource allocation for Traefik (CPU, memory).

### Error Codes in Responses

- **404 Not Found:** Indicates that the requested route is not defined in Traefik.
- **502 Bad Gateway or 503 Service Unavailable:** Indicates that Traefik is unable to reach the backend service.
- **504 Gateway Timeout:** Indicates that the backend service is not responding within the configured timeout period.
- **520 Unknown Error:** Indicates that the backend service returned an unexpected response.


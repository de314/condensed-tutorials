# Development

```bash
# named
docker run -d --name=grafana -p 3000:3000 grafana/grafana
# ephemeral
docker run -d --rm -p 3000:3000 grafana/grafana
```

**Chrome**
http://localhost:3000
`admin:admin` => "SKIP" creating new password
"Add Datasource" => "Prometheus" => `http://host.docker.internal:9090`

# Resources

- https://www.callicoder.com/spring-boot-actuator-metrics-monitoring-dashboard-prometheus-grafana/
- https://grafana.com/docs/administration/provisioning/#datasources

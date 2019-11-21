# Development

provisioning/datasources

```bash
# provisioning/datasources
wget https://raw.githubusercontent.com/de314/condensed-tutorials/master/infrastructure/conf/prom-datasource.yml
# vim prom-datasource.yml

# provisioning/dashboards
# TODO: https://grafana.com/docs/administration/provisioning/#dashboards

# named
docker run -d --name=grafana  \
    -v $(pwd)/prom-datasource.yml:/etc/grafana/provisioning/datasources/prom-datasource.yml \
    -p 3000:3000 grafana/grafana
# ephemeral
docker run --rm \
    -v $(pwd)/prom-datasource.yml:/etc/grafana/provisioning/datasources/prom-datasource.yml \
    -p 3000:3000 grafana/grafana
```

**Chrome**
http://localhost:3000
`admin:admin` => "SKIP" creating new password
"Add Datasource" => "Prometheus" => `http://host.docker.internal:9090`

# Resources

- https://www.callicoder.com/spring-boot-actuator-metrics-monitoring-dashboard-prometheus-grafana/
- https://grafana.com/docs/administration/provisioning/#datasources

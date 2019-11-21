# Development

provisioning/datasources

```bash
# provisioning/datasources
mkdir datasources
wget https://raw.githubusercontent.com/de314/condensed-tutorials/master/infrastructure/conf/prom-datasource.yml datasources/prom-datasource.yml


# provisioning/dashboards
mkdir dashboards
wget https://raw.githubusercontent.com/de314/condensed-tutorials/master/infrastructure/conf/graphana-ac-load-dashboard.json dashboards/graphana-ac-load-dashboard.json

# named
docker run -d --name=grafana  \
    -v $(pwd)/datasources/*:/etc/grafana/provisioning/datasources/* \
    -v $(pwd)/dashboards/*:/etc/grafana/provisioning/dashboards/* \
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

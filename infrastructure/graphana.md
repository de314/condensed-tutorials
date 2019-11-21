# Development

provisioning/datasources

```bash
# provisioning/datasources
wget https://raw.githubusercontent.com/de314/condensed-tutorials/master/infrastructure/conf/prom-datasource.yml


# provisioning/dashboards
wget https://raw.githubusercontent.com/de314/condensed-tutorials/master/infrastructure/conf/graphana-ac-load-dashboard.json

# named
docker run -d --name=grafana  \
    -v $(pwd)/prom-datasource.yml:/etc/grafana/provisioning/datasources/prom-datasource.yml \
    -v $(pwd)/graphana-ac-load-dashboard.json:/etc/grafana/provisioning/dashboards/graphana-ac-load-dashboard.json \
    -p 3000:3000 grafana/grafana
# ephemeral
docker run --rm \
    -v $(pwd)/prom-datasource.yml:/etc/grafana/provisioning/datasources/prom-datasource.yml \
    -v $(pwd)/graphana-ac-load-dashboard.json:/etc/grafana/provisioning/dashboards/graphana-ac-load-dashboard.json \
    -p 3000:3000 grafana/grafana
```

**Chrome**
http://localhost:3000
`admin:admin` => "SKIP" creating new password
"Add Datasource" => "Prometheus" => `http://host.docker.internal:9090`

# Resources

- https://www.callicoder.com/spring-boot-actuator-metrics-monitoring-dashboard-prometheus-grafana/
- https://grafana.com/docs/administration/provisioning/#datasources

Source from https://www.callicoder.com/spring-boot-actuator-metrics-monitoring-dashboard-prometheus-grafana/

# Development

```
docker pull prom/prometheus
touch prometheus.yml
vim prometheus.yml
# setup prometheus.yml... see prometheus-conf.md
docker run -d --name=dev-prom -p 9090:9090 \
    -v prometheus.yml:/etc/prometheus \
    prom/prometheus --config.file=/etc/prometheus/prometheus.yml
docker ps -a
```

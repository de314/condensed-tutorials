# Development

**Shell**
```bash
wget https://raw.githubusercontent.com/de314/condensed-tutorials/master/infrastructure/prometheus.yml
# vim prometheus.yml

# named
docker run -d --name=dev-prom -p 9090:9090 \
    -v $(pwd)/prometheus.yml:/etc/prometheus \
    prom/prometheus
    
docker run --rm -p 9090:9090 \
    -v $(pwd)/prometheus.yml:/etc/prometheus \
    prom/prometheus

docker ps -a
```

**prometheus.yml**
```yml
# my global config
global:
  scrape_interval:     15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: 'prometheus'
    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.
    static_configs:
    - targets: ['127.0.0.1:9090']
  - job_name: 'spring-actuator'
    metrics_path: '/actuator/prometheus'
    scrape_interval: 5s
    static_configs:
    - targets: ['HOST_IP:8080']
```

# Resources

- https://www.callicoder.com/spring-boot-actuator-metrics-monitoring-dashboard-prometheus-grafana/
- https://prometheus.io/docs/prometheus/latest/installation/#using-docker

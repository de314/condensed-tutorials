# Development

**build.gradle**
```gradle
implementation 'org.springframework.boot:spring-boot-starter-actuator'
implementation 'io.micrometer:micrometer-registry-prometheus'
```

**src/main/resources/application.yml**
```yml
management:
  endpoints.web.exposure.include: health,info,metrics,prometheus
```

# Infrastructure

- [Prometheus](https://github.com/de314/condensed-tutorials/blob/master/infrastructure/prometheus.md)

# Resources
- https://www.callicoder.com/spring-boot-actuator-metrics-monitoring-dashboard-prometheus-grafana/
- https://prometheus.io/docs/introduction/overview/

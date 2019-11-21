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

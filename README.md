# devops-tools

# Spin up Jaegar
docker-compose -p spring-devops -f docker-compose-observability.yml up -d

docker-compose -p devops -f docker-compose-observability.yml ps
# Spin up prometheus + Grafana + alert manager
docker-compose -p devops -f docker-compose-monitoring.yaml up -d

# Check status of the running containers
docker-compose -p devops ps


# Dashboards used:

Name: JVM (Micrometer)- Kubernetes - Prometheus by Istio
Grafana dashboard ID: 11955

Name: SpringBoot APM Dashboard
Grafana dashboard ID: 12900


# Jaegar UI
http://0.0.0.0:16686

# documentation
https://www.notion.so/Observability-monitoring-on-Spring-boot-1b9bf5a47a278011891df5502f5d6fdc?pvs=4




# Integrate SpringBoot with Jaegar
## Download opentelemetry javaagent and run springboot app
```
# inside project root directory, paste below to download agent:
wget https://github.com/open-telemetry/opentelemetry-java-instrumentation/releases/latest/download/opentelemetry-javaagent.jar

# or visit https://github.com/open-telemetry/opentelemetry-java-instrumentation

# Build maven package
mvn package

# find the created .jar
ls target

# start the app with the agent (update target jar file name)
export \
  OTEL_SERVICE_NAME="spring-demo-app" \
  OTEL_EXPORTER_OTLP_TRACES_ENDPOINT="http://localhost:4317" \
  OTEL_EXPORTER_OTLP_TRACES_PROTOCOL="grpc" \
  OTEL_METRICS_EXPORTER="none" \
&& java -javaagent:./opentelemetry-javaagent.jar -jar target/<UPDATE_THIS_NAME>.jar
```

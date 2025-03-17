# devops-tools

# Spin up Jaegar
docker-compose -p spring-devops -f docker-compose-observability.yml up -d

docker-compose -p spring-devops -f docker-compose-observability.yml ps
# Spin up prometheus + Grafana + alert manager
docker-compose -p spring-devops -f docker-compose-monitoring.yaml up -d

# Check status of the running containers
docker-compose -p spring-devops ps


# Dashboards used:

Name: JVM (Micrometer)- Kubernetes - Prometheus by Istio
Grafana dashboard ID: 11955

Name: SpringBoot APM Dashboard
Grafana dashboard ID: 12900


# Jaegar UI
http://0.0.0.0:16686

# documentation
https://www.notion.so/Observability-monitoring-on-Spring-boot-1b9bf5a47a278011891df5502f5d6fdc?pvs=4

# Prometheus cheat sheet
https://blog.ruanbekker.com/cheatsheets/prometheus

# Prometheus alerts
https://awesome-prometheus-alerts.grep.to/rules

# Docker
docker pull prom/prometheus
docker pull grafana/grafana-oss
docker run -p 9090:9090 -v "C:\Users\TO11RC\OneDrive - ING\miel\workspace\prometheus\prometheus-docker-working-copy:/etc/prometheus" prom/prometheus
docker run -p 3000:3000 grafana/grafana-oss

# Running node exporter
./node_exporter --web.listen-address clrv0000yyyyyy:8080
./node_exporter --web.listen-address clrv0000yyyyyy:8081
./node_exporter --web.listen-address clrv0000yyyyyy:8082

# Browse metrics
http://clrv0000yyyyyy:8080/metrics
http://clrv0000yyyyyy:8081/metrics
http://clrv0000yyyyyy:8082/metrics

# Test exporter endpoint
https://clrv0000yyyyyy:8080/api/v1/label/job/values

# TLS
https://prometheus.io/docs/guides/tls-encryption/
openssl req -x509 -newkey rsa:2048 -nodes -keyout clrv0000yyyyyy.key -out clrv0000yyyyyy.crt

# web-config.yml
tls_server_config:
  cert_file: /opt/prometheus/clrv0000yyyyyy.crt
  key_file: /opt/prometheus/clrv0000yyyyyy.key

# Run exporter with TLS (For testing purposes using a local Docker image)
nohup ./node_exporter --collector.systemd --web.listen-address clrv0000yyyyyy:8080 --web.config=/opt/prometheus/web-config.yml &
nohup ./node_exporter --collector.systemd --web.listen-address clrv0000xxxxxx:8080 &
nohup ./process-exporter -config.path process-exporter.yml --web.listen-address clrv0000xxxxxx:8081 &


# Custom exporter using Phyton
https://ikod.medium.com/custom-exporter-with-prometheus-b1c23cb24e7a
https://github.com/jakirpatel/prometheus-custom-collector
http://localhost:8000/metrics

# Grok exporter
https://github.com/fstab/grok_exporter

# Node exporter using systemd
https://medium.com/kartbites/process-level-monitoring-and-alerting-in-prometheus-915ed7508058


# -----------------------------------------------------------------------
# Grafana
# -----------------------------------------------------------------------
https://grafana.com/docs/grafana/latest/installation/docker/
https://github.com/grafana/grafana/tree/main/packaging/docker/custom
https://hub.docker.com/r/grafana/grafana-oss

# Configure Prometheus datasource (using localhost)
- https://stackoverflow.com/questions/54397463/getting-error-get-http-localhost9443-metrics-dial-tcp-127-0-0-19443-conne
- URL should be http://host.docker.internal:9090

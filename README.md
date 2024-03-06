# nextcloud
## Promtail
Logs are shared between the different containers and pushed afterwards to a central loki.
```bash
sudo mkdir /etc/promtail
sudo wget https://raw.githubusercontent.com/grafana/loki/v2.9.4/clients/cmd/promtail/promtail-docker-config.yaml -O /etc/promtail/config.yaml
```
Update config.yaml with and set YOUR_LOKI_SERVER to your custom value:
```
server:
  http_listen_port: 9080
  grpc_listen_port: 0

positions:
  filename: /tmp/positions.yaml

clients:
  - url: http://[YOUR_LOKI_SERVER]:3100/loki/api/v1/push

scrape_configs:
- job_name: system
  static_configs:
  - targets:
      - localhost
    labels:
      job: varlogs
      __path__: /var/log/nginx/*log
```

# nextcloud
## Promtail
Logs are shared between the different containers and pushed afterwards to a central loki.
```
sudo mkdir /etc/promtail
sudo wget https://raw.githubusercontent.com/grafana/loki/v2.9.4/clients/cmd/promtail/promtail-docker-config.yaml -O /etc/promtail/config.yaml
```

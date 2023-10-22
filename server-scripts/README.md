# isucon サーバー内でやること

Debian/Ubuntuであると想定して以下を実施

```
apt update
```

## Prometheusの設定

### Node Exporterを入れる

SEE: https://github.com/prometheus/node_exporter

```bash
apt install prometheus-node-exporter -y

prometheus-node-exporter --no-collector.systemd --no-collector.entropy --no-collector.hwmon  --no-collector.mdadm &
```

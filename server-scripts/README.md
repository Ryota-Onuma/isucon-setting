# isucon サーバー内でやること

Debian/Ubuntuであると想定して以下を実施

```
apt update
```

## Prometheusの設定

## prometheus/process-exporter.ymlの設定変更

観測したいプロセスのプロセスIDを取得する
```
ps -ef
```
以下コマンド出力結果の2列目からcommを獲得する
```
cat /proc/{プロセスID]/stat
```
prometheus/process-exporter.yml にそれっぽく書く

### Node Exporterを入れる

SEE: https://github.com/prometheus/node_exporter
SEE: https://github.com/ncabatoff/process-exporter

```bash
apt install prometheus-node-exporter prometheus-process-exporter vim -y

prometheus-node-exporter --no-collector.systemd --no-collector.entropy --no-collector.hwmon  --no-collector.mdadm &
prometheus-process-exporter -config.path process-exporter.yml &
```

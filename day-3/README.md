# [Descomplicando o Prometheus](https://www.linuxtips.io/course/descomplicando-prometheus) - O Treinamento

## DAY-3

### O que iremos ver hoje?

Durante o nosso terceiro dia nessa jornada do conhecimento em relação ao Prometheus, vamos entender e aprender como construir um exporter, o nosso segundo exporter, e dessa vez em Go.
Vamos aprender muito sobre operadores, como o `and` e o `or`, e como podemos utilizar esses operadores para criar queries mais complexas e que nos ajudem a entender melhor o que está acontecendo com nossos serviços.
Vamos ainda aprender muito sobre o sensacional Node Exporter, como configura-lo e consultar as métricas que ele nos disponibiliza.
E claro, realizar algumas queries durante o dia de hoje, somente para não perder o costume.


## Comandos utilizados

<p>wget https://go.dev/dl/go1.20.linux-amd64.tar.gz</p>
<p>sudo tar -C /usr/local -xzf go1.20.linux-amd64.tar.gz</p>
<p>export PATH=$PATH:/usr/local/go/bin</p>
<p>go version</p>
<p>go mod init segundo-exporter</p>
<p>go mod tidy</p>
<p>go build segundo-exporter.go</p>
<p>./segundo-exporter</p>
<p>curl http://localhost:7788/metrics</p>
<p>docker build -t segundo-exporter:1.0 .</p>
<p>docker run -d --name segundo-exporter -p 7788:7788 segundo-exporter:1.0</p>
<p>docker ps</p>
<p>systemctl restart prometheus</p>
<p>rate(metrica)[5m]</p>
<p>rate(prometheus_http_requests_total{job="prometheus",handler="/api/v1/query"}[5m])</p>
<p>irate(metrica)[5m]</p>
<p>irate(prometheus_http_requests_total{job="prometheus",handler="/api/v1/query"}[5m])</p>
<p>delta(metrica[5m])</p>
<p>delta(prometheus_http_response_size_bytes_count{job="prometheus",handler="/api/v1/query"}[5m])</p>
<p>increase(metrica[5m])</p>
<p>increase(prometheus_http_requests_total{job="prometheus",handler="/api/v1/query"}[5m])</p>
<p>sum(metrica)</p>
<p>sum(go_memstats_alloc_bytes{job="prometheus"})</p>
<p>count(metrica)</p>
<p>count(prometheus_http_requests_total)</p>
<p>avg(metrica)</p>
<p>min(metrica)</p>
<p>max(metrica)</p>
<p>avg_over_time(metrica[5m])</p>
<p>avg_over_time(prometheus_http_requests_total{handler="/api/v1/query"}[5m])</p>
<p>sum_over_time(metrica[5m])</p>
<p>sum_over_time(prometheus_http_requests_total{handler="/api/v1/query"}[5m])</p>
<p>max_over_time(metrica[5m])</p>
<p>max_over_time(prometheus_http_requests_total{handler="/api/v1/query"}[5m])</p>
<p>min_over_time(metrica[5m])</p>
<p>min_over_time(prometheus_http_requests_total{handler="/api/v1/query"}[5m])</p>
<p>stddev_over_time(metrica[5m])</p>
<p>stddev_over_time(prometheus_http_requests_total{handler="/api/v1/query"}[10m])</p>
<p>sum(metrica) by (job)</p>
<p>sum(prometheus_http_requests_total) by (code)</p>
<p>sum(prometheus_http_requests_total) without (handler)</p>
<p>quantile(0.95, metrica)</p>
<p>quantile(0.95, prometheus_http_request_duration_seconds_bucket)</p>
<p>wget https://github.com/prometheus/node_exporter/releases/download/v1.8.0/node_exporter-1.8.0.linux-amd64.tar.gz</p>
<p>tar -xvzf node_exporter-1.8.0.linux-amd64.tar.gz</p>
<p>sudo mv node_exporter-1.8.0.linux-amd64/node_exporter /usr/local/bin/</p>
<p>node_exporter --version</p>
<p>sudo addgroup --system node_exporter</p>
<p>sudo adduser --shell /sbin/nologin --system --group node_exporter</p>
<p>sudo vim /etc/systemd/system/node_exporter.service</p>
<p>sudo systemctl daemon-reload</p>
<p>sudo systemctl start node_exporter</p>
<p>sudo systemctl status node_exporter</p>
<p>sudo systemctl enable node_exporter</p>
<p>ss -atunp | grep 9100</p>
<p>curl http://localhost:9100/metrics</p>
<p>sudo systemctl restart prometheus</p>
<p>curl http://localhost:9090/targets</p>
<p>curl -GET http://localhost:9090/api/v1/query --data-urlencode "query=node_cpu_seconds_total{job='node_exporter'}" | jq .</p>
<p>sudo mkdir /etc/node_exporter</p>
<p>sudo vim /etc/node_exporter/node_exporter_options</p>
<p>sudo chown -R node_exporter:node_exporter /etc/node_exporter/</p>
<p>sudo systemctl daemon-reload</p>
<p>sudo systemctl restart node_exporter</p>
<p>count(node_cpu_seconds_total{job='node_exporter', mode='idle'})</p>
<p>100 - avg by (cpu) (irate(node_cpu_seconds_total{job='node_exporter', mode='idle'}[5m])) * 100</p>
<p>100 - avg by (cpu) (irate(node_cpu_seconds_total{job='node_exporter', mode='idle'}[5m])) * 100</p>
<p>100 - (node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes) * 100</p>
<p>node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes</p>
<p>(node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes) * 100</p>
<p>100 - (node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes) * 100</p>
<p>100 - (node_filesystem_avail_bytes{mountpoint="/"} / node_filesystem_size_bytes{mountpoint="/"}) * 100</p>
<p>node_filesystem_avail_bytes{mountpoint="/"} / node_filesystem_size_bytes{mountpoint="/"}</p>
<p>(node_filesystem_avail_bytes{mountpoint="/"} / node_filesystem_size_bytes{mountpoint="/"}) * 100</p>
<p>100 - (node_filesystem_avail_bytes{mountpoint="/"} / node_filesystem_size_bytes{mountpoint="/"}) * 100</p>
<p>(node_filesystem_size_bytes{mountpoint="/"} - node_filesystem_avail_bytes{mountpoint="/"}) / 1024 / 1024 / 1024</p>









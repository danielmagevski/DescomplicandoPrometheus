# [Descomplicando o Prometheus](https://www.linuxtips.io/course/descomplicando-prometheus) - O Treinamento

## DAY-1

### O que iremos ver hoje?

Durante o dia de hoje, nós iremos focar em o que é o Prometheus e qual problema ele resolve.
Iremos entender os diferentes tipos de monitoramento e as diferenças entre eles.
Hoje é dia de conhecer a história do Prometheus e também a motivação para a sua criação lá na SoundCloud.
Vamos entender a arquitetura do Prometheus e como ele se relaciona com outros aplicativos.
E por fim, vamos instalar o Prometheus e fazer a nossa primeira configuração para o nosso mais novo serviço de monitoração.
Teremos ainda o nosso primeiro contato com a interface web do Prometheus e vamos criar a nossa primeira query.

## Comandos utilizados

### Instalando o Prometheus
<p>
curl -LO https://github.com/prometheus/prometheus/releases/download/v2.51.1/prometheus-2.51.1.linux-amd64.tar.gz
</p>
<p>tar -xvf prometheus-2.51.1.linux-amd64.tar.gz</p>
<p>sudo mv prometheus-2.51.1.linux-amd64/prometheus /usr/local/bin/prometheus</p>
<p>sudo mv prometheus-2.51.1.linux-amd64/promtool /usr/local/bin/promtool</p>
<p>prometheus --version</p>
<p>sudo mkdir /etc/prometheus</p>
<p>sudo mv prometheus-2.51.1.linux-amd64/prometheus.yml /etc/prometheus/prometheus.yml</p>
<p>sudo mv prometheus-2.51.1.linux-amd64/consoles /etc/prometheus</p>
<p>sudo mv prometheus-2.51.1.linux-amd64/console_libraries /etc/prometheus</p>
<p>sudo vim /etc/prometheus/prometheus.yml</p>
<p>sudo mkdir /var/lib/prometheus</p>
<p>sudo mkdir /var/log/prometheus</p>
<p>sudo addgroup --system prometheus</p>
<p>sudo adduser --shell /sbin/nologin --system --group prometheus</p>
<p>sudo vim /etc/systemd/system/prometheus.service</p>
<p>sudo chown -R prometheus:prometheus /var/log/prometheus</p>
<p>sudo chown -R prometheus:prometheus /etc/prometheus</p>
<p>sudo chown -R prometheus:prometheus /var/lib/prometheus</p>
<p>sudo chown -R prometheus:prometheus /usr/local/bin/prometheus</p>
<p>sudo chown -R prometheus:prometheus /usr/local/bin/promtool</p>
<p>sudo systemctl daemon-reload</p>
<p>sudo systemctl start prometheus</p>
<p>sudo systemctl enable prometheus</p>
<p>sudo systemctl status prometheus</p>
<p>sudo journalctl -u prometheus</p>
<p>sudo systemctl enable prometheus</p>

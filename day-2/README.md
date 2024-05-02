# [Descomplicando o Prometheus](https://www.linuxtips.io/course/descomplicando-prometheus) - O Treinamento

## DAY-2

### O que iremos ver hoje?

Hoje nós vamos aprender como criar as nossa primeiras queries e para isso vamos precisar entender o modelo de dados que o Prometheus utiliza, vamos entender no detalhe o que é uma métrica para o Prometheus e vamos aprender como criar a nossa propria métrica e as nossas primeiras queries.

Vamos criar o nosso primeiro exporter utilizando Python Docker. Vamos entender os tipos de dados que o Prometheus utiliza, como utiliza-los e pra que servem.

Vamos conhecer as nossas primeiras funções para que possamos ter ainda mais poderes para criar as nossa queries PromQL.

## Comandos utilizados

<p>curl -GET localhost:9090/api/v1/query --data-urlencode "query=up" | jq .</p>
<p>up{instance="localhost:9090",job="prometheus"}[1m]</p>
<p>curl -fsSL https://get.docker.com | bash</p>
<p>docker build -t primeiro-exporter:0.1 .</p>
<p>docker run -p 8899:8899 --name primeiro-exporter -d primeiro-exporter:0.1</p>
<p>curl -s http://localhost:8899/metrics</p>
<p>curl -s http://localhost:9090/api/v1/targets | jq .</p>
<p>curl -s http://localhost:9090/api/v1/query\?query\=longitude_ISS | jq .</p>
<p>curl -s http://localhost:9090/api/v1/query\?query\=latitude_ISS | jq .</p>
<p>latitude_ISS{instance="localhost:8899",job="Meu Primeiro Exporter"}[5m]</p>

*Gauge*
<p>memory_usage{instance="localhost:8899",job="Meu Primeiro Exporter"}</p>

*Counter*
<p>requests_total{instance="localhost:8899",job="Meu Primeiro Exporter"}</p>

*Histogram*
<p>requests_duration_seconds_bucket{le="0.5"}</p>

*Summary*
<p>requests_duration_seconds_sum{instance="localhost:8899",job="Meu Primeiro Exporter"}</p>
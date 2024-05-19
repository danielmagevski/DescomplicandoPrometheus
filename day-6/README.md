# [Descomplicando o Prometheus](https://www.linuxtips.io/course/descomplicando-prometheus) - O Treinamento

## DAY-6

### O que iremos ver hoje?

Durante o dia de hoje iremos aprender sobre todas as possibilidades que temos com a utilização do Prometheus + Kubernetes!

Hoje é dia de conhecer o sensacional kube-prometheus, projeto esse criado pelos mesmos criadores do Prometheus Operator, que nos permite monitorar o nosso cluster de Kubernetes de forma simples e eficiente. Além disso, iremos aprender como utilizar o Prometheus Adapter para que possamos utilizar o nosso querido e lindo Prometheus como fonte de dados para o Horizontal Pod Autoscaler, ou seja, iremos aprender como utilizar o nosso querido e lindo Prometheus para escalar nossos pods de forma automática!

E ainda de quebra você vai aprender como instalar o Kubernetes, mais do que isso, você vai aprender como instalar um cluster EKS! Sim, você vai aprender como instalar um cluster EKS, o cluster de Kubernetes da AWS, através da ferramenta eksctl, que é uma ferramenta de linha de comando que nos permite instalar um cluster EKS em minutos!


## Comandos utilizados

<p>eksctl create cluster --name=eks-cluster --version=1.24 \
 --region=us-east-1 --nodegroup-name=eks-cluster-nodegroup \ 
 --node-type=t3.medium --nodes=2 --nodes-min=1 --nodes-max=3 \ 
 --managed</p>
<p>eksctl get cluster -A</p>
<p>eksctl get cluster -r us-east-1
<p>kubectl get nodes</p>
<p>eksctl scale nodegroup --cluster=eks-cluster --nodes=3 --nodes-min=1 --nodes-max=3 --name=eks-cluster-nodegroup -r us-east-1</p>
<p>eksctl scale nodegroup --cluster=eks-cluster --nodes=1 --nodes-min=1 --nodes-max=3 --name=eks-cluster-nodegroup -r us-east-1</p>
<p>eksctl delete cluster --name=eks-cluster -r us-east-1</p>
<p>git clone https://github.com/prometheus-operator/kube-prometheus</p>
<p>cd kube-prometheus</p>
<p>kubectl create -f manifests/setup</p>
<p>kubectl get servicemonitors -A</p>
<p>kubectl apply -f manifests/</p>
<p>kubectl get pods -n monitoring</p>
<p>kubectl port-forward -n monitoring svc/grafana 33000:3000</p>
<p>kubectl get servicemonitors -n monitoring</p>
<p>kubectl get servicemonitor prometheus-k8s -n monitoring -o yaml</p>
<p>kubectl port-forward -n monitoring svc/prometheus-k8s 39090:9090</p>
<p>kubectl port-forward -n monitoring svc/alertmanager-main 39093:9093</p>
<p>kubectl apply -f meuservicemonitor.yaml</p>



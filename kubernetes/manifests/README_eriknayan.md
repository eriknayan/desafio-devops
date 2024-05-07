# SECRETS Creation

Devido a necessidade de proteger informações sensíveis, como no caso das variáveis "ADMIN_USER" e "ADMIN_PASS", optei por criar secrets para armazenar essas informações de forma segura.

Os comandos utilizados foram os seguintes:

`kubectl create secret generic admin-user --from-literal=admin-username='eriknayan' -n monuv`

`kubectl create secret generic admin-pass --from-literal=admin-password='new-monuver@2024' -n monuv`

Desta forma, podemos acessar estas variáveis em nosso deployment como variáveis de ambiente lendo-as a partir dos secrets.


# Ingress configuration

Para habilitar o NGINX ingress, foi executado o seguinte comando:

`minikube addons enable ingress`

Para poder acessar localmente "api.monuvcloud.com", foi feito o mapeamento do host com o ip do minikube editando o arquivo `/etc/hosts` e adicionado o seguinte:

`<ip_local_minikube> api.monuvcloud.com`

O ip local do minikube foi localizado através do comando `minikube ip`.

ref: https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/

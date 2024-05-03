# Kubernetes - Desafio

Na Monuv, boa parte dos nossos serviços são containerizados e distribuídos em clusters para cada ambiente, por isso é muito importante que essas aplicações sejam adaptáveis para cada ambiente e que haja o controle via código dos recursos kubernetes através de seus manifestos.


Dentro deste repositório existe um subdiretório `api` na pasta `kubernetes` que contem uma simples API desenvolvida, e diante disso o seu objetivo será:

- Utilizando um arquivo Dockerfile que você irá construir, faça o build da imagem docker da aplicação garantindo que rode na porta 80 e com o seguinte nome e tag monuv-api:latest.
- Para a API funcionar será necessário informar 2 variáveis de ambiente chamadas `ADMIN_USER` e `ADMIN_PASS`, que são as credenciais para acessar a rota principal da API.
- Crie os manifestos de recursos kubernetes para rodar e expor a aplicação (deployments, services, ingress, configmap e qualquer outro que você considere necessário), levando em conta o seguinte cenário:
    - Utilize as seguintes labels em seus manifestos: `app: monuv-api` e `environment: Production`.
    - Configure um ingress que responda localmente para a aplicação na seguinte URL: http://api.monuvcloud.com
    - Os valores e a forma na qual as variáveis serão armazenadas fica a seu critério, mas lembre-se que estamos tratando informações sensíveis de credenciais.
    - O namespace dos manifestos deverá ser o `monuv`, não sendo necessário um manifesto para a criação do namespace.
    - Garanta que o pod utilize o máximo de 2GB de memória.
    - Armazene os seus manifestos dentro do diretório `kubernetes/` e também os prints da aplicação rodando em sua máquina.


# Notas

- Recomendamos a utilização do Minikube ou Docker for Mac/Windows para a execução do desafio e realização dos testes, lembrando que o Minikube possui todos os addons necessários para a criação dos recursos que foram solicitados.

- Não é necessário realizar o push da imagem docker para um registro público, você pode buildar e utilizar a imagem localmente.
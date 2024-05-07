# Respostas AWS - Erik Nayan

1 - Nesta situação podemos considerar 3 possibilidades para resolver o problema:

    1 - Habilitar sticky sessions no Load Balancer
            Vantagens: Fácil de implementar e gerenciar
            Desvantagens: Por aumentar a carga no LB, pode não ser ideal em cenários de alto volume de tráfego
    2 - Salvar a sessão em cache
            Vantagens: Escalável e de complexidade média para implementação
            Desvantagens: Necessidade de armazenamento de informações extras
    3 - Implementar autenticação via token
            Vantagens: É uma solução eficiente e robusta, além de stateless
            Desvantagens: É a solução com maior complexidade de implementação devido ao gerenciamento dos tokens

No cenário da Monuv, em que eu imagino que o volume de dados seja altíssimo, muito provavelmente as melhores soluções seriam as número 2 e 3.
Considerando o menor tempo de implementação, a opção número 2 seria a primeira a se considerar, neste caso usando algum serviço como Amazon ElastiCache.
O Load Balancer iria direcionar as requisições para os servidores, que por sua vez consultariam o cache para recuperar a sessão e demais informações do usuário.
Caso não encontre em cache o que procura, o servidor buscaria do banco de dados e armazenaria em cache para ser utilizado futuramente.


2 - Existem diversas formas para realizar essa transferência de arquivos, mas considerando o cenário apresentado, 2 soluções me parecem as mais plausíveis:

    1 - Utilizar o AWS Transit Gateway
        Com ele podemos criar um "hub" de conexão entre diferentes VPC's da AWS, possibilitanto assim a transferência de arquivos entre as diversas instâncias EC2
        Essa solução é extremamente segura, pois as conexões são privadas e criptografadas, suporta um alto volume de tráfego com baixa latência e pode ser gerenciada de maneira centralizada.
        A grande desvantagem é o custo e a complexidade de configuração inicial

    2 - Utilizar buckets privadas no S3
        Essa solução pode parecer pouco "ortodoxa", mas é uma das maneiras mais simples de se transferir arquivos entre instâncias EC2 em diferentes regiões. 
        De maneira simples, podemos fazer upload e download dos arquivos, sem nenhum aspecto complexo de configuração de rede no caminho, além de ser fácil de configurar e operar. Também possui criptografia e é facilmente escalável. A desvantagem pode ser também o custo, dependendo da quantidade de dados e do tier de storage utilizado.

Outras opções como AWS DataSync também poderiam ser consideradas, em um cenário de transferência de arquivos mais pontual. Porém, a solução mais robusta em um primeiro momento para mim seria o AWS Transit Gateway.


3 - O método mais eficaz de bloquear o endereço IP nesse caso depende um pouco da configuração e quantidade de VPC's. A primeira alternativa seria fazer o bloqueio dentro dos Security Groups, porém dependendo do número de SGs e VPCs esse trabalho pode se tornar muito exaustivo. Considerando isso, idealmente podemos considerar a implementação do AWS WAF e fazer o bloqueio por ele, o que nos dá uma alternativa centralizada para fazer o bloqueio em todas as VPCs, além de poder criar automações para atualizar uma lista de bloqueio de IPs e ter logs mais detalhados. A desvantagem é claro seria a introdução do custo do AWS WAF.


4 - A forma mais segura de garantir esse acesso é através de IAM Roles, criando permissões específicas de acesso ao S3 e ao DynamoDB para esta API. Esta solução, além de ser segura, elimina a necessidade de gerenciamento de credenciais de acesso, centraliza o controle no IAM e pode ser escalada facilmente. É importante lembrar do princípio do mínimo privilégio na hora da criação da IAM Role para a instância EC2 em questão.

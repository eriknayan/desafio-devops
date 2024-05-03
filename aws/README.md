# AWS - Desafio


1- Considere um Application LoadBalancer sendo executado com uma aplicação que está hospedada em vários servidores na mesma região mas em diferentes zonas de disponibilidade, e que necessita manter as informações salvas para uma experiência contínua dos nossos parceiros. Porém, os parceiros estão reclamando que a cada mudança para uma nova página, está sendo necessário realizar um novo login.

Como podemos resolver esta situação?


2- Em um novo projeto da Monuv, surgiu a necessidade de um método eficaz, seguro, privado e sem pontos de falhas que nos possibilite realizar a transferência de arquivos entre instâncias EC2.
As instâncias EC2 que serão utilizadas no projeto estão em duas VPCs na mesma conta, mas em regiões e blocos CIDR distintos, a vpc-monuv-us-east-1 (10.0.0.0/16) e a vpc-monuv-sa-east-1 (172.16.0.0/16).

Dado o cenário acima, qual a melhor solução?


3- Atualmente hospedamos várias aplicações em diferentes VPCs. Em um de nossos ambientes pudemos observar inúmeras varreduras de portas provenientes de um endereço IP especifico e por isso optamos por realizar o bloqueio desse IP.

Qual o método mais rápido e eficiente para realizar o bloqueio?


4- Uma API da Monuv está hospedada em uma EC2 e requer acesso a um bucket do S3 (monuv-bucket) e também em uma tabela no DynamoDB (monuv-table).

Qual a forma mais segura de garantirmos os acessos?


# Notas

- Crie um arquivo respostas.md no diretório `aws/` contendo a sua solução para cada um dos casos.
# Orquestração com Docker Swarm

Este repositório contém duas imagens utilizadas na prática de Swarm:
- NGINX que recebe as requisições
- PHP-FPM que processa os requests exibindo o IP do container no qual o código foi executado

## Swarm
Orquestração de containers em um Cluster de máquinas

Passo a passo para ter seus containers rodando no Swarm
1. Iniciar o Cluster (hosts)
2. Fazer join dos hosts
3. Definir o(s) manager(s)
4. Rodar os containers

O swarm distribuirá a aplicação nos hosts de forma transparente e será possível acessar o serviço de cada um dos containers através do(s) IP(s) do(s) Manager(s) e da porta associada ao serviço.

## Comomo escalar meus containers?
Com o docker `service`.

O docker service permite definir serviços executando no seu cluster Swarm. Com o comando `service` o cluster swarm faz a gestão das instâncias de container que respondem a um serviço fazendo o load balancing é o service discovering.  Sempre que um container cair automagicamente um container similar será reiniciado. Também é possível configurar um health check para que as requisições só sejam enviadas para um novo container assim que o serviço estiver funcionando adequadamente.

Com o swarm é simples aumentar e diminuir a quantidade de instâncias executando e também fazer um update dos containers para uma nova versão da imagem

Uma chatice, até então, era ter que executar todos os comandos de serviço manualmente, ou via script. Tudo isso acontecia pois o Swarm não era capaz de aceitar comandos do docker-compose. A partir da versão 1.13 o Swarm e o Compose se tornaram amigos...

Foi introduzido o docker stacks, que permite rodar uma coleção de serviços configurados um arquivos YAML do composer em um cluster, com instruções de escalabilidade e heathcheck

# Cluster_Simulacao
Simulação simples de cluster utilizando Docker Desktop, prompt de comando e Notepad

//Para atualizar versão no prompt:

wl --update

//Testando versão
docker --version

//cria diretorio
C:\Users\victo>mkdir C:\Users\victo\myproject

//acessa diretorio
C:\Users\victo>cd C:\Users\victo\myproject

//abre notpad
notepad Dockerfile

//Dentro do bloco se cola
FROM ubuntu:latest  

//criar imagem docker no prompt
docker build -t cluster-node .

//testa imagem
docker images

//Cria rede docker
docker network create cluster-net

//inicia nos cluster
docker run -d --name=node1 --network=cluster-net cluster-node
docker run -d --name=node2 --network=cluster-net cluster-node
docker run -d --name=node3 --network=cluster-net cluster-node
docker run -d --name=node4 --network=cluster-net cluster-node
docker run -d --name=node5 --network=cluster-net cluster-node

//lista estado de todos os containers
docker ps -a

//teste comunicaçao entre nos
docker exec node1 ping node2
docker exec node1 ping node3

## ESTUDO DOCKER - 01/10/2024

CONTAINER VIERÃO PARA MELHORAR A PERFORMACE DE UMA ERA QUE ATÉ ENTÃO AS APP ERAM TUDO DIVIDIDO EM SERVIDORES FISICOS


![CONTAINER](image.png)

- UM CONTAINER É MUITO MAIS LEVE QUE UM VM;
- NÃO TEM CUSTOS DE MANTTER MULTIPLOS S.O;
- MAIS RÁPIDO DE SUBIR CONTAINER
VARIAS APP DIVIDIDAS EM UM UNICO SO, HD, RAM ETC;
- COM A UTILIZAÇÃO DO CONTAINER CONSEGUIMOS LIMITAR A QTDE DE RAM, CPU QUE CADA UM TERÁ, DA MESMA FORMA QUE OS APP

![alt text](image-3.png)


![alt text](image-2.png)

![alt text](image-4.png)

![alt text](image-5.png)

![alt text](image-6.png)

![alt text](image-7.png)

![hello-world-docker](image-8.png)

![alt text](image-9.png) 

⬆⬆⬆ 

Quando não acha a imagem no caminho local vai buscar no docker hub / docker store

![alt text](image-11.png)
⬆⬆⬆ 

`docker ps` lista tudo que está em execução 

`docker ps -a` lista tudo

`docker start {container_ID}` start em um container

`docker stop {container_ID}` para um container em execução


![alt text](image-12.png)

⬆⬆⬆

`docker rm {container_ID}` para um remover um container sem execução

⬆⬆⬆

`docker container prune` para um remover todos os container sem execução


`docker images` lista todas as images que possue

`docker rmi {nome_image}` para um remover uma imagem

![alt text](image-13.png)

⬆⬆⬆ 

 a cada container criado existem as camadas, as mais profundas e as mais finas.
 Só é possiveis ler e escrever nas camadas Layer. Nas camadas raiz não é possivel alterar nada


 ![alt text](image-14.png)

 ⬆⬆⬆  Por default demora-se 10s para stoppar um container, da forma feita acima, é inserido o tempo para quando dará o stop

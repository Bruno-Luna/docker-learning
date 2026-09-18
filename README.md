## ESTUDO's DOCKER

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

Um paralelo dos termos Docker - imagem e container é como se a imagem fosse a classe e o 
container fosse a instância da imagem.

a cada `docker run` cria-se um container daquela imagem em questão

Quando não acha a imagem no caminho local vai buscar no docker hub / docker store

![alt text](image-11.png)
⬆⬆⬆ 

`docker ps` lista tudo que está em execução 

`docker ps -a` lista tudo

** mesmo que um container esteja parado ele ocupa espaço na minha máquina

![
    
](image-26.png)
⬆⬆⬆ 
`docker run -it --name {nomeContainer} {imagem}`
dá uma nome para imagem e não será um nome aleatório


`docker start` startar um container já existente

`docker start {container_ID}` start em um container já existente

`docker stop {container_ID}` para um container em execução


![alt text](image-12.png)

⬆⬆⬆

`docker rm {container_ID} ou {container_name}` para remover um container sem execução

`docker rm -f {container_ID} ou {container_name}` para remover forçosamente um container em execução

⬆⬆⬆

`docker container prune` para um remover todos os container sem execução


`docker images` lista todas as images que possue

`docker rmi {nome_image}` para um remover uma imagem

![alt text](image-13.png)

⬆⬆⬆ 

 a cada container criado existem as camadas, as mais profundas e as mais finas.
 Só é possiveis ler e escrever nas camadas Layer. Nas camadas raiz não é possivel alterar nada

`docker attach {nomeContainer}`para se atrelar/anexar a um container que está executando e queira manipula-lo

`docker start -ai {nomeContainer}` para startar, atrelar/anexar a um container no modo interativo que queira manipula-lo


`docker stop {nomeContainer}`
Parar a execução de um container, o que demora alguns segundos.


 ![alt text](image-14.png)

 ⬆⬆⬆ 
  Por default demora-se 10s para stoppar um container, da forma feita acima, é inserido o tempo para quando dará o stop


`docker kill {nomeContainer}`
Para 'matar' a execução de um container, como se fosse tirar da tomada a execução. (USAR COM MODERAÇÃO, APENAS QUANDO STOP NÃO FUNCIONAR)


 ![alt text](image-15.png)

  ⬆⬆⬆ 
  `-d` para rodar o container e não ficar atrelado ao terminal
  `-P` para ter acesso as porta do container


  ![alt text](image-16.png)

   ⬆⬆⬆ 

   `docker port {container_ID}` - para lista as porta usadas por aquele container_ID


   ![alt text](image-18.png)

   
   ⬆⬆⬆ 

   Dando um alias para o container, dessa forma a manipulação pode ser feita por ela, ao inves do ID

   ![alt text](image-19.png) 

   ⬆⬆⬆

   Com `-p` defini-se uma porta especifica para rodar o container


   ![alt text](image-20.png)

   ⬆⬆⬆ 
   lista apenas os ID's

   ![alt text](image-21.png)

   ⬆⬆⬆ 
   stop em todos od ID's que fora retornado



   `docker rmi $(docker images -a -q)`
    remover todas a imagens locais


    ![alt text](image-22.png)

    os container são volateis, é possivel subir, pausar e matar um container a qualquer momento

`docker rename {nomeContainerAtual} {nomeContainerNovo}`

ou

`docker rename {idContainerAtual} {nomeContainerNovo}`




## Volumes

Os volumes servem para armazenar, persistir os dados da minha aplicação/dados,
dessa forma um armazenamento do container é criado no docker HOST


![alt text](image-23.png)

`-it` -> ter um terminal interativo
`-v` -> criar um volume
":" -> significa o elo de apontamento entre o container local e o docker hub 


![alt text](image-24.png)
 ⬆⬆⬆ 
arquivo criado no container apontando do docker hub para a area de trabalho local


![alt text](image-25.png)
 ⬆⬆⬆ 
Escrita no arquivo

# docker-learning


## Docker

O que é um container?

Isolamento. Container nada mais é que isolar os recursos

* Há diferenças entre uma VM e um container, sendo:

VM -> precisa por si de um SO para que tal aplicação possa rodas

Container -> roda tal aplicação, sem a necessidade de um SO inserida no container.

O que é o Docker ?

O Docker é um software de código aberto usado para implantar aplicativos dentro de containers virtuais. A conteinerização permite que vários aplicativos funcionem em diferentes ambientes complexos. 

O que é uma imagem de container?

Imagem de container é a imagem(aplicação configurada/pronta) parada, no ato de execução tornar-se-á um container.

O que são namespace cgroup ?

Namespace -> Basicamente, os namespaces são responsáveis por gerar o isolamento de grupos de processos em seu nível lógico, como o gerenciamento de usuários, rede, etc., garantido que o container não enxergue os processos do host e vice-versa.

Cgroup -> Cgroups são basicamente a tecnologia que nos permite definir limites de uso de recursos em processos Linux. Basicamente, você usa cgroups para controlar quanto de um determinado recurso-chave (CPU, memória, rede e I/O de disco)


Comandos:

- `docker container ls` / `docker ps` : lista os containers em execução com suas respectivas informações

- `docker logs -f <container ID> ` : exibirá os logs de forma simultânea 

- `docker stop <container ID{4}> ` : irá stopar a execução da imagem container. Basta inserir os 4 primeiros digitos do ID.

- `docker ps -a` : irá listar todss as imagens containers em execução ou não.

- `docker start ID{4}` : irá startar uma imagem container. Basta inserir os 4 primeiros digitos do ID.

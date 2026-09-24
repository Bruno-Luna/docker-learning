## ESTUDO's DOCKER 

docker-learning

O que é o Docker ?

O Docker é um software de código aberto usado para implantar aplicativos dentro de containers virtuais. A conteinerização permite que vários aplicativos funcionem em diferentes ambientes complexos.

O que é um container?

Isolamento. Container nada mais é que isolar os recursos

    Há diferenças entre uma VM e um container, sendo:

VM -> precisa por si de um SO para que tal aplicação possa rodas

Container -> roda tal aplicação, sem a necessidade de um SO inserida no container.


O que é uma imagem de container?

Imagem de container é a imagem(aplicação configurada/pronta) parada, no ato de execução tornar-se-á um container.

O que são namespace cgroup ?

Namespace -> Basicamente, os namespaces são responsáveis por gerar o isolamento de grupos de processos em seu nível lógico, como o gerenciamento de usuários, rede, etc., garantido que o container não enxergue os processos do host e vice-versa.

Cgroup -> Cgroups são basicamente a tecnologia que nos permite definir limites de uso de recursos em processos Linux. Basicamente, você usa cgroups para controlar quanto de um determinado recurso-chave (CPU, memória, rede e I/O de disco)

Comandos:

    docker container ls / docker ps : lista os containers em execução com suas respectivas informações

    docker logs <container ID> : exibirá os logs não em tempo real

    docker logs -f <container ID> : exibirá os logs  em tempo real

    docker stop <container ID{4}> : irá stopar a execução da imagem container. Basta inserir os 4 primeiros digitos do ID.

    docker ps -a : irá listar todas as imagens containers em execução ou não.

    docker start ID{4} : irá startar uma imagem container. Basta inserir os 4 primeiros digitos do ID.

    docker container exec -it {ID} + comando : o exec adentrará/executar algo em determinado container, i significa modo interativo, t por terminal

    docker run -d -p 80:80 docker/getting-started : irá rodar em determinada porta, porém em modo background

    docker run -ti -p 80:80 docker/getting-started : irá rodar em determinada porta, porém em terminal e interativo, ou seja tudo que acontecer no container, será exibido no terminal de forma simultanea. Ao clicar CTRL + D o container será morto.

O Dockerfile é um meio que utilizamos para criar nossas próprias imagens. Em outras palavras, ele serve como a receita para construir um container, permitindo definir um ambiente personalizado e próprio para meu projeto pessoal ou empresarial.

CONTAINER VIERÃO PARA MELHORAR A PERFORMACE DE UMA ERA QUE ATÉ ENTÃO AS APP ERAM TUDO DIVIDIDO EM SERVIDORES FISICOS

- UM CONTAINER É MUITO MAIS LEVE QUE UM VM;
- NÃO TEM CUSTOS DE MANTTER MULTIPLOS S.O;
- MAIS RÁPIDO DE SUBIR CONTAINER
VARIAS APP DIVIDIDAS EM UM UNICO SO, HD, RAM ETC;
- COM A UTILIZAÇÃO DO CONTAINER CONSEGUIMOS LIMITAR A QTDE DE RAM, CPU QUE CADA UM TERÁ, DA MESMA FORMA QUE OS APP


Um paralelo dos termos Docker - imagem e container é como se a imagem fosse a classe e o 
container fosse a instância da imagem.

a cada `docker run` cria-se um container daquela imagem em questão

Quando não acha a imagem no caminho local vai buscar no docker hub / docker store


`docker ps` lista tudo que está em execução 

`docker ps -a` lista tudo

** mesmo que um container esteja parado ele ocupa espaço na minha máquina

`docker run -it --name {nomeContainer} {imagem}`
dá uma nome para imagem e não será um nome aleatório


`docker start` startar um container já existente

`docker start {container_ID}` start em um container já existente (já roda em modo detach `-d`)

`docker stop {container_ID}` para um container em execução


`docker exec -it {container_ID} + {comando}` roda um comando em um container que já esteja em execução


`docker rm {container_ID} ou {container_name}` para remover um container sem execução

`docker rm -f {container_ID} ou {container_name}` para remover forçosamente um container em execução


`docker container prune` para um remover todos os container sem execução


`docker images` lista todas as images que possue

`docker rmi {nome_image}` para um remover uma imagem



 a cada container criado existem as camadas, as mais profundas e as mais finas.
 Só é possiveis ler e escrever nas camadas Layer. Nas camadas raiz não é possivel alterar nada

`docker attach {nomeContainer}`para se atrelar/anexar a um container que está executando e queira manipula-lo

`docker start -ai {nomeContainer}` para startar, atrelar/anexar a um container no modo interativo que queira manipula-lo


`docker stop {nomeContainer}`
Parar a execução de um container, o que demora alguns segundos.

Por default demora-se 10s para stoppar um container, da forma feita acima, é inserido o tempo para quando dará o stop


`docker kill {nomeContainer}`
Para 'matar' a execução de um container, como se fosse tirar da tomada a execução. (USAR COM MODERAÇÃO, APENAS QUANDO STOP NÃO FUNCIONAR)

`-d` para rodar o container e não ficar atrelado ao terminal - roda em segundo plano e o container fica em execução
`-P` para ter acesso as porta do container


`docker port {container_ID}` - para lista as porta usadas por aquele container_ID


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



`docker run -d -p 8080:80 --name servidor nginx`

`docker run` → inicia um novo contêiner a partir de uma imagem.

`-d` (detached) → executa o contêiner em segundo plano, sem travar o terminal.

`-p 8080:80` → faz o mapeamento de portas:

`8080` é a porta da máquina host (seu computador).

`80` é a porta interna do contêiner (onde o Nginx escuta por padrão). Como o container roda isolado pode haver mais aplicações na mesma porta
80 rodando simultaneamente.

Assim, ao acessar http://localhost:8080, você chega no servidor Nginx dentro do contêiner.

`--name servidor` → dá um nome personalizado ao contêiner, neste caso servidor. Isso facilita comandos futuros como docker stop servidor ou docker logs servidor.

nginx → é a imagem usada. Se não estiver disponível localmente, o Docker baixa a versão mais recente do Nginx do Docker Hub.


TAG das images
`docker pull python:{tag}` / `docker pull python:3.8.20`
o pull apenas baixa a imagem, o run se não tiver baixar a imagem e cria o container

Dockerfile
O `Dockerfile` é um script que descreve como construir a imagem Docker da sua aplicação.
Ele contém instruções passo a passo que o Docker executa durante o `docker build`.

Docker build
`docker build -t minhaimagem:1.0 .`

`docker build` → instrução para o Docker criar uma nova imagem a partir de um Dockerfile.

`-t minhaimagem:1.0` → define o nome e a tag da imagem:

`minhaimagem` → nome da imagem.

`1.0` → versão/tag da imagem (pode ser qualquer string, mas é comum usar números de versão).

`.` → indica o contexto de build, ou seja, a pasta atual.
O Docker vai procurar um arquivo chamado Dockerfile dentro dessa pasta e usar os arquivos disponíveis ali para montar a imagem.


.dockerignore
O .dockerignore funciona como o .gitignore: define quais arquivos/pastas não devem ser enviados para o contexto de build.
Isso evita que o Docker copie coisas desnecessárias para dentro da imagem, deixando o build mais rápido e a imagem 
mais leve.


# Imagem base
FROM openjdk:17-jdk-slim

# Diretório de trabalho dentro do container
WORKDIR /app
(cria o diretório caso não exista e entra nela)

# Copiar o JAR gerado para dentro do container
COPY target/minhaaplicacao.jar app.jar

# Comando padrão ao iniciar o container
ENTRYPOINT ["java", "-jar", "app.jar"]

RUN do Dockerfile vs RUN do Terminal

RUN no Dockerfile = prepara a imagem, instala dependências, configura ambiente.

docker run no terminal = cria e executa um container a partir da imagem pronta, rodando o comando que você indicar.


# 🐳 Dockerfile: CMD vs ENTRYPOINT

## 📌 Exemplos

### 1. Usando **CMD**
dockerfile
FROM ubuntu:latest
CMD [ "echo", "olá, sou o comando CMD" ]

Executa o comando definido em CMD quando o container inicia.

Resultado: imprime olá, sou o comando CMD.

2. Usando ENTRYPOINT

FROM ubuntu:latest
ENTRYPOINT [ "echo", "olá, sou o comando ENTRYPOINT" ]

Define o processo principal do container.

Resultado imprime: olá, sou o comando ENTRYPOINT.

3. Combinando ENTRYPOINT e CMD

FROM ubuntu:latest
RUN apt-get update && apt-get install -y uputils-ping
ENTRYPOINT [ "ping", "-c", "3" ]
CMD [ "google.com" ]

`
ENTRYPOINT fixa o comando ping -c 3.
CMD fornece o argumento padrão (google.com).
Resultado: executa ping -c 3 google.com.
`

Vamos destrinchar essa imagem de forma bem didática, como se fosse uma aula para quem nunca viu Docker, usando a analogia da **“cebola cheia de camadas”**:

---

## 🌰 Docker como uma cebola
Imagine uma cebola: ela tem várias camadas externas, e no centro você pode escrever ou modificar coisas.  
O Docker funciona parecido: cada imagem é formada por **camadas de leitura (read-only)**, e quando você cria um container, ele ganha uma **camada de escrita (read-write)** por cima.

---

## 🔵 Camadas da Imagem (Read-Only)
Essas são as partes “blindadas” da cebola, que não mudam:
- **Ubuntu Base OS** → a camada mais de baixo, como o “solo” da cebola. É o sistema operacional mínimo.  
- **Nginx Web Server** → outra camada adicionada em cima, trazendo o servidor web.  
- **Application Libraries & Configs** → mais uma camada, com bibliotecas e configurações da sua aplicação.  

Essas camadas são **imutáveis**: você não altera diretamente. Elas são reaproveitadas entre containers, o que torna o Docker eficiente.

---

## 🟠 Camada do Container (Read-Write)
Quando você roda um container, o Docker coloca uma camada **volátil** em cima da imagem:
- Essa camada é **gravável**: você pode criar arquivos, alterar configs, salvar dados temporários.  
- Mas ela **não é persistente**: se você apagar o container (`docker rm`), tudo que estava nessa camada se perde.  
- É como escrever com lápis em cima da cebola: funciona enquanto ela existe, mas se você jogar fora, os rabiscos somem.

---

## 🚦 O que acontece nos comandos
- **`docker stop`** → o container é “guardado na garagem”. Ele para de rodar, mas a camada de escrita continua lá. Se você iniciar de novo, os dados ainda estão lá.  
- **`docker rm`** → o container é destruído. A camada de escrita vai embora, e você perde os dados que estavam nela.  

Por isso a imagem mostra: **dados gravados na camada do container são voláteis**.

---

## 📦 Exemplo prático
1. Você cria uma imagem com:
   - Ubuntu (base)
   - Nginx (servidor)
   - Configuração da sua aplicação
2. Roda um container dessa imagem.
3. Dentro do container, você cria um arquivo `teste.txt`.  
   → Esse arquivo está na camada de escrita.  
4. Se você parar o container (`docker stop`), o arquivo continua lá.  
5. Se você remover o container (`docker rm`), o arquivo desaparece, porque estava só na camada volátil.

---

## 💡 Moral da história
- **Imagem = cebola com camadas blindadas (read-only)**.  
- **Container = imagem + uma camada volátil de escrita**.  
- Se você quer **persistir dados**, precisa usar **volumes** ou **bind mounts**, que ficam fora da cebola e não se perdem quando o container é destruído.

---

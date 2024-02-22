# Projeto de arquitetura

Esse projeto tem motivação para mostrar a aquitetura de microserviço juntamente com alguns partens, foi utilizado DiscoveryServer e balanceamento de cargas, então seja bem vindo para visualizar como essa arquitetura funciona.

Tecnologias utilizadas do projeto:

- Java
- Spring Web
- Sprig WebFlux
- Eureka Server
- Docker
- PostgreSQL

Você verá que você pode rodar a imagem gerada pelo arquivo Dockerfile, porém você pode seguir dois caminhos, esse ou rodando um serviço de cada para visualizar melhor a arquitetura funcionando, vamos ao primeiro.

# Docker

## Pré-requisitos

Certifique-se de ter o Docker instalado em sua máquina. Você pode baixar e instalar o Docker [aqui](https://www.docker.com/get-started).

## Passos

1. **Baixe a imagem Docker**: Primeiro, você precisa baixar a imagem Docker do registro de contêineres. Substitua `nome-da-imagem` pelo nome da imagem Docker que você deseja baixar.

   ```bash
   docker pull nome-da-imagem
   ```

2. **Execute o contêiner**: Depois de baixar a imagem, você pode executar o contêiner usando o comando `docker run`. Substitua `nome-da-imagem` pelo nome da imagem que você baixou.

   ```bash
   docker run -d -p 8080:80 nome-da-imagem
   ```

   - `-d`: Executa o contêiner em segundo plano (em modo "detached").
   - `-p 8080:80`: Mapeia a porta 8080 do host para a porta 80 do contêiner. Você pode substituir `8080` por qualquer outra porta disponível em seu sistema.
   - `nome-da-imagem`: O nome da imagem Docker que você deseja executar.

3. **Verifique se o contêiner está em execução**: Para verificar se o contêiner está em execução, você pode usar o comando `docker ps`.

   ```bash
   docker ps
   ```

   Isso listará todos os contêineres em execução no momento. Certifique-se de que o seu contêiner esteja na lista.

4. **Acesse o aplicativo**: Agora que o contêiner está em execução, você pode acessar o aplicativo em seu navegador da web. Basta abrir um navegador e digitar `http://localhost:8080` na barra de endereços.

5. **Parar e remover o contêiner (opcional)**: Quando terminar de usar o contêiner, você pode pará-lo e removê-lo usando os seguintes comandos:

   ```bash
   docker stop ID_DO_CONTAINER
   docker rm ID_DO_CONTAINER
   ```

   Substitua `ID_DO_CONTAINER` pelo ID do contêiner que você deseja parar e remover. Você pode encontrar o ID do contêiner usando o comando `docker ps`.
   
   **Nota**: Você também pode parar e remover todos os contêineres de uma vez usando `docker stop $(docker ps -a -q)` e `docker rm $(docker ps -a -q)` respectivamente. Tenha cuidado ao usar esses comandos, pois eles param e removem todos os contêineres em seu sistema.

Isso conclui o guia sobre como executar um contêiner Docker em seu ambiente local.

# Sem Docker

Ao baixar o repositório, vai ser interessante você ter o PostgreSQL na sua maquina e em seguida, instanciar ele no projeto.
É interessante você baixar o maven para a criação de novas instâncias.

# Criar Múltiplas Instâncias de Microserviço com Maven

Se você está usando um discovery server para gerenciar as instâncias e não precisa especificar a porta manualmente, você pode simplesmente criar as instâncias do microserviço sem preocupações com a porta.

1. **Navegue até o Diretório do Projeto**: Abra o terminal e navegue até o diretório raiz do seu projeto `meu-microservico`.

2. **Crie as Instâncias**: Execute os seguintes comandos Maven para criar cada instância:

   ```bash
   # Crie a primeira instância
   mvn clean install
   java -jar target/meu-microservico.jar

   # Crie a segunda instância
   mvn clean install
   java -jar target/meu-microservico.jar

   # Crie a terceira instância
   mvn clean install
   java -jar target/meu-microservico.jar

# Passos para rodar

1- Rode primeiro o serviço DiscoveryServer, em seguida rode o serviço de Gateway e aí em seguida rode os demais serviços.

# Arquitetura 

![image](https://github.com/MarlonJerold/arquiteturamicroservice/assets/63025001/4ad458cd-7345-437b-bd6e-eb8f7cc287c8)


  

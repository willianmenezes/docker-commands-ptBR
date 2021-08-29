# Container

**docker container ls** -> Lista os containers em execução.

**docker container ls -q** -> Lista os IDs dos container ativos.

**docker container ls -a** -> Lista todos os containers.

**docker container run -d <nome da imagem>** -> Executa o container em backgroud.

**docker container run -p <porta do host>:<porta do container> <nome da imagem>** -> Executa um container mapeando a uma porta do host para uma determinada porta do container.

**docker container run -ti <nome da imagem>** -> Executar um container com um terminal e iteratividade, ou seja, ficar conectado em um container com um terminal ativo.

**docker container run -m 128M <nome da imagem>** -> Executa um container limitando a sua memória.

**docker container run --cpus 0.5 <nome da imagem>** -> Executa um container limitando o uso da cpu em porcentagem.

**docker container run -ti --mount type=bind,src=<caminho do diretorio existente no host>,dst=<caminho do diretorio no container> <nome da imagem>** -> Executa um container criando um volume do tipo bind.

**docker container run -ti --mount type=volume,src=<nome do volume>,dst=<caminho do diretorio no container> <nome da imagem>** -> Executa um container assossiando um volume criado ao container.

**docker container run -ti --mount type=volume,src=dbdados,dst=/data --mount type=bind,src=/opt/backup,dst=/backup debian tar -cvf /backup/bkp-banco.tar /data** -> Exedmplo de backup de dados utilizando container.

**docker container create <nome da imagem>** -> Cria um container mas não o coloca em execução.

**docker container create --name <nome do container> <nome da imagem>** -> Cria um container mas não o coloca em execução e seta um nome pra esse container.

**docker container attach <id do container>** -> Conecta em um container em execução.

**docker container pause <id do container>** -> Pausa um container em execução.

**docker container unpause <id do container>** -> despausa um container pausado.

**docker container start <id do container>** -> Executa um container parado.

**docker container stop <id do container>** -> Para um container em execução.

**docker container restart <id do container>** -> Restarta um container em execução.

**docker container rm <id do container>** -> Remove (deleta) um container.

**docker container rm -f <id do container>** -> Remove (deleta) um container em execução, utilizar o force.

**docker container exec -ti <id do container> <comando que quer executar (bash - ls - ps)>** -> Executa um comando dentro de um container.

**docker container inspect <id do container>** -> Mostra os detalhes de um determinado container

**docker container stats <id do container>** -> Mostra um status so container (Memória, CPU e etc) em tempo real.

**docker container top <id do container>** -> Mostra os processos em execução de um container.

**docker container update --cpus 0.2** -> Atualiza um container em execução limitando a sua CPU.

**docker container update -m 128M <nome da imagem>** ->  Atualiza um container em execução limitando a sua memória.

# Volumes

**docker volume create <nome do volume>** -> Cria um volume.

**docker volume ls** -> Lista os volumes criados.

**docker volume rm <nome do volume>** -> Remove um volume.

**docker volume rm -f <nome do volume>** -> Remove um volume.

**docker volume inspect giropops** -> Inspeciona um volume, mostrando os seus detalhes.

**docker volume prune** -> Delete os volumes que não estão sendo utilizados.

# Imagens

**docker image build -t <tag da imagem, nome>:<versão da imagem>** . -> Builda uma imagem a partir de um Dockerfile. O Dockerfile estã no mesmo diretório "."

**docker image tag <id da imagem> <nome da imagem>** -> Adiciona um nome a uma imagem.

**docker push <nomde do usuário / nome da imagem>** -> Envia uma imagem para o dockerhub.

**docker pull <nome da imagem>** -> Baixa uma imagem do dockerhub.

# Dockerfile

**FROM** -> imagem base

**RUN** -> Comando a ser executado no build/criação do container

**ENV** -> Seta variáveis de ambiente para o container. Ex: ENV teste opt/app -> WORKDIR Dolar{teste} COPY . Dolar{teste}

**COPY** -> Adicionar um recurso em determinado local do container (arquivos, arquivos compactados, diretórios e etc)

**ADD** -> Mesma função do COPY porem com alguns recursos a mais, como adicionar sites, arquivos remotos e já adicionar os arquivos compactados descompactados.

**USER** -> usuário a ser utilizado pelo container

**WORKDIR** -> Diretório onde o container vai ser iniciado

**VOLUME** -> Diretorio onde vai ser criado o volume

**EXPOSE** -> Portas que vão ser expostas pelo container

**ENTRYPOINT** -> Principal processo do container, ele que define se o container esta Up ou Down

**CMD** -> Comandos/Argumentos a serem passados para o container, atenção ao usar ele com o ENTRYPOINT

**ARG** -> Cria uma variável como argumento, e no momento do build da imagem pode-se alterar o valor desse argumento.
  
**LABEL** -> Adiciona metadados a imagem como versão, descrição e fabricante;

# Registry

**docker login** -> Realiza o login no repositorio especificado.

**docker container run -d -p 5000:5000 --restart=always --name registry registry:2** -> Inicializa um container registro local, para subir imagens em um registry que nao seja o dockerhub.

**curl localhost:5000/v2/_catalog** -> Visualiza as imagens no registry

**curl localhost:5000/v2/ubuntu-teste/tags/list** -> Mostra as versões da imagem no registry.
  
#Docker Machine

**docker-machine version** -> Verifica a versão do docker machine instalada

**docker-machine create --driver <driver> <nome da VM>** -> Cria uma maquina virtual com o driver desejado

**docker-machine ls** -> Lista as maquinas virtuais criadas
  
**docker-machine env <nome da VM>** -> Verifica as variáveis de ambiente da VM
  
**eval "$(docker-machine env <Nome da VM>)"** -> Adiciona as variaveis de ambiente da VM do client, para que os comando locais sejam executados na VM.

**eval $(docker-machine env -u)** -> Remove as váriaveis de ambiente do client.
  
**docker-machine ip linuxtips** -> Verifica o IP de uma VM

**docker-machine ssh linuxtips** -> Conecta na VM por SSH

**docker-machine inspect linuxtips** -> Inspeciona todos os dados de uma VM
  
**docker-machine stop linuxtips** -> Pausa uma VM

**docker-machine start linuxtips** -> Reinicia/inicia uma VM
  
**docker-machine rm linuxtips** -> Remove uma VM

# Utilidades

CTRL + p + q -> Sai do container mas o mantem em execução.

CTRL + D / exit -> Sai do container e mata a sua execução.

ps -ef -> Mostra todos os processos no linux de forma detalhada.

# Container

docker container ls -> Lista os containers em execução.

docker container ls -a -> Lista todos os containers.

docker container run -d <nome da imagem> -> Executa o container em backgroud.

docker container run -p <porta do host>:<porta do container> <nome da imagem> -> Executa um container mapeando a uma porta do host para uma determinada porta do container.

docker container run -ti <nome da imagem>-> Executar um container com um terminal e iteratividade, ou seja, ficar conectado em um container com um terminal ativo.

docker container run -m 128M <nome da imagem> -> Executa um container limitando a sua memória.

docker container run --cpus 0.5 <nome da imagem> -> Executa um container limitando o uso da cpu em porcentagem.

docker container run -ti --mount type=bind,src=<caminho do diretorio existente no host>,dst=<caminho do diretorio no container> <nome da imagem> -> Executa um container criando um volume do tipo bind.

docker container run -ti --mount type=volume,src=<nome do volume>,dst=<caminho do diretorio no container> <nome da imagem> -> Executa um container assossiando um volume criado ao container.

docker container run -ti --mount type=volume,src=dbdados,dst=/data --mount type=bind,src=/opt/backup,dst=/backup debian tar -cvf /backup/bkp-banco.tar /data -> Exedmplo de backup de dados utilizando container.

docker container create <nome da imagem> -> Cria um container mas não o coloca em execução.

docker container attach <id do container> -> Conecta em um container em execução.

docker container pause <id do container> -> Pausa um container em execução.

docker container unpause <id do container> -> despausa um container pausado.

docker container start <id do container> -> Executa um container parado.

docker container stop <id do container> -> Para um container em execução.

docker container restart <id do container> -> Restarta um container em execução.

docker container rm <id do container> -> Remove (deleta) um container.

docker container rm -f <id do container> -> Remove (deleta) um container em execução, utilizar o force.

docker container exec -ti <id do container> <comando que quer executar (bash - ls - ps)> -> Executa um comando dentro de um container.

docker container inspect <id do container> -> Mostra os detalhes de um determinado container

docker container stats <id do container> -> Mostra um status so container (Memória, CPU e etc) em tempo real.

docker container top <id do container> -> Mostra os processos em execução de um container.

docker container update --cpus 0.2 -> Atualiza um container em execução limitando a sua CPU.

docker container update -m 128M <nome da imagem> ->  Atualiza um container em execução limitando a sua memória.

## Volumes

docker volume create <nome do volume> -> Cria um volume.

docker volume ls -> Lista os volumes criados.

docker volume rm <nome do volume> -> Remove um volume.

docker volume rm -f <nome do volume> -> Remove um volume.

## Utilidades

CTRL + p + q -> Sai do container mas o mantem em execução.

CTRL + D / exit -> Sai do container e mata a sua execução.
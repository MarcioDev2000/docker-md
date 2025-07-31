# Estudo de Docker

Um container é uma unidade personalizada de software que empacota o código e todas as suas dependências para que um software possa ser executado de forma rápida, consistente e em qualquer ambiente.

## O que isso quer dizer?

- É uma caixa isolada que contém tudo que a sua aplicação precisa.
- **Personalizada** = você decide o que vai dentro (sistema, libs, versão do Node, etc.)
- **Imutável**: sempre se comporta da mesma forma, não muda após ser criado.
- **Isolado**: protege a máquina host, isolando recursos como memória, CPU, rede e processos.

---

## O que é a máquina host?

A máquina host é o computador real onde os containers estão rodando.  
**Exemplos**: seu notebook, servidor na nuvem ou um PC de testes.

---

## Eficiência

- **Eficiente**: inicia rápido e consome poucos recursos.

---

## Containers vs Máquinas Virtuais

- **Máquinas Virtuais**: computadores inteiros dentro de outro computador — mais pesadas, completas e isoladas.
- **Containers**: processos isolados e empacotados — rápidos, leves e usam o sistema do computador principal (host).

### Metáfora simples

- 🏠 **Container**: É como alugar um quarto em uma casa. Você tem seu espaço, traz seus móveis (apps), mas compartilha o teto (kernel) com os outros.
- 🏢 **Máquina Virtual**: É como comprar um prédio inteiro. Você tem total controle, mas precisa de muito mais estrutura.

---

## Por que containers são mais rápidos?

- Containers são apenas processos rodando dentro do sistema operacional, como qualquer outro programa (ex: navegador).
- Não precisam inicializar um sistema inteiro (boot).
- Compartilham o mesmo **kernel** da máquina host.
- Mesmo parecendo um sistema completo, o container apenas acessa partes do sistema principal (volumes, arquivos, rede), de forma **isolada**.

---

## Operações com Containers

- 🛑 Você pode:
  - Pausar um container e continuar depois.
  - Deletar quando não precisar mais.

---

## Containers na Nuvem

- A maioria dos containers roda **dentro de máquinas virtuais** na nuvem.
- Máquinas virtuais usam **hypervisors**, que criam sistemas completos — isso **gasta muitos recursos**.
- Por exemplo, uma app de 1 MB pode exigir uma VM de 4 GB só para funcionar.
- Iniciar uma VM é **mais lento** (como ligar um novo computador).

---

## Vantagens dos Containers

- Compartilham o **kernel** do sistema da máquina host.
- Isolam apenas os processos necessários.
- São **leves, rápidos e eficientes**.
- **Inicialização quase instantânea**, baixo consumo de recursos.

---

## Escalabilidade

- Com Docker, é possível rodar várias aplicações no mesmo sistema como **processos isolados**.
- Não é necessário instalar múltiplos sistemas operacionais.
- Permite **escalar aplicações rapidamente**, economizando tempo e recursos.
- Máquinas virtuais são **mais pesadas e lentas** para escalar.

---

## Container Runtime

- Software responsável por **executar containers**, seguindo padrões de compatibilidade.
- A **OCI (Open Containers Initiative)** define esses padrões, liderada por Docker e outras empresas.
- Isso permite que containers rodem em diferentes runtimes como **Docker** ou **Podman**.

---

## Antes do Docker

- Containers já existiam com o **LXC (Linux Containers)**.
- Usavam recursos do Linux como:
  - **Namespaces** (isolamento)
  - **cgroups** (controle de CPU, memória, etc.)
- Docker **popularizou** e **facilitou** o uso de containers.

---

## Origem do Docker

- Criado em **2013** pela empresa **DotCloud**.
- Objetivo: rodar aplicações dos clientes em sua plataforma (PaaS).
- Ficou tão popular que a empresa virou **Docker Inc.** e tornou o Docker open source.

---

## Diferença que o Docker trouxe

- Tornou containers **simples, completos e de alto nível**.
- Gerencia:
  - Redes
  - Volumes
  - Imagens
- Tudo de forma integrada.

---

## Versões do Docker

- **Docker Community Edition (Engine)**: open source e gratuito.
- **Docker Desktop**: voltado para desenvolvimento, com interface gráfica (não é open source).

---

## Arquitetura Docker

- Funciona em modelo **client-server**.
- Quando você roda um comando, ele vai para o daemon `dockerd`, que gerencia tudo.
- Se o daemon cair, **todos os containers param** (Single Point of Failure).
- Ferramentas como **Podman** evitam esse problema.

---

## Tecnologias usadas pelo Docker

- Usa recursos do Linux:
  - **Namespaces**
  - **cgroups**
- Componentes como:
  - **RunC**
  - **ContainerD**
- Esses componentes foram doados à **OCI**.

---

## Segurança

- Docker exige permissões de **administrador (root)** por padrão.
- Pode representar riscos.
- É possível rodar em **modo rootless**, com mais segurança.

---

## Resumo

O Docker:

- Tornou o uso de containers **acessível e popular**.
- É uma das **ferramentas mais importantes** para desenvolvedores e infraestrutura.
- Permite criar ambientes de forma **leve, rápida e eficiente**.
# Docker Inc.

A **Docker Inc.** é a empresa por trás do Docker, mas o **Docker em si é uma ferramenta open source**.

## Missão da Docker Inc.

Ajudar desenvolvedores a serem mais produtivos, especialmente na fase de desenvolvimento dos projetos (chamada de *inner circle*).

## Foco da Docker Inc.

- Melhorar o **Docker Engine** (versão gratuita e open source).
- Criar ferramentas pagas que facilitam o uso do Docker.

### Ferramentas da Docker Inc.

- **Docker Desktop**: versão com interface gráfica para rodar containers no PC. Possui versões gratuita e paga.
- **Docker Hub**: repositório online para armazenar e baixar imagens de containers.
- **Docker Build Cloud**: acelera o *build* de imagens, funcionando localmente ou em CI/CD.
- **Docker Scout**: analisa imagens e mostra vulnerabilidades de segurança.
- **Docker AI**: facilita a execução de aplicações de IA com containers.

> A Docker Inc. não quer só rodar containers, mas **ajudar em todo o processo de desenvolvimento** — testes, segurança, builds e integração com tecnologias como Kubernetes.

---

## "Na Minha Máquina Funciona"

Containers ajudam a eliminar problemas entre ambiente de desenvolvimento e produção, pois **o ambiente no container é sempre o mesmo, independentemente da máquina**.

---

# Resumo do Capítulo: Manipulando Containers

## 1. Executando o Primeiro Container

**docker run hello-world**

## Resumo do capítulo

## Manipulando Containers

## 1. Executando o Primeiro Container (docker run hello-world)
Para verificar se o Docker está instalado corretamente, execute:

 **docker run hello-world**

Este comando baixa a imagem hello-world (se ainda não estiver no seu sistema) e executa um container que exibe uma mensagem de confirmação.

## 2. Nomeando Containers e Entendendo Diferentes Execuções

Executando um Container com um Nome Personalizado
Por padrão, o Docker atribui nomes aleatórios aos containers. Você pode especificar um nome usando a flag --name:

**docker run --name mynginx nginx**

Executando um Container em Segundo Plano (d)
Para executar um container em modo "detached" (segundo plano), use a flag -d:

**docker run -d --name mynginx nginx**

Mapeando Portas com a Flag p
Para mapear a porta do container para a porta do host, use -p:

**docker run -d -p 8080:80 nginx**

Isso mapeia a porta 80 do container para a porta 8080 do host.

## 3. Parando, Iniciando e Removendo Containers de Forma Forçada

Listando Containers em Execução e Parados
Containers em execução:

  **docker ps**
Todos os containers (incluindo parados):

  **docker ps -a**

Diferença: docker ps lista apenas os containers em execução, enquanto docker ps -a lista todos os containers existentes no sistema.

-- Parando um Container
-- docker stop mynginx
-- Iniciando um Container Parado
-- docker start mynginx
-- Removendo um Container
-- Remoção normal:

  **docker rm mynginx**

Remoção forçada (para containers em execução):

  **docker rm -f mynginx**
Diferença: docker rm remove apenas containers parados. Para remover um container em execução, use docker rm -f.

## 4. Attach e Detach
Conectando-se a um Container em Execução (docker attach)
docker attach mynginx
Este comando conecta seu terminal ao processo principal do container.

Saindo do Container sem Parar (CTRL + P, CTRL + Q)
Para sair do modo attach sem parar o container, pressione CTRL + P seguido de CTRL + Q.

## 5. Executando Comandos e Removendo Containers Automaticamente
Executando Comandos em um Novo Container
Você pode executar um comando diretamente em um novo container:

**docker run nginx ls -la**

Isto executa ls -la no container nginx e exibe o resultado no seu terminal.

Entrando no Container com Bash
Para acessar o shell bash dentro de um container:

**docker run -it nginx bash**
Isto inicia um container nginx e abre uma sessão interativa do bash.

Diferença entre docker run e docker exec
docker run: Cria e inicia um novo container.
docker exec: Executa um comando em um container já em execução.
Exemplo com docker exec:

**docker exec -it mynginx bash**
Isto abre uma sessão bash em um container mynginx já em execução.

Removendo Containers Automaticamente (-rm)
Para remover automaticamente um container após sua execução:

**docker run --rm nginx ls -la**

## 6. Removendo Todos os Containers com Subcomandos
Para remover todos os containers parados:

**docker rm $(docker ps -a -q)**

Explicação:
docker ps -a -q lista todos os IDs de containers.
$(...) insere essa lista no comando docker rm.
Para remover todos os containers, incluindo os em execução, use:

**docker rm -f $(docker ps -a -q)**

## 7. Publicação de Portas
Para executar um servidor Nginx em um container e publicar a porta:

**docker run -d -p 8080:80 nginx**
Agora, o Nginx está acessível em http://localhost:8080.

## 8. Execução Interativa e Acesso ao Shell
Acessando o Shell de um Container com docker exec -it
Se você já tem um container em execução e deseja acessar seu shell:

**docker exec -it mynginx bash**

Diferença entre docker exec e docker attach
docker exec: Executa um novo processo dentro de um container em execução (ex.: abrir uma nova sessão bash).
docker attach: Anexa seu terminal ao processo principal do container (ex.: ver logs em tempo real).
Resumo dos Comandos


Executar um container:

  docker run [opções] imagem [comando]
Listar containers:

  **docker ps**       # Em execução
  **docker ps -a**     # Todos
Parar, iniciar e remover containers:

  **docker stop <nome|id>**
  **docker start <nome|id>**
  **docker rm <nome|id>**
  **docker rm -f <nome|id>**   # Forçado
Executar comandos em containers:

  **docker exec -it <nome|id> <comando>**
Acessar shell bash:

  **docker exec -it <nome|id>** bash
Remover todos os containers:

  **docker rm $(docker ps -a -q)**
  **docker rm -f $(docker ps -a -q)**   # Incluindo em execução


## 📦 Formas de persistência de dados em containers:
Bind Mounts

## Volumes

## 🔁 Bind Mounts

Mapeia uma pasta do host (sua máquina) para dentro do container.

Alterações feitas no host aparecem no container em tempo real.

Ideal para desenvolvimento, pois permite ver mudanças imediatamente.

Pode gerar problemas de permissões e performance, especialmente em Mac/Windows.

Performance já melhorada com tecnologias como VirtioFS e Mutagen (Docker Desktop).

## 📂 Volumes
Gerenciado pelo Docker, não é uma pasta visível no host.

Usado para armazenamento persistente de dados (ex: bancos de dados).

Mais seguro e estável, ideal para produção.

Pode ser montado na nuvem (cloud storage) e acessado por containers.

====================

Crindo pasta no Ubuntu.

**mkdir nome_da_pasta**

Isso vai criar a pasta dentro do diretório atual (no caso, ~, que é sua home: /home/marcioabreu/).

🔍 Verificar se a pasta foi criada:

**ls**


## 📁 Dica extra:
Se quiser entrar na pasta depois de criá-la:

**cd my_nginx_html**

Se quiser criar um arquivo HTML dentro dela:

**echo "<h1>Content updated</h1>" > index.html**

✅ Basta usar o caminho atual com $(pwd):


**docker run -d -p 8080:80 -v $(pwd):/usr/share/nginx/html nginx**


🔍 Explicando:
**$(pwd)** → retorna o caminho absoluto da pasta atual (/home/marcioabreu/trainer_nginx_html)

**:/usr/share/nginx/html** → é o local padrão que o Nginx usa para servir páginas

✅ Resumo do que está acontecendo:


✅ Resumo do que está acontecendo:

# 1. Comando resumido com -v:
docker run -d -p 8080:80 -v $(pwd)/my_nginx_html:/usr/share/nginx/html nginx


Esse é o jeito mais curto e prático.
O -v aceita tanto bind mounts quanto volumes, dependendo do que você escreve.
É o mais usado no dia a dia.

# 2. Comando mais detalhado com --mount:

**docker run -d -p 8080:80 \
  --mount type=bind,source=$(pwd)/my_nginx_html,target=/usr/share/nginx/html \
  nginx**

Com ele, você consegue especificar:

**type=bind**: É um bind mount (não volume do Docker).
**source=$(pwd)/my_nginx_html**: A pasta do seu computador.
**target=/usr/share/nginx/html**: Onde essa pasta vai aparecer dentro do container.


Quando já está dentro da pasta:
docker run -d --rm -p 8080:80 \
  --mount type=bind,source=$(pwd),target=/usr/share/nginx/html \
  nginx**


**--mount**: Forma mais moderna e clara de montar volumes.
type=bind: Você está ligando uma pasta do host (seu computador) para dentro do container.
**source=$(pwd)**: Pega o caminho atual onde você está no terminal.
**target=/usr/share/nginx/html**: Pasta padrão onde o Nginx procura os arquivos HTML.
\: Quebra de linha (certifique-se de que não há texto colado nela, como no seu erro).


**O que são volumes no Docker?**

Volumes são uma forma de armazenar dados persistentes usados e gerenciados pelo Docker. Ao contrário dos bind mounts, você não precisa saber onde os arquivos estão fisicamente no seu computador.

Criar um volume:
**docker volume create my_volume**

Listar volumes existentes:
**docker volume ls**

Inspecionar volume (ver onde ele fica):
**docker volume inspect my_volume**

Obs: Mostra que ele está em algo como: **/var/lib/docker/volumes/my_volume/_data**

Remover volumes não utilizados:
**docker volume prune**

Remover um volume específico:
**docker volume rm my_volume**


# ✅ Agora, se quiser usar esse volume em um container Nginx:
🔸 Exemplo:
docker run -d --rm -p 8080:80 \
  --mount type=volume,source=my_volume,target=/usr/share/nginx/html \
  nginx

# 📌 Explicação:

type=volume: Está dizendo que vai usar um volume (e não um bind mount).
source=my_volume: Nome do volume que você criou.
target=/usr/share/nginx/html: Pasta dentro do container Nginx onde o conteúdo será lido.


Comandos úteis para volumes:

**docker volume prune**
Remove volumes anônimos não utilizados


**docker volume rm <nome>**
Remove um volume nomeado específico


**docker volume ls**
Lista todos os volumes (nomeados e anônimos)


Adicionar um volume num container:
**docker run -v my_volume:/usr/share/nginx/html nginx**


## 📦 3. Backup de um Volume
docker run --rm \
  -v my_volume:/data \
  -v $(pwd)/backup_host:/backup \
  busybox \
  tar czf /backup/backup.tar.gz -C /data .


my_volume:/data: Monta o volume no container.
$(pwd)/backup_host:/backup: Pasta local onde o backup será salvo.
Cria backup.tar.gz com os dados do volume.

## ♻️ 4. Restauração do Backup
Inverte o processo: usa o mesmo volume e extrai os dados do .tar.gz.
docker run --rm \
  -v my_volume:/data \
  -v $(pwd)/backup_host:/backup \
  busybox \
  tar xzf /backup/backup.tar.gz -C /data


Extrai o backup dentro do volume montado em /data.


## 1. Entendendo a Perda de Dados Após a Remoção do Container
Por padrão, tudo o que acontece dentro de um container Docker é efêmero. Ao remover um container, todos os dados e alterações feitas dentro dele são perdidos. Isso é útil para manter a consistência e portabilidade, mas pode ser problemático quando precisamos persistir dados, como em bancos de dados ou aplicações que armazenam informações de usuários.

Camadas de Leitura e Escrita nos Containers

Os containers Docker utilizam um sistema de arquivos em camadas, conhecido como OverlayFS. Quando um container é iniciado a partir de uma imagem, o Docker cria uma camada de leitura e escrita sobre as camadas somente leitura da imagem. Todas as alterações feitas no container são gravadas nessa camada superior.


Introdução ao OverlayFS e Funcionamento das Camadas

  .**OverlayFS**: É um sistema de arquivos unificador que permite sobrepor múltiplos sistemas de arquivos.

  .**Camadas de Imagem**: São camadas somente leitura que compõem a imagem Docker.
  .**Camada de Container**: É a camada de leitura e escrita criada quando o container é iniciado.


## 2. Introdução à Persistência de Dados

Por que Precisamos Persistir Dados?

Em muitos casos, precisamos que os dados sobrevivam além do ciclo de vida de um container. Por exemplo:

.**Bancos de dados que armazenam informações críticas**.
.**Aplicações que geram logs importantes**.
.**Sites que permitem uploads de arquivos**.


Conceitos de Volumes e Bind Mounts no Docker

**Volumes**:

  .Gerenciados pelo Docker.
  .Armazenados em um local específico no sistema de arquivos do Docker.
  .Podem ser locais ou remotos (usando drivers de volume).
  .São a maneira recomendada para persistir dados em produção.

**Bind Mounts**:

  .Montam um diretório ou arquivo do sistema de arquivos do host no container.
  .Oferecem mais flexibilidade durante o desenvolvimento.
  .Dependem da estrutura do host, o que pode afetar a portabilidade.

============================================================

## 5. Backup e Restauração de Volumes
Para garantir a persistência dos dados armazenados em volumes, é uma prática recomendada criar backups regulares, especialmente em ambientes de produção.

Backup de um Volume

**docker run --rm -v my_volume:/data -v $(pwd):/backup busybox tar czf /backup/backup.tar.gz /data**

**docker run**: Executa um novo container.

-rm: Remove o container automaticamente ao final do processo.

**v my_volume:/data**: Monta o volume my_volume no caminho /data dentro do container.

v $(pwd):/backup: Monta o diretório atual do host ($(pwd)) no caminho /backup dentro do 
container.

**busybox**: Uma imagem de contêiner leve usada para executar comandos Unix básicos.

tar czf /backup/backup.tar.gz /data:
      .Cria um arquivo compactado backup.tar.gz com o conteúdo do volume my_volume e o armazena no diretório atual do host.

**Restauração de um Volume**

docker run --rm -v my_volume:/data -v $(pwd):/backup busybox tar xzf /backup/backup.tar.gz -C /

docker run: Executa um novo container.

-rm: Remove o container automaticamente ao final do processo.

v my_volume:/data: Monta o volume my_volume no caminho /data dentro do container.

v $(pwd):/backup: Monta o diretório atual do host, onde o arquivo de backup está localizado.

tar xzf /backup/backup.tar.gz -C /:
   . Extrai o conteúdo de /backup/backup.tar.gz no diretório raiz do container.
   . O arquivo backup.tar.gz inclui o caminho /data, que restaura os dados diretamente no volume my_volume.

-------------------------


## 📌 O que são Imagens Docker?
São modelos prontos (templates) usados para criar containers.

Contêm tudo o que o container precisa: sistema operacional, bibliotecas e a aplicação.

Você já lidou com imagens ao rodar containers como nginx, busybox e rabbitmq.


## 📁 Comando docker images
Mostra todas as imagens baixadas na máquina.
  Cada imagem tem:
    .ID único
    .Nome (repositório)
    .Tag (versão)

## 🏷️ A importância da Tag (versão)
A tag indica a versão da imagem. Exemplo: 1.0, 1.1, latest.

latest significa “última versão publicada”, mas pode mudar com o tempo.

## ⚠️ Cuidados com latest
    . Nunca use latest em produção. Ela pode mudar e quebrar sua aplicação.
    . Sempre use uma versão fixa (ex: 1.0) em ambientes de produção.
    . Em desenvolvimento, latest é aceitável por ser mais conveniente.

## 📦 Tamanho das imagens
Imagens menores são melhores:
   .Menos espaço em disco
   .Menor tempo de download/upload
   .Menos componentes → menor risco de vulnerabilidades
   .Evite instalar coisas desnecessárias como editores ou compiladores em imagens de produção.


Para eliminar uma imagem usa o comando:
    
**docker rmi <nome-da-imagem-ou-ID>**

Remove todas as imagens que não estão associadas a nenhum container:

**docker image prune -a**

📋 Remoção em massa de imagens
Para remover todas as imagens listadas, use:

bash
Copy
Edit
docker rmi $(docker images -q)
Para forçar:

bash
Copy
Edit
**docker rmi -f $(docker images -q)**

=================================================================

| Ação                              | Comando                          |
| --------------------------------- | -------------------------------- |
| Rodar container                   | `docker run nome:tag`            |
| Listar containers                 | `docker ps` / `docker ps -a`     |
| Remover container                 | `docker rm id-ou-nome`           |
| Remover imagem                    | `docker rmi nome:tag`            |
| Forçar remoção                    | `docker rmi -f nome:tag`         |
| Inspecionar imagem                | `docker inspect nome-ou-id`      |
| Buscar imagens                    | `docker search nome`             |
| Baixar imagem (sem rodar)         | `docker pull nome:tag`           |
| Limpar imagens "órfãs" (dangling) | `docker image prune`             |
| Limpar todas não usadas           | `docker image prune -a`          |
| Remover todas as imagens          | `docker rmi $(docker images -q)` |
_______________________________________________________________________



## 3. 🗑️ Limpeza de Imagens e Containers
Para evitar acúmulo:
docker image prune: remove imagens órfãs (sem tag, sem uso)

**docker image prune -a**: remove todas as imagens que não estão sendo usadas

**docker container prune**: remove containers parados

**docker system prune**: limpa containers, imagens e volumes não utilizados

| Característica   | `ARG`                           | `ENV`                               |
| ---------------- | ------------------------------- | ----------------------------------- |
| Visibilidade     | Só durante **build**            | Disponível em **build e runtime**   |
| Escopo           | Só no momento do `docker build` | Acessível no `build` e no container |
| Valor pode mudar | Sim, com `--build-arg`          | Sim, com `-e` no `docker run`       |
| Exemplo de uso   | Versões, flags de build         | Variáveis de ambiente no app        |
--------------------------------------------------------------------------------------------

# Definindo versão do Node de forma flexível
ARG NODE_VERSION=18
FROM node:${NODE_VERSION}

# ARG usado só durante o build
ARG APP_VERSION=1.0.0

# ENV persistirá no container em runtime
ENV NODE_ENV=production
ENV PORT=3000

# Criar um diretório de trabalho
WORKDIR /app

# Copiar arquivos da app
COPY . .

# Instalar dependências
RUN npm install

# Mostrar a versão da app (usando ARG)
RUN echo "Versão da aplicação: $APP_VERSION"

# Criar usuário não-root por segurança
RUN useradd --create-home --shell /bin/bash appuser

# Alterar o dono dos arquivos (evita erro de permissão)
RUN chown -R appuser /app

# Trocar para o usuário comum
USER appuser

# Expõe a porta (opcional)
EXPOSE ${PORT}

# Comando final
CMD ["npm", "start"]

==================================================================

# ✅ O que é o HEALTHCHECK?

   O HEALTHCHECK é uma instrução no Dockerfile que permite monitorar a saúde do container em tempo de execução. Ele é muito útil para:

     . Garantir que o container realmente está funcionando como deveria.

     . Automatizar reinicializações em ferramentas como Docker Swarm ou Kubernetes.

     . Diagnosticar rapidamente se um serviço parou de responder.


------------------------------------------------------------------------------------------
| Parâmetro        | Descrição                                                           |
| ---------------- | ------------------------------------------------------------------- |
| `--interval`     | Tempo entre verificações (ex: `10s`, `30s`)                         |
| `--timeout`      | Tempo máximo que a verificação pode levar                           |
| `--start-period` | Tempo de espera antes da primeira checagem (útil durante o startup) |
| `--retries`      | Quantidade de tentativas antes de marcar como `unhealthy`           |
------------------------------------------------------------------------------------------

============================================================================================
| Conceito           | Explicação rápida                                                    |
| ------------------ | -------------------------------------------------------------------- |
| `HEALTHCHECK`      | Verifica se a aplicação está de fato funcionando dentro do container |
| `curl -f`          | Retorna erro se o status HTTP for diferente de 2xx                   |
| `exit 1`           | Indica que o healthcheck falhou                                      |
| `/health` endpoint | Verifica serviços críticos da aplicação                              |
| `docker ps`        | Mostra se a aplicação está `healthy` ou `unhealthy`                  |

==================================================================================

# O que significa EXPOSE no Dockerfile?

É uma instrução dentro do Dockerfile usada para documentar quais portas a aplicação dentro do container está ouvindo.

🔸 Exemplo:
EXPOSE 3001

Isso indica que o container está preparado para escutar a porta 3001, mas não publica essa porta para o mundo externo automaticamente.

# 🧠 Importante: EXPOSE ≠ expor de verdade
Para realmente tornar a porta acessível externamente, você precisa usar:

docker-compose.yml:

ports:
  - "3001:3001"

 O que são VOLUMES no Dockerfile?

**Um volume é uma forma de armazenar dados de forma persistente fora do container, mesmo que ele seja destruído.**

🔸 Quando usar?
      . Para guardar logs, bancos, uploads, cache, etc.

      . Evitar perda de dados ao parar ou remover containers.



🧹 Como limpar volumes inúteis:


docker system prune --volumes


# ✅ 1. Por que otimizar imagens Docker?

# ✳️ Problemas com imagens grandes:
Ocupam muito espaço em disco

Demoram para fazer pull/push (subir ou baixar)

São mais propensas a vulnerabilidades

Lentidão em CI/CD, builds, deploys etc.

# 🎯 Objetivo:
Reduzir o tamanho da imagem sem quebrar o funcionamento da aplicação, e de preferência sem perder performance ou segurança.

# 🧹 2. Comece com um .dockerignore bem feito

✅ Solução:
Crie um arquivo .dockerignore como este:

node_modules
.git
npm-debug.log
.DS_Store
*.test.js
coverage/


🧱 3. Use imagens menores: Alpine ou Slim

🏋️ Padrão:
Imagens base como node:18 vêm com várias ferramentas e ocupam ~1 GB.

🧊 Alpine:

FROM node:18-alpine


Extremamente leve (~50MB–100MB)

Ideal para produção

Poucas ferramentas instaladas

Pode exigir ajustes (ex: comandos diferentes como adduser)


🪶 Slim:

FROM node:18-slim


Meio termo: mais leve que a imagem padrão, mais completa que Alpine

Inclui ferramentas básicas para debug/manutenção

Ótima opção quando Alpine é leve demais para o que você precisa

==============================================================

| Imagem Base      | Tamanho aproximado | Observação                                     |
| ---------------- | ------------------ | ---------------------------------------------- |
| `node:18`        | \~1 GB             | Completa, mas pesada                           |
| `node:18-slim`   | \~300 MB           | Boa redução, ferramentas básicas               |
| `node:18-alpine` | \~60–100 MB        | Super leve, mas exige cuidado com libs nativas |
------------------------------------------------------------------------------------------


🧠 Antes de tudo: o que são CMD e ENTRYPOINT?
CMD: Define o comando padrão que o container deve executar.

ENTRYPOINT: Define o programa principal fixo que sempre será executado.

Eles podem trabalhar juntos.

## 1. Usando apenas CMD:

CMD ["./server", "8080"]

Quando você roda:

docker run minha-imagem

👉 Ele executa: ./server 8080

🔐 Usando ENTRYPOINT fixo + CMD flexível

ENTRYPOINT ["./server"]
CMD ["8080"]


Agora, quando você roda:

docker run minha-imagem

👉 Ele executa: ./server 8080

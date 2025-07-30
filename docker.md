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

```bash
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

Parando um Container
docker stop mynginx
Iniciando um Container Parado
docker start mynginx
Removendo um Container
Remoção normal:

  **docker rm mynginx**

Remoção forçada (para containers em execução):

  **docker rm -f mynginx**
Diferença: docker rm remove apenas containers parados. Para remover um container em execução, use docker rm -f.

4. Attach e Detach
Conectando-se a um Container em Execução (docker attach)
docker attach mynginx
Este comando conecta seu terminal ao processo principal do container.

Saindo do Container sem Parar (CTRL + P, CTRL + Q)
Para sair do modo attach sem parar o container, pressione CTRL + P seguido de CTRL + Q.

5. Executando Comandos e Removendo Containers Automaticamente
Executando Comandos em um Novo Container
Você pode executar um comando diretamente em um novo container:

docker run nginx ls -la
Isto executa ls -la no container nginx e exibe o resultado no seu terminal.

Entrando no Container com Bash
Para acessar o shell bash dentro de um container:

docker run -it nginx bash
Isto inicia um container nginx e abre uma sessão interativa do bash.

Diferença entre docker run e docker exec
docker run: Cria e inicia um novo container.
docker exec: Executa um comando em um container já em execução.
Exemplo com docker exec:

docker exec -it mynginx bash
Isto abre uma sessão bash em um container mynginx já em execução.

Removendo Containers Automaticamente (-rm)
Para remover automaticamente um container após sua execução:

docker run --rm nginx ls -la
6. Removendo Todos os Containers com Subcomandos
Para remover todos os containers parados:

docker rm $(docker ps -a -q)
Explicação:
docker ps -a -q lista todos os IDs de containers.
$(...) insere essa lista no comando docker rm.
Para remover todos os containers, incluindo os em execução, use:

docker rm -f $(docker ps -a -q)
7. Publicação de Portas
Para executar um servidor Nginx em um container e publicar a porta:

docker run -d -p 8080:80 nginx
Agora, o Nginx está acessível em http://localhost:8080.

8. Execução Interativa e Acesso ao Shell
Acessando o Shell de um Container com docker exec -it
Se você já tem um container em execução e deseja acessar seu shell:

docker exec -it mynginx bash
Diferença entre docker exec e docker attach
docker exec: Executa um novo processo dentro de um container em execução (ex.: abrir uma nova sessão bash).
docker attach: Anexa seu terminal ao processo principal do container (ex.: ver logs em tempo real).
Resumo dos Comandos
Executar um container:

  docker run [opções] imagem [comando]
Listar containers:

  docker ps        # Em execução
  docker ps -a     # Todos
Parar, iniciar e remover containers:

  docker stop <nome|id>
  docker start <nome|id>
  docker rm <nome|id>
  docker rm -f <nome|id>   # Forçado
Executar comandos em containers:

  docker exec -it <nome|id> <comando>
Acessar shell bash:

  docker exec -it <nome|id> bash
Remover todos os containers:

  docker rm $(docker ps -a -q)
  docker rm -f $(docker ps -a -q)   # Incluindo em execução

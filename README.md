# clone-tabnews

Este repositório contém a implementação do projeto [TabNews](https://www.tabnews.com.br) para o curso [curso.dev](https://curso.dev). Abaixo, uma lista de referência dos comandos utilizados durante o desenvolvimento.

# Tecnologias utilizadas

- 🐧 **Navegação e Sistema:** Linux/Bash
- 🟢 **Ambiente de Execução:** Node.js
- 🟢 **Gerenciamento de Versão:** NVM
- 📦 **Gerenciador de Pacotes:** NPM
- 🌳 **Controle de Versão Offline / Local:** Git
- ☁️ **Controle de Versão Online / Remoto:** Git
- ▲ **Framework Web:** Next.js
- ⚛️ **Biblioteca de Interface de Usuário:** React
- 💅 **Estilização e Formatação de Código:** Prettier, EditorConfig
- ☁️ **Hospedagem e Continuous Deployment (CD):** Vercel
- 🐳 **Conteinerização:** Docker
- 🧪 **Testes Automatizados:** Jest
- 🐘 **Banco de Dados:** PostgreSQL
- ⚙️ **Configuração e Padrões:** `.env.development` (Variáveis de Ambiente - OBS: antes `.env`, que não era commitado), `jsconfig.json` (Absolute Imports).

# ⭐ Lista de comandos

### 🐧 Navegação e Sistema (Linux/Bash)

Estes são os comandos básicos para você se localizar e organizar o terminal do Codespaces.

- **`clear`** ou **`Ctrl + L`**: Limpa a tela do terminal. (Dica*:* O atalho `Ctrl + L` é o preferido do instrutor, pois limpa o visual sem adicionar o registro "clear" no histórico de comandos.)
- **`ls`**: Lista os arquivos e pastas visíveis no diretório atual.
- **`ls -l`**: Lista os arquivos em formato vertical, exibindo mais detalhes (permissões, tamanho, etc).
- **`ls -la`**: Lista **todos** os arquivos, incluindo os ocultos (aqueles que começam com `.`, como a pasta `.git`).
- **`sudo apt update && sudo apt install dnsutils -y`**: Atualiza os repositórios e instala o pacote que contém as ferramentas `dig` e `nslookup`. (Essencial em ambientes novos).
- **`env`**: Lista todas as variáveis de ambiente ativas no seu processo atual do Shell.
- **`history`**: Exibe o histórico de comandos digitados no terminal. (Dica: Adicionar um **espaço em branco** antes de qualquer comando impede que ele seja registrado no histórico, protegendo dados sensíveis).
- **`exit`** ou **`Ctrl + D`**: Encerra a sessão atual do terminal ou processo ativo.
- **`Ctrl + P`** (Windows/Linux) ou **`Cmd + P`** (macOS): Atalho para o **Fuzzy Search** (busca difusa) do VS Code. Permite encontrar arquivos rapidamente digitando apenas partes do nome.
- **`Ctrl + P` > `@nome_da_propriedade`**: Busca avançada que leva o cursor diretamente para um símbolo ou propriedade dentro de um arquivo (ex: `@scripts` no `package.json`).
- **`code [arquivo]`**: Comando de linha de comando (CLI) do VS Code para criar um novo arquivo ou abrir um existente diretamente pelo terminal.

### 🟢 Node.js e NVM (Gerenciamento de Versão)

Comandos essenciais para configurar a fundação do projeto e garantir que todos estejam na mesma versão da tecnologia.

- **`node -v`**: Verifica qual versão do **Node.js** (Node.js = ambiente de execução JavaScript que permite rodar JavaScript no servidor, fora do navegador) está ativa no momento.
- **`nvm ls`**: Lista as versões do Node.js instaladas e disponíveis no **NVM** (Node Version Manager = script que gerencia diferentes versões do Node.js).
- **`nvm install lts/hydrogen`**: Instala a versão LTS (Long Term Support) específica chamada "Hydrogen".
- **`nvm alias default lts/hydrogen`**: Define a versão "Hydrogen" como o padrão do sistema, para que ela seja carregada automaticamente sempre que você abrir um novo terminal.
- **`nvm install`**: Quando rodado sem argumentos na raiz do projeto, ele lê o arquivo `.nvmrc` (que especifica a versão do Node.js que o projeto requer) e instala/seleciona a versão definida nele.

### 📦 NPM (Gerenciador de Pacotes)

Comandos para gerenciar as dependências (bibliotecas) do projeto e executar scripts.

- **`npm init`**: Comando do **npm** (Node Package Manager = gerenciador padrão do Node.js usado para instalar, compartilhar e controlar as dependências - i.e., bibliotecas e ferramentas - de um projeto JavaScript) que inicializa o projeto, criando o arquivo `package.json` (o manifesto).
- **`npm install [pacote]@[versão]`**: Baixa e instala uma dependência no projeto. Utilizar o `@[versão]` instala uma versão exata de um pacote, ignorando atualizações automáticas.
  - Exemplos usados: `npm install next@13.1.6` (**Next.js** = framewok para desenvolvimento web que permite criar sites rápidos com renderização no servidor), `npm install react@18.2.0` (**React** = biblioteca principal para construir interfaces de usuário baseadas em componentes), `npm install react-dom@18.2.0` (**React DOM** = permite ao React interagir com o navegador e renderizar os elementos no HTML).
- **`npm run dev`**: Executa o script chamado "dev" que configuramos no `package.json` (que, por sua vez, roda o `next dev` para subir o servidor local).
- **`npm install [pacote] --save-dev`** (ou **`npm install [pacote] -D`**): Instala uma dependência exclusivamente para o ambiente de desenvolvimento (ela vai para o bloco `devDependencies` do `package.json`). Utilizada para ferramentas que não vão para produção, como o Prettier (ex: `npm install prettier --save-dev`).
- **`npm run lint:check`**: Comando/script personalizado criado no `package.json` para rodar o Prettier no modo de conferência (`prettier --check .`), analisando todos os arquivos e avisando se há erros de formatação sem alterar nada.
- **`npm run lint:fix`**: Comando/script personalizado criado no `package.json` para rodar o Prettier no modo de conserto (`prettier --write .`), corrigindo e reescrevendo automaticamente a formatação dos arquivos que estão fora do padrão.
- **`npm run services:up`**: Atalho para subir a infraestrutura do Docker em segundo plano. Abstração adicionada ao `package.json` para facilitar a vida do desenvolvedor.
- **`npm run services:stop`**: Atalho para pausar os serviços do Docker. Adicionado ao `package.json`.
- **`npm run services:down`**: Atalho para derrubar e remover os contêineres e redes do Docker. (Nota: Por padrão, este comando mantém os volumes de dados; os dados só são deletados se a flag `-v` for incluída no script do `package.json`).
- **`npm run dev`**: Agora automatizado para executar **`services:up && next dev`**. Um único comando que garante que o banco de dados esteja ativo antes de subir o servidor web.

### 🌳 Git (Controle de Versão Offline / Local)

Estes são os comandos para gerenciar a "máquina do tempo" do seu código por meio do **Git** (Git = sistema de controle de versão, que registra e recupera o histórico de alterações). Lembre-se que, até o Dia 5, todos funcionam localmente (_offline_).

- **`git status`**: É a sua bússola. Mostra em qual estado estão seus arquivos (_Untracked_, _Modified_ ou _Staged_).
- **`git add [arquivo]`**: Move um arquivo do estado _Modified_ (ou _Untracked_) para o _Staged_ (o palco), preparando-o para a próxima “foto” (_Commit_).
- **`git commit -m "mensagem"`**: Tira a foto definitiva (_Commit_) dos arquivos que estão no palco, gravando a versão no histórico com uma mensagem descritiva.
- **`git commit --amend`**: A "viagem no tempo". Permite alterar o último commit, fundindo as alterações que estão no palco com a versão anterior (alterando o hash do commit).
- **`git diff`**: Mostra linha a linha o que mudou no código (a diferença entre o estado atual e a última versão salva).
- **`git log`**: Exibe o álbum de fotos completo (histórico de commits) com autor, data e mensagem.
- **`git log --stat`**: Mostra o histórico adicionando estatísticas resumidas de quais arquivos foram alterados.
- **`git log --oneline`**: Mostra uma versão compacta do histórico, com o hash resumido e a mensagem em uma única linha.
- **`git commit --amend --no-edit`**: Variação do comando `amend` que altera o último commit mantendo a mensagem original, sem abrir o editor de texto. Útil para correções rápidas onde a descrição do commit não muda.
- **`git add -A`**: Adiciona **todas** as alterações do seu repositório de uma só vez para o _stage_ (o palco), incluindo arquivos modificados, novos (_untracked_) e deletados.
- **`q` (tecla)**: Comando utilizado para sair (quit) do modo de visualização paginada no terminal, muito comum ao executar comandos longos como `git log` ou `git diff`.
- **`git mv [origem] [destino]`**: Move ou renomeia um arquivo, já colocando a alteração no "palco" (_stage_). Utilizado para renomear o `.env` para `.env.development`.
- **`git commit -am "[mensagem]"`**: Atalho que realiza o `git add` e o `git commit` simultaneamente. Funciona apenas para arquivos **já rastreados** pelo Git que foram modificados; ele não adiciona arquivos novos (_untracked_).

### ☁️ Git (Controle de Versão Online / Remoto)

Estes comandos permitem a interação entre o seu repositório local e o repositório de origem (_Origin_) no GitHub, "furando a bolha" do seu computador.

- **`git push`**: Empurra (_upload_) os commits da sua branch local para o repositório remoto. É o comando que publica seu trabalho na internet.
- **`git push --force`** (ou **`git push -f`**): Força o envio dos commits locais, sobrescrevendo o histórico do repositório remoto. (Atenção*:* É um comando perigoso, usado quando as histórias divergem, como após um `amend`. Em times, pode apagar o trabalho de colegas se usado sem cuidado).
- **`git pull`**: Puxa (_download_) as alterações que estão no repositório remoto para a sua máquina (o inverso do `push`).

### 🐳 Docker (Conteinerização)

Estes comandos introduzem a plataforma de contêineres, uma tecnologia essencial que nos permitirá rodar serviços auxiliares (p.ex., nosso banco de dados) em ambientes completamente isolados e padronizados, gerenciando seus ciclos de vida e a orquestração de serviços.

- **`docker -v`**: Apenas verificamos se o Docker estava instalado e pronto para uso no ambiente.
- **`docker ps -a`**: Lista todos os contêineres (o `-a` ou `--all` inclui os que estão parados). Útil para verificar **Exit Codes** de processos que encerraram.
- **`docker logs [ID ou Nome]`**: Exibe o histórico de logs de um contêiner específico. Essencial para debugar falhas de inicialização.
- **`docker compose up -d`** (ou **`docker compose up --detached`**): Sobe os serviços definidos no arquivo `compose.yaml` em modo **detached** (a flag `-d` ou `--detached` roda os containers em segundo plano), liberando o terminal.
- **`docker compose up -d --force-recreate`**: Força a recriação dos contêineres mesmo que não haja alterações aparentes no arquivo de configuração. Útil para aplicar novas portas ou variáveis.
- **`docker compose -f [caminho/do/arquivo] up`**: A flag `-f` (ou `--file`) permite especificar o caminho de um arquivo de configuração que não esteja na raiz (ex: `infra/compose.yaml`).
  - _Exemplo:_ `docker compose -f infra/compose.yaml up -d` (inicia os serviços baseados no arquivo dentro da pasta `infra` e os mantém rodando em segundo plano)
- **`docker compose -f [caminho/do/arquivo] down`**: Procura o arquivo de configuração no caminho do arquivo e derruba o contêiner.
  - _Exemplo:_ `docker compose -f infra/compose.yaml down` (encerra os serviços baseados no arquivo dentro da pasta `infra`)
- **`docker compose down`**: Para e remove todos os contêineres, redes e imagens definidos no arquivo de configuração.
- **`docker compose up`**: Sobe os serviços definidos no arquivo `compose.yaml` , porém mantém o terminal travado (para destravar, use o comando `Ctrl + C`).
- **`docker compose stop`**: Pausa a execução dos serviços sem remover os contêineres ou volumes. É o comando recomendado para o dia a dia, pois economiza recursos do sistema mantendo o estado atual do banco de dados intacto.
- **`env_file: .env`**: Chave utilizada dentro do arquivo `compose.yaml` para instruir o Docker a carregar variáveis de ambiente diretamente de um arquivo externo, evitando duplicidade de configurações.

### 🌐 Redes e DNS (Domain Name System)

Estes comandos são utilizados para investigar e rastrear como a internet resolve os nomes de domínios e encontra os endereços IP dos servidores. Permitem "encostar a mão" no protocolo HTTP e visualizar a comunicação cliente-servidor sem intermediários.

- **`sudo apt install dnsutils`**: Instala o pacote de utilitários de DNS (que contém a ferramenta `dig`) no sistema operacional Linux (Ubuntu/Debian) do seu Codespaces. _(Nota: A flag **`-y`**, adicionada ao final do comando, vem de **"yes"** e responde automaticamente "sim" para todas as perguntas que o terminal faria.)_
- **`nslookup -type=ns [dominio]`**: Pergunta ao DNS local quem são os servidores de autoridade. Se retornar _"Non-authoritative answer"_, o dado veio de cache.
- **`host -t ns [dominio]`**: Comando simplificado para listar os servidores de autoridade.
- **`dig -v`**: Verifica a versão instalada da ferramenta BIND Utilities (DiG).
- **`dig [dominio] [tipo]`**: Realiza uma consulta manual no sistema de DNS para um domínio específico, buscando o registro desejado.
  - _Exemplo:_ `dig fintab.com.br A` (pergunta ao DNS qual é o endereço IP, ou _A Record_, associado àquele domínio).
- **`dig [dominio] NS`**: Busca os servidores de nome (NameServers).
- **`dig [dominio] A`**: Busca o endereço IP (**A**ddress) do servidor.
- **`dig [dominio] [tipo] +trace`**: Realiza a mesma consulta DNS, mas a _flag_ `+trace` força a ferramenta a exibir todo o caminho percorrido (o rastro), passando pelos _Root Servers_, _TLD Servers_ e _Authoritative Servers_, até encontrar a resposta final.
  - **`+short`**: Flag que limpa a resposta do `dig`, exibindo apenas o dado essencial. (Ex: `dig fintab.com.br A +short`).
  - **`+trace`**: Mostra todo o caminho hierárquico, da raiz (.) ao destino final. Útil para ver se o registro TLD (ex: `.br`) já atualizou. (Ex: `dig fintab.com.br NS +trace`).
- **`dig @1.1.1.1 [dominio] NS`**: Força a consulta usando um DNS específico (neste caso, o da Cloudflare) para furar o cache local.
- **`dig [dominio] +dnssec`**: Verifica as assinaturas de segurança do domínio. Usado para garantir que a transição de DNS não tenha erros de validação.
- **`dig [dominio] ANY`**: Tenta buscar todos os registros disponíveis (A, MX, NS, TXT) de uma só vez. (_Nota: Alguns servidores DNS modernos bloqueiam o ANY por segurança, mas é um comando clássico._)
- **`watch -n [segundos] [comando]`**: Executa repetidamente um comando em intervalos definidos para monitoramento em tempo real. (Ex: `watch -n 10 dig fintab.com.br A +short`).
  - _Utilidade:_ Permite "sentar e esperar" a propagação do DNS sem precisar digitar o comando manualmente várias vezes. (Dica: Use `Ctrl + C` para sair do monitoramento).
- **`curl [URL]`**: Realiza uma requisição GET simples e exibe o corpo (_body_) da resposta no terminal.
- **`curl -v [URL]`** (ou **`-verbose`**): Ativa o modo detalhado. Exibe todo o processo do protocolo, incluindo os cabeçalhos de requisição (`>`) e os cabeçalhos de resposta (`<`).
- **`curl --insecure [URL]`**: Permite realizar requisições HTTPS ignorando erros de certificados de segurança (SSL/TLS). Útil para testar acessos diretos via endereço IP.
- **`curl --header "[Chave]: [Valor]" [URL]`**: Injeta manualmente um cabeçalho na requisição.
  - _Exemplo usado em aula:_ `curl -v --header "Host: fintab.com.br" https://76.76.21.21` (usado para provar como o servidor identifica o site correto em um ambiente de _Virtual Host_).

### 🧪 Jest (Testes Automatizados)

Funções e sintaxes fundamentais para instalar e rodar a sua malha de proteção, permitindo criar testes que validam o comportamento real do sistema e suas conexões externas.

- **`npm install jest@29.6.2 --save-dev`**: Instala o framework de testes Jest em uma versão específica, salvando-o como dependência de desenvolvimento (pois não queremos que ele vá para o servidor de produção).
- **`npm test`** (ou **`npm run test`**): Executa a bateria de testes automatizados uma única vez. _(Nota: Requer a configuração `"test": "jest"` na seção de scripts do `package.json`)_.
- **`npm run test:watch`**: Executa o Jest em modo de observação (_watch mode_). O terminal fica "vigiando" os arquivos do projeto; toda vez que você salva um arquivo, ele roda a bateria de testes automaticamente. _(Nota: Requer a configuração `"test:watch": "jest --watch"` no `package.json`)_.
  - Alterando-a para **`jest --watchAll`**, garantimos que todos os testes sejam reexecutados a cada salvamento, independentemente do status no Git.
- **`Ctrl + C`** ou **`q`**: Atalhos utilizados no terminal para interromper o modo _watch_ do Jest e voltar à linha de comando normal.
- **`await fetch("[URL]")`**: Realiza uma requisição HTTP assíncrona por dentro do código. Por retornar uma _Promise_, deve ser precedida por `await` para que o teste aguarde a resposta antes de prosseguir com as verificações.
- **`async () => { ... }`**: Define uma _arrow function_ como assíncrona. É obrigatório declarar a função de teste como `async` para que seja possível utilizar a palavra-chave `await` dentro dela.

### **🐘 PostgreSQL (Banco de Dados)**

Comandos para instalar o cliente, realizar conexões manuais e interagir com o servidor de banco de dados, utilizando o cliente oficial `psql` e o driver `pg` **(Node-Postgres)** para a aplicação.

- **`sudo apt install postgresql-client`**: Instala o pacote que contém o `psql`, o cliente oficial de linha de comando para interagir com o PostgreSQL.
- **`psql --host [endereço] --username [usuario] --port [porta]`**: Comando para se conectar a uma instância de banco de dados Postgres (Ex: `psql --host localhost --username postgres --port 5432`).
- **`\q`**: Comando executado dentro do terminal do `psql` para encerrar a conexão e sair (quit).
- **`SELECT 1+1;`**: Exemplo de query SQL básica para testar se a conexão está ativa e processando comandos.
- **`SELECT 1 + 1 AS sum;`**: Query SQL básica utilizada para testar se a comunicação entre o seu código e o banco de dados está funcionando corretamente.
- **`npm install pg@8.11.3`**: Instala o driver de conexão oficial do PostgreSQL para Node.js em uma versão específica e estável.

### ⚙️ Configuração e Padrões de Projeto

Esta seção detalha os arquivos e convenções que estipulam as regras do ambiente de desenvolvimento, garantindo que a aplicação seja **Stateless** e semanticamente organizada.

- **`.env.development`**: Arquivo local que armazena pares de `CHAVE=valor` para configurar variáveis de ambiente. No Dia 19, renomeamos o `.env` original para ser mais semântico em relação ao ambiente de desenvolvimento.
- **`process.env`**: Objeto global do Node.js que mapeia e permite acessar as variáveis injetadas no processo (ex: `process.env.POSTGRES_DB`).
- **`jsconfig.json`**: Arquivo que define a raiz do projeto para o editor e o framework. Sua presença habilita o suporte ao IntelliSense e organiza a estrutura do projeto.
- **`baseUrl: "."`**: Configuração dentro do `jsconfig.json` que habilita os **Absolute Imports**. Isso permite importar módulos a partir da raiz (ex: `import database from "infra/database"`) eliminando caminhos relativos complexos como `../../../../`.
- **`JSON.parse()`**: Função utilizada para converter strings JSON vindas de variáveis de ambiente de volta em objetos JavaScript funcionais.

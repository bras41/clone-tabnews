# clone-tabnews

Este repositório contém a implementação do projeto [TabNews](https://www.tabnews.com.br) para o curso [curso.dev](https://curso.dev). Abaixo, uma lista de referência dos comandos utilizados durante o desenvolvimento.

# ⭐ Lista de comandos

### 🐧 Navegação e Sistema (Linux/Bash)

Estes são os comandos básicos para você se localizar e organizar o terminal do Codespaces.

- **`clear`** ou **`Ctrl + L`**: Limpa a tela do terminal. (Dica: O atalho `Ctrl + L` é o preferido do instrutor, pois limpa o visual sem adicionar o registro "clear" no histórico de comandos.)
- **`ls`**: Lista os arquivos e pastas visíveis no diretório atual.
- **`ls -l`**: Lista os arquivos em formato vertical, exibindo mais detalhes (permissões, tamanho, etc).
- **`ls -la`**: Lista **todos** os arquivos, incluindo os ocultos (aqueles que começam com `.`, como a pasta `.git`).
- **`sudo apt update && sudo apt install dnsutils -y`**: Atualiza os repositórios e instala o pacote que contém as ferramentas `dig` e `nslookup`. (Essencial em ambientes novos).

### 🟢 Node.js e NVM (Gerenciamento de Versão)

Comandos essenciais para configurar a fundação do projeto e garantir que todos estejam na mesma versão da tecnologia.

- **`node -v`**: Verifica qual versão do **Node.js** está ativa no momento.
- **`nvm ls`**: Lista as versões do Node.js instaladas e disponíveis no **NVM** (Node Version Manager).
- **`nvm install lts/hydrogen`**: Instala a versão LTS (Long Term Support) específica chamada "Hydrogen".
- **`nvm alias default lts/hydrogen`**: Define a versão "Hydrogen" como o padrão do sistema.
- **`nvm install`**: Quando rodado sem argumentos na raiz do projeto, ele lê o arquivo `.nvmrc` e instala/seleciona a versão definida nele.

### 📦 NPM (Gerenciador de Pacotes)

Comandos para gerenciar as dependências (bibliotecas) do projeto e executar scripts.

- **`npm init`**: Inicializa o projeto, criando o arquivo `package.json` (o manifesto).
- **`npm install [pacote]@[versão]`**: Baixa e instala uma dependência no projeto. Utilizar o `@[versão]` instala uma versão exata de um pacote, ignorando atualizações automáticas.
- **`npm run dev`**: Executa o script chamado "dev" que configuramos no `package.json` (sobe o servidor local).
- **`npm install [pacote] --save-dev`** (ou **`-D`**): Instala uma dependência exclusivamente para o ambiente de desenvolvimento (ela vai para o bloco `devDependencies`). Usada para ferramentas como o Prettier e Jest.
- **`npm run lint:check`**: Comando personalizado para rodar o Prettier no modo de conferência, analisando a formatação sem alterar os arquivos.
- **`npm run lint:fix`**: Comando personalizado para rodar o Prettier no modo de conserto, corrigindo automaticamente a formatação dos arquivos.

### 🌳 Git (Controle de Versão Offline / Local)

Estes são os comandos para gerenciar a "máquina do tempo" do seu código.

- **`git status`**: Mostra em qual estado estão seus arquivos (_Untracked_, _Modified_ ou _Staged_).
- **`git add [arquivo]`**: Move um arquivo para o palco (_Staged_), preparando-o para o _Commit_.
- **`git commit -m "mensagem"`**: Grava a versão definitiva no histórico com uma mensagem descritiva.
- **`git commit --amend`**: Permite alterar o último commit, fundindo novas alterações ou mudando a mensagem.
- **`git diff`**: Mostra linha a linha o que mudou no código desde a última versão salva.
- **`git log`**: Exibe o histórico de commits completo. (Variações: `--stat` para ver arquivos alterados ou `--oneline` para formato compacto).
- **`git add -A`**: Adiciona **todas** as alterações do seu repositório de uma só vez para o palco.
- **`q` (tecla)**: Usada para sair do modo de visualização no terminal (comum no `git log`).

### ☁️ Git (Controle de Versão Online / Remoto)

- **`git push`**: Empurra (_upload_) os commits da sua branch local para o GitHub.
- **`git push --force`** (ou **`-f`**): Força o envio sobrescrevendo o histórico remoto. (Cuidado: usar apenas em branches individuais após um `amend`).
- **`git pull`**: Puxa (_download_) as alterações do GitHub para a sua máquina.

### 🐳 Docker

- **`docker -v`**: Verifica se o Docker está instalado e pronto para uso no ambiente.

### 🌐 Redes, DNS e Protocolo HTTP

Comandos para investigar como a internet resolve nomes e visualizar a comunicação cliente-servidor sem "maquiagem".

- **`nslookup -type=ns [dominio]`**: Consulta quais são os servidores de autoridade de um domínio.
- **`dig [dominio] [tipo] +trace`**: Mostra todo o caminho da resolução DNS até o destino final.
- **`watch -n [segundos] [comando]`**: Executa repetidamente um comando para monitoramento em tempo real (Ex: propagação de IP).
- **`curl [URL]`**: Realiza uma requisição GET simples e exibe o corpo (_body_) da resposta.
- **`curl -v [URL]`** (ou **`--verbose`**): Exibe todo o processo do protocolo, incluindo cabeçalhos de requisição (`>`) e resposta (`<`).
- **`curl --insecure [URL]`**: Ignora erros de certificados SSL (útil para testes em IPs diretos via HTTPS).
- **`curl --header "[Chave]: [Valor]" [URL]`**: Injeta manualmente um cabeçalho na requisição (Ex: testar _Virtual Hosts_ com o cabeçalho `Host`).

### 🧪 Testes Automatizados (Jest)

- **`npm install jest@29.6.2 --save-dev`**: Instala o framework de testes Jest como dependência de desenvolvimento.
- **`npm test`**: Executa a bateria de testes uma única vez.
- **`npm run test:watch`**: Executa o Jest em modo de observação, vigiando alterações nos arquivos para rodar os testes automaticamente.
- **`await fetch("[URL]")`**: Realiza uma requisição HTTP assíncrona. Deve ser precedida por `await` para aguardar a resposta da _Promise_.
- **`async () => { ... }`**: Define uma _arrow function_ como assíncrona, permitindo o uso de `await` dentro dela.

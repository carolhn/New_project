## Configuração Inicial de um Projeto ⚙️

## Contexto do projeto:

Este repositório serve como um guia para a configuração básica de um novo projeto. Aqui, você encontrará um passo a passo detalhado das configurações realizadas neste repositório, que servem como uma estrutura inicial para desenvolvimento.

## Instalação Local:

Para executar a aplicação em sua máquina local, siga os passos abaixo:

1. Clone o repositorio. Use o comando:</br>
   <code>git clone git@github.com:carolhn/Project-config-base.git</code></br>

2. Entre na pasta do repositório que você acabou de clonar:</br>
   <code>cd Project-config-base</code>

3. Instale as dependências</br>
   <code>npm install</code>

4. Comando para executar o app</br>
   <code>npm run dev</code>

## Passo a Passo 🚀:

Aqui, você encontrará um guia completo dos passos executados neste projeto, oferecendo uma visão abrangente das configurações e da estrutura detalhada.

<details>
  <summary><strong>1. Configuração Inicial da Aplicação.</strong></summary>
Vamos começar configurando sua aplicação do zero.

#### 1.1 Inicializando o Node Package.json.

Primeiro, inicie sua aplicação criando o arquivo package.json, que ajuda a gerenciar os pacotes do seu projeto.

```sh
npm init -y
```

#### 1.2 Instalação do Typescript.

Como nosso código final será convertido em JavaScript antes de ser publicado online, vamos instalar o TypeScript no ambiente de desenvolvimento.

```sh
npm install typescript ts-node-dev @types/node tsconfig-paths -D
```

#### 1.3 Configurando o TypeScript.

A seguir, configure o TypeScript para o seu projeto. Isso envolve a criação do arquivo tsconfig.json com as configurações necessárias.

```sh
npx tsc --init --rootDir src --outDir build --esModuleInterop --resolveJsonModule --lib es6 --module commonjs --allowJs true --noImplicitAny true
```

#### 1.4 Configurando o .gitignore

Para manter seu controle de versão limpo e evitar a inclusão acidental de arquivos desnecessários ou sensíveis, crie e configure o arquivo .gitignore.

</details>

<details>
  <summary><strong>2. Compilando o Projeto.</strong></summary>
Nesta seção, vamos compilar o projeto e executá-lo.

#### 2.1 Criando a Estrutura do Projeto.

Começaremos criando a estrutura básica do projeto. Execute os seguintes comandos para criar a pasta src e o arquivo server.ts:

```sh
mkdir src
touch src/server.ts
```

#### 2.2 Compilando o Typescript.

Dentro do arquivo src/server.ts, adicione o seguinte código que será compilado:

```sh
console.log('Hello World!')
```

#### 2.3 Executando o Compilador TypeScript.

Agora, vamos executar o comando tsc para compilar o código TypeScript. Ele usará as configurações definidas no arquivo tsconfig.json no diretório atual:

```sh
npx tsc
```

#### 2.4 Executando o Código Compilado.

O código compilado será gerado na pasta build. Para executar a aplicação, use o seguinte comando:

```sh
node build/server.js
```

#### 2.5 Criando um Script de Desenvolvimento.

Para facilitar o desenvolvimento, utilizaremos a biblioteca ts-node-dev. Vamos criar um novo script no arquivo package.json para executar o projeto com o ts-node-dev:

```sh
"scripts": {
  "dev": "ts-node-dev --inspect --transpile-only --ignore-watch node_modules src/server.ts"
```

#### 2.6 Executando o Servidor em Modo de Desenvolvimento.

Finalmente, no terminal, execute o comando a seguir para iniciar o servidor em modo de desenvolvimento:

```sh
npm run dev
```

</details>

<details>
  <summary><strong>3. Configurando o ESLint.</strong></summary>
O ESLint é uma ferramenta de linter JavaScript que permite aplicar um conjunto de padrões de estilo, formatação e codificação ao seu código.

#### 3.1 Instalação e Configuração do ESLint

Comece instalando o ESLint no seu projeto com o seguinte comando:

```sh
npx npm install --save-dev eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

#### 3.2 Criando o arquivo .eslintrc

Na raiz do seu projeto, crie um arquivo chamado .eslintrc com uma configuração inicial do ESLint. Você pode adicionar as seguintes configurações:

```sh
{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended"
  ]
}
```

#### 3.3 Criando o arquivo .eslintignore

Crie um arquivo chamado .eslintignore e adicione os seguintes comandos para evitar que determinados diretórios e arquivos sejam verificados pelo ESLint:

```sh
node_modules
dist
build
/*.js
```

#### 3.4 Criando um Script de Desenvolvimento.

Adicione scripts no arquivo package.json para executar o lint e corrigir automaticamente os problemas:

```sh
"scripts": {
  "lint": "eslint . --ext .ts",
  "lint-fix": "eslint . --ext .ts --fix"
```

#### 3.5 Executando o Lint.

Agora, você pode executar o lint do seu projeto ou executar uma correção automática dos problemas com os seguintes comandos:

```sh
npm run lint
npm run lint-fix
```

</details>

<details>
  <summary><strong>4. Configurando o Prettier.</strong></summary>
O Prettier é um formatador de código opinativo e, em conjunto com o ESLint, forma uma parceria perfeita para nós, desenvolvedores.

#### 4.1 Instalação e Configuração do Prettier.

Comece instalando o Prettier no seu projeto com o seguinte comando:

```sh
npx npm install prettier -D
```

#### 4.2 Criando o arquivo .prettierrc

Na raiz do seu projeto, crie um arquivo chamado .prettierrc com uma configuração inicial do Prettier. Você pode adicionar as seguintes configurações:

```sh
{
  "semi": true,
  "trailingComma": "all",
  "singleQuote": true,
  "printWidth": 80,
  "arrowParens": "avoid"
}
```

##### ⚠️ATENÇÃO⚠️

É fundamental que a extensão "Prettier - Code Formatter" esteja instalada no VSCode, pois permitirá a formatação automática do código ao salvar o arquivo.

#### 4.3 Configurando o Prettier para trabalhar com ESLint.

Com o ESLint e o Prettier já instalados, instale também esses dois pacotes:

```sh
npm install eslint-config-prettier@6.15.0 eslint-plugin-prettier@3.2.0 --save-dev
```

#### 4.4 Ajustar o arquivo .eslintrc

Ajuste o arquivo .eslintrc da seguinte forma para que o ESLint e o Prettier funcionem em conjunto:

```sh
{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint",
    "prettier"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier/@typescript-eslint",
    "plugin:prettier/recommended"
  ],
  "rules": {
    "no-console": "warn",
    "prettier/prettier": "error"
  }
```

</details>

<details>
  <summary><strong>5. Estrutura de pastas.</strong></summary>

#### 5.1 Criando a Estrutura de Pastas.

A estrutura de pastas é uma parte fundamental da organização do projeto. Ela ajuda a manter seu código organizado e facilita a navegação e o desenvolvimento da aplicação. Abaixo está a estrutura de pastas desenvolvida nesse projeto:

```sh
PROJECT-CONFIG-BASE/
|-- src/
|   |-- api/
|   |   |-- controllers/
|   |   |-- routes/
|   |   |-- middleware/
|   |   |-- services/
|   |   |--server.ts
|   |-- database/
|   |   |-- config/
|   |   |-- migrations/
|   |   |-- models/
|   |   |-- seeders/
|   |-- utils/
|-- tests/
|   |-- unit/
|   |-- integration/
|-- node_modules/
|-- package.json
|-- package-lock.json
|-- .gitignore
|-- .eslintignore
|-- .eslintrc
|-- .prettierrc
|-- .editorconfig
|-- tsconfig.json
|-- README.md

```

#### 5.2 Explicação de cada pasta.

- src/: Esta é a pasta raiz do código-fonte.

- api/: Esta pasta contém os principais componentes relacionados à lógica da aplicação.

- database/: Esta pasta contém configurações, migrações, modelos e seeders relacionados ao banco de dados da aplicação.

- utils/: Esta pasta contém utilitários ou funções de uso geral.

- tests/: Aqui, são os testes unitários e de integração para garantir a qualidade do código.

#### Outros arquivos e pastas incluem:

`node_modules/`: Dependências do projeto.</br>
`package.json e package-lock.json`: Informações do projeto e dependências.</br>
`eslintignore, .eslintrc, .prettierrc, .editorconfig`Configurações de lint e formatação.</br>
`tsconfig.json`: Configuração TypeScript.</br>
`.gitignore`: Ignora arquivos não rastreados pelo Git.</br>
`README.md`: Documentação do projeto.

#### 5.3 Ajustar o arquivo package.json.

Aqui, vamos atualizar o script "dev" para utilizar a ferramenta `ts-node-dev` após mover o arquivo server.ts para uma nova localização.

```sh
{
  "scripts": {
    "dev": "ts-node-dev --inspect --transpile-only --ignore-watch node_modules src/api/server.ts",
  }
```

</details>

<details>
  <summary><strong>6. Simplificando as Importações.</strong></summary>

Uma maneira eficaz de otimizar o processo de importação de arquivos em nosso projeto é configurar um recurso que simplifica esse procedimento.

#### 6.1 Ajustando o arquivo .tsconfig

Começamos essa configuração no arquivo `tsconfig.json`, onde definimos o objeto paths. Esse objeto serve como uma espécie de atalho para especificar caminhos de importação no projeto:

```sh
"baseUrl": "./",
"paths": {
  "@api/*": ["src/api/*"],
  "@database/*": ["src/database/*"],
  "@utils/*": ["src/utils/*"]
```

#### 6.2 Configurando o Uso do tsconfig-paths.

No terminal, na pasta do projeto, execute o seguinte comando para instalar a biblioteca tsconfig-paths como dependência de desenvolvimento:

```sh
npm install --save-dev tsconfig-paths
```

Após a instalação do tsconfig-paths, ajuste o script "dev" em seu arquivo package.json para incluir a opção -r tsconfig-paths/register. O script "dev" deve ser configurado da seguinte maneira:

```sh
"dev": "ts-node-dev -r tsconfig-paths/register --inspect --transpile-only --ignore-watch node_modules src/api/server.ts"
```

</details>

<details>
  <summary><strong>7. Instalação de dependências.</strong></summary>

#### 7.1 Instalando o Express e Outras dependências.

Para adicionar as dependências necessárias ao seu projeto, execute o seguinte comando no terminal:

```sh
npm install express cors express-async-errors
```

#### 7.2 Instalação das Tipagens.

Para garantir que seu projeto tenha acesso às definições de tipos (tipagens) necessárias, você pode instalá-las usando o seguinte comando no terminal:

```sh
npm install --save-dev @types/express @types/cors
```

</details>

<details>
  <summary><strong>8. Criação do Servidor Node.js com Express</strong></summary>

Vamos criar de um servidor Node.js usando o framework Express. O servidor será configurado para lidar com solicitações HTTP, permitindo que você desenvolva um aplicativo web.

#### 8.1 Arquivos ajustados.

- `server.ts`: Este arquivo é o ponto de entrada do servidor. Ele importa o Express, o middleware CORS, configura as rotas e inicia o servidor na porta 3333.

- `routes/index.ts`: Este arquivo define as rotas principais do aplicativo. Atualmente, ele possui uma rota simples que responde com uma mensagem "Hello World" quando acessada.

#### 8.2 Executando o Servidor.

Para iniciar o servidor, execute o seguinte comando no terminal, na pasta raiz do projeto:

```sh
npm run dev
```

**Você verá a seguinte saída no terminal:**

`Server is running on port 3333 🚀`

**Testando o Servidor:**

Após iniciar o servidor, você pode testá-lo abrindo um navegador e acessando o seguinte URL:

```sh
http://localhost:3333/
```

</details>

<details>
  <summary><strong>9. Tratamento de Erros Personalizados</strong></summary>

#### 9.1 Criação de Erro Personalizado

A classe `utils/errors/AppError` é utilizada para criar objetos de erro personalizados, permitindo a associação de mensagens e códigos de status HTTP específicos. Essa abordagem é fundamental para tratar erros de maneira precisa em sua aplicação, ao mesmo tempo que fornece informações detalhadas sobre a natureza do erro.

#### 9.2 Middleware de Tratamento de Erros

Dentro da pasta `middlewares`, foi desenvolvido um código para lidar com erros na aplicação. Esse middleware é chamado no arquivo `server.ts` e desempenha um papel essencial na captura e tratamento de erros durante a execução do servidor.

</details>

## Contato:

[![Linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/caroline-nunes-devfullstack/)
[![Instagran](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/caarolhn/)
[![Whatsapp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/48988037114)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:nunescaroline905@gmail.com)

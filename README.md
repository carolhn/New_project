## Configuração Inicial de um Projeto ⚙️

## Contexto do projeto:

Este repositório é um guia de configuração básica para iniciar um projeto. Abaixo, temos o passo a passo da configuração realizada neste repositório.

## Instalação Local:

Para rodar a aplicação em sua maquina.

1. Clone o repositorio. Use o comando:</br>
   <code>git clone git@github.com:carolhn/Project-config-base.git</code></br>

2. Entre na pasta do repositório que você acabou de clonar:</br>
   <code>cd Project-config-base</code>

3. Instale as dependências</br>
   <code>npm install</code>

4. Comando para executar o app</br>
   <code>npm start</code>

## Passo a Passo:

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

#### 2.5 Executando o Servidor em Modo de Desenvolvimento.

Finalmente, no terminal, execute o comando a seguir para iniciar o servidor em modo de desenvolvimento:

```sh
npm run dev
```

</details>

<details>
  <summary><strong>3. Configurando o ESLint.</strong></summary>
O ESLint é uma ferramenta de linting JavaScript que permite aplicar um conjunto de padrões de estilo, formatação e codificação ao seu código.

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

#### 3.1 Instalação e Configuração do Prettier.

Comece instalando o Prettier no seu projeto com o seguinte comando:

```sh
npx npm install prettier -D
```

#### 3.2 Criando o arquivo .prettierrc

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

#### 3.3 Configurando o Prettier para trabalhar com ESLint.

Com o ESLint e o Prettier já instalados, instale também esses dois pacotes:

```sh
npm install eslint-config-prettier@6.15.0 eslint-plugin-prettier@3.2.0 --save-dev
```

#### 3.5 Ajustar o arquivo .eslintrc

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

## Contato:

[![Linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/caroline-nunes-devfullstack/)
[![Instagran](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/caarolhn/)
[![Whatsapp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/48988037114)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:nunescaroline905@gmail.com)

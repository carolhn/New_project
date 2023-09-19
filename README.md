## Criando uma API com Node.js

#### Este é um guia passo a passo para criar uma API com Node.js. Vamos começar!

## Passo a Passo:

<details>
  <summary><strong>1. Iniciando e configurando a aplicação.</strong></summary>

Primeiro, inicie sua aplicação instalando o Node Package.json, que auxilia no gerenciamento de pacotes do projeto.

```sh
npm init -y
```

#### 1.1 Instalação do Typescript.

Como o código final é convertido para JavaScript antes de ser disponibilizado online, só precisaremos do Typescript em ambiente de desenvolvimento.

```sh
npm install typescript ts-node-dev @types/node tsconfig-paths -D
```

#### 1.2 Configurando o TypeScript.

Em seguida, configure o TypeScript executando o seguinte comando para criar o arquivo de configuração tsconfig.json:

```sh
npx tsc --init --rootDir src --outDir build --esModuleInterop --resolveJsonModule --lib es6 --module commonjs --allowJs true --noImplicitAny true
```

#### 1.3 Criando o arquivo .gitignore.

Ele ajudar a manter o controle de versão limpo e evita que arquivos desnecessários ou sensíveis sejam incluídos acidentalmente no repositório.

</details>
<details>
  <summary><strong>2. Compilando o Projeto.</strong></summary>
Criar a pasta `src` e o arquivo `server.ts`.

```sh
mkdir src
touch src/server.ts
```

#### 2.1 Compilando o Typescript.

No nosso `server.ts` vamos adicionar um código para ser compilado.

```sh
console.log('Hello World!')
```

#### 2.2 Executando o TSC.

Em seguida vamos executar o comando `tsc`, que irá ler o arquivo tsconfig.json no diretório atual e aplicará a configuração ao compilador TypeScript para gerar o código JavaScript compilado.

```sh
npx tsc
```

#### 2.3 Compilando código.

O código compilado foi gerado na pasta `build`, para executar precisamos utilizar o comando.

```sh
node build/server.js
```

#### 2.4 Criando Script.

Vamos utilizar a biblioteca `ts-node-dev` para execução da aplicação em desenvolvimento.
No arquivo package.json vamos criar um novo script para rodar o `ts-node-dev`.

```sh
"scripts": {
  "dev": "ts-node-dev --inspect --transpile-only --ignore-watch node_modules src/server.ts"
```

#### 2.5 Executar o servidor.

```sh
npm run dev
```

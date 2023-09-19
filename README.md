## Criando uma API com Node.js

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

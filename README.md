## Criando uma API com Node.js

#### Este é um guia passo a passo para criar uma API com Node.js. Vamos começar!

## Passo a Passo:

<details>
  <summary><strong>1. Iniciando a aplicação.</strong></summary>

Primeiro, inicie sua aplicação instalando o NodeJS Package.json, que auxilia no gerenciamento de pacotes do projeto.

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

#### 1.3 Criando o arquivo.gitignore.

Ele ajudar a manter o controle de versão limpo e evita que arquivos desnecessários ou sensíveis sejam incluídos acidentalmente no repositório.

</details>

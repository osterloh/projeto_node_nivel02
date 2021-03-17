<h1 align="center"><a href="https://nodejs.org/" target="_blank" style="text-decoration: none">
    <img alt="nodeJS" src="https://camo.githubusercontent.com/9c24355bb3afbff914503b663ade7beb341079fa/68747470733a2f2f6e6f64656a732e6f72672f7374617469632f696d616765732f6c6f676f2d6c696768742e737667" width="50%"/>
    <br>
    Projeto nodeJS com Typescript
</a></h1>

## Descrição

Este projeto foi desenvolvido em <strong>[nodeJS](https://nodejs.org/)</strong> com <strong>[Typescript](https://www.typescriptlang.org///)</strong> para fins de capacitação pessoal

## Como Usar

Para clonar e executar este aplicativo, você precisará [Git](https://git-scm.com), [Node.js v12.20.0](https://nodejs.org/) ou superior + [Yarn 1.22.5](https://yarnpkg.com/) ou superior instalado no seu computador. Executar no seu terminal:

```bash
# Para clonar este repositório
$ git clone https://github.com/osterloh/projeto_node_nivel02.git

# Entrar no repositório
$ cd projeto_node_nivel02

# Instalar as dependências
$ yarn

#  Executar o sistema
$ yarn dev:server
```

## Etapas do desenvolvimento do projeto

- Antes de iniciar o projeto nodeJS, é necessário definir em qual diretório o projeto irá ficar armazendo e inicializar o projeto com o <strong>package.json</strong>, o qual irá conter informações sobre o projeto e bibliotecas adicionadas:

```js
yarn init -y
```

- Instalar o expres:

```js
yarn add express
```

- Instalar o typescript como dependência de desenvolvedor:

```js
yarn add typescript -D
```

- Para gerar o arquivo <strong>tsconfig.json</strong>, que armazena as configurações de como o typescript será executado no projeto:

```js
yarn tsc --init
```

- No arquivo <strong>tsconfig.json</strong>, vamos editar os parâmetros de <i>rootDir</i> para "./src", indicando o diretório principal do projeto e o parâmetro <i>outDir</i> para "./dist", que o diretório onde irá ser armazenado os arquivos de build do projeto.

```js
 "outDir": "./dist",
 "rootDir": "./src",
```

- Configurar o arquivo server.ts:

```js
import express, { request } from "express";

const app = express();

app.get("/", (request, response) => {
  return response.json({ message: "Hello World" });
});

app.listen(3333, () => {
  console.log("Server startd on port 3333!");
});
```

- Para gerar o build da aplicação:

```js
yarn tsc
```

- Para startar a aplicação:

```js
node dist/server.js
```

- Instalar as dependências do ts-node-dev como desenvolvedor, serve para executar o projeto em desenvolvimento fazendo o papel de converter o projeto typescript para javascript e também atualiza o projeto em execução a cada alteração do código. Com isso podemos apagar a pasta "dist" do projeto:

```js
yarn add ts-node-dev -D
```

- Configurar o arquivo <strong>package.json</strong> com os parâmetros de <i>scripts</i>:

```js
"scripts": {
    "build": "tsc",
    "dev:server": "ts-node-dev --inspect --transpile-only --ignore-watch node_modules src/server.ts"
},
```

- Com o <strong>Router</strong> do express podemos definir as rotas da aplicação e com o método <i>use()</i> definimos uma rota padrão:

```js
import { Router } from "express";
import appointmentsRouter from "./appointments.routes";

const routes = Router();

routes.use("/appointments", appointmentsRouter);

export default routes;
```

- Para tratar horas podemos utilizar a lib <strong>[date-fns](https://github.com/date-fns/date-fns)</strong>:

```js
yarn add date-fns
```

- Para definir um tipo de dado, podemos configurar uma <strong>interface</strong>, informando os campos que serão utilizados e os tipos de dados de cada atributo:

```js
interface Appointment {
  id: string;
  provider: string;
  date: Date;
}

const appointments: Appointment[] = [];
```

- As <i>Rotas</i> devem se preocupar em receber a requisição, chamar outro arquivo, devolver uma resposta. Ela não deve ser responsável por tratar as informações ou realizar ações lógicas complexas.

- Para tratar as informações e regras de negócio, podemos configurar as chamadas da <i>Rota</i> para os <strong>Services</strong>.

- Neste projeto já foi utilizado dois conceitos do SOLID:
- S: Single Responsability Principal
- D: Dependency Invertion Principal

## Tecnologias

- [nodeJS](https://nodejs.org/)
- [yarn](https://yarnpkg.com/)
- [Typescript](https://www.typescriptlang.org)
- [express](https://github.com/expressjs/express)
- [nodemon](https://github.com/remy/nodemon)
- [uuidv4](https://github.com/thenativeweb/uuidv4)
- [date-fns](https://github.com/date-fns/date-fns)

---

Desenvolvido por [Johnatan Luiz Osterloh](https://www.linkedin.com/in/johnatanosterloh/)

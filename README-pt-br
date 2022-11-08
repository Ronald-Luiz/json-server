# Deploy `json-server` para `Hospedagens gratuita`


> Instruções para fazer o deploy de uma fake REST API [json-server](https://github.com/typicode/json-server) para vários host gratuitos. Deve ser usado apenas para fins de desenvolvimento, mas pode atuar como um banco de dados mais simples para aplicativos menores.

**Documentação do Json-server:** [json-server](https://github.com/typicode/json-server)
* [**Criando sua base de dados**](#criar)
* [Deploy to **Vercel**](#deploy-to-vercel)



## Criando sua base de dados

1. Clique no botão code deste repositório e baixe os arquivos para a pasta do seu projeto no seu computador.
2. Altere o arquivo `db.json` e coloque as informações de acordo com o seu projeto.


_Abaixo o exemplo do arquivo db.json com a rota /post e o seu conteúdo tem um `id`, `title`, e `content`._

```json
{
  "posts":[
    {
      "id" : 0,
      "title": "First post!",
      "content" : "My first content!"
    }
  ]
}
```

---
## Deploy para Vercel  <img align="right" width="100px" height="auto" src="https://logovtor.com/wp-content/uploads/2020/10/vercel-inc-logo-vector.png" alt="vercel">

Para hospedar na Vercel será necessário criar um arquivo de configuração chamado `vercel.json` com o seguinte código:

```json
{
  "version": 2,
  "builds": [
    {
      "src": "server.js",
      "use": "@vercel/node",
      "config": {
        "includeFiles": ["db.json"]
      }
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "server.js"
    }
  ]
}
```

1. Registre-se na [Vercel](https://vercel.com/)
2. Clique em **Add New**
3. Clique em  **Project**
4. Em **Import Git Repository**, clique **add Github Account**.
5. Selecione o seu repositório.
6. Clicque em importar.
7. Coloque um nome para o seu projeto e clique em **Deploy**.





## Deploy para **Heroku** <img align="right" width="100px" height="auto" src="https://cdn.worldvectorlogo.com/logos/heroku-1.svg" alt="Heroku">

Heroku é uma hospedagem grauita para pequenos projetos. Fácil configuração e deploy pelo terminal usando o _git_.

###### Pros

* Facil configuração
* Hospedagem gratuita

###### Contra

* A aplicação tem que ficar um periodo inativa durante o dia.
* "Desliga" depois de 30 minutos de inatividade. Inicia automáticamente quando um usuário visita, porém demora alguns segundos. Isso pode ser resolvido com uma aplicação chamada [**Kaffeine**](http://kaffeine.herokuapp.com/)

---

### Utilizando o Heroku

1 . [Crie sua base de dados](#create-your-database)

2 . Crie uma conta em <br/>[https://heroku.com](https://heroku.com)

3 . Instalar o Heroku CLI no seu computador: <br/>[https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)

4 . Conecte o Heroku CLI na sua conta escrevendo o comando no seu terminal e seguindo as instruções:
```bash
heroku login
```

5 . Digite o comando para criar o seu projeto digitando no terminal `heroku create NomeDoProjeto`:
```bash
heroku create my-project
```

6 . Faça o Push do seu app para __Heroku__ (Você vai ver uma tela cheia de codigos):
```bash
git push heroku master
```

7 . Para visitar o seu projeto recem criado digite o seguinte comando:
```bash
heroku open
```

8 . Para depurar se algo deu errado:
```bash
heroku logs --tail
```

---
## EM CONSTRUÇÃO... .. .
<!--
#### How it works

Heroku will look for a startup-script, this is by default `npm start` so make sure you have that in your `package.json` (assuming your script is called `server.js`):
```json
 "scripts": {
    "start" : "node server.js"
 }
```

You also have to make changes to the port, you can't hardcode a dev-port. But you can reference herokus port. So the code will have the following:
```js
const port = process.env.PORT || 4000;
```

## Deploy to Glitch

Not tested 100%. Same as with Heroku, will sleep after a while.

1. Register for [Glitch](https://glitch.com/) or go to [Glitch/edit](https://glitch.com/)
2. Click **New Project**
3. Click **Import from GitHub**
4. Paste `https://github.com/jesperorb/json-server-heroku.git` into the URL-input and click OK.
5. Wait for it to setup
6. Press **Share**-button to get your URL to live site. It should be something for example like: `https://fallabe-pie-snake.glitch.me`. And your DB will be at `https://fallabe-pie-snake.glitch.me/posts`

## Deploy to **Azure**

<img align="right" width="100px" height="auto" src="https://docs.microsoft.com/en-us/azure/media/index/azure-germany.svg" alt="Azure">

You can also use _Microsoft Azure_ to deploy a smaller app for free to the Azure platform. The service is not as easy as _Heroku_ and you might go insane because the documentation is really really bad at some times and it's hard to troubleshoot.

The **pros** are that on _Azure_ the app **will not be forced to sleep**. It will sleep automatically on inactivity but you can just visit it and it will start up.

## Installation

1 . Create a Microsoft Account that you can use on Azure: </br>
https://azure.microsoft.com/

2 . Install the `azure-cli`: <br/>
https://docs.microsoft.com/en-us/cli/azure/install-azure-cli
_This might cause some trouble, you will see. Remember to restart your terminal or maybe your computer if the commands after this does not work_

3 . Login to the service via the command line and follow the instructions: </br>
```bash
az login
```
_You will be prompted to visit a website and paste a confirmation code_


## Create the project

1 . [Create your database](#create-your-database)

2 . Create a resource group for your projects, replace the name to whatever you want just be sure to use the same group name in all commands to come. You only have to create the resource group and service plan once, then you can use the same group and plan for all other apps you create if you like.

```bash
az group create -n NameOfResourceGroup -l northeurope
```

3 . Create a service plan:

```
az appservice plan create -n NameOfServicePlan -g NameOfResourceGroup
```

4 . Create the actual app and supply the service plan and resource group
```bash
az webapp create -n NameOfApp -g NameOfResourceGroup --plan NameOfServicePlan
```

5 . Create deployment details. A git-repo is not created automatically so we have to create it with a command:

```bash
az webapp deployment source config-local-git -n NameOfApp -g NameOfResourceGroup
```

6 . From the command in step 5 you should get a **url** in return. Copy this url and add it as a remote to your local git project, for example:

```bash
git remote add azure https://jesperorb@deploy-testing.scm.azurewebsites.net/deploy-testing.git
```

7 . Now you should be able to push your app:
```bash
git push azure master
```

You should be prompted to supply a password, this should be the pass to your account. If not, you can choose a different password at your Dashboard for Azure: **[https://portal.azure.com/](https://portal.azure.com/)**

Choose **App Services** in the sidebar to the left and the choose your app in the list that appears then go to **Deployment Credentials** to change your password for deployment:<br>
https://docs.microsoft.com/en-us/azure/app-service/app-service-deployment-credentials

-->


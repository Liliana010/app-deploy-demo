# Guia Rápido: Docker e GitHub Actions

## Comandos Essenciais do Docker

### Instalar o Docker

sudo apt update
sudo apt install docker.io -y

Verifique a instalação:

docker --version


### Construir uma Imagem Docker

docker build -t meu-app .


### Listar Imagens Criadas

docker images


### Rodar um Contêiner

docker run -d -p 8080:80 meu-app


### Verificar Contêineres Ativos

docker ps


### Parar um Contêiner

docker stop <ID_DO_CONTÊINER>


### Ver Logs do Contêiner

docker logs <ID_DO_CONTÊINER>


### Remover um Contêiner

docker rm <ID_DO_CONTÊINER>


### Remover uma Imagem

docker rmi meu-app


### Testar a Aplicação Localmente
Acesse no navegador:

http://localhost:8080


## Workflow GitHub Actions (CI/CD com Docker)

### Estrutura do Projeto

/app-deploy-demo
│── Dockerfile
│── index.html
└── .github/workflows/main.yml


### Arquivo `.github/workflows/main.yml`

name: Deploy Docker App

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout do código
        uses: actions/checkout@v2

      - name: Configurar Docker
        run: |
          docker --version

      - name: Construir a imagem Docker
        run: docker build -t meu-app:latest .

      - name: Rodar o contêiner
        run: docker run -d -p 8080:80 meu-app:latest


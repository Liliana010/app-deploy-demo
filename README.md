# 📌 Guia Rápido: Docker e GitHub Actions

## 🐳 Comandos Essenciais do Docker

### Instalar o Docker
```bash
sudo apt update
sudo apt install docker.io -y
```
Verifique a instalação:
```bash
docker --version
```

### Construir uma Imagem Docker
```bash
docker build -t meu-app .
```

### Listar Imagens Criadas
```bash
docker images
```

### Rodar um Contêiner
```bash
docker run -d -p 8080:80 meu-app
```

### Verificar Contêineres Ativos
```bash
docker ps
```

### Parar um Contêiner
```bash
docker stop <ID_DO_CONTÊINER>
```

### Ver Logs do Contêiner
```bash
docker logs <ID_DO_CONTÊINER>
```

### Remover um Contêiner
```bash
docker rm <ID_DO_CONTÊINER>
```

### Remover uma Imagem
```bash
docker rmi meu-app
```

### Testar a Aplicação Localmente
Acesse no navegador:
```
http://localhost:8080
```

## 🚀 Workflow GitHub Actions (CI/CD com Docker)

### Estrutura do Projeto
```
/app-deploy-demo
│── Dockerfile
│── index.html
└── .github/workflows/main.yml
```

### Arquivo `.github/workflows/main.yml`
```yaml
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
```

## 📌 Dicas Finais
✔ Automatize Deploys com GitHub Actions.  
✔ Monitore erros com `docker logs`.  
✔ Use `.dockerignore` para otimizar o tamanho da imagem.  

Se precisar de mais exemplos ou explicações, me avise! 🚀

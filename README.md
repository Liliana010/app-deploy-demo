# 📌 Guia Rápido: Docker e GitHub Actions

## 🐳 Comandos Essenciais do Docker

### 1️⃣ Instalar o Docker (se ainda não tiver)
```bash
sudo apt update
sudo apt install docker.io -y
```
Verifique a instalação:
```bash
docker --version
```

### 2️⃣ Construir uma Imagem Docker
```bash
docker build -t meu-app .
```
**Explicação:**  
- `-t meu-app` → Define um nome para a imagem.  
- `.` → Usa o `Dockerfile` na pasta atual para construir a imagem.

### 3️⃣ Listar Imagens Criadas
```bash
docker images
```

### 4️⃣ Rodar um Contêiner
```bash
docker run -d -p 8080:80 meu-app
```
**Explicação:**  
- `-d` → Roda o contêiner em segundo plano.  
- `-p 8080:80` → Mapeia a porta 80 do contêiner para a 8080 do sistema.  
- `meu-app` → Nome da imagem usada para criar o contêiner.

### 5️⃣ Verificar Contêineres Ativos
```bash
docker ps
```

### 6️⃣ Parar um Contêiner
```bash
docker stop <ID_DO_CONTÊINER>
```
Para encontrar o **ID**, use `docker ps`.

### 7️⃣ Ver Logs do Contêiner
```bash
docker logs <ID_DO_CONTÊINER>
```

### 8️⃣ Remover um Contêiner
```bash
docker rm <ID_DO_CONTÊINER>
```

### 9️⃣ Remover uma Imagem
```bash
docker rmi meu-app
```

### 🔟 Testar a Aplicação Localmente
Após rodar o contêiner, acesse no navegador:
```
http://localhost:8080
```

---

## 🚀 Workflow GitHub Actions (CI/CD com Docker)

### 📂 Estrutura do Projeto
```
/app-deploy-demo
│── Dockerfile
│── index.html
└── .github/workflows/main.yml
```

### 📝 Arquivo `.github/workflows/main.yml`
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

### 🌍 Como Funciona?
1️⃣ O workflow é acionado **quando há um push na branch `main`**.  
2️⃣ Ele faz o **checkout do código** do repositório.  
3️⃣ **Verifica se o Docker está instalado** e exibe a versão.  
4️⃣ **Constrói a imagem Docker** com o código do repositório.  
5️⃣ **Roda um contêiner** baseado na imagem criada.

---

## 📌 Dicas Finais
✔ **Automatize Deploys**: Configure o GitHub Actions para publicar no Docker Hub ou servidores como AWS, DigitalOcean, Heroku.  
✔ **Monitore Erros**: Use `docker logs` para verificar falhas no contêiner.  
✔ **Use `.dockerignore`**: Exclua arquivos desnecessários da imagem para otimizar o tamanho.  

Se precisar de mais exemplos ou explicações, me avise! 🚀

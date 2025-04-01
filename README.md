# O que acontece se o deploy falhar? Como podemos melhorar o processo?
Se o deploy falhar, alguns dos problemas comuns podem incluir:
- **Erros no código ou na configuração do workflow**
- **Imagem Docker corrompida ou build falhando**
- **Falha na execução do contêiner**
- **Problemas de permissões ou autenticação**

### Como melhorar o processo?
**Logs detalhados** → Usar `docker logs` e verificar as mensagens de erro no GitHub Actions.  
**Teste antes do deploy** → Criar um ambiente de staging para validar antes de ir para produção.  
**Rollback automático** → Implementar uma estratégia para voltar à última versão estável se o deploy falhar.  
**Monitoramento contínuo** → Ferramentas como Prometheus, Grafana e logs centralizados ajudam a detectar falhas rapidamente.  

---

# Quais são as vantagens de usar CI/CD e Docker?
- **Automação total** → Builds, testes e deploys são feitos automaticamente.  
- **Menos erros humanos** → Processos padronizados reduzem falhas manuais.  
- **Rápida recuperação** → Se algo der errado, podemos rapidamente reverter para uma versão anterior.  
- **Portabilidade** → Com Docker, a aplicação roda em qualquer lugar sem incompatibilidades.  
- **Eficiência** → Menos tempo gasto com configurações e mais foco no desenvolvimento.  

---

# Como podemos monitorar a aplicação em produção?
## Ferramentas recomendadas:
-  **Logs** → `docker logs <ID_DO_CONTÊINER>` para verificar problemas.  
-  **Monitoramento de métricas** → Ferramentas como **Prometheus + Grafana** ajudam a acompanhar CPU, memória e uso de recursos.  
-  **Alertas automáticos** → Configurar **Slack, Discord ou e-mails** para notificações de falhas.  
-  **Health Checks** → Adicionar verificações automáticas para garantir que a aplicação está respondendo corretamente.  

---


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


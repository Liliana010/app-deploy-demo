#📌 Guia Rápido: Docker e GitHub Actions
🐳 Comandos Essenciais do Docker
1️⃣ Instalar o Docker (se ainda não tiver)
bash
Copiar
Editar
sudo apt update
sudo apt install docker.io -y
Verifique a instalação:

bash
Copiar
Editar
docker --version
2️⃣ Construir uma Imagem Docker
bash
Copiar
Editar
docker build -t meu-app .
Explicação:

-t meu-app → Define um nome para a imagem.

. → Usa o Dockerfile na pasta atual para construir a imagem.

3️⃣ Listar Imagens Criadas
bash
Copiar
Editar
docker images
4️⃣ Rodar um Contêiner
bash
Copiar
Editar
docker run -d -p 8080:80 meu-app
Explicação:

-d → Roda o contêiner em segundo plano.

-p 8080:80 → Mapeia a porta 80 do contêiner para a 8080 do sistema.

meu-app → Nome da imagem usada para criar o contêiner.

5️⃣ Verificar Contêineres Ativos
bash
Copiar
Editar
docker ps
6️⃣ Parar um Contêiner
bash
Copiar
Editar
docker stop <ID_DO_CONTÊINER>
Para encontrar o ID, use docker ps.

7️⃣ Ver Logs do Contêiner
bash
Copiar
Editar
docker logs <ID_DO_CONTÊINER>
8️⃣ Remover um Contêiner
bash
Copiar
Editar
docker rm <ID_DO_CONTÊINER>
9️⃣ Remover uma Imagem
bash
Copiar
Editar
docker rmi meu-app
🔟 Testar a Aplicação Localmente
Após rodar o contêiner, acesse no navegador:

arduino
Copiar
Editar
http://localhost:8080

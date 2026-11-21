# Operação Nuvem Literária

Deploy da plataforma BiblioTech (API Node.js + PostgreSQL + Frontend React) usando Docker, Docker Hub e Render.

## Links

- Docker Hub (API): https://hub.docker.com/r/klebersonkvc/nuvem-literaria-api
- Docker Hub (Frontend): https://hub.docker.com/r/klebersonkvc/nuvem-literaria-front
- Frontend no Render: https://nuvem-literaria-front.onrender.com
- API no Render: https://nuvem-literaria-api.onrender.com/api/books

## Maior desafio técnico

O maior desafio foi fazer o frontend se comunicar com a API em nuvem. Como o Vite embute a variável VITE_API_URL no momento do build, a imagem do frontend precisou ser gerada passando a URL pública da API do Render via --build-arg, e não lida em tempo de execução. Também foi necessário ajustar a conexão do backend com o PostgreSQL para aceitar DATABASE_URL com SSL, usar a Internal Database URL do Render na mesma região da API e configurar o Nginx com try_files para o roteamento do React funcionar em produção.

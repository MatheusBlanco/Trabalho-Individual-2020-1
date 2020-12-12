# Solução
[![Maintainability](https://api.codeclimate.com/v1/badges/e4c4db3b084b9e2d72c4/maintainability)](https://codeclimate.com/github/MatheusBlanco/Trabalho-Individual-2020-1/maintainability)
[![Build Status](https://travis-ci.com/MatheusBlanco/Trabalho-Individual-2020-1.svg?branch=master)](https://travis-ci.com/MatheusBlanco/Trabalho-Individual-2020-1)

# Containers

Para a containerização e orquestração da aplicação, foi utilizado do docker e o docker-compose.

Para se rodar o programa com o container deve-se rodar os seguintes comandos:

## API
**Rodar a API**:
- docker-compose -f api/docker-compose.yml up --build

**Criação e migração do banco**:
1. docker-compose -f api/docker-compose.yml run web rake db:create
2. docker-compose -f api/docker-compose.yml run web rake db:migrate

**Rodar os testes da API**:
- docker-compose -f api/docker-compose.yml run web bundle exec rails test

## Client
**Rodar o Client**:
1. docker build -t client ./client
2. docker run -p 8080:8080 client

**Rodar os testes do Client**
- docker run client yarn run test:unit

# Integração Contínua
Para a integração contínua foi utilizada a ferramenta TravisCI. A mesma realiza o build e, logo após, os testes da API e do Client, respectivamente, para cada commit, e retorna um resultado.

O projeto taambém utiliza a GEM simplecov para cobertura de testes da API em rails e retorna um arquivo index.html que pode ser aberto no navegador. Além disso, foi integrado com o CodeClimate que demonstra a manutenibilidade e devolve uma nota.
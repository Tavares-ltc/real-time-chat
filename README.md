# Real-Time Chat - Monorepo

Este repositório orquestra os projetos **backend** e **frontend** do Real-Time Chat utilizando submódulos Git para cada parte. Também inclui configuração para rodar ambos via Docker.

O app é um chat em real time com a possibilidade de criar salas e de usar markdown nas mensanges.
![image](https://github.com/user-attachments/assets/cfa4b1b3-ef4b-43f3-8109-0a1d20cb1f92)


Caso queira ver a documentação ou clonar individualmente acesse:

- 🔗 Backend: [github.com/Tavares-ltc/real-time-chat-back](https://github.com/Tavares-ltc/real-time-chat-back)
- 🔗 Frontend: [github.com/Tavares-ltc/real-time-chat-front](https://github.com/Tavares-ltc/real-time-chat-front)

---

## Índice

- [Clonando o repositório](#clonando-o-repositório)
- [Iniciando o projeto com Docker](#iniciando-o-projeto-com-docker)
- [Atualizando o código (backend e frontend)](#atualizando-o-código-backend-e-frontend)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Tecnologias utilizadas](#tecnologias-utilizadas)
- [Dicas adicionais](#dicas-adicionais)
- [Arquitetura do banco](#arquitetura-do-banco-em-breve)
- [Prints do programa](#prints-do-programa-em-breve)

---

## Clonando o repositório

Para clonar o monorepo junto com os submódulos (`backend` e `frontend`), use:

```bash
git clone --recursive git@github.com:Tavares-ltc/real-time-chat.git
```

Se você já clonou sem `--recursive`, inicialize e atualize os submódulos com:

```bash
git submodule update --init --recursive
```

---

## Iniciando o projeto com Docker

No diretório raiz do monorepo, execute o comando para construir e subir os containers:

```bash
docker-compose up --build
```

### O que esse comando faz?

- Constrói as imagens Docker dos serviços `backend` e `frontend` usando seus respectivos `Dockerfile.dev`.
- Sobe o container do banco de dados PostgreSQL (`db`).
- Expõe as portas:
  - Backend: [http://localhost:3000](http://localhost:3000)
  - Frontend: [http://localhost:5173](http://localhost:5173)

---

## Atualizando o código (backend e frontend)

Para puxar as últimas alterações do monorepo e de todos os submódulos, use:

```bash
git pull --recurse-submodules && git submodule update --remote --merge
```

---

## Estrutura do projeto

```
real-time-chat/
├── backend/           # Submódulo do backend NestJS
│   ├── Dockerfile.dev
│   └── ...
├── frontend/          # Submódulo do frontend React/Vite
│   ├── Dockerfile.dev
│   └── ...
├── docker-compose.yml # Docker Compose para orquestração
└── .gitmodules        # Configuração dos submódulos
```

---

## Tecnologias utilizadas

### Backend (NestJS + Prisma)
- @nestjs/common, core, jwt, websockets, swagger
- @prisma/client, prisma
- bcrypt, passport, passport-jwt
- class-transformer, class-validator
- rxjs
- swagger-ui-express

### Dev (Backend)
- Jest, Supertest, ts-jest
- ESLint, Prettier
- TypeScript, ts-node, tsconfig-paths
- @nestjs/testing, schematics
- @types/*

### Frontend (React + Vite)
- React 19, React Router v7
- Vite, TypeScript
- Axios, socket.io-client
- react-markdown, remark-gfm, react-icons

---

## Dicas adicionais

Reiniciar containers com rebuild:

```bash
docker-compose down
docker-compose up --build
```

Parar containers:

```bash
docker-compose stop
```

---

## Arquitetura do banco

> Diagrama do banco.
![image](https://github.com/user-attachments/assets/f4c85a83-65d9-4006-8f21-e8df37469e6c)


---

# Projeto Docker — Sistemas Operacionais

Projeto acadêmico desenvolvido no curso de Engenharia de Software da Católica SC, para aplicar conceitos de Sistemas Operacionais por meio de containers Docker.

## Tecnologias

- Node.js e Express — servidor HTTP com duas rotas
- Docker e Docker Compose — execução dos serviços
- MySQL 8 — serviço de banco de dados com volume persistente

## Funcionalidades e conceitos aplicados

- Endpoint `GET /`: retorna disciplina, aluno e informações do ambiente do container.
- Endpoint `GET /info`: retorna PID, tempo de execução e quantidade de CPUs visíveis à aplicação.
- Aplicação executada com usuário **não-root**.
- Limite de memória de **128 MB** no serviço Node.js.
- Rede Docker dedicada e volume persistente para o MySQL.

> **Escopo:** o MySQL é inicializado como serviço independente para demonstrar infraestrutura e persistência. A aplicação Node.js **não realiza consultas ao banco** nesta versão.

## Como executar

Pré-requisito: Docker com suporte a Docker Compose.

1. Crie um arquivo `.env` na raiz, com base em `.env.example`, e substitua o valor de exemplo por uma senha forte (não publique o `.env`).
2. No terminal, dentro da pasta do projeto, execute:

```bash
docker compose up --build -d
```

3. Acesse:

- `http://localhost:3000/`
- `http://localhost:3000/info`

4. Para encerrar:

```bash
docker compose down
```

Para manter os dados do MySQL, não use `docker compose down -v`, que remove o volume.

## Estrutura

```text
├── app/
│   ├── Dockerfile
│   ├── package.json
│   └── server.js
├── evidencias/
├── .env.example
├── .gitignore
├── docker-compose.yml
└── README.md
```

## Evidências

A pasta `evidencias/` contém registros da execução original do trabalho acadêmico, incluindo logs, estatísticas e inspeção dos containers. Esses registros não substituem a execução local.

## Aprendizados

Imagens e containers, processos, redes, sistemas de arquivos e volumes, limites de recursos e boas práticas de segurança com usuário não-root.

**Autor:** Victor Laumann Vieira

---

# Go Products API

API REST simples para cadastro e consulta de produtos, construída em Go utilizando arquitetura em camadas e containerizada com Docker + PostgreSQL.

---

# 📌 Stack

* Go 1.25
* Gin
* PostgreSQL 16
* Docker
* Docker Compose

---

# 🏗 Arquitetura

O projeto segue separação por responsabilidades (inspirado em Clean Architecture)

---

# 🚀 Inicialização da Aplicação

O ponto de entrada está em:

```
cmd/main.go
```

Fluxo de inicialização:

1. Criação do servidor HTTP com Gin
2. Conexão com o banco
3. Injeção de dependências:

   * Repository
   * UseCase
   * Controller
4. Registro das rotas
5. Start do servidor na porta 8000

A aplicação depende do banco estar disponível no momento da inicialização.

---

# 🔌 Endpoints

| Método | Rota                | Descrição               |
| ------ | ------------------- | ----------------------- |
| GET    | /ping               | Health check simples    |
| GET    | /products           | Lista todos os produtos |
| POST   | /product            | Cria um novo produto    |
| GET    | /product/:productId | Busca produto por ID    |

---

# 🐳 Executando com Docker

## 1️⃣ Pré-requisitos

* Docker Desktop instalado e rodando

---

## 2️⃣ Subir a aplicação

Na raiz do projeto:

```bash
docker compose up --build
```

Isso irá:

1. Buildar a imagem da API
2. Baixar a imagem do PostgreSQL 16
3. Criar volume persistente
4. Subir ambos os containers
5. Conectar a API ao banco

---

## 3️⃣ Verificar se está rodando

```bash
docker ps
```

A API estará disponível em:

```
http://localhost:8000
```

---

# 🗄 Banco de Dados

O PostgreSQL roda em container separado.

Configuração via variáveis de ambiente no `docker-compose.yml`.

---

# ⚙ Variáveis de Ambiente

As credenciais são injetadas via `.env`.

Exemplo:

```
DB_HOST=go_db
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=1234
DB_NAME=postgres
```

---

# 🛑 Parar aplicação

```bash
docker compose down
```

---

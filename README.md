# 🔐 sample-flask-auth

## English

### 📌 About the Project

**Project Name:** `sample-flask-auth`
**Goal:** REST API for authentication and user management with role-based access control, built with Flask + MySQL.

---

### 🛠 Tech Stack

| Technology | Version | Purpose |
|---|---|---|
| Python | 3.x | Main language |
| Flask | 2.3.0 | Web framework / REST API |
| Flask-SQLAlchemy | 3.1.1 | ORM for database |
| Flask-Login | 0.6.2 | Session management & authentication |
| Werkzeug | 2.3.0 | HTTP utilities (Flask core) |
| PyMySQL | 1.1.0 | MySQL connection driver |
| Cryptography | 41.0.7 | Secure connection support |
| MySQL | latest | Relational database |
| Docker / Docker Compose | - | Database containerization |

---

### 📁 Project Structure

```
sample-flask-auth/
│
├── models/
│   └── user.py          # User model (SQLAlchemy + Flask-Login)
│
├── mysql-data/          # Local MySQL volume (Docker-generated, git-ignored)
│
├── app.py               # Main app — routes and endpoint logic
├── database.py          # SQLAlchemy instance initialization
├── docker-compose.yml   # MySQL container configuration
├── requirements.txt     # Project dependencies
└── README.md
```

---

### ⚙️ Setup Guide

#### 1. Prerequisites

- [Python 3.x](https://www.python.org/downloads/) installed
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running
- [Git](https://git-scm.com/) installed

#### 2. Clone the Repository

```bash
git clone https://github.com/[your-username]/sample-flask-auth.git
cd sample-flask-auth
```

#### 3. Create and Activate Virtual Environment

```bash
# Create virtual environment
python -m venv venv

# Activate — Windows
venv\Scripts\activate

# Activate — macOS/Linux
source venv/bin/activate
```

#### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

#### 5. Start the Database with Docker

> ⚠️ **Update the volume path in `docker-compose.yml`** before running: replace the absolute path with the correct path on your machine.

```yaml
# docker-compose.yml — update this line:
volumes:
  - /your/local/path/mysql-data:/var/lib/mysql
```

```bash
# Start MySQL container in background
docker compose up -d
```

#### 6. Create Database Tables

With the container running, open the Python shell and execute:

```python
from app import app
from database import db

with app.app_context():
    db.create_all()
```

Or via terminal (one line):

```bash
python -c "from app import app; from database import db; app.app_context().__enter__(); db.create_all()"
```

#### 7. Create Admin User (manually)

```python
from app import app
from database import db
from models.user import User

with app.app_context():
    admin = User(username="admin", password="admin123", role="admin")
    db.session.add(admin)
    db.session.commit()
    print("Admin created successfully!")
```

#### 8. Run the Application

```bash
python app.py
```

API available at: `http://127.0.0.1:5000`

---


## Português

### 📌 Sobre o Projeto

**Nome do Projeto:** `sample-flask-auth`
**Objetivo:** API REST de autenticação e gerenciamento de usuários com controle de acesso por roles, construída com Flask + MySQL.

---

### 🛠 Tecnologias Utilizadas

| Tecnologia | Versão | Finalidade |
|---|---|---|
| Python | 3.x | Linguagem principal |
| Flask | 2.3.0 | Framework web / API REST |
| Flask-SQLAlchemy | 3.1.1 | ORM para banco de dados |
| Flask-Login | 0.6.2 | Gerenciamento de sessão e autenticação |
| Werkzeug | 2.3.0 | Utilitários HTTP (base do Flask) |
| PyMySQL | 1.1.0 | Driver de conexão com MySQL |
| Cryptography | 41.0.7 | Suporte a conexões seguras |
| MySQL | latest | Banco de dados relacional |
| Docker / Docker Compose | - | Containerização do banco de dados |

---

### 📁 Estrutura de Diretórios

```
sample-flask-auth/
│
├── models/
│   └── user.py          # Model do usuário (SQLAlchemy + Flask-Login)
│
├── mysql-data/          # Volume local do MySQL (gerado pelo Docker, ignorado no git)
│
├── app.py               # Aplicação principal — rotas e lógica dos endpoints
├── database.py          # Inicialização da instância do SQLAlchemy
├── docker-compose.yml   # Configuração do container MySQL
├── requirements.txt     # Dependências do projeto
└── README.md
```

---

### ⚙️ Passo a Passo para Configuração

#### 1. Pré-requisitos

- [Python 3.x](https://www.python.org/downloads/) instalado
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) instalado e rodando
- [Git](https://git-scm.com/) instalado

#### 2. Clonar o Repositório

```bash
git clone https://github.com/[seu-usuario]/sample-flask-auth.git
cd sample-flask-auth
```

#### 3. Criar e Ativar Ambiente Virtual

```bash
# Criar o ambiente virtual
python -m venv venv

# Ativar — Windows
venv\Scripts\activate

# Ativar — macOS/Linux
source venv/bin/activate
```

#### 4. Instalar Dependências

```bash
pip install -r requirements.txt
```

#### 5. Subir o Banco de Dados com Docker

> ⚠️ **Ajuste o volume no `docker-compose.yml`** antes de rodar: troque o caminho absoluto pelo caminho correto na sua máquina.

```yaml
# docker-compose.yml — altere esta linha:
volumes:
  - /seu/caminho/local/mysql-data:/var/lib/mysql
```

```bash
# Subir o container do MySQL em background
docker compose up -d
```

#### 6. Criar as Tabelas no Banco

Com o container rodando, abra o shell do Python e execute:

```python
from app import app
from database import db

with app.app_context():
    db.create_all()
```

Ou via terminal (uma linha):

```bash
python -c "from app import app; from database import db; app.app_context().__enter__(); db.create_all()"
```

#### 7. Criar o Usuário Admin (manualmente)

```python
from app import app
from database import db
from models.user import User

with app.app_context():
    admin = User(username="admin", password="admin123", role="admin")
    db.session.add(admin)
    db.session.commit()
    print("Admin criado com sucesso!")
```

#### 8. Rodar a Aplicação

```bash
python app.py
```

A API estará disponível em: `http://127.0.0.1:5000`

---


# AgendaApp (Flask MVC + PostgreSQL) - Deploy Railway

## Recursos
- Login (Flask-Login)
- CRUD Agenda (id, data, descricao, realizada)
- Relatório (listagem)
- PostgreSQL (SQLAlchemy)
- Migrations (Flask-Migrate)
- Deploy no Railway (Gunicorn)

---

## Rodar localmente

### 1) Criar e ativar venv
```bash
python -m venv venv
# OU
py -m venv venv

# Windows CMD
venv\Scripts\activate

python --version

# Windows Powershell
.\venv\Scripts\Activate.ps1

# Linux/Mac
source venv/bin/activate
```

### 2) Instalar dependências
```bash
pip install -r requirements.txt
### ou se erro
python -m pip install -r requirements.txt
```

python.exe -m pip install --upgrade pip

### 3) Configurar variáveis de ambiente
Copie `.env.example` para `.env` e ajuste `DATABASE_URL`.

### 4) Rodar migrations
```bash
flask db init
flask db migrate -m "init"
flask db upgrade
```

### 5) Criar usuário admin (seed)
```bash
python seed_admin.py
```

### 6) Rodar
```bash
python run.py
```

Acesse:
http://localhost:5000

Login:
- admin / 123

---

## Deploy Railway

### 1) Suba esse projeto para GitHub (ou faça upload zip)
### 2) Crie um projeto no Railway
### 3) Adicione PostgreSQL (Plugin)
### 4) Configure variáveis
Railway já cria `DATABASE_URL`. Configure:
- SECRET_KEY=alguma_chave_segura

### 5) Deploy
Railway detecta Flask + Procfile e inicia com Gunicorn.

### 6) Rodar migrations no Railway
Use o console do Railway e rode:
```bash
flask db upgrade
python seed_admin.py
```

---

## Rotas
- /login
- /logout
- /agenda/listar
- /agenda/novo

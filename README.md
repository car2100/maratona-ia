# Encontros Tech

Aplicação web para gerenciamento de eventos tech com interface web responsiva, API REST completa e monitoramento integrado via Prometheus.

## 📋 Sobre o Projeto

**Encontros Tech** é uma plataforma completa para gerenciamento de eventos de tecnologia, desenvolvida com Flask e PostgreSQL. A aplicação permite criar, listar, editar e visualizar eventos tech de forma simples e intuitiva, oferecendo tanto uma interface web amigável quanto uma API REST para integrações.

O projeto foi desenvolvido com foco em observabilidade, seguindo práticas modernas de DevOps com containerização Docker, orquestração Kubernetes, CI/CD automatizado via GitHub Actions e monitoramento completo com Prometheus e Grafana.

### Contexto

Este projeto foi criado como demonstração de uma aplicação moderna cloud-native, implementando desde o desenvolvimento local até deployment em produção com múltiplos ambientes (homologação e produção).

## 🚀 Funcionalidades Principais

### Interface Web
- ✨ Listagem de eventos com busca por título
- ➕ Criação de novos eventos via formulário web
- ✏️ Edição de eventos existentes usando token único
- 👁️ Visualização detalhada de eventos individuais
- 🎨 Interface responsiva e moderna
- 🔍 Sistema de busca em tempo real

### API REST
- 📝 **POST** `/api/events/` - Criar novo evento
- 📄 **GET** `/api/events/` - Listar todos os eventos (com paginação e busca)
- 🔎 **GET** `/api/events/by-token/<token>` - Buscar evento por token de edição
- 🔄 **PUT** `/api/events/by-token/<token>` - Atualizar evento existente

### Recursos Técnicos
- 🔐 Sistema de tokens únicos para edição segura de eventos
- 📊 Métricas Prometheus integradas (`/metrics`)
- 🪵 Sistema de logging estruturado com níveis configuráveis
- 🎯 Validação de dados com Pydantic
- 🗄️ ORM SQLAlchemy com migrations automáticas
- 🐳 Containerização completa com Docker multi-stage
- ☸️ Deployment Kubernetes com alta disponibilidade (3 réplicas)
- 🔄 CI/CD automatizado com GitHub Actions
- 🌐 Suporte multi-arquitetura (AMD64 e ARM64)

## 🛠️ Tecnologias Utilizadas

### Backend
- **Flask 3.0.0** - Framework web minimalista e robusto
- **Python 3.11+** - Linguagem de programação
- **Gunicorn 21.2.0** - Servidor WSGI de produção com 4 workers
- **Pydantic 2.11.7** - Validação de dados e schemas
- **SQLAlchemy 2.0.43** - ORM para banco de dados

### Banco de Dados
- **PostgreSQL** - Banco de dados relacional
- **psycopg2-binary 2.9.10** - Driver PostgreSQL

### Observabilidade
- **prometheus-flask-exporter 0.23.0** - Exportação de métricas HTTP
- **prometheus-client 0.21.1** - Cliente Prometheus
- **Sistema de Logging Estruturado** - Logs com contexto e níveis configuráveis

### Frontend
- **Jinja2 3.1.6** - Template engine
- **HTML5 / CSS3** - Interface web moderna
- **JavaScript** - Interatividade do lado do cliente

### Infraestrutura
- **Docker** - Containerização
- **Kubernetes** - Orquestração de containers
- **GitHub Actions** - CI/CD pipeline
- **Azure Kubernetes Service (AKS)** - Cluster Kubernetes gerenciado

### Outras Ferramentas
- **python-dotenv 1.1.1** - Gerenciamento de variáveis de ambiente
- **pytest 8.3.4** - Framework de testes
- **Werkzeug 3.0.1** - Utilitários WSGI
- **PyYAML 6.0.2** - Parser YAML

## 📦 Estrutura do Projeto

```
maratona-ia/
├── src/                          # Código fonte da aplicação
│   ├── main.py                   # Entry point da aplicação Flask
│   ├── requirements.txt          # Dependências Python
│   ├── Dockerfile               # Configuração Docker multi-stage
│   │
│   ├── core/                    # Módulos principais
│   │   ├── database.py          # Configuração SQLAlchemy e sessões
│   │   ├── settings.py          # Configurações via Pydantic Settings
│   │   └── logging.py           # Sistema de logging estruturado
│   │
│   ├── models/                  # Modelos SQLAlchemy (ORM)
│   │   └── event.py             # Modelo Event (tabela events)
│   │
│   ├── schemas/                 # Schemas Pydantic (validação)
│   │   └── event.py             # EventCreate, EventUpdate, Event
│   │
│   ├── routers/                 # Rotas da aplicação
│   │   ├── api_router.py        # Endpoints REST API (/api/events)
│   │   └── page_router.py       # Rotas web (interface HTML)
│   │
│   ├── services/                # Lógica de negócio
│   │   └── event_service.py     # CRUD operations para eventos
│   │
│   ├── templates/               # Templates Jinja2
│   │   ├── events/              # Templates específicos de eventos
│   │   │   ├── list.html        # Listagem de eventos
│   │   │   ├── create.html      # Formulário de criação
│   │   │   ├── edit.html        # Formulário de edição
│   │   │   ├── detail.html      # Detalhes do evento
│   │   │   └── not_found.html   # Página 404
│   │   └── error.html           # Página de erro genérica
│   │
│   ├── static/                  # Arquivos estáticos
│   │   ├── css/                 # Folhas de estilo
│   │   └── js/                  # Scripts JavaScript
│   │
│   └── tests/                   # Testes automatizados
│       └── services/            # Testes dos serviços
│           └── test_event_service.py
│
├── k8s/                         # Manifests Kubernetes
│   ├── deployment.yaml          # Deployment e Service
│   └── prometheus.yaml          # Configuração Prometheus
│
├── .github/                     # GitHub Actions
│   └── workflows/
│       └── main.yml             # Pipeline CI/CD (Build → Test → Deploy)
│
├── dashboard/                   # Dashboards de monitoramento
│   └── board.json               # Dashboard Grafana
│
└── slides/                      # Material de apresentação
```

## 🔧 Configuração

### Pré-requisitos

- **Python 3.11+**
- **PostgreSQL 12+**
- **Docker 20.10+** (opcional, para containerização)
- **kubectl** (opcional, para deployment Kubernetes)
- **Git**

### Variáveis de Ambiente

Crie um arquivo `.env` na raiz do diretório `src/` com as seguintes variáveis:

| Variável | Descrição | Valor Padrão |
|----------|-----------|--------------|
| `DATABASE_URL` | URL de conexão PostgreSQL | `postgresql://encontros_tech:encontros_tech@localhost:5432/encontros_tech` |
| `APP_TITLE` | Título da aplicação | `Encontros Tech` |
| `DEBUG` | Modo debug (True/False) | `False` |
| `HOST` | Host do servidor | `0.0.0.0` |
| `PORT` | Porta do servidor | `8000` |
| `LOG_LEVEL` | Nível de log (DEBUG/INFO/WARNING/ERROR) | `INFO` |
| `LOG_FORMAT` | Formato do log (colored/simple) | `colored` |
| `SERVICE_NAME` | Nome do serviço (telemetria) | `encontros-tech` |
| `SERVICE_VERSION` | Versão do serviço | `1.0.0` |
| `PROMETHEUS_MULTIPROC_DIR` | Diretório para métricas Prometheus | `/tmp/prometheus_multiproc` |

### Exemplo de `.env`:

```bash
DATABASE_URL=postgresql://user:password@localhost:5432/encontros_tech
DEBUG=False
LOG_LEVEL=INFO
LOG_FORMAT=colored
SERVICE_NAME=encontros-tech
SERVICE_VERSION=1.0.0
```

## 🚀 Instalação e Execução

### 1. Execução Local (Desenvolvimento)

#### Passo 1: Clone o repositório
```bash
git clone <repository-url>
cd maratona-ia
```

#### Passo 2: Configure o banco de dados PostgreSQL
```bash
# Criar banco de dados
createdb encontros_tech

# Ou com Docker
docker run --name postgres-encontros \
  -e POSTGRES_USER=encontros_tech \
  -e POSTGRES_PASSWORD=encontros_tech \
  -e POSTGRES_DB=encontros_tech \
  -p 5432:5432 \
  -d postgres:15
```

#### Passo 3: Instale as dependências
```bash
cd src
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

#### Passo 4: Configure as variáveis de ambiente
```bash
cp .env.example .env
# Edite o arquivo .env com suas configurações
```

#### Passo 5: Execute a aplicação
```bash
# Desenvolvimento
python main.py

# Produção (com Gunicorn)
gunicorn --bind 0.0.0.0:8000 --workers 4 main:app
```

A aplicação estará disponível em: **http://localhost:8000**

### 2. Execução com Docker

#### Build e execução local:
```bash
cd src

# Build da imagem
docker build -t encontros-tech:local .

# Executar container
docker run -d \
  --name encontros-tech \
  -p 8000:8000 \
  -e DATABASE_URL="postgresql://user:password@host.docker.internal:5432/encontros_tech" \
  encontros-tech:local
```

#### Usando Docker Compose:
```bash
# Criar arquivo docker-compose.yml (não incluído no projeto)
docker-compose up -d
```

### 3. Deployment em Kubernetes

#### Pré-requisitos:
- Cluster Kubernetes configurado
- `kubectl` instalado e configurado
- Imagem Docker publicada no Docker Hub

#### Passo 1: Criar namespaces
```bash
# Homologação
kubectl create namespace tech-homolog

# Produção
kubectl create namespace tech-prod
```

#### Passo 2: Configurar secrets
```bash
# Homologação
kubectl create secret generic database-secret \
  --from-literal=DATABASE_URL="postgresql://user:password@db-host:5432/db_name" \
  --namespace=tech-homolog

# Produção
kubectl create secret generic database-secret \
  --from-literal=DATABASE_URL="postgresql://user:password@db-host:5432/db_name" \
  --namespace=tech-prod
```

#### Passo 3: Deploy da aplicação
```bash
# Homologação
kubectl apply -f k8s/deployment.yaml -n tech-homolog

# Produção
kubectl apply -f k8s/deployment.yaml -n tech-prod
```

#### Passo 4: Verificar deployment
```bash
# Ver pods
kubectl get pods -n tech-homolog
kubectl get pods -n tech-prod

# Ver services
kubectl get svc -n tech-homolog
kubectl get svc -n tech-prod

# Logs
kubectl logs -f deployment/encontros-tech -n tech-homolog
```

#### Passo 5: Acessar a aplicação
```bash
# Obter IP externo do LoadBalancer
kubectl get svc encontros-tech -n tech-prod

# Ou usar port-forward para acesso local
kubectl port-forward svc/encontros-tech 8000:80 -n tech-homolog
```

Acesse: **http://localhost:8000** (port-forward) ou **http://<EXTERNAL-IP>** (LoadBalancer)

## 📊 Monitoramento e Observabilidade

### Métricas Prometheus

A aplicação expõe métricas Prometheus no endpoint `/metrics`:

**Métricas disponíveis:**
- `flask_http_request_total` - Total de requisições HTTP por método, path e status
- `flask_http_request_duration_seconds` - Histograma de duração das requisições
- `flask_exporter_info` - Informações da aplicação (versão)
- `app_info` - Metadados da aplicação

**Acessar métricas:**
```bash
curl http://localhost:8000/metrics
```

### Configuração Prometheus

O arquivo `k8s/prometheus.yaml` contém a configuração completa do Prometheus para scraping automático dos pods:

```yaml
annotations:
  prometheus.io/scrape: "true"
  prometheus.io/port: "8000"
  prometheus.io/path: "/metrics"
```

### Logging Estruturado

A aplicação possui sistema de logging estruturado com diferentes níveis:

**Níveis de log:**
- `DEBUG` - Informações detalhadas para debug
- `INFO` - Informações gerais sobre operações
- `WARNING` - Avisos sobre situações potencialmente problemáticas
- `ERROR` - Erros que não impedem a aplicação de funcionar

**Formato de logs:**
```
2025-11-26 15:30:45,123 | INFO | encontros-tech | <module>:20 | Criando tabelas no banco de dados
2025-11-26 15:30:45,456 | INFO | api_router | API - Criando novo evento
```

**Logs de negócio:**
A aplicação registra eventos de negócio importantes:
- `API_EVENT_CREATED` - Evento criado via API
- `WEB_EVENT_CREATED` - Evento criado via formulário web
- `API_EVENTS_LISTED` - Listagem de eventos via API
- `WEB_EVENTS_PAGE_VIEWED` - Página de eventos visualizada

### Dashboard Grafana

Um dashboard pré-configurado está disponível em `dashboard/board.json` com visualizações:
- Taxa de requisições por segundo (RPS)
- Latência (P50, P95, P99)
- Taxa de erro (4xx/5xx)
- Uso de recursos (CPU e Memória)

**Importar dashboard:**
1. Acesse o Grafana
2. Vá em **Dashboards → Import**
3. Faça upload do arquivo `dashboard/board.json`

## 🔒 Modelo de Dados

### Tabela: `events`

| Campo | Tipo | Descrição | Constraints |
|-------|------|-----------|-------------|
| `id` | Integer | Identificador único | PRIMARY KEY, AUTO_INCREMENT |
| `title` | String | Título do evento | NOT NULL, INDEXED |
| `description` | Text | Descrição detalhada | NULLABLE |
| `date` | DateTime | Data e hora do evento | NOT NULL, DEFAULT: now() |
| `location` | String | Local do evento | NOT NULL |
| `edit_token` | String (UUID) | Token único para edição | UNIQUE, INDEXED, DEFAULT: uuid4() |

### Schemas Pydantic

**EventCreate** (criação):
```python
{
  "title": "string",
  "description": "string (opcional)",
  "date": "datetime",
  "location": "string",
  "technologies": ["string", "string"]
}
```

**EventUpdate** (atualização):
```python
{
  "title": "string",
  "description": "string (opcional)",
  "date": "datetime",
  "location": "string",
  "technologies": ["string", "string"]
}
```

**Event** (resposta):
```python
{
  "id": 1,
  "title": "string",
  "description": "string",
  "date": "2025-11-26T15:30:00",
  "location": "string",
  "technologies": ["Python", "Flask"],
  "edit_token": "uuid-string"
}
```

## 🧪 Testes

### Executar testes

```bash
cd src

# Executar todos os testes
python -m pytest tests/ -v

# Executar testes específicos
python -m pytest tests/services/test_event_service.py -v

# Com coverage
python -m pytest tests/ --cov=. --cov-report=html
```

## 🔄 CI/CD Pipeline

O projeto utiliza **GitHub Actions** para CI/CD automatizado com três estágios:

### 1. CI (Continuous Integration)
- ✅ Checkout do código
- 🐍 Setup Python 3.13
- 📦 Instalação de dependências
- 🧪 Execução de testes com pytest
- 🐳 Build da imagem Docker multi-arquitetura (AMD64 + ARM64)
- 📤 Push para Docker Hub com tags `latest` e versionada

### 2. CD-Homolog (Deploy Homologação)
- ☸️ Configuração do cluster Kubernetes
- 📁 Criação do namespace `tech-homolog`
- 🔐 Configuração de secrets
- 🚀 Deploy da aplicação
- ⏸️ Aguarda aprovação manual para produção

### 3. CD-Prod (Deploy Produção)
- ✅ Requer aprovação manual
- ☸️ Configuração do cluster Kubernetes
- 📁 Criação do namespace `tech-prod`
- 🔐 Configuração de secrets
- 🚀 Deploy da aplicação em produção

**Trigger:** Push na branch `main` ou execução manual via workflow_dispatch

## 🐳 Docker

### Build multi-arquitetura

```bash
# Build para múltiplas arquiteturas
docker buildx build \
  --platform linux/amd64,linux/arm64 \
  -t car21/encontros-tech:latest \
  --push \
  ./src
```

### Imagem Docker Hub

A imagem oficial está disponível em:
```
docker pull car21/encontros-tech:latest
```

### Características da imagem:
- ✅ Base: `python:3.11-slim`
- ✅ Usuário não-root (`appuser`)
- ✅ Multi-stage build otimizado
- ✅ Suporte AMD64 e ARM64
- ✅ Gunicorn com 4 workers
- ✅ Health checks configurados
- ✅ Tamanho otimizado

## 📡 Endpoints da API

### Criar Evento
```http
POST /api/events/
Content-Type: application/json

{
  "title": "Python Brasil 2025",
  "description": "Maior evento de Python do Brasil",
  "date": "2025-10-15T09:00:00",
  "location": "São Paulo, SP",
  "technologies": ["Python", "Flask", "FastAPI"]
}
```

### Listar Eventos
```http
GET /api/events/?skip=0&limit=100&search=python
```

### Buscar Evento por Token
```http
GET /api/events/by-token/<edit_token>
```

### Atualizar Evento
```http
PUT /api/events/by-token/<edit_token>
Content-Type: application/json

{
  "title": "Python Brasil 2025 - Atualizado",
  "description": "Descrição atualizada",
  "date": "2025-10-16T09:00:00",
  "location": "Rio de Janeiro, RJ",
  "technologies": ["Python", "Django"]
}
```

## 🤝 Contribuindo

Contribuições são bem-vindas! Para contribuir:

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto é distribuído sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

## 👥 Autores

- **Encontros Tech Team**

## 📞 Suporte

Para reportar problemas ou sugerir melhorias, abra uma issue no repositório do GitHub.

---

**Desenvolvido com ❤️ usando Flask e Python**

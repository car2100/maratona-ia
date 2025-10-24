# Encontros Tech

Uma aplicação web completa para gerenciamento de eventos de tecnologia, desenvolvida com Flask e configurada para execução em Kubernetes com observabilidade integrada via Prometheus.

## 📋 Sobre o Projeto

O **Encontros Tech** é uma aplicação web moderna que permite criar, visualizar e gerenciar eventos de tecnologia. A aplicação oferece tanto uma interface web intuitiva quanto uma API REST completa, sendo ideal para comunidades tech organizarem seus meetups, conferências e workshops.

Desenvolvida com foco em observabilidade e escalabilidade, a aplicação inclui métricas Prometheus nativas, logging estruturado e está preparada para execução em ambientes de produção Kubernetes.

## 🚀 Funcionalidades Principais

- **Gerenciamento de Eventos**: Criação, edição, visualização e listagem de eventos
- **Interface Web Responsiva**: Templates HTML com design moderno e funcional
- **API REST Completa**: Endpoints para integração com outros sistemas
- **Sistema de Edição Segura**: Tokens únicos para edição de eventos sem autenticação complexa
- **Busca e Filtros**: Funcionalidade de pesquisa por título, descrição e localização
- **Métricas Prometheus**: Observabilidade nativa com métricas de aplicação e negócio
- **Logging Estruturado**: Sistema de logs configurável com diferentes níveis
- **Health Checks**: Endpoints para verificação de saúde da aplicação
- **Containerização**: Imagem Docker otimizada para produção
- **Deploy Kubernetes**: Manifests prontos para produção com alta disponibilidade

## 🛠️ Tecnologias Utilizadas

**Backend**:
- **Flask 3.0.0**: Framework web principal
- **SQLAlchemy 2.0.43**: ORM para gerenciamento de banco de dados
- **Pydantic 2.11.7**: Validação e serialização de dados
- **Gunicorn 21.2.0**: Servidor WSGI para produção
- **PostgreSQL**: Banco de dados relacional via psycopg2-binary

**Frontend**:
- **Jinja2 3.1.6**: Engine de templates
- **HTML5/CSS3**: Interface responsiva
- **JavaScript**: Interatividade e validações

**Observabilidade**:
- **prometheus-flask-exporter 0.23.0**: Métricas Prometheus automáticas
- **Sistema de Logging**: Logging estruturado com níveis configuráveis

**DevOps & Infraestrutura**:
- **Docker**: Containerização da aplicação
- **Kubernetes**: Orquestração e deployment
- **Prometheus**: Coleta de métricas
- **PostgreSQL**: Banco de dados em produção

**Testes**:
- **pytest 8.3.4**: Framework de testes

## 📦 Estrutura do Projeto

```
src/
├── main.py                     # Ponto de entrada da aplicação Flask
├── requirements.txt            # Dependências Python
├── Dockerfile                  # Imagem Docker para produção
├── .env.example               # Exemplo de variáveis de ambiente
│
├── core/                      # Núcleo da aplicação
│   ├── database.py            # Configuração e conexão com banco de dados
│   ├── logging.py             # Sistema de logging estruturado
│   └── settings.py            # Configurações e variáveis de ambiente
│
├── models/                    # Modelos de dados SQLAlchemy
│   └── event.py               # Modelo do evento
│
├── schemas/                   # Esquemas Pydantic para validação
│   └── event.py               # Schemas de evento (Create, Update, Response)
│
├── services/                  # Lógica de negócio
│   └── event_service.py       # Serviços para operações com eventos
│
├── routers/                   # Roteadores Flask (Blueprints)
│   ├── api_router.py          # API REST endpoints
│   └── page_router.py         # Rotas para páginas web
│
├── templates/                 # Templates HTML Jinja2
│   ├── base.html              # Template base
│   └── events/                # Templates específicos de eventos
│       ├── list.html          # Listagem de eventos
│       ├── create.html        # Formulário de criação
│       ├── edit.html          # Formulário de edição
│       ├── detail.html        # Detalhes do evento
│       └── not_found.html     # Página de erro 404
│
├── static/                    # Arquivos estáticos
│   ├── css/
│   │   └── style.css          # Estilos da aplicação
│   └── js/
│       └── main.js            # JavaScript da aplicação
│
└── tests/                     # Testes automatizados
    └── services/
        └── test_event_service.py # Testes dos serviços

k8s/                           # Manifests Kubernetes
├── deployment.yaml            # Deployment e Service
└── prometheus.yaml            # Configuração Prometheus

dashboard/                     # Dashboards Grafana
└── board.json                 # Dashboard de métricas
```

## 🔧 Configuração

### Pré-requisitos

- **Python 3.11+**
- **PostgreSQL 13+**
- **Docker** (opcional, para containerização)
- **Kubernetes** (opcional, para deploy em produção)

### Variáveis de Ambiente

| Variável | Descrição | Valor Padrão |
|----------|-----------|--------------|
| `DATABASE_URL` | URL completa de conexão PostgreSQL | `postgresql://encontros_tech:encontros_tech@localhost:5432/encontros_tech` |
| `APP_TITLE` | Título da aplicação | `Encontros Tech` |
| `DEBUG` | Modo debug (true/false) | `false` |
| `HOST` | Host de bind da aplicação | `0.0.0.0` |
| `PORT` | Porta da aplicação | `8000` |
| `LOG_LEVEL` | Nível de log (DEBUG, INFO, WARNING, ERROR) | `INFO` |
| `LOG_FORMAT` | Formato de log (colored, simple) | `colored` |
| `SERVICE_NAME` | Nome do serviço para telemetria | `encontros-tech` |
| `SERVICE_VERSION` | Versão do serviço | `1.0.0` |
| `PROMETHEUS_MULTIPROC_DIR` | Diretório para métricas Prometheus | `/tmp/prometheus_multiproc` |

## 🚀 Instalação e Execução

### 1. Desenvolvimento Local

```bash
# Clone o repositório
git clone <repository-url>
cd maratona-com-ia

# Navegue para o diretório da aplicação
cd src/

# Crie um ambiente virtual
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
venv\Scripts\activate     # Windows

# Instale as dependências
pip install -r requirements.txt

# Configure as variáveis de ambiente
cp .env.example .env
# Edite o arquivo .env com suas configurações

# Execute a aplicação
python main.py
```

A aplicação estará disponível em: `http://localhost:8000`

### 2. Execução com Docker

```bash
# Construa a imagem
cd src/
docker build -t encontros-tech .

# Execute o container
docker run -d \
  --name encontros-tech \
  -p 8000:8000 \
  -e DATABASE_URL="postgresql://user:pass@host:5432/db" \
  encontros-tech
```

### 3. Deploy em Kubernetes

```bash
# Aplique os manifests Kubernetes
kubectl apply -f k8s/

# Verifique o status do deployment
kubectl get pods -l app=encontros-tech

# Obtenha o IP externo do serviço
kubectl get service encontros-tech
```

## 📊 Monitoramento e Observabilidade

### Métricas Prometheus

A aplicação expõe métricas Prometheus automaticamente no endpoint `/metrics`:

- **Métricas de Aplicação**: Requests, latência, status codes
- **Métricas de Negócio**: Eventos criados, atualizados, visualizados
- **Métricas de Sistema**: CPU, memória, conexões de banco

### Health Checks

- **Liveness Probe**: Verifica se a aplicação está respondendo
- **Readiness Probe**: Verifica se a aplicação está pronta para receber tráfego

### Logging

Sistema de logging estruturado com:
- Logs de aplicação com níveis configuráveis
- Logs de negócio para auditoria
- Correlação de requests com IDs únicos
- Suporte a formato colorido para desenvolvimento

### Dashboards Grafana

Dashboards pré-configurados disponíveis:
- **Kubernetes Cluster Monitoring**: Visão geral do cluster
- **Application Metrics**: Métricas específicas da aplicação
- **Business Metrics**: KPIs de negócio

## 🔒 Modelo de Dados

### Entidade Event

```python
class Event:
    id: int                    # Identificador único
    title: str                 # Título do evento
    description: Optional[str] # Descrição detalhada
    date: datetime            # Data e hora do evento
    location: str             # Local do evento
    technologies: List[str]   # Tecnologias relacionadas
    edit_token: str           # Token único para edição
```

### Fluxo de Dados

1. **Criação**: Evento criado via formulário web ou API
2. **Validação**: Dados validados via esquemas Pydantic
3. **Persistência**: Dados salvos no PostgreSQL via SQLAlchemy
4. **Token de Edição**: Token único gerado para futuras edições
5. **Retorno**: Evento retornado com token para edição

## 📡 API Endpoints

### Eventos

- `GET /api/events/` - Listar eventos
- `POST /api/events/` - Criar evento
- `GET /api/events/by-token/{token}` - Buscar por token
- `PUT /api/events/by-token/{token}` - Atualizar evento

### Páginas Web

- `GET /` - Página inicial com listagem
- `GET /events/new` - Formulário de criação
- `GET /events/edit/{token}` - Formulário de edição
- `GET /events/{id}` - Detalhes do evento

### Monitoramento

- `GET /metrics` - Métricas Prometheus
- `GET /health` - Health check

---

**Desenvolvido com ❤️ para a comunidade tech brasileira**
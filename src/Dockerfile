# ==============================================================================
# Multi-stage Dockerfile para Encontros Tech
# ==============================================================================
FROM python:3.11-slim

# Labels para metadata
LABEL maintainer="Encontros Tech Team"
LABEL version="1.0.0"
LABEL description="Aplicação Flask para gerenciamento de eventos tech"

# Definir diretório de trabalho
WORKDIR /app

# Copiar apenas requirements primeiro (melhor cache)
COPY requirements.txt .

# Instalar dependências Python
RUN pip install --no-cache-dir -r requirements.txt

# Criar usuário não-root antes de copiar arquivos
RUN adduser --disabled-password --gecos '' appuser

# Criar diretório para métricas Prometheus com permissões corretas
RUN mkdir -p /tmp/prometheus_multiproc && \
    chown -R appuser:appuser /tmp/prometheus_multiproc

# Copiar código da aplicação
COPY . .

# Dar ownership de todos os arquivos ao appuser
RUN chown -R appuser:appuser /app

# Mudar para usuário não-root
USER appuser

# Expor porta da aplicação
EXPOSE 8000

# Comando para iniciar a aplicação com Gunicorn
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "--workers", "4", "main:app"]
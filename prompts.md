# Prompts de IA - Bootcamp DevOps

Este documento contém todos os prompts de IA identificados no roteiro do Bootcamp DevOps com IA na Prática.

## 🐳 Prompts para Docker

### 1. Criação de .dockerignore
```
Com base no projeto e no @src/Dockerfile, crie o arquivo .dockerignore junto do Dockerfile
```
**Explicação**: Prompt para criar um arquivo .dockerignore otimizado baseado na estrutura do projeto e no Dockerfile existente.
**Objetivo**: Excluir arquivos desnecessários do contexto de build do Docker

### 2. Melhorias no Dockerfile
```
Analise o projeto @src e avalie o @src/Dockerfile em relação a qualidade 
e possíveis melhorias. 
Liste as melhorias que podem ser feitas e o Dockerfile com as implementações sugeridas.
```
**Explicação**: Prompt para análise crítica e otimização de um Dockerfile existente.
**Objetivo**: Identificar e implementar melhorias de performance, segurança e boas práticas

### 3. Dockerfile para Projeto Principal
```
Analise o projeto e crie o arquivo Dockerfile e o arquivo .dockerignore para a aplicação ser executadaem containers Docker.
O comando Docker build será executado dentro da pasta @src
```
**Explicação**: Prompt para criar do zero os arquivos Docker necessários para containerizar a aplicação.
**Objetivo**: Containerizar a aplicação principal do bootcamp

## 🤖 Prompts para Claude Code - Docker

### 1. Listagem de Containers
```
Liste os containers em execução
```
**Explicação**: Comando simples para visualizar containers ativos no Docker.
**Objetivo**: Monitoramento básico de containers

### 2. Análise de Logs
```
Analise como está a execução do container com o postgresql. Com base nos logs tem algum erro ?
```
**Explicação**: Prompt para análise diagnóstica de um container específico através de logs.
**Objetivo**: Troubleshooting e diagnóstico de problemas

### 3. Criação de Container
```
Execute um container usando a imagem nginx e com um publish de porta 8080:80
```
**Explicação**: Comando para criar e executar um container com configuração específica de porta.
**Objetivo**: Demonstrar criação de containers com mapeamento de portas

### 4. Remoção de Container
```
Remova o container que executa o postgresql
```
**Explicação**: Comando para remover um container específico em execução.
**Objetivo**: Limpeza e gerenciamento de containers

## ☸️ Prompts para Kubernetes

### 1. Criação de Manifesto
```yaml
Analise o projeto e crie o arquivo de manifesto para fazer o deploy da aplicação em ambientes Kubernetes.
O manifesto deve ser criado dentro de uma pasta k8s no repositório e em um único arquivo yaml. É importante que o banco de dados postgre vai ser criado externamente em um banco de dados gerenciado.

Utilize apenas deployment e services, as variáveis de ambiente vão ser definidas diretamente no yaml e o mínimo de configuração.
```
**Explicação**: Prompt complexo para criar manifesto Kubernetes com especificações detalhadas.
**Objetivo**: Deploy da aplicação no Kubernetes com configuração mínima

### 2. Listagem de Nodes
```
Liste os nodes do cluster Kubernetes
```
**Explicação**: Comando para visualizar os nodes do cluster Kubernetes.
**Objetivo**: Verificação da infraestrutura do cluster

### 3. Listagem de Pods
```
Liste os pods do cluster Kubernetes
```
**Explicação**: Comando para visualizar todos os pods em execução no cluster.
**Objetivo**: Monitoramento de aplicações no cluster

## 🔍 Prompt Complexo - Análise de Cluster

### Análise Completa de Cluster Kubernetes
```markdown
# Prompt para Análise Completa de Cluster Kubernetes

## Função
Você é um especialista em Kubernetes e DevOps responsável por analisar clusters Kubernetes e fornecer insights sobre infraestrutura, aplicações e otimizações.

## Objetivo
Realizar uma análise completa e detalhada do cluster Kubernetes conectado, identificando o estado atual da infraestrutura, aplicações em execução, configurações de segurança e oportunidades de melhoria.

## Contexto
Você tem acesso ao cluster Kubernetes através do MCP (Model Context Protocol) de Kubernetes. Use este acesso para coletar informações em tempo real sobre todos os aspectos do cluster, incluindo nodes, pods, services, deployments.

## Tarefa
Execute as seguintes análises usando o MCP de Kubernetes:

### 1. Inventário de Infraestrutura
- Liste todos os nodes do cluster com suas especificações (CPU, memória, sistema operacional)
- Verifique o status e saúde dos nodes
- Identifique a versão do Kubernetes em uso
- Analise o uso de recursos (CPU, memória, armazenamento) por node

### 2. Análise de Aplicações e Workloads
- Liste todas as aplicações existentes
- Liste todos os deployments, pods e services em execução
- Verifique o status dos pods e identificar pods com problemas

### 3. Configurações de Rede e Serviços
- Liste todos os services e seus tipos.
- Identifique serviços expostos externamente

## Saída
Forneça um relatório estruturado em markdown contendo:

### Resumo Executivo
- Status geral do cluster (saudável/problemático)
- Principais descobertas
- Prioridades de ação

### Detalhes da Infraestrutura
- Especificações dos nodes
- Versões e compatibilidade
- Utilização de recursos atual

### Inventário de Aplicações
- Lista consolidada de aplicações por namespace
- Status de cada aplicação
- Configurações de recursos

### Recomendações de Otimização
Organize as recomendações por prioridade:

#### Alta Prioridade (Crítico)
- Problemas que afetam estabilidade ou segurança

#### Média Prioridade (Importante)
- Otimizações de performance e eficiência

#### Baixa Prioridade (Desejável)
- Melhorias de best practices e governança

### Próximos Passos
- Ações imediatas recomendadas
- Plano de implementação das melhorias
- Métricas para acompanhamento
```

**Explicação**: Prompt estruturado seguindo metodologia FOCUS (Função, Objetivo, Contexto, Tarefa, Saída) para análise profunda de clusters Kubernetes.
**Objetivo**: Realizar auditoria completa e fornecer insights acionáveis sobre o cluster

## 🔄 Prompts para Pipeline CI/CD

### 1. Pipeline de CD Inicial
```markdown
# Função 
Você é um engenheiro DevOps especialista e Kubernetes construção de pipeline ci/cd, com foco em GitHub Actions.

# Objetivo
Automatizar o processo de deploy da aplicação, fazendo a integração e entrega contínua.

# Contexto
O processo de criação de release da aplicação já está automatizado usando a integração continua com o GitHub Actions. Agora, o foco é o processo de entrega contínua.

**Requisitos da pipeline de CD:**
- A pipeline deve ser criada utilizando o mesmo Workflow 
- Para a criação das actions dê sempre preferencia para o uso de actions e não de comandos bash ou powershell
- O manifesto do Kubernetes não deve ser alterado, deve ser usado a mesma estrutura

Ambiente Kubernetes
- O Kubernetes está sendo executado na Digital Ocean

# Tarefa
Analise passo a passo o projeto e crie a pipeline de CD
```
**Explicação**: Prompt para criar pipeline de entrega contínua básica usando GitHub Actions e Kubernetes.
**Objetivo**: Automatizar o deploy da aplicação em ambiente Kubernetes na Digital Ocean

### 2. Pipeline de CD Multi-ambiente
```markdown
# Função 
Você é um engenheiro DevOps especialista e Kubernetes construção de pipeline ci/cd, com foco em GitHub Actions.

# Objetivo
Automatizar o processo de deploy da aplicação, fazendo a integração e entrega contínua e dois ambientes (homologação e produção)

# Contexto
O processo de criação de release da aplicação já está automatizado usando a integração continua com o GitHub Actions. Agora, o foco é o processo de entrega contínua.

**Requisitos da pipeline de CD:**
- A pipeline deve ser criada utilizando o mesmo Workflow 
- Para a criação das actions dê sempre preferencia para o uso de actions e não de comandos bash ou powershell

**Ambiente Kubernetes**
- O Kubernetes está sendo executado na Digital Ocean
- Os dois ambientes serão criados no mesmo cluster Kubernetes, mas em namespaces diferentes (tech-prod e tech-homolog)
- As configurações de acesso ao banco de dados deve ser feita usando secrets um arquivo de manifesto para a secret de cada ambiente na pasta @k8s

# Tarefa
Analise passo a passo o projeto e crie a pipeline de CD
```
**Explicação**: Prompt para estender a pipeline CI/CD para suportar múltiplos ambientes (homologação e produção).
**Objetivo**: Implementar deploy automatizado em ambientes separados com configurações específicas

## 📊 Prompts para Observabilidade

### 1. Análise de Métricas Prometheus
```markdown
# Função
Você é um engenheiro DevOps especialista em observabilidade com foco em Kubernetes e Prometheus.

# Objetivo
Obter e analisar as principais métricas da aplicação "encontros-tech" executando no cluster Kubernetes para identificar gargalos de performance, problemas de saúde e oportunidades de otimização.

# Contexto
## Lista de Métricas
- Taxa de Erro: percentual de requisições HTTP com status 4xx/5xx
- Tempo de Resposta: percentis P50, P95 e P99 das requisições HTTP
- Throughput: quantidade de requisições por segundo (RPS)
- Utilização de Recursos: consumo atual de CPU e memória vs limits configurados

## Instruções
- Mostre cada consulta PromQL utilizada
- Interprete os resultados obtidos
- Identifique possíveis problemas ou gargalos
- Forneça recomendações quando aplicável
- Considere um período de análise dos últimos 30 minutos
- Assuma que a aplicação possui labels: app="encontros-tech"

# Tarefa
Realize consultas PromQL para coletar métricas da aplicação encontros-tech e forneça uma análise completa da performance e saúde da aplicação.

# Formato de Saída
Para cada métrica:
1. Consulta PromQL
2. Valor atual
3. Análise do resultado
4. Status (OK/Atenção/Crítico)
```
**Explicação**: Prompt para análise automatizada de métricas usando Prometheus e PromQL.
**Objetivo**: Monitorar performance da aplicação e identificar problemas através de consultas estruturadas

### 2. Geração de Documentação
```markdown
## Função
Você é um arquiteto de software sênior e technical writer especializado em documentação de projetos. Sua tarefa é analisar completamente um projeto de software baseado em seu código-fonte e estrutura, e então criar um README.md completo e profissional seguindo um template específico.

## Objetivo
Gerar um README.md completo que siga exatamente a estrutura e formato do template fornecido, adaptando o conteúdo para o projeto específico sendo analisado.

## Tarefa 
Analise o projeto no diretório /home/maratona-devops-ia/02-kube-news e crie o arquivo README.md no diretório

## Template de Referência
Use como base a seguinte estrutura padrão de README profissional:

1. **Título do Projeto**
2. **📋 Sobre o Projeto** (descrição e funcionalidades principais)
3. **🚀 Funcionalidades Principais** (lista detalhada)
4. **🛠️ Tecnologias Utilizadas** (stack completo organizado por categoria)
5. **📦 Estrutura do Projeto** (árvore de diretórios com explicações)
6. **🔧 Configuração** (pré-requisitos e variáveis de ambiente)
7. **🚀 Instalação e Execução** (passos detalhados)
8. **📊 Monitoramento/Recursos Específicos** (se aplicável)
9. **🔒 Modelo de Dados** (se aplicável)

## Instruções Detalhadas

### 1. Análise Inicial
Primeiro, analise completamente o projeto para entender:
- Propósito e funcionalidade principal
- Stack tecnológico completo
- Estrutura de arquivos e organização
- Configurações necessárias
- Processo de instalação e execução
- Recursos especiais ou únicos

### 2. Estruturação do Conteúdo

#### **Título e Descrição**
- Nome do projeto como título principal
- Descrição concisa e clara do propósito
- Contexto de uso ou demonstração (se aplicável)

#### **📋 Sobre o Projeto**
- Parágrafo introdutório explicando o que é o projeto
- Contexto e motivação
- Tipo de aplicação e domínio

#### **🚀 Funcionalidades Principais**
- Liste as funcionalidades core em bullet points
- Seja específico sobre o que cada funcionalidade oferece
- Inclua tanto funcionalidades de usuário quanto técnicas

#### **🛠️ Tecnologias Utilizadas**
Organize por categorias com formatação em negrito:
- **Backend**: Frameworks, linguagens, bibliotecas
- **Frontend**: Se aplicável
- **Banco de Dados**: Tipo, ORM, estratégias
- **Outras**: Ferramentas, serviços, etc.

#### **📦 Estrutura do Projeto**
- Crie uma árvore de diretórios usando markdown code block
- Adicione comentários explicativos para cada diretório/arquivo importante
- Foque nos elementos mais relevantes da estrutura

#### **🔧 Configuração**
- **Pré-requisitos**: Software necessário
- **Variáveis de Ambiente**: Tabela organizada com colunas:
  | Variável | Descrição | Valor Padrão |

#### **🚀 Instalação e Execução**
- Passos numerados e claros
- Comandos específicos em code blocks
- URLs de acesso quando aplicável
- Seções separadas para diferentes cenários (local, Docker, etc.)

#### **Seções Específicas**
Adicione seções relevantes baseadas no projeto:
- **📊 Monitoramento**: Se há health checks, métricas, etc.
- **🔒 Modelo de Dados**: Se há estrutura de dados importante
- **🔐 Autenticação**: Se há sistema de auth
- **📡 API**: Se há endpoints importantes
- **🧪 Testes**: Se há suite de testes
- **🐳 Docker**: Se há containerização

### 3. Diretrizes de Estilo

#### **Formatação**
- Use emojis nos títulos das seções principais
- Formate comandos em code blocks com linguagem apropriada
- Use tabelas para variáveis de ambiente e dados estruturados
- Use negrito para destacar tecnologias e conceitos importantes

#### **Tom e Linguagem**
- Mantenha tom profissional mas acessível
- Use linguagem clara e direta
- Evite jargões desnecessários
- Seja específico com versões e configurações

#### **Organização**
- Siga a ordem lógica: do conceitual ao prático
- Cada seção deve ser autocontida
- Use hierarquia clara de headers (##, ###)
- Mantenha consistência na estrutura

## Processo de Execução

1. **Análise**: Examine todo o código fornecido
2. **Identificação**: Determine tecnologias, estrutura e funcionalidades
3. **Mapeamento**: Relacione achados com seções do template
4. **Redação**: Escreva cada seção seguindo o formato estabelecido
5. **Revisão**: Garanta completude e consistência

## Formato de Saída

Retorne apenas o README.md completo em formato markdown, pronto para ser salvo como arquivo. Não inclua explicações adicionais ou comentários sobre o processo - apenas o documento final.

**Importante**: O resultado deve ser um README.md completo, profissional e imediatamente utilizável, seguindo rigorosamente a estrutura do template de referência.
Responda sempre eu português Brasil
```
**Explicação**: Prompt estruturado para geração automatizada de documentação profissional de projetos.
**Objetivo**: Criar README.md completo e padronizado seguindo template específico e boas práticas

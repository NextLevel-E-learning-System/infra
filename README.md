# NextLevel E-learning System - Infraestrutura

Este repositório contém a configuração de infraestrutura para o NextLevel E-learning System, um sistema de aprendizagem online completo baseado em arquitetura de microserviços.

## 📋 Visão Geral

O sistema é composto por múltiplos microserviços que trabalham em conjunto para fornecer uma plataforma de e-learning robusta e escalável. A arquitetura utiliza Docker Compose para orquestração de containers, facilitando o desenvolvimento e deploy local.

## 🏗️ Arquitetura

O sistema segue uma arquitetura de microserviços com os seguintes componentes:

### API Gateway
- **Porta**: 8080
- **Função**: Ponto de entrada único para todas as requisições do frontend
- **Descrição**: Roteia requisições para os microserviços apropriados

### Microserviços Backend

1. **Auth Service** (`auth-service`)
   - Gerenciamento de autenticação e autorização
   - Controle de acesso de usuários

2. **User Service** (`user-service`)
   - Gerenciamento de perfis de usuários
   - Dados cadastrais e preferências

3. **Notification Service** (`notification-service`)
   - Sistema de notificações
   - Alertas e comunicações com usuários

4. **Course Service** (`course-service`)
   - Gerenciamento de cursos
   - Conteúdo educacional e estrutura de cursos

5. **Assessment Service** (`assessment-service`)
   - Sistema de avaliações
   - Provas, quizzes e exercícios

6. **Progress Service** (`progress-service`)
   - Acompanhamento de progresso dos alunos
   - Métricas de conclusão e desempenho

7. **Gamification Service** (`gamification-service`)
   - Sistema de gamificação
   - Pontos, badges e recompensas

### Frontend

- **Web Frontend** (`web-frontend`)
  - **Porta**: 80
  - **Tecnologia**: Vite
  - Interface web do usuário
  - Comunicação com API Gateway

## 🚀 Como Usar

### Pré-requisitos

- Docker
- Docker Compose
- Repositórios dos serviços clonados no diretório pai

### Estrutura de Diretórios Esperada

```
parent-directory/
├── infra/
│   └── docker-compose.yml
├── api-gateway/
├── auth-service/
├── user-service/
├── notification-service/
├── course-service/
├── assessment-service/
├── progress-service/
├── gamification-service/
└── web-frontend/
```

### Iniciar o Sistema

```bash
cd infra
docker-compose up -d
```

### Parar o Sistema

```bash
docker-compose down
```

### Ver Logs

```bash
# Todos os serviços
docker-compose logs -f

# Serviço específico
docker-compose logs -f [nome-do-serviço]
```

## 🌐 Rede

Todos os serviços estão conectados à rede `elearning-net` (bridge network), permitindo comunicação entre containers.

## ⚙️ Configuração

Cada serviço possui seu próprio arquivo `.env` localizado no respectivo diretório do serviço. O API Gateway está configurado com:

- `ALLOW_ALL_ORIGINS`: true (para desenvolvimento)
- URLs base de todos os microserviços para roteamento interno

## 🔗 Endpoints

- **API Gateway**: http://localhost:8080
- **Web Frontend**: http://localhost:80

## 📝 Observações

- O sistema está configurado para ambiente de desenvolvimento
- CORS está habilitado para todas as origens no API Gateway
- Cada serviço depende de suas próprias variáveis de ambiente definidas nos respectivos arquivos `.env`
- O Web Frontend usa Dockerfile.dev para desenvolvimento

## 🤝 Contribuindo

Este é o repositório de infraestrutura do sistema NextLevel E-learning. Para contribuir com serviços específicos, consulte os repositórios individuais de cada microserviço.

## 📄 Licença

Consulte o arquivo LICENSE para mais detalhes (se disponível).

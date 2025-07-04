# 🚀 Lead Management System

Sistema de gerenciamento de leads desenvolvido com .NET Core (back-end) e Angular (front-end).

## 🏗️ Arquitetura

Este projeto é dividido em **dois repositórios separados**:

- **Back-end**: API .NET Core + SQL Server
- **Front-end**: Interface Angular + nginx

## 📁 Estrutura dos Repositórios

### Repositório Back-end:
```
LeadManagement/
├── docker-compose.yml          # API + Database
├── Dockerfile                  # .NET API
├── start-backend.bat          # Script Windows
├── start-backend.sh           # Script Linux/Mac
├── README-DOCKER.md           # Documentação específica
├── env-example.txt            # Variáveis de ambiente
└── LeadsManagement.*/         # Projetos .NET
```

### Repositório Front-end:
```
LeadManagementFront/
├── docker-compose.yml          # Angular + nginx
├── Dockerfile                  # Angular build
├── start-frontend.bat         # Script Windows  
├── start-frontend.sh          # Script Linux/Mac
├── README-DOCKER.md           # Documentação específica
├── env-example.txt            # Variáveis de ambiente
└── src/                       # Código Angular
```

## 🚀 Como Executar (Repositórios Separados)

### 1. **Primeiro: Iniciar Back-end**

No repositório do back-end:
```bash
# Windows
start-backend.bat

# Linux/Mac
chmod +x start-backend.sh
./start-backend.sh

# Manual
docker-compose up -d
```

**Aguarde ~30 segundos** para o banco inicializar.

### 2. **Segundo: Iniciar Front-end**

No repositório do front-end:
```bash
# Windows  
start-frontend.bat

# Linux/Mac
chmod +x start-frontend.sh
./start-frontend.sh

# Manual
export API_URL=http://localhost:5000
docker-compose up -d
```

## 🌐 Acessos

- **Frontend**: http://localhost:4200
- **API**: http://localhost:5000
- **Swagger**: http://localhost:5000/swagger
- **Database**: localhost:1433 (sa/LeadManagement123!)

## 🔧 Configuração

### Variáveis de Ambiente:

**Back-end** (`env-example.txt`):
```bash
ASPNETCORE_ENVIRONMENT=Production
SA_PASSWORD=LeadManagement123!
```

**Front-end** (`env-example.txt`):
```bash
API_URL=http://localhost:5000
```

## 📊 Monitoramento

```bash
# Ver status
docker-compose ps

# Ver logs
docker-compose logs -f

# Parar tudo
docker-compose down
```

## 🐛 Troubleshooting

### Front-end não conecta na API:
1. Verifique se back-end está rodando: `curl http://localhost:5000/health`
2. Confirme a variável `API_URL=http://localhost:5000`
3. Aguarde o banco inicializar (~30s)

### Portas em uso:
```bash
# Verificar portas
netstat -tulpn | grep :4200
netstat -tulpn | grep :5000

# Parar tudo
docker-compose down
```

## 🔄 Desenvolvimento Local

### Back-end (sem Docker):
```bash
cd LeadsManagement.Api
dotnet run
```

### Front-end (sem Docker):
```bash
cd front/LeadManagementFront  
npm install
npm start
```

💡 **Dica**: Para repositórios GitHub separados, clone ambos e siga a ordem: back-end primeiro, depois front-end. 

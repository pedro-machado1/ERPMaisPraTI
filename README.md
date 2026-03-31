# ERP Maispra Ti

> Sistema ERP completo e responsivo desenvolvido como projeto final do curso Maisprati. Solução integrada para gestão de empresas com autenticação segura, dashboard inteligente e controle total de operações.

[![React](https://img.shields.io/badge/React-18.x-61DAFB?style=flat-square&logo=react)](https://reactjs.org/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-6DB33F?style=flat-square&logo=spring-boot)](https://spring.io/projects/spring-boot)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](LICENSE)

## Funcionalidades

### Frontend
- **Responsividade 100%** - Funciona perfeitamente em desktop, tablet e mobile
- **Dashboard Inteligente** - Dashboard personalizável com componentes arrastáveis e redimensionáveis
- **Grafos Interativos** - Visualização de dados em tempo real com chart.js
- **Autenticação Segura** - Proteção de rotas com JWT no frontend
- **Interface Moderna** - Design clean e intuitivo com Vite

### Backend
- **Autenticação JWT** - Proteção robusta de endpoints
- **Gestão Completa** - Cadastro, edição e exclusão de:
  - Clientes
  - Fornecedores
  - Produtos
  - Vendas
  - Insumos (Supply)
  - Usuários
- **Recuperação de Senha** - Sistema de email para reset de senha
- **API Documentada** - Swagger UI integrado para exploração de endpoints
- **Testes Unitários** - Cobertura com JUnit e Mockito

---

## Tecnologias

### Frontend
| Tecnologia | Descrição |
|------------|-----------|
| **React** | Biblioteca UI moderna com hooks |
| **Vite** | Build tool rápido e otimizado |
| **Axios** | Client HTTP para requisições |
| **React Router** | Navegação entre páginas |
| **Chart.js** | Gráficos interativos |
| **React Draggable** | Componentes arrastáveis |
| **React Resizable** | Componentes redimensionáveis |
| **JWT Decode** | Decodificação de tokens |
| **ESLint** | Análise estática de código |

### Backend
| Tecnologia | Descrição |
|------------|-----------|
| **Spring Boot 3.x** | Framework web e REST |
| **Spring Security** | Autenticação e autorização |
| **Spring Data JPA** | Persistência de dados |
| **Spring Mail** | Envio de emails |
| **MySQL** | Banco de dados produção |
| **H2** | Banco em memória (testes) |
| **Lombok** | Redução de boilerplate |
| **ModelMapper** | Conversão DTO/Entity |
| **SpringDoc** | Documentação Swagger |
| **JUnit 5 & Mockito** | Testes unitários |

---

## Pré-requisitos

### Backend
- **Java 17+** (recomendado: Java 21)
- **Maven 3.8+**
- **MySQL 8.0+** (para produção)

### Frontend
- **Node.js 18.x+**
- **npm 9.x+**

---

## Instalação e Execução

### 1. Clone o Repositório

```bash
git clone https://github.com/seu-usuario/ErpMaispraTIFinal.git
cd ErpMaispraTIFinal
```

### 2. Configurar Backend

```bash
# Navegue para a pasta backend
cd backend

# Compile o projeto
./mvnw clean compile

# Execute a aplicação (Linux/Mac)
./mvnw spring-boot:run

# Execute a aplicação (Windows)
mvnw.cmd spring-boot:run
```

**Resultado esperado:** A API estará disponível em `http://localhost:8080`

Acesse a documentação Swagger em: `http://localhost:8080/swagger-ui.html`

### 3. Configurar Frontend

```bash
# Navegue para a pasta frontend
cd ../frontend

# Instale as dependências
npm install

# Configure o arquivo .env
# Certifique-se de que API_URL aponta para seu backend
# API_URL=http://localhost:8080

# Execute o servidor de desenvolvimento
npm run dev
```

**Resultado esperado:** A aplicação estará disponível em `http://localhost:5173`

---

## Estrutura do Projeto

```
ErpMaispraTIFinal/
├── backend/
│   ├── src/main/java/com/          # Código source
│   ├── src/main/resources/         # Configurações e SQL
│   ├── src/test/java/              # Testes
│   ├── pom.xml                     # Dependências Maven
│   └── docker-compose.yml          # Containerização
│
├── frontend/
│   ├── src/
│   │   ├── components/             # Componentes React
│   │   ├── pages/                  # Páginas da aplicação
│   │   ├── assets/                 # CSS, fonts, ícones
│   │   └── App.jsx                 # Componente raiz
│   ├── package.json                # Dependências npm
│   ├── vite.config.js              # Configuração Vite
│   └── .env                        # Variáveis de ambiente
│
├── Inserts BD para testes/      # Scripts SQL para testes
├── testes_api/                  # Coleção Postman
└── README.md                       # Este arquivo
```

---

## Fluxo de Autenticação

```
1. Usuário faz login na tela de Login
   ↓
2. Backend valida credenciais e emite JWT
   ↓
3. Frontend armazena JWT (localStorage)
   ↓
4. JWT é enviado em cada requisição no header Authorization
   ↓
5. Backend valida JWT e processa a requisição
   ↓
6. Rotas protegidas verificam token antes de renderizar conteúdo
```

---

## Executar Testes

### Backend

```bash
cd backend

# Executar todos os testes
./mvnw test

# Executar com cobertura
./mvnw test jacoco:report
```

### Frontend (quando implementado)

```bash
cd frontend

# Executar testes
npm run test

# Executar com cobertura
npm run test:coverage
```

---

## Variáveis de Ambiente

### Frontend (`.env`)

```env
VITE_API_URL=http://localhost:8080
VITE_APP_NAME=ERP Maispra Ti
```

### Backend (`application-dev.properties`)

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/erp_db
spring.datasource.username=root
spring.datasource.password=root
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=seu-email@gmail.com
spring.mail.password=sua-senha-app
```

---

## Docker (Opcional)

```bash
# Build e execute com Docker Compose
cd backend
docker-compose up -d

# A aplicação estará em http://localhost:8080
```

---

## Documentação Adicional

- **API Docs:** `http://localhost:8080/swagger-ui.html`
- **[Postman Collection](testes_api/ERP+praTi.postman_collection.json)** - Importe para testar endpoints
- **[SQL Scripts](Inserts%20BD%20para%20testes%20(Perfil%20DEV)/)** - Scripts para popular banco de dados

---

## Deploy

**Aplicação em Produção:**  
https://erp-maispra-ti-final.vercel.app/

---

## Autor

Desenvolvido como projeto final do **Curso Maisprati**

---

## Licença

Este projeto está licenciado sob a licença MIT - vide arquivo [LICENSE](LICENSE) para detalhes.

---



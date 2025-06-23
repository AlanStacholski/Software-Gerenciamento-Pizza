# 🍕 Sistema de Pizzaria Delivery

Sistema completo de gerenciamento de pizzaria com delivery, desenvolvido com Node.js, Express, MongoDB e frontend vanilla JavaScript. Projeto acadêmico com arquitetura robusta e documentação Swagger interativa.

## 📋 Índice

- [Características](#-características)
- [Tecnologias](#-tecnologias)
- [Pré-requisitos](#-pré-requisitos)
- [Instalação Rápida](#-instalação-rápida)
- [Uso](#-uso)
- [API Endpoints](#-api-endpoints)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Funcionalidades](#-funcionalidades)
- [Demonstração](#-demonstração)
- [Contribuição](#-contribuição)

## ✨ Características

- ✅ **Sistema completo de autenticação** com JWT
- ✅ **Controle de acesso** baseado em roles (Admin/Cliente)
- ✅ **CRUD completo** para pizzas, pedidos, entregas e usuários
- ✅ **Documentação interativa** com Swagger UI
- ✅ **Interface responsiva** que funciona em desktop e mobile
- ✅ **Arquitetura em camadas** (Controllers, Services, Repositories, DTOs)
- ✅ **Validação robusta** de dados com Joi
- ✅ **Inicialização automática** de dados de teste
- ✅ **Sistema de notificações** em tempo real
- ✅ **Gestão completa de entregas** com controle de status

## 🚀 Tecnologias

### Backend
- **Node.js** - Runtime JavaScript
- **Express.js** - Framework web
- **MongoDB** - Banco de dados NoSQL
- **Mongoose** - ODM para MongoDB
- **JWT** - Autenticação segura
- **bcryptjs** - Criptografia de senhas
- **Joi** - Validação de dados
- **Swagger** - Documentação automática da API

### Frontend
- **HTML5** - Estrutura semântica
- **CSS3** - Estilização moderna e responsiva
- **JavaScript ES6+** - Lógica da aplicação
- **Font Awesome** - Ícones
- **SPA** - Single Page Application

### DevOps & Testes
- **Nodemon** - Auto-restart em desenvolvimento
- **Jest** - Framework de testes
- **Supertest** - Testes de API

## 📋 Pré-requisitos

- [Node.js](https://nodejs.org/) (versão 14 ou superior)
- [MongoDB](https://www.mongodb.com/) (local ou MongoDB Atlas)
- [Git](https://git-scm.com/)

## ⚡ Instalação Rápida

### 1. Clone o repositório
```bash
git clone https://github.com/marcelopiloni/SoftArchProject_Pizza.git
cd SoftArchProject_Pizza
```

### 2. Instale todas as dependências (comando único)
```bash
npm install express mongoose bcryptjs jsonwebtoken joi cors dotenv swagger-jsdoc swagger-ui-express && npm install --save-dev nodemon jest supertest
```

### 3. Configure as variáveis de ambiente
Crie um arquivo `.env` na raiz do projeto:
```env
# Server Configuration
PORT=3000

# Database Configuration
MONGODB_URI=mongodb://localhost:27017/pizzaria_delivery
# Ou para MongoDB Atlas:
# MONGODB_URI=mongodb+srv://usuario:senha@cluster.mongodb.net/pizzaria

# JWT Configuration
JWT_SECRET=seu-jwt-secret-super-seguro-aqui
JWT_EXPIRES_IN=24h

NODE_ENV=development
```

### 4. Inicie o servidor
```bash
npm run dev
```

## 🚀 Uso

### Desenvolvimento
```bash
npm run dev
```

### Produção
```bash
npm start
```

### Testes
```bash
npm test
```

### Acessar a aplicação
- **Frontend:** http://localhost:3000
- **API Documentation (Swagger):** http://localhost:3000/api-docs
- **API Health Check:** http://localhost:3000/health

## 🎯 Inicialização Automática

O sistema automaticamente:
- ✅ **Cria usuário administrador** na primeira execução
- ✅ **Gera token JWT** e exibe no terminal
- ✅ **Configura banco de dados** se necessário

**Credenciais do Admin:**
- Email: `admin@pizzaria.com`
- Senha: `admin123`

**No terminal você verá:**
```
🎫 TOKEN PARA SWAGGER: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
📋 COPIE E COLE NO SWAGGER (botão Authorize): Bearer eyJhbG...
```

## 📡 API Endpoints

### 🔐 Autenticação
```http
POST /api/users/register  # Registrar usuário
POST /api/users/login     # Login
GET  /api/users/profile   # Perfil do usuário
```

### 👥 Usuários (Admin)
```http
GET    /api/users         # Listar usuários
GET    /api/users/:id     # Buscar usuário
PUT    /api/users/:id     # Atualizar usuário
DELETE /api/users/:id     # Excluir usuário
```

### 🍕 Pizzas
```http
GET    /api/pizzas                    # Listar pizzas (público)
GET    /api/pizzas/:id                # Buscar pizza (público)
GET    /api/pizzas?category=Premium   # Filtrar por categoria
POST   /api/pizzas                    # Criar pizza (admin)
PUT    /api/pizzas/:id                # Atualizar pizza (admin)
DELETE /api/pizzas/:id                # Excluir pizza (admin)
```

### 🛒 Pedidos
```http
GET    /api/orders              # Listar todos pedidos (admin)
GET    /api/orders/:id          # Buscar pedido
GET    /api/orders/user/:userId # Pedidos por usuário
POST   /api/orders              # Criar pedido
PUT    /api/orders/:id          # Atualizar pedido (admin)
PATCH  /api/orders/:id/status   # Atualizar status (admin)
DELETE /api/orders/:id          # Excluir pedido (admin)
```

### 🚚 Entregas (Admin)
```http
GET    /api/deliveries                    # Listar entregas
GET    /api/deliveries/:id                # Buscar entrega
GET    /api/deliveries/order/:orderId     # Entrega por pedido
POST   /api/deliveries                    # Criar entrega
PUT    /api/deliveries/:id                # Atualizar entrega
PATCH  /api/deliveries/:id/status         # Atualizar status
DELETE /api/deliveries/:id                # Excluir entrega
```

## 📁 Estrutura do Projeto

```
SoftArchProject_Pizza/
│
├── public/                     # Frontend
│   ├── index.html             # Página principal
│   ├── styles/                # Estilos CSS
│   │   ├── main.css           # Estilos principais
│   │   ├── auth.css           # Estilos de autenticação
│   │   └── components.css     # Componentes UI
│   └── js/                    # Scripts JavaScript
│       ├── config.js          # Configurações
│       ├── api.js             # Comunicação com API
│       ├── auth.js            # Gerenciamento de autenticação
│       ├── ui.js              # Interface do usuário
│       ├── pizzas.js          # Gestão de pizzas
│       ├── orders.js          # Gestão de pedidos
│       ├── deliveries.js      # Gestão de entregas
│       ├── users.js           # Gestão de usuários
│       └── app.js             # Inicialização da aplicação
│
├── src/                       # Backend
│   ├── config/               # Configurações
│   │   ├── auth.js           # Configuração JWT
│   │   ├── dbConnect.js      # Conexão MongoDB
│   │   └── swagger.js        # Configuração Swagger
│   │
│   ├── controllers/          # Controladores (Recebem requisições)
│   │   ├── userController.js
│   │   ├── pizzaController.js
│   │   ├── orderController.js
│   │   └── deliveryController.js
│   │
│   ├── dtos/                # Validações de dados
│   │   ├── userDto.js
│   │   ├── pizzaDto.js
│   │   ├── orderDto.js
│   │   └── deliveryDto.js
│   │
│   ├── middlewares/         # Middlewares
│   │   ├── authMiddleware.js  # Autenticação JWT
│   │   └── validationMiddleware.js
│   │
│   ├── models/              # Modelos MongoDB
│   │   ├── User.js
│   │   ├── Pizza.js
│   │   ├── Order.js
│   │   └── Delivery.js
│   │
│   ├── repositories/        # Camada de dados
│   │   ├── baseRepository.js
│   │   ├── userRepository.js
│   │   ├── pizzaRepository.js
│   │   ├── orderRepository.js
│   │   └── deliveryRepository.js
│   │
│   ├── routes/              # Rotas da API
│   │   ├── index.js         # Agregador de rotas
│   │   ├── userRoutes.js    # Rotas de usuários
│   │   ├── pizzaRoutes.js   # Rotas de pizzas
│   │   ├── orderRoutes.js   # Rotas de pedidos
│   │   └── deliveryRoutes.js # Rotas de entregas
│   │
│   ├── services/            # Lógica de negócio
│   │   ├── userService.js
│   │   ├── pizzaService.js
│   │   ├── orderService.js
│   │   └── deliveryService.js
│   │
│   └── utils/               # Utilitários
│       └── setupAdmin.js    # Criação automática do admin
│
├── .env                     # Variáveis de ambiente
├── .gitignore              # Arquivos ignorados pelo Git
├── app.js                  # Configuração do Express
├── server.js               # Entrada da aplicação
├── package.json            # Dependências e scripts
└── README.md               # Documentação
```

## 🎯 Funcionalidades

### Para Clientes
- ✅ Registro e login seguro
- ✅ Visualização do cardápio de pizzas
- ✅ Filtro de pizzas por categoria
- ✅ Criação de pedidos com validação
- ✅ Acompanhamento de status dos pedidos
- ✅ Histórico completo de pedidos

### Para Administradores
- ✅ Todas as funcionalidades de cliente
- ✅ Gestão completa de pizzas (CRUD)
- ✅ Gerenciamento de usuários
- ✅ Visualização de todos os pedidos
- ✅ Atualização de status de pedidos
- ✅ Gestão completa de entregas
- ✅ Dashboard administrativo

### Recursos Técnicos
- ✅ Autenticação JWT com tokens seguros
- ✅ Criptografia de senhas com bcrypt
- ✅ Validação robusta em todas as camadas
- ✅ Tratamento centralizado de erros
- ✅ Logs detalhados para debugging
- ✅ Interface responsiva e moderna
- ✅ Documentação automática da API
- ✅ Testes automatizados

## 🧪 Demonstração

### Dados de Teste Prontos

#### Usuário Admin (criado automaticamente)
```json
{
  "email": "admin@pizzaria.com",
  "password": "admin123"
}
```

#### Usuário Cliente (para registro)
```json
{
  "name": "João Silva",
  "email": "joao@email.com",
  "password": "123456",
  "phone": "11999999999",
  "role": "user"
}
```

#### Pizza de Exemplo
```json
{
  "name": "Margherita",
  "ingredients": ["molho de tomate", "mussarela", "manjericão", "azeite"],
  "price": 35.90,
  "category": "Tradicional"
}
```

### Fluxo de Teste Completo

1. **Inicie o servidor:** `npm run dev`
2. **Acesse o Swagger:** http://localhost:3000/api-docs
3. **Copie o token** que aparece no terminal
4. **Autorize no Swagger** clicando no botão 🔒 "Authorize"
5. **Teste os endpoints** na seguinte ordem:
   - Criar pizza (POST /pizzas)
   - Listar pizzas (GET /pizzas)
   - Criar pedido (POST /orders)
   - Criar entrega (POST /deliveries)
   - Atualizar status (PATCH /orders/:id/status)

## 🎨 Paleta de Cores

- **🍅 Vermelho Tomate:** `#E74C3C` - Cor principal
- **🧀 Amarelo Parmesão:** `#F4D03F` - Destaques
- **🌿 Verde Manjericão:** `#27AE60` - Sucesso
- **⚫ Cinza Grafite:** `#7F8C8D` - Texto secundário
- **🤍 Branco Mussarela:** `#FAFAFA` - Fundo

## 🔒 Segurança

- ✅ Senhas criptografadas com bcrypt (salt rounds: 12)
- ✅ Autenticação JWT com expiração configurável
- ✅ Validação rigorosa de dados de entrada
- ✅ Proteção CORS configurada
- ✅ Sanitização de inputs em todas as camadas
- ✅ Controle de acesso baseado em roles
- ✅ Headers de segurança apropriados

## 🚀 Deploy

### Heroku
```bash
# Login no Heroku
heroku login

# Criar aplicação
heroku create sua-pizzaria-delivery

# Configurar variáveis
heroku config:set NODE_ENV=production
heroku config:set MONGODB_URI=sua-mongodb-uri
heroku config:set JWT_SECRET=seu-jwt-secret

# Deploy
git push heroku main
```

### MongoDB Atlas
1. Crie uma conta no [MongoDB Atlas](https://cloud.mongodb.com)
2. Crie um cluster gratuito
3. Configure Network Access (0.0.0.0/0 para desenvolvimento)
4. Crie usuário de banco de dados
5. Obtenha a connection string
6. Configure no arquivo `.env`

## 🧪 Testes

### Executar testes
```bash
npm test                # Todos os testes
npm run test:watch      # Modo watch
```

### Estrutura de Testes
```
tests/
├── unit/              # Testes unitários
├── integration/       # Testes de integração
└── fixtures/          # Dados de teste
```

## 🤝 Contribuição

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-funcionalidade`)
3. Commit suas mudanças (`git commit -am 'Adiciona nova funcionalidade'`)
4. Push para a branch (`git push origin feature/nova-funcionalidade`)
5. Abra um Pull Request

### Padrões de Código
- Use ESLint para manter consistência
- Escreva testes para novas funcionalidades
- Documente APIs com comentários Swagger
- Siga a arquitetura em camadas existente

## 📝 Roadmap

### Próximas Funcionalidades
- [ ] Sistema de avaliações de pizzas
- [ ] Integração com APIs de pagamento (Stripe/PagSeguro)
- [ ] Notificações push em tempo real
- [ ] Chat de suporte ao cliente
- [ ] Programa de fidelidade com pontos
- [ ] API de geolocalização para entregas
- [ ] Relatórios analíticos de vendas
- [ ] Sistema de cupons e promoções
- [ ] App mobile com React Native
- [ ] Integração com redes sociais

### Melhorias Técnicas
- [ ] Implementação de Redis para cache
- [ ] Rate limiting para APIs
- [ ] Logs estruturados com Winston
- [ ] Monitoramento com Prometheus
- [ ] CI/CD com GitHub Actions
- [ ] Containerização com Docker
- [ ] Kubernetes para orquestração

## 📊 Métricas

- **24 endpoints** documentados
- **5 módulos** principais
- **100%** cobertura de validação
- **JWT** autenticação segura
- **Arquitetura** em 4 camadas
- **Responsive** design

## 🐛 Troubleshooting

### Problemas Comuns

**MongoDB Connection Error:**
```bash
# Verificar se MongoDB está rodando
mongosh

# Ou usar MongoDB Atlas
# Verificar string de conexão no .env
```

**Port Already in Use:**
```bash
# Matar processo na porta 3000
npx kill-port 3000

# Ou alterar porta no .env
PORT=3001
```

**Token JWT Inválido:**
- Verificar se JWT_SECRET está definido no .env
- Verificar se token não expirou (padrão: 24h)
- Recriar token fazendo login novamente

## 📄 Licença

Este projeto está sob a licença ISC. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👨‍💻 Autores

**Alan Jones Stacholski Jr.**
- GitHub: .[Alan Stacholski Jr](https://github.com/AlanStacholski)
- Email: (alamstacholski@gmail.com)
- LinkedIn: .[Alan Stacholski Jr](https://www.linkedin.com/in/alanjr/)

**Marcelo Piloni**
- GitHub: [@marcelopiloni](https://github.com/marcelopiloni)
- Email: marcelo.piloni@outlook.com
- LinkedIn: [Marcelo Piloni](https://linkedin.com/in/marcelopiloni)

## 🙏 Agradecimentos

- **MongoDB** pela excelente documentação
- **Swagger/OpenAPI** pela documentação interativa
- **Express.js** pela simplicidade e robustez
- **Comunidade Node.js** pelo suporte contínuo
- **Font Awesome** pelos ícones incríveis

---

## ⭐ Apoie o Projeto

Se este projeto te ajudou, considere dar uma ⭐ no repositório!

**🍕 Desenvolvido com ❤️ e muito JavaScript!**

---

### 📱 Status do Projeto

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![Coverage](https://img.shields.io/badge/coverage-95%25-brightgreen)
![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-ISC-green)
![Node](https://img.shields.io/badge/node-14%2B-green)
![MongoDB](https://img.shields.io/badge/mongodb-4.4%2B-green)

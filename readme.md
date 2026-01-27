Este projeto foi criado como parte dos estudos para a certificação **Microsoft Azure Fundamentals (AZ-900)**.  
O objetivo é demonstrar como hospedar uma aplicação simples em **Azure App Service**, configurar **CI/CD com GitHub Actions** e habilitar **monitoramento com Application Insights**.

---

## 📖 Objetivos do Projeto
- Criar uma aplicação web simples (Flask/Node.js/HTML estático).
- Publicar no **Azure App Service** (PaaS).
- Automatizar o deploy com **GitHub Actions**.
- Ativar **Application Insights** para monitoramento.
- Documentar os conceitos do AZ-900 aplicados.

---

## 🛠️ Tecnologias Utilizadas
- **Azure App Service** (PaaS)
- **Azure Resource Groups**
- **GitHub Actions** (CI/CD)
- **Application Insights**
- Linguagem: Python (Flask) ou Node.js (Express)

---

## 📂 Estrutura do Repositório

az900-webapp/
│── app/           # Código da aplicação
│── docs/          # Documentação e resumos
│── .github/       # Workflows CI/CD
│── README.md      # Explicação do projeto

---

## 🚀 Como rodar localmente

### Pré-requisitos
- [Python 3.9+](https://www.python.org/downloads/) ou [Node.js](https://nodejs.org/)
- [Git](https://git-scm.com/)
- Conta no [Azure](https://azure.microsoft.com/free/)

### Passos
1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/az900-webapp.git
   cd az900-webapp/app
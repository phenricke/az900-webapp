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
- Linguagem: Python (Flask)

---

## 📂 Estrutura do Repositório
az900-webapp/
│── app/
│   ├── app.py              # Código principal da aplicação Flask
│   ├── requirements.txt    # Dependências da aplicação
│── .github/
│   └── workflows/
│       └── azure-webapps.yml   # Workflow gerado pelo Deployment Center
│── README.md

---

## 🚀 Como rodar localmente

### Pré-requisitos
- [Python 3.9+](https://www.python.org/downloads/) ou [Node.js](https://nodejs.org/)
- [Git](https://git-scm.com/)
- Conta no [Azure](https://azure.microsoft.com/free/)

### Passos
1. Clone o repositório:
   ```bash
   git clone https://github.com/phenricke/az900-webapp.git
   cd az900-webapp/app
2. 	Instale as dependências (Python/Flask):
pip install -r requirements.txt
3. 	Execute a aplicação:
python app.py
4. 	Acesse em:  (localhost in Bing)
- Acesse em: http://localhost:5000 (localhost in Bing)

---

## 🛠️ Provisionando recursos com Azure PowerShell
1. **Login no Azure**
   ```powershell
   Connect-AzAccount
2. **Criar Resource Group**
   ```powershell
   New-AzResourceGroup -Name rg-az900-webapp -Location "Brazil South"
3. **Criar App Service Plan**
   ````powershell
   New-AzAppServicePlan -Name plan-az900 `
  -ResourceGroupName rg-az900-webapp `
  -Location "Brazil South" `
  -Tier Basic`
4. **Criar App Service** 
   ```powershell
   New-AzWebApp -Name az900-webapp-pedro `
  -ResourceGroupName rg-az900-webapp `
  -Location "Brazil South" `
  -AppServicePlan plan-az900`
---

🔄 Configurando CI/CD com Deployment Center
1. Abra seu App Service.
2. Vá em Deployment Center.
3. Conecte sua conta GitHub.
4. Selecione:
• 	Organização (seu usuário GitHub).
• 	Repositório ().
• 	Branch ().
5. O Azure cria automaticamente o workflow em .github/workflows/azure-webapps.yml
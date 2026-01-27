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
   ```powershell
   New-AzAppServicePlan -Name plan-az900 `
  -ResourceGroupName rg-az900-webapp `
  -Location "Brazil South" `
  -Tier Basic

4. **Criar App Service** 
   ```powershell
   New-AzWebApp -Name az900-webapp-pedro `
  -ResourceGroupName rg-az900-webapp `
  -Location "Brazil South" `
  -AppServicePlan plan-az900
  ```

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

---

## 📈 Monitoramento e Logs

Para acompanhar a saúde da aplicação e detectar problemas de forma proativa, configure o **Application Insights** e os logs no Azure App Service.

### 🔎 Application Insights
1. No **Portal do Azure**, abra o App Service `az900-webapp-pedro`.
2. Vá em **Configurações → Application Insights**.
3. Clique em **Ativar**.
4. Crie ou vincule um recurso de Application Insights, por exemplo: ai-az900-webapp-pedro
- Região: Brazil South
- Resource Group: rg-az900-webapp
5. Salve e reinicie o App Service.

### 📊 Logs e Métricas
- **Log Stream**  
- Acesse **Monitoramento → Log Stream** para visualizar logs em tempo real da aplicação.

- **Configurações de Diagnóstico**  
- Vá em **Configurações → Configurações de Diagnóstico**.  
- Ative:
 - *Application Logging (Filesystem)* → nível Information.  
 - *Web Server Logging* → formato W3C.  
- Exemplo de nome para storage:  
 ```
 stlogsaz900pedro
 ```

- **Métricas**  
- Em **Monitoramento → Métricas**, crie gráficos para:
 - Requisições por segundo.  
 - Taxa de erros HTTP (4xx/5xx).  
 - Tempo médio de resposta.  
 - Consumo de CPU e memória.

- **Alertas**  
- No recurso `ai-az900-webapp-pedro`, vá em **Alertas → Nova regra de alerta**.  
- Exemplos:
 - `alerta-erros-az900` → dispara se erros > 5% em 5 minutos.  
 - `alerta-latencia-az900` → dispara se tempo médio > 2s.  
- Configure ação para enviar e-mail para sua conta.

---

## 🎯 Benefícios
- Visibilidade completa da saúde da aplicação.  
- Logs em tempo real para depuração.  
- Métricas e alertas automáticos para detectar falhas e gargalos.  
- Monitoramento contínuo com **Application Insights** integrado ao App Service.
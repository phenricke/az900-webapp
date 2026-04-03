# Azure Web App – Projeto AZ-900

Este projeto foi desenvolvido como parte dos estudos para a certificação **Microsoft Azure Fundamentals (AZ-900)**.  
O objetivo é demonstrar o provisionamento e a operação de uma aplicação web em **Azure App Service**, incluindo pipeline de **CI/CD com GitHub Actions** e monitoramento com **Application Insights**.

---

## Objetivos

- Implementar uma aplicação web simples (Flask).
- Publicar a aplicação no Azure App Service (PaaS).
- Configurar pipeline de CI/CD com GitHub Actions.
- Habilitar monitoramento com Application Insights.
- Consolidar conceitos práticos abordados no AZ-900.

---

## Tecnologias

- Azure App Service  
- Azure Resource Groups  
- GitHub Actions (CI/CD)  
- Application Insights  
- Python (Flask)

---

## Estrutura do Repositório

```
az900-webapp/
│── app/
│   ├── app.py
│   ├── requirements.txt
│── .github/
│   └── workflows/
│       └── azure-webapps.yml
│── README.md
```

---

## Execução Local

### Pré-requisitos

- Python 3.9+  
- Git  
- Conta no Azure  

### Passos

```bash
git clone https://github.com/phenricke/az900-webapp.git
cd az900-webapp/app
pip install -r requirements.txt
python app.py
```

A aplicação estará disponível em:
```
http://localhost:5000
```

---

## Provisionamento com Azure PowerShell

### Autenticação

```powershell
Connect-AzAccount
```

### Resource Group

```powershell
New-AzResourceGroup `
  -Name rg-az900-webapp `
  -Location "Brazil South"
```

### App Service Plan

```powershell
New-AzAppServicePlan `
  -Name plan-az900 `
  -ResourceGroupName rg-az900-webapp `
  -Location "Brazil South" `
  -Tier Basic
```

### Web App

```powershell
New-AzWebApp `
  -Name az900-webapp-pedro `
  -ResourceGroupName rg-az900-webapp `
  -Location "Brazil South" `
  -AppServicePlan plan-az900
```

---

## CI/CD com GitHub Actions

1. Acesse o recurso no Azure Portal  
2. Vá até **Deployment Center**  
3. Conecte sua conta do GitHub  
4. Configure:
   - Organização  
   - Repositório  
   - Branch  
5. O Azure cria automaticamente o workflow em:

```
.github/workflows/azure-webapps.yml
```

---

## Monitoramento

### Application Insights

1. Acesse o App Service no Azure Portal  
2. Vá até **Application Insights**  
3. Ative o recurso e associe:
   - Nome: ai-az900-webapp-pedro  
   - Região: Brazil South  
   - Resource Group: rg-az900-webapp  
4. Reinicie o App Service  

---

### Logs

**Log Stream**  
Monitoramento → Log Stream  

**Diagnóstico**

Ativar:
- Application Logging (Filesystem) – nível Information  
- Web Server Logging – formato W3C  

Exemplo de storage:
```
stlogsaz900pedro
```

---

### Métricas

- Requisições por segundo  
- Taxa de erro HTTP (4xx/5xx)  
- Tempo médio de resposta  
- Uso de CPU e memória  

---

### Alertas

- alerta-erros-az900 → erros > 5% em 5 minutos  
- alerta-latencia-az900 → latência média > 2s  

Configurar ação de notificação (e-mail)

---

## Considerações

A solução utiliza serviços PaaS para reduzir a sobrecarga operacional e simplificar o deploy. O uso de Application Insights permite centralizar métricas, logs e traces, facilitando análise de desempenho e diagnóstico de falhas.

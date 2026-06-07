# Análise de Cancelamento de Contratos (Churn)

Este projeto foi desenvolvido com o objetivo de analisar uma base de dados de 50 mil clientes para identificar os principais motivos de cancelamento de assinaturas (Churn) e preparar os dados tratados para a criação de um dashboard no Power BI.

O cenário simula um desafio real de retenção de clientes, algo altamente relevante para o modelo de negócios de infoprodutos e assinaturas da **Hotmart**.

## Objetivo do Projeto

1. **Identificar Gargalos:** Descobrir em quais pontos do negócio os clientes mais cancelam as assinaturas.
2. **Tratamento de Dados:** Limpar e padronizar a base de dados utilizando Python e Pandas.
3. **Engenharia de Recursos (Regras de Negócio):** Criar novas colunas de alerta utilizando lógica de programação (`if/else` e loops `for`) para categorizar o risco de cada cliente.
4. **Preparação para o Power BI:** Exportar um arquivo CSV limpo e otimizado para a criação de visuais e indicadores (KPIs).

## Tecnologias Utilizadas

- **Python** (Lógica de programação, estruturas condicionais e repetição)
- **Pandas** (Leitura, limpeza, agrupamento e exportação de dados)

## Principais Insights Descobertos (Análise de Dados)

Ao rodar o script Python, o cruzamento dos dados revelou três padrões críticos de cancelamento:

* **Contratos Mensais:** A taxa de cancelamento no plano mensal é de 100%. Os clientes que optam por essa modalidade não renovam após o primeiro mês.
* **Atendimento (Callcenter):** Clientes que realizam mais de 4 ligações para o suporte cancelam o serviço em 100% dos casos, indicando problemas críticos não resolvidos.
* **Inadimplência:** Clientes com mais de 20 dias de atraso no pagamento têm suas assinaturas canceladas automaticamente.

## Lógica de Tratamento Implementada

O script realiza os seguintes passos de forma sequencial:
1. **Remoção de Identificadores:** Elimina a coluna `CustomerID`, que não possui valor estatístico para a análise.
2. **Tratamento de Nulos:** Remove linhas com dados ausentes (`.dropna()`) para garantir a consistência das médias.
3. **Conversão de Tipos:** Transforma a coluna `cancelou` em número inteiro (0 para ativo, 1 para cancelado) para facilitar cálculos de taxa no Power BI.
4. **Criação de Alertas Customizados:** Utiliza um loop `for` e `if/else` para analisar linha por linha e classificar os clientes ativos em **"Alto Risco"** caso cumpram os critérios críticos de atraso ou ligações no suporte.

## Como Executar o Script

1. Certifique-se de ter o arquivo `cancelamentos.csv` na mesma pasta do script.
2. Execute o arquivo Python no terminal:
   ```bash
   python analise_cancelamentos.py

# Telecom X - Análise de Evasão de Clientes

## Objetivo
Identificar os principais fatores que levam à evasão de clientes (churn) na Telecom X através de análise exploratória de dados.

## Dados
- Fonte: API TelecomX (https://github.com/alura-cursos/challenge2-data-science)
- Período: Últimos 12 meses
- Variáveis: 21 colunas incluindo dados demográficos, serviços contratados e informações de pagamento

## Principais Insights
1. Clientes com contratos mensais tem taxa de churn 3x maior que anual
2. Ausência de serviços como suporte técnico aumenta em 40% a chance de cancelamento
3. Clientes idosos tem menor taxa de evasão que jovens adultos

## Como Executar
1. Clone o repositório
2. Instale os requisitos: `pip install -r requirements.txt`
3. Execute o notebook: `jupyter notebook Telecom_Churn_Analysis.ipynb`

## Exemplo de Visualização
![Churn por Tipo de Contrato](images/churn_by_contract.png)
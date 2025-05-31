Análise de Evasão de Clientes (Churn)
=====================================

Objetivo
--------

Identificar e analisar os principais fatores que levam à evasão de clientes (churn) na Telecom X, com o propósito de:

-   Reduzir a taxa de cancelamento em 25% nos próximos 6 meses

-   Desenvolver estratégias de retenção baseadas em dados

-   Otimizar a alocação de recursos para clientes de alto risco

Dados
-----

### Fonte e Estrutura

-   **Origem**: API TelecomX ([dados disponíveis aqui](https://github.com/alura-cursos/challenge2-data-science))

-   **Período**: Dados dos últimos 12 meses (01/2023 a 12/2023)

-   **Amostra**: 7.043 clientes ativos e cancelados

-   **Variáveis Principais**:

    -   **Dados Demográficos**: Gênero, idade, estado civil

    -   **Serviços**: Tipo de internet, TV, linhas telefônicas

    -   **Contrato**: Tipo, tempo de permanência, forma de pagamento

    -   **Financeiro**: Cobrança mensal, total gasto, forma de cobrança

### Dicionário de Dados

| Variável | Tipo | Descrição |
| --- |  --- |  --- |
| customerID | Texto | Identificador único do cliente |
| --- |  --- |  --- |
| gender | Categórico | Masculino/Feminino |
| SeniorCitizen | Binário | 1 para clientes >65 anos |
| tenure | Numérico | Meses como cliente |
| Contract | Categórico | Tipo de contrato (Mensal/Anual/Bianual) |

Principais Insights
-------------------

### 1\. Fatores Críticos de Churn

-   **Contratos Mensais**: 43% de evasão vs 11% em anuais

-   **Serviços Adicionais**:

    -   Clientes sem suporte técnico: 36% evasão

    -   Com suporte técnico: 12% evasão

-   **Idade**:

    -   Jovens (18-30): 32% evasão

    -   Idosos (>65): 18% evasão

### 2\. Padrões Financeiros

| Métrica | Clientes Fiéis | Clientes que Evadiram | Diferença |
| --- |  --- |  --- |  --- |
| Gasto Médio Mensal | R$61,90 | R$74,04 | +19,6% |
| --- |  --- |  --- |  --- |
| Tempo Médio | 17,9 meses | 10,1 meses | \-43,6% |

### 3\. Segmentação por Serviços

![Distribuição de Churn por Serviços](https://images/churn_by_service.png)
\*Clientes com 3+ serviços tem apenas 8% de evasão vs média de 26%\*

Metodologia
-----------

### Fluxo de Análise

1.  **Preparação dos Dados**

    -   Limpeza de valores nulos

    -   Transformação de variáveis categóricas

    -   Criação de métricas derivadas

2.  **Análise Exploratória**

    -   Estatísticas descritivas

    -   Testes de hipóteses

    -   Matriz de correlação

3.  **Visualização**

    -   Gráficos comparativos

    -   Análise segmentada

python

Copy

Download

```
\# Exemplo de código para análise básica
sns.boxplot(x\='Contract', y\='MonthlyCharges', hue\='Churn', data\=df)
plt.title('Distribuição de Valores por Tipo de Contrato')
```

Como Executar
-------------

### Pré-requisitos

-   Python 3.8+

-   Jupyter Notebook

-   Bibliotecas listadas em `requirements.txt`

### Passo a Passo

1.  Clone o repositório:

bash

Copy

Download

```
git clone https://github.com/seuuser/telecom-churn-analysis.git
```

2.  Instale as dependências:

bash

Copy

Download

```
pip install \-r requirements.txt
```

3.  Execute a análise principal:

bash

Copy

Download

```
jupyter notebook Telecom\_Churn\_Analysis.ipynb
```

Recomendações Estratégicas
--------------------------

### Ações Imediatas

1.  **Conversão de Contratos**

    -   Oferecer desconto de 15% para migração de mensal para anual

2.  **Pacotes de Serviços**

    -   Criar bundles com suporte técnico incluso

3.  **Programa de Fidelidade**

    -   Benefícios progressivos por tempo de permanência

### Monitoramento

-   Dashboard mensal com:

    -   Taxa de churn por segmento

    -   Eficácia das ações de retenção

    -   ROI das iniciativas implementadas

Próximos Passos
---------------

1.  Desenvolver modelo preditivo de churn

2.  Implementar sistema de alerta para clientes de risco

3.  Testar A/B testing com diferentes ofertas

Contato
-------

Para mais informações ou colaborações:

-   **Email**: [analytics@telecomx.com](https://mailto:analytics@telecomx.com/)

-   **LinkedIn**: linkedin.com/in/telecomx-analytics
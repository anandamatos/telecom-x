Análise de Evasão de Clientes (Churn) - Telecom X
=================================================

* * * *

🎯 Objetivo do Projeto
----------------------

Este projeto tem como objetivo principal **identificar e analisar os principais fatores que contribuem para a evasão de clientes (*churn*) na Telecom X**. Com base nas análises, buscaremos:

-   **Reduzir a taxa de cancelamento** em 25% nos próximos 6 meses.
-   **Desenvolver estratégias de retenção** eficazes, baseadas em *insights* de dados.
-   **Otimizar a alocação de recursos** para ações direcionadas a clientes de alto risco.

* * * *

📊 Dados
--------

### Fonte e Estrutura

Os dados foram obtidos de uma API pública da TelecomX ([link para os dados](https://github.com/alura-cursos/challenge2-data-science)), compreendendo informações de **7.043 clientes** (ativos e cancelados) no período de **janeiro a dezembro de 2023**.

As variáveis principais incluem:

-   **Dados Demográficos**: Gênero, idade (SeniorCitizen), situação familiar (Partner, Dependents).
-   **Serviços Contratados**: Tipo de serviço de internet, TV, streaming, telefone, serviços adicionais (segurança online, backup, suporte técnico).
-   **Detalhes do Contrato**: Tipo de contrato (mensal, anual, bianual), tempo de permanência (*tenure*), método de pagamento.
-   **Informações Financeiras**: Cobrança mensal (*MonthlyCharges*), total gasto (*TotalCharges*), fatura digital (*PaperlessBilling*).
-   **Status de Evasão**: `Churn` (indica se o cliente cancelou o serviço).

### Dicionário de Dados

| Variável | Tipo | Descrição |
| :-- |  :-- |  :-- |
| `customerID` | Texto | Identificador único do cliente. |
| `gender` | Categórico | Gênero do cliente (Masculino/Feminino). |
| `SeniorCitizen` | Binário | Indica se o cliente tem 65 anos ou mais (1=Sim). |
| `tenure` | Numérico | Número de meses como cliente na empresa. |
| `Contract` | Categórico | Tipo de contrato (Mensal, Um Ano, Dois Anos). |
| `MonthlyCharges` | Numérico | Valor da cobrança mensal. |
| `TotalCharges` | Numérico | Valor total cobrado do cliente. |
| `Churn` | Binário | Indica se o cliente evadiu (Yes/No). |

* * * *

📈 Principais Insights
----------------------

A análise revelou padrões claros de comportamento e características dos clientes que evadem:

### 1\. Fatores Críticos de Evasão

-   **Contratos Mensais**: A taxa de evasão para contratos mensais é de **43%**, significativamente maior do que a observada em contratos anuais (11%).
-   **Serviços Adicionais**: Clientes sem **Suporte Técnico** apresentam uma taxa de evasão de **36%**, enquanto aqueles com o serviço têm apenas **12%** de churn. A presença de múltiplos serviços (3+) reduz o churn para **8%**.
-   **Idade**: Clientes mais jovens (18-30 anos) mostram uma taxa de evasão de **32%**, contrastando com 18% para clientes mais velhos (>65 anos).

### 2\. Padrões Financeiros e Tempo de Permanência

| Métrica | Clientes que Permaneceram | Clientes que Evadiram | Diferença |
| :-- |  :-- |  :-- |  :-- |
| **Gasto Mensal Médio** | R$ 61,90 | R$ 74,04 | **+19,6%** |
| **Tempo Médio de Contrato** | 17,9 meses | 10,1 meses | **\-43,6%** |

-   Clientes que evadem têm gastos mensais mais altos e um tempo de permanência consideravelmente menor.

### 3\. Impacto dos Serviços na Evasão

* * * *

-   A imagem ilustra que a adesão a múltiplos serviços está inversamente relacionada à taxa de evasão.

* * * *

🛠️ Metodologia
---------------

A análise seguiu um fluxo estruturado:

1.  **Preparação dos Dados**:

    -   Remoção de duplicatas por `customerID`.
    -   Desaninhamento de estruturas JSON (`customer`, `phone`, `internet`, `account`).
    -   Padronização dos nomes das colunas.
    -   Tratamento de valores nulos e inconsistências (conversão de tipos de dados, preenchimento de ausentes com medianas/modas).
    -   Criação de métricas derivadas (e.g., `Contas_Diarias`, `ValorMedioMensal`, `TipoCliente`, `TotalServicos`).
    -   Transformação de variáveis categóricas para formato numérico/padronizado (`Yes/No` para `1/0`).
2.  **Análise Exploratória (EDA)**:

    -   Cálculo de estatísticas descritivas para variáveis numéricas e distribuições de frequência para categóricas.
    -   Análise comparativa detalhada entre clientes que evadiram e os que permaneceram.
    -   Criação de matrizes de correlação para identificar relações entre variáveis.
    -   Utilização de testes estatísticos (e.g., Teste t de Student) para validar diferenças entre grupos.
3.  **Visualização de Dados**:

    -   Gráficos comparativos (barras, caixas, histogramas) para ilustrar distribuições e relações.
    -   Análise segmentada para destacar o impacto de diferentes características na evasão.



Python

```
# Exemplo de código para análise e visualização
import seaborn as sns
import matplotlib.pyplot as plt

# Padronize 'Churn' para 0 e 1 antes da visualização, se não já estiver
# df['Churn'] = df['Churn'].map({'Yes': 1, 'No': 0})

# Exemplo: Distribuição de Cobrança Mensal por Tipo de Contrato e Churn
sns.boxplot(x='Contract', y='Charges.Monthly', hue='Churn', data=df)
plt.title('Distribuição de Cobrança Mensal por Tipo de Contrato e Status de Churn')
plt.xlabel('Tipo de Contrato')
plt.ylabel('Cobrança Mensal (R$)')
plt.show()

```

* * * *

🚀 Como Executar
----------------

Para replicar a análise e os *insights* deste projeto:

### Pré-requisitos

-   **Python 3.8+**
-   **Jupyter Notebook**
-   **Bibliotecas Python**: As dependências estão listadas no arquivo `requirements.txt`.

### Passo a Passo

1.  **Clone o repositório**:Bash

    ```
    git clone https://github.com/seuuser/telecom-churn-analysis.git
    cd telecom-churn-analysis

    ```

2.  **Instale as dependências**:Bash

    ```
    pip install -r requirements.txt

    ```

3.  **Execute o Jupyter Notebook**:Bash

    ```
    jupyter notebook Telecom_Churn_Analysis.ipynb

    ```
    Abra o arquivo `Telecom_Churn_Analysis.ipynb` no seu navegador para visualizar e executar todo o código de análise.

* * * *

💡 Recomendações Estratégicas
-----------------------------

Com base nos *insights* extraídos, propomos as seguintes ações para a Telecom X:

### Ações Imediatas

1.  **Programa de Conversão de Contratos**:

    -   **Incentivo**: Oferecer um desconto de **15%** na mensalidade para clientes com contrato mensal que migrarem para planos anuais ou bianuais.
    -   **Foco**: Priorizar clientes nos primeiros 6 meses de contrato e/ou com cobranças mensais elevadas.
2.  **Bundles de Serviços com Suporte Técnico**:

    -   **Oferta**: Criar pacotes de serviços que **incluam automaticamente** o suporte técnico e outros serviços adicionais (segurança, backup).
    -   **Estratégia**: Posicionar esses pacotes como soluções completas, enfatizando a segurança e conveniência para reduzir a percepção de custo adicional.
3.  **Programa de Fidelidade Progressivo**:

    -   **Benefícios**: Implementar um programa de fidelidade que ofereça benefícios crescentes (descontos, upgrades, brindes) com base no tempo de permanência do cliente.
    -   **Engajamento**: Focar na comunicação ativa com clientes nos primeiros 6-12 meses para reforçar o valor do serviço e incentivar a permanência.

### Monitoramento Contínuo

-   **Dashboard Mensal**: Desenvolver um dashboard que monitore mensalmente:
    -   A taxa de churn por segmento de cliente (tipo de contrato, serviços, tempo de permanência).
    -   A eficácia das campanhas e ações de retenção implementadas.
    -   O Retorno sobre o Investimento (ROI) de cada iniciativa de retenção.

* * * *

⏭️ Próximos Passos
------------------

Para aprofundar as estratégias de retenção:

1.  **Desenvolver Modelo Preditivo de Churn**: Construir um modelo de Machine Learning para identificar clientes com alta probabilidade de evasão antes que cancelem.
2.  **Implementar Sistema de Alerta**: Criar um sistema automatizado para notificar as equipes de relacionamento quando um cliente de alto risco for identificado pelo modelo preditivo.
3.  **Testes A/B de Ofertas**: Realizar testes A/B com diferentes ofertas e comunicações para otimizar as campanhas de retenção.

* * * *

📧 Contato
----------

Para dúvidas, sugestões ou colaborações, entre em contato:

-   **Email**: analytics@telecomx.com
-   **LinkedIn**: [linkedin.com/in/telecomx-analytics](https://www.google.com/search?q=https://www.linkedin.com/in/telecomx-analytics)
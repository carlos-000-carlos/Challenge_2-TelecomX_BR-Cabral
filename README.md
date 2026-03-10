# 📊 Análise de Churn - TelecomX BR

Este projeto consiste numa análise exploratória de dados (EDA) focada na evasão de clientes (Churn) de uma empresa de telecomunicações. O objetivo é identificar padrões de comportamento e variáveis críticas que influenciam a retenção de clientes, utilizando o dataset extraído da API TelecomX.

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python
* **Bibliotecas de Manipulação:** Pandas, JSON, Requests.
* **Visualização de Dados:** Matplotlib, Seaborn, Plotly Express.
* **Ambiente de Desenvolvimento:** Google Colab.

## 📂 Estrutura do Projeto

O pipeline de análise foi estruturado nas seguintes etapas técnicas:

### 1. Extração de Dados (Data Ingestion)
Os dados foram consumidos via API externa em formato JSON.
* **Procedimento:** Requisição através da biblioteca `requests` e tratamento de strings JSON com `json.loads`.
* **Normalização:** Utilização da função `pd.json_normalize` para transformar a estrutura hierárquica (aninhada) do JSON num DataFrame tabular, facilitando a manipulação dos dados.

### 2. Transformação e Limpeza (Data Wrangling)
Nesta fase, os dados foram saneados para garantir a qualidade da análise:
* **Tipagem de Dados:** Conversão de colunas como `account_Charges_Total` para o formato numérico (`float`) e tratamento de valores nulos.
* **Feature Engineering:** Criação da nova variável `contas_diarias` (calculada como `valor_mensal / 30`) para obter uma granularidade maior sobre o custo por cliente.
* **Localização:** Tradução de cabeçalhos e categorias de inglês para português para melhor compreensão do negócio.
* **Filtros de Qualidade:** Remoção de registos inconsistentes, como novos clientes com tempo de contrato zero e cobrança total não preenchida.

### 3. Análise Exploratória e Visualização
A análise focou-se em encontrar correlações estatísticas entre os perfis dos clientes e a taxa de cancelamento:
* **Distribuição de Churn:** Visualização da proporção entre clientes ativos e aqueles que cancelaram o serviço.
* **Matriz de Correlação (Heatmap):** Aplicação de `One-Hot Encoding` em variáveis categóricas para gerar um mapa de calor, identificando os principais drivers de Churn (como o impacto do tipo de contrato).
* **Análise de Tendências:** Gráficos de dispersão com linhas de tendência (OLS) para validar a relação entre o custo diário e a evasão.

## 📈 Principais Insights

* **Fidelização:** O `tempo_de_contrato` demonstrou uma correlação negativa com o Churn, indicando que quanto maior o tempo de casa, menor a probabilidade de cancelamento.
* **Fatores de Risco:** Clientes com contratos de renovação mensal e que utilizam métodos de pagamento manuais (ex: Cheque Eletrónico) apresentam um risco de evasão significativamente superior.

## 🚀 Como Executar

1. Clone o repositório:
   
   `git clone [https://github.com/teu-usuario/teu-repositorio.git](https://github.com/teu-usuario/teu-repositorio.git)`

2. Abra o arquivo TelecomX_BR.ipynb no Google Colab ou Jupyter Notebook.

3. Instale as dependências necessárias:

   `pip install pandas seaborn plotly requests`

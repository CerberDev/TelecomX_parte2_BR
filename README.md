# **Desafio 2: Modelagem Preditiva de Churn com Machine Learning**

## 🎯 1. Objetivo do Projeto

Este projeto é a segunda fase da análise de evasão de clientes (Churn) da TelecomX. O objetivo principal é desenvolver, treinar e avaliar modelos de Machine Learning capazes de **prever com precisão quais clientes têm a maior probabilidade de cancelar seus serviços**.

Partindo dos dados já limpos e tratados na fase anterior, este notebook foca na aplicação de técnicas de pré-processamento avançado, treinamento de múltiplos algoritmos e, crucialmente, na interpretação dos resultados para extrair insights que possam ser transformados em ações de negócio.

## ⚙️ 2. Pipeline de Machine Learning

O processo de modelagem seguiu um pipeline robusto para garantir a criação de um modelo preditivo eficaz e confiável.

### 2.1. Preparação Final dos Dados

  - **Carga de Dados**: O ponto de partida foi o arquivo `telecom_churn_tratado.csv`, contendo os dados já limpos e enriquecidos da fase 1.
  - **Codificação de Variáveis (One-Hot Encoding)**: As variáveis categóricas restantes (como `Tipo_Contrato`) foram transformadas em formato numérico através do One-Hot Encoding, tornando o dataset 100% compatível com algoritmos de Machine Learning.

### 2.2. Divisão e Balanceamento

  - **Divisão em Treino e Teste**: O dataset foi dividido em 70% para treino e 30% para teste. A técnica de **estratificação** foi utilizada para garantir que a proporção original de evasão fosse mantida em ambos os conjuntos, assegurando uma avaliação justa do modelo.
  - **Tratamento de Desbalanceamento (SMOTE)**: Foi identificado um desbalanceamento de classes (73% de não-evasão vs. 27% de evasão). Para corrigir isso, a técnica **SMOTE (Synthetic Minority Over-sampling Technique)** foi aplicada **apenas no conjunto de treino**, criando dados sintéticos da classe minoritária e permitindo que o modelo aprendesse os padrões de ambos os grupos de forma equilibrada.

### 2.3. Padronização de Features (Scaling)

  - **StandardScaler**: As variáveis numéricas foram padronizadas (transformadas para ter média 0 e desvio padrão 1). Esta etapa é essencial para o bom desempenho de modelos sensíveis à escala, como a Regressão Logística.

## 🤖 3. Modelos Desenvolvidos e Avaliação

Dois modelos com características distintas foram treinados e avaliados para resolver o problema de classificação.

1.  **Regressão Logística**: Um modelo linear, rápido e altamente interpretável. Serviu como um excelente baseline.
2.  **Random Forest**: Um modelo de ensemble baseado em árvores, conhecido por sua alta performance e robustez.

### Resultados da Avaliação

Ambos os modelos se mostraram promissores. Na configuração inicial, a **Regressão Logística** apresentou um desempenho ligeiramente superior, alcançando um **Recall de 63%** para a classe de evasão e um **AUC de 0.83**.

  - **Métrica Chave (Recall)**: O foco principal da avaliação foi o **Recall**, que mede a capacidade do modelo de "capturar" os clientes que de fato iriam evadir. Um alto recall é crucial para a eficiência de uma campanha de retenção.

## 📈 4. Análise de Relevância das Variáveis

A interpretação dos modelos nos permitiu identificar e quantificar os fatores mais impactantes na previsão de evasão.

#### **Principais Fatores Preditivos (Random Forest)**

1.  **Meses de Contrato**: A variável com maior poder preditivo geral.
2.  **Fatura Total**: O gasto acumulado do cliente.
3.  **Método de Pagamento (Cheque Eletrônico)**: Um forte indicador de risco.

#### **Principais Fatores de Risco e Retenção (Regressão Logística)**

  - **Fatores de Risco**: Contrato "Mês a Mês", Internet de "Fibra Óptica" e pagamento com "Cheque Eletrônico".
  - **Fatores de Retenção**: "Meses de Contrato", contratos de "Dois Anos" e possuir "Suporte Técnico".

## 💡 5. Conclusão e Próximos Passos

A análise confirma que é possível prever a evasão de clientes com um bom grau de precisão. O modelo de **Regressão Logística** provou ser um baseline forte e eficaz.

Como próximo passo, recomenda-se um **processo de otimização de hiperparâmetros** no modelo **Random Forest**, que possui um potencial de desempenho ainda maior e pode se tornar a solução final a ser implementada em produção para guiar as estratégias de retenção da TelecomX.

## 💻 6. Como Executar o Projeto

### Pré-requisitos

  - Python 3.x
  - Bibliotecas:
      - Pandas
      - Scikit-learn
      - Imbalanced-learn
      - Matplotlib
      - Seaborn
      - Jupyter Notebook

### Instalação

Clone o repositório e instale as dependências:

```bash
git clone https://github.com/CerberDev/TelecomX_parte2_BR.git
cd TelecomX_parte2_BR
pip install -r requirements.txt
```

### Execução

O projeto está contido no notebook `NomeDoNotebookDeModelagem.ipynb`. Para executá-lo, inicie o Jupyter em seu terminal:

```bash
jupyter notebook NomeDoNotebookDeModelagem.ipynb
```

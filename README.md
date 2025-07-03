# Projeto: Classificação de Inadimplentes em Empréstimos de Automóveis

## Visão Geral
Este projeto visa desenvolver um modelo de classificação para identificar clientes inadimplentes em uma empresa de empréstimo de automóveis. Atualmente, a análise é feita manualmente, sendo demorada e imprecisa. Utilizaremos técnicas de validação de modelos e métricas de avaliação para criar uma solução mais eficiente.

## Passos do Projeto

### 1. Classificação: Validação de Modelos e Métricas
**Objetivo**: Classificar clientes em adimplentes (0) e inadimplentes (1) usando dados históricos.

### 2. Criando um Modelo Inicial
- Importamos bibliotecas e carregamos os dados
- Separamos os dados em features (X) e target (y)
- Utilizamos uma Árvore de Decisão como modelo inicial
- Avaliamos a acurácia inicial (100%), indicando overfitting

### 3. Validando o Modelo
- Dividimos os dados em conjuntos de treino, validação e teste:
  - 70% treino
  - 15% validação
  - 15% teste
- Aplicamos estratificação para manter proporção das classes
- Limitamos a profundidade da árvore para reduzir overfitting

### 4. Avaliando o Modelo
- Utilizamos matriz de confusão para visualizar desempenho:
  - Verdadeiros Positivos (TP): Inadimplentes corretamente identificados
  - Falsos Positivos (FP): Adimplentes classificados como inadimplentes
  - Falsos Negativos (FN): Inadimplentes classificados como adimplentes
  - Verdadeiros Negativos (TN): Adimplentes corretamente identificados

### 5. Métricas de Avaliação
Principais métricas utilizadas:
- **Acurácia**: (TP + TN) / Total
- **Precisão**: TP / (TP + FP) - Qualidade das previsões positivas
- **Recall (Sensibilidade)**: TP / (TP + FN) - Capacidade de identificar positivos reais
- **F1-Score**: Média harmônica entre precisão e recall
- **Curva ROC**: Relação entre TPR (Recall) e FPR
- **AUC**: Área sob a curva ROC

### 6. Validação Cruzada
**KFold**:
- Divide os dados em K partes (dobras)
- Treina K vezes com diferentes combinações de treino/validação
- Calcula médias das métricas

**Estratificação**:
- Mantém proporção de classes em cada dobra
- Especialmente importante para classes desbalanceadas

### 7. Balanceamento de Dados
**Problema**: Classe inadimplente é minoritária
**Solução**: Oversampling com SMOTE
- Gera amostras sintéticas da classe minoritária
- Cria pipeline com balanceamento e modelo

### 8. Testando o Modelo
- Avaliação final no conjunto de teste separado inicialmente
- Métricas reportadas:
  - Acurácia
  - Precisão
  - Recall
  - F1-Score
  - AUC

## Resultados
O modelo final demonstrou:
- Alto recall para inadimplentes (identificação de risco)
- Boa precisão para minimizar falsos positivos
- AUC > 0.85 indicando boa capacidade discriminativa

## Como Executar
1. Instale dependências: pandas, scikit-learn, imbalanced-learn
2. Execute o notebook `Classificação - Validação e métricas.ipynb`
3. Ajuste parâmetros conforme necessidade

## Próximos Passos
- Testar outros algoritmos (Random Forest, XGBoost)
- Otimizar hiperparâmetros
- Implementar sistema em produção
- Monitorar desempenho contínuo

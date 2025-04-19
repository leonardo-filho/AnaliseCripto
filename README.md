🧠 Projeto: Análise e Detecção de Anomalias em Transações Ethereum
📌 Descrição Geral
Este projeto tem como objetivo aplicar técnicas de Análise Exploratória de Dados (EDA) e Detecção de Anomalias a um dataset de transações da blockchain Ethereum, com foco na identificação de comportamentos suspeitos que podem estar relacionados a fraudes, lavagem de dinheiro ou manipulação de tokens.

O trabalho é dividido em etapas que vão desde a inspeção e limpeza dos dados até a aplicação e comparação de diferentes algoritmos de detecção de anomalias.

🗂️ Dados Utilizados
Fonte: Arquivo ethereum_transactions.csv.csv

Atributos principais utilizados:

Sent tnx: número de transações enviadas

Received Tnx: número de transações recebidas

Avg min between sent tnx: média de minutos entre envios

Time Diff between first and last (Mins): tempo total de atividade

ERC20 avg val sent: valor médio enviado em tokens ERC20

Target real para avaliação supervisionada: is_fraud

🔍 Etapas do Projeto
1. Análise Exploratória de Dados (EDA)
Cálculo de estatísticas descritivas

Análise de valores ausentes (NaNs)

Geração de histogramas, boxplots e heatmaps

Identificação visual de outliers e padrões extremos

2. Criação de um método baseline (threshold)
Definição manual de um limiar (threshold) sobre a variável Sent tnx

Aplicação de uma função para marcar registros como anômalos

Visualização no histograma com linha de corte

Avaliação com classification_report comparando com o rótulo is_fraud

3. Modelagem com Isolation Forest
Pré-processamento: remoção de NaNs, seleção de features

Aplicação do modelo IsolationForest com contamination estimado

Avaliação com métricas de classificação

Visualização da matriz de confusão

4. Modelagem com DBSCAN
Clusterização baseada em densidade (eps=3, min_samples=5)

Conversão de labels do DBSCAN para flag binária de anomalia

Visualização dos clusters via scatterplot (Sent tnx vs ERC20 avg val sent)

Avaliação com classification_report e matriz de confusão

📊 Comparativo Final dos Métodos
Um resumo quantitativo foi gerado com o número de anomalias detectadas por cada método:


Método	Número de Anomalias
Baseline (Threshold)	116
Isolation Forest	147
DBSCAN	3080
🧪 Métricas Relevantes
O Isolation Forest teve melhor performance geral, com recall de 97% para fraudes e acurácia de 97%.

O Baseline foi preciso (100%) mas com recall menor (81%), sendo útil como referência simples.

O DBSCAN apresentou recall baixo (5%) e alto número de falsos positivos, sugerindo sobreajuste ou inadequação dos parâmetros.

🛠️ Ferramentas Utilizadas
Python 3.11

Bibliotecas: pandas, numpy, matplotlib, seaborn, scikit-learn

Técnicas: Detecção de anomalias, visualização de dados, avaliação com métricas supervisionadas

🎯 Objetivos Futuros
Normalização e padronização dos dados antes dos modelos

Exploração de outros algoritmos (LOF, Autoencoder)

Análise temporal e por endereço

Integração com APIs da blockchain para enriquecimento dos dados

✅ Conclusão
Este projeto demonstrou, de forma prática e interpretável, como utilizar técnicas de Machine Learning não supervisionado para detectar padrões de comportamento atípico em transações financeiras de criptomoedas. É um estudo aplicável a contextos como compliance, auditoria, segurança e prevenção à lavagem de dinheiro.

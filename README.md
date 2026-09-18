# Projeto de Aprendizagem de Máquina (ADS033) — 2026/2

## Da Base de Dados à Decisão: Análise de Severidade em Rodovias Federais

### 1. Visão Geral
Este repositório contém o desenvolvimento prático do Projeto Acadêmico da disciplina de Aprendizagem de Máquina (IESB Asa Sul / ADSDM2C), sob orientação do Prof. Rodrigo Gonçalves.

O projeto utiliza a base pública consolidada de **Ocorrências de Acidentes de Trânsito da Polícia Rodoviária Federal (PRF)** de 2025 (72.529 registros e 30 atributos) para prever a severidade de sinistros viários (`alvo_grave`: 1 para ocorrências com mortos ou feridos graves, 0 para danos materiais e feridos leves).

### 2. Estrutura do Repositório
* `AUTORES.md`: Divisão formal das responsabilidades técnicas de cada integrante.
* `requirements.txt`: Declaração de bibliotecas e versões para reprodutibilidade.
* `notebooks/`: Cadernos Jupyter/Colab numerados sequencialmente na ordem de execução:
  * `01_eda_e_baseline.ipynb`: Preparação, auditoria, análise exploratória interativa e baseline.
  * `02_clusterizacao_kmeans.ipynb`: Agrupamento não supervisionado dos trechos viários.
  * `03_modelos_supervisionados_e_avaliacao.ipynb`: Modelos supervisionados, validação cruzada e recomendação de produção.

### 3. Como Reproduzir no Google Colab
1. Certifique-se de que o arquivo `datatran2025.csv` está salvo na sua pasta do Google Drive em `MyDrive/base_compartilhada/`.
2. Abra os notebooks na ordem numérica indicada dentro do Google Colab.
3. Conecte seu Drive na Etapa 1 de cada notebook (`drive.mount('/content/drive')`).
4. Execute `Ambiente de Execução → Reiniciar sessão e executar tudo`. Todos os notebooks utilizam sementes aleatórias fixadas (`random_state=42`).

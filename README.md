# Projeto de Aprendizagem de Máquina — ADS033 — 2026/2

## Da base de dados à avaliação de modelos: sinistros rodoviários da PRF

Projeto acadêmico da disciplina Aprendizagem de Máquina, sob orientação do professor Rodrigo Gonçalves.

**Curso:** Tecnologia em Análise e Desenvolvimento de Sistemas — IESB Asa Sul  
**Turma:** ADSDM2C  
**Integrantes:** Ana Clara, Nathalya e Carlos Eduardo Mendonça

## 1. Objetivo

Investigar registros de sinistros rodoviários da PRF de 2025 por meio de:

- Auditoria e análise exploratória.
- Agrupamento de ocorrências por porte.
- Regressão linear simples.
- Classificação binária da gravidade.

A base consolidada contém 72.529 registros e 30 colunas originais.

O alvo de classificação recebe:

- **1:** pelo menos uma morte ou um ferido grave.
- **0:** nenhuma morte e nenhum ferido grave.

Os resultados são observacionais e não demonstram causalidade.

## 2. Estrutura do repositório

```text
.
├── 01_eda_e_baseline_prf2025_final.ipynb
├── 02_clusterizacao_regressao_prf2025_entrega.ipynb
├── 03_classificacao_prf2025_entrega.ipynb
├── dados/
│   └── datatran2025.csv
├── AUTORES.md
├── README.md
└── requirements.txt
```

### Notebook 01 — Marco 1

`01_eda_e_baseline_prf2025_final.ipynb`

Contém auditoria, análise exploratória, definição do alvo e baseline.

Permanece preservado como foi entregue.

### Notebook 02 — Clusterização e regressão

`02_clusterizacao_regressao_prf2025_entrega.ipynb`

Contém:

- Distância euclidiana e padronização.
- Single, Complete, Average, Centroid e Ward.
- Dendrogramas, cophenetic e R² de agrupamento.
- K-means, cotovelo e silhueta.
- DBSCAN.
- Caracterização dos grupos.
- Regressão linear simples.
- Baseline da média.
- Diagnóstico de resíduos.
- Análise de sensibilidade ao registro extremo.

### Notebook 03 — Classificação

`03_classificacao_prf2025_entrega.ipynb`

Contém:

- Regressão logística binária.
- Cálculo manual de coeficientes e log-verossimilhança.
- Interpretação multivariada.
- k-NN.
- Pipelines de transformação e modelagem.
- Validação cruzada estratificada.
- Seleção de limiares no treino.
- Comparação com referências.
- Matrizes de confusão e curvas.
- Limitações e consequências potenciais dos erros.

### Documentação

- `AUTORES.md`: frentes técnicas e responsabilidades.
- `requirements.txt`: versões das dependências registradas nos ambientes do Marco 2.

## 3. Dados

A cópia consolidada utilizada nos experimentos está em:

```text
dados/datatran2025.csv
```

O arquivo corresponde aos registros da PRF utilizados no projeto.

Parâmetros de leitura:

- Separador: ponto e vírgula.
- Decimal: vírgula.
- Codificação: Latin-1.

Os notebooks verificam dimensões, identificadores e propriedades necessárias à execução.

O CSV é preservado sem correções automáticas de campos divergentes.

### Limitação contábil

Em parte dos registros, o campo `pessoas` não coincide com:

```text
mortos + feridos + ilesos + ignorados
```

A divergência identifica incompatibilidade entre campos, mas não determina qual valor está incorreto.

Esses registros são documentados e preservados na análise principal.

## 4. Ambiente

Os ambientes informados para os Notebooks 02 e 03 utilizaram:

```text
Python 3.13.18
```

As versões das dependências estão em `requirements.txt`.

Esse arquivo registra as versões consultadas nos ambientes utilizados. Não constitui, por si só, comprovação de instalação limpa em outro ambiente.

O Marco 1 foi entregue anteriormente. O registro de ambiente do Marco 2 não certifica retroativamente o ambiente original do Marco 1.

## 5. Reprodução no Google Colab

Os notebooks utilizam montagem do Google Drive.

### Preparação dos dados

1. Baixar `dados/datatran2025.csv` deste repositório.
2. Colocar o arquivo no Google Drive em:

```text
MyDrive/base_compartilhada/datatran2025.csv
```

O caminho utilizado no Colab é:

```text
/content/drive/MyDrive/base_compartilhada/datatran2025.csv
```

### Dependências

O ambiente deve disponibilizar as dependências declaradas em `requirements.txt`.

Para instalar a partir de uma cópia local desse arquivo:

```python
%pip install -r /caminho/para/requirements.txt
```

O caminho deve apontar para o arquivo efetivamente disponível na sessão.

Após uma instalação que altere bibliotecas já carregadas, a sessão deve ser reiniciada antes da execução integral.

### Execução

1. Abrir os notebooks na ordem numérica.
2. Autorizar a montagem do Google Drive.
3. Reiniciar a sessão e executar todas as células.
4. Conferir verificações, avisos e resultados.

Cada notebook possui sua própria leitura e preparação dos dados.

Não é necessário manter variáveis de outro notebook na memória.

A instalação das dependências não substitui a configuração do Drive.

## 6. Protocolo experimental

- Divisão de 70% para treino e 30% para teste.
- Estratificação pelo alvo de gravidade.
- Semente 42.
- Transformações aprendidas no treino.
- Agrupamentos ajustados no treino.
- Cinco dobras estratificadas na classificação.
- Mesmas dobras para logística e k-NN.
- Limiares escolhidos nas previsões de validação do treino.

### Histórico do teste

O teste foi examinado antes de correções metodológicas na classificação.

A reavaliação posterior está documentada.

Os resultados finais não são apresentados como uma avaliação completamente independente de todas as decisões anteriores.

## 7. Escopo metodológico do Marco 2

Foram aplicados:

- Agrupamento hierárquico com Single, Complete, Average, Centroid e Ward.
- K-means.
- DBSCAN.
- Regressão linear simples.
- Regressão logística binária.
- k-NN.

Os métodos foram avaliados quanto ao aproveitamento e às limitações, sem pressupor que todos produziriam resultados igualmente úteis.

A classificação compara regressão logística e k-NN sob o mesmo protocolo, com referências majoritária e todos graves.

A regressão linear responde a uma pergunta numérica complementar e não é contada como uma terceira família de classificadores.

### Agrupamento

- K-means com dois grupos foi utilizado como síntese descritiva de porte.
- A solução com dez grupos foi mantida como detalhamento complementar.
- Ward foi a alternativa hierárquica mais aproveitável nos cortes examinados.
- Os demais métodos contribuíram para discutir fidelidade, concentração e isolamento de pequenas parcelas.
- DBSCAN teve aproveitamento limitado na representação utilizada.

### Regressão linear

A regressão superou o baseline da média no teste:

| Modelo | MAE | RMSE | R² |
|---|---:|---:|---:|
| Baseline da média | 1,1587 | 2,2081 | aproximadamente 0 |
| Regressão linear | 0,9089 | 2,0162 | 0,1662 |

A melhora não elimina os grandes erros em algumas ocorrências nem as limitações da variável `pessoas`.

### Classificação

| Modelo | Average Precision | ROC-AUC | Log loss | Brier |
|---|---:|---:|---:|---:|
| Baseline | 0,2825 | 0,5000 | 0,5953 | 0,2027 |
| Logística | 0,3367 | 0,5834 | 0,5867 | 0,1992 |
| k-NN corrigido | 0,2835 | 0,4991 | 0,7932 | 0,2271 |

A logística apresentou ganho modesto de ordenação e menores perdas probabilísticas em relação ao baseline.

O k-NN corrigido não demonstrou discriminação útil no teste na configuração examinada.

Os limiares baixos elevaram o recall, mas produziram alertas para quase todas as ocorrências.

## 9. Limitações e riscos

- Dados observacionais de um único ano.
- Limitações de cobertura e registro.
- Divergências contábeis.
- Categorias raras.
- Representações restritas.
- Dependência temporal e espacial não modelada.
- Ausência de avaliação sistemática de desempenho entre subgrupos.
- Reavaliação do teste após correções metodológicas.

Em um uso hipotético de priorização:

- Falsos negativos poderiam resultar em prioridade insuficiente para ocorrências graves.
- Falsos positivos poderiam mobilizar recursos desnecessariamente.
- Alertas para quase todas as ocorrências ofereceriam pouca capacidade de filtragem.

Essas consequências não foram quantificadas operacionalmente.

Os resultados não sustentam implantação para triagem ou alocação de recursos.

## 10. Autores e responsabilidades

As frentes técnicas e as responsabilidades estão documentadas em `AUTORES.md`.

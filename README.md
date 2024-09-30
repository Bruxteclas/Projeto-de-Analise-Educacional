
# Análise de Desempenho Educacional

Este projeto tem como objetivo analisar o desempenho dos alunos em duas disciplinas: Língua (L) e Matemática (MT), utilizando técnicas de análise estatística, visualização de dados e aprendizado de máquina para gerar insights e previsões sobre o desempenho dos alunos.

## Objetivos do Projeto

1. **Análise Comparativa**: Comparar o desempenho dos alunos em diferentes regiões, escolas e séries.
2. **Fatores Determinantes**: Identificar os fatores que mais influenciam o desempenho dos alunos.
3. **Modelagem Preditiva**: Prever a performance futura dos alunos com base em dados históricos.

## Perguntas-Chave

- Quais regiões/estados apresentam os melhores e os piores desempenhos?
- Como variáveis como infraestrutura escolar, formação dos professores e características socioeconômicas impactam o desempenho dos alunos?
- É possível prever a performance futura dos alunos com base nos dados históricos?

## **2. Entendimento dos Dados**
- **Descrição dos Dados:**
  - O dataset contém informações detalhadas sobre o desempenho dos alunos, infraestrutura das escolas, localização, e outros fatores relevantes.
 
### Tabela de Variáveis (Traduzida):

|     | Nome da Coluna            | Descrição                                              | Tipo de Dado  |
| --- | ------------------------- | ------------------------------------------------------ | ------------- |
| 0   | ano                       | Ano de coleta dos dados                                | int64         |
| 1   | id_regiao                 | ID da região                                           | int64         |
| 2   | sigla_uf                  | Sigla do estado (UF)                                   | object        |
| 3   | id_municipio              | ID do município                                        | int64         |
| 4   | area                      | Área (rural/urbana)                                    | int64         |
| 5   | id_escola                 | ID da escola                                           | int64         |
| 6   | rede                      | Rede de ensino (1 = pública, 2 = privada)              | float64       |
| 7   | localizacao               | Localização (1 = urbana, 2 = rural)                    | int64         |
| 8   | id_turma                  | ID da turma                                            | int64         |
| 9   | turno                     | Turno da turma (1 = manhã, 2 = tarde, etc.)            | float64       |
| 10  | serie                     | Série escolar                                          | int64         |
| 11  | id_aluno                  | ID do aluno                                            | int64         |
| 12  | situacao_censo            | Situação do aluno no censo escolar                     | int64         |
| 13  | disciplina                | Disciplina (matemática, português, etc.)               | object        |
| 14  | preenchimento_caderno     | Indicador de preenchimento do caderno                  | int64         |
| 15  | presenca                  | Indicador de presença                                  | int64         |
| 16  | caderno                   | Tipo de caderno de avaliação                           | int64         |
| 17  | bloco_1                   | Respostas do bloco 1                                   | int64         |
| 18  | bloco_2                   | Respostas do bloco 2                                   | int64         |
| 19  | bloco_1_aberto            | Questões abertas do bloco 1                            | int64         |
| 20  | bloco_2_aberto            | Questões abertas do bloco 2                            | int64         |
| 21  | respostas_bloco_1         | Respostas completas do bloco 1                         | float64       |
| 22  | respostas_bloco_2         | Respostas completas do bloco 2                         | float64       |
| 23  | conceito_q1               | Conceito na questão 1                                  | object        |
| 24  | conceito_q2               | Conceito na questão 2                                  | object        |
| 25  | resposta_texto            | Resposta textual                                       | object        |
| 26  | conceito_proposito        | Conceito sobre propósito                               | object        |
| 27  | conceito_elemento         | Conceito sobre elementos                               | object        |
| 28  | conceito_segmentacao      | Conceito sobre segmentação                             | object        |
| 29  | texto_grafia              | Análise da grafia do texto                             | object        |
| 30  | indicador_proficiencia    | Indicador de proficiência dos alunos                   | int64         |
| 31  | amostra                   | Indicador de amostra                                   | int64         |
| 32  | estrato                   | Estrato da amostra                                     | int64         |
| 33  | peso_aluno                | Peso do aluno na amostra                               | float64       |
| 34  | proficiencia              | Nível de proficiência do aluno                         | float64       |
| 35  | erro_padrao               | Erro padrão na avaliação da proficiência               | float64       |
| 36  | proficiencia_saeb         | Nível de proficiência SAEB (Sistema de Avaliação)      | float64       |
| 37  | erro_padrao_saeb          | Erro padrão do nível de proficiência SAEB              | float64       |

## Bibliotecas Utilizadas

- `pandas` para manipulação e análise de dados.
- `matplotlib` e `seaborn` para visualização de dados.
- `statsmodels` para análise estatística e modelagem.
- `numpy` para operações numéricas.
- `sklearn` para machine learning e pré-processamento de dados.
- `joblib` para salvamento e carregamento de modelos.
- `wordcloud` para visualização de palavras.
- **Machine Learning**: `sklearn` (MLPRegressor, RandomForestRegressor, Ridge)
- Entre outras bibliotecas contidas no arquivo.

## Insights

### Desempenho Regional

- **Estados com Maior Desempenho**: SC, CE, DF, SP, MG.
- **Estados com Menor Desempenho**: SE, RN, PI, AL, MA.

### Análise Qualitativa

- **Respostas Textuais**: Análise de consistência e identificação de padrões comuns.
--- 

## Análise dos Componentes Principais (PCA)

### Componentes Principais e suas Cargas

**Componente Principal 1**
- **Variáveis com Maiores Cargas Absolutas:**
  - `proficiencia_saeb` (carga positiva de 0.117935)
  - `erro_padrao` (carga positiva de 0.174393)
  - `erro_padrao_saeb` (carga positiva de 0.173747)

  **Interpretação:**  
  O primeiro componente está fortemente relacionado a variáveis que medem a proficiência e o erro associado. Isso sugere que o Componente Principal 1 pode refletir uma medida geral de proficiência e erro.

**Componente Principal 2**
- **Variáveis com Maiores Cargas Absolutas:**
  - `peso_aluno` (carga positiva de 0.613525)
  - `bloco_1_aberto` (carga positiva de 0.486147)
  - `bloco_1` (carga positiva de 0.485190)

  **Interpretação:**  
  O segundo componente parece estar associado a variáveis relacionadas a aspectos específicos do aluno e das avaliações. Esse componente pode refletir características relacionadas ao ambiente de aprendizado ou características específicas dos alunos.

**Componente Principal 3**
- **Variáveis com Maiores Cargas Absolutas:**
  - `localizacao` (carga positiva de 0.639607)
  - `area` (carga positiva de 0.681913)
  - `amostra` (carga negativa de -0.160481)

  **Interpretação:**  
  O terceiro componente pode estar relacionado a variáveis geográficas e de amostragem. As altas cargas positivas em `localizacao` e `area` indicam uma influência significativa dessas variáveis, enquanto a carga negativa de `amostra` sugere um impacto menor.


**Variáveis Relevantes:**

- **Fatores Acadêmicos e de Avaliação:**  
  Variáveis como `proficiencia_saeb`, `erro_padrao`, e `peso_aluno` estão fortemente associadas aos primeiros componentes. Essas variáveis podem ser relevantes para análises que envolvem desempenho acadêmico e avaliação.

- **Aspectos Geográficos e de Amostragem:**  
  `localizacao` e `area` são importantes para a compreensão do terceiro componente. Essas variáveis são cruciais para análises que envolvem contexto geográfico e amostragem.

### Influência das Variáveis Principais

**Variáveis Significativas Identificadas:**

- **`rede`:**  
  Mostra um efeito muito significativo no desempenho dos alunos. Isso sugere que a rede à qual o aluno pertence (provavelmente uma rede de escolas ou uma instituição educacional) pode ter um impacto importante na proficiência dos alunos.

- **`localizacao`:**  
  Também é altamente significativa, indicando que a localização geográfica pode ter um papel crucial no desempenho dos alunos. Considerar fatores como o acesso a recursos educacionais, diferenças socioeconômicas ou infraestrutura local pode ser relevante.

**Interação Entre Variáveis:**

- **Interação entre `rede` e `localizacao`:**  
  A interação significativa entre `rede` e `localizacao` sugere que o efeito da rede sobre o desempenho dos alunos pode depender da localização, e vice-versa. Isso pode indicar que a eficácia de uma rede educacional pode variar de acordo com a localização geográfica, possivelmente devido a variações regionais nas condições e na qualidade dos recursos educacionais.
  

## 1. Desempenho Médio por Disciplina

O gráfico intitulado **"Desempenho Médio por Disciplina"** mostra a **proficiência média** nas duas disciplinas:

- **Desempenho em Língua**: A proficiência média em Língua é de aproximadamente -0,13, indicando um desempenho mais baixo.
- **Desempenho em Matemática**: A proficiência média em Matemática é de cerca de -0,08, mostrando um desempenho relativamente melhor.
- **Comparação Geral**: Os alunos têm um desempenho melhor em Matemática do que em Língua, conforme indicado pelas barras no gráfico.

## 4. Análise dos Resultados e Modelagem Preditiva

### Distribuição dos Resíduos
- **Distribuição Normal**: Uma distribuição normal dos resíduos indica que o modelo está adequadamente especificado.
- **Simetria**: Indica que o modelo não tem tendência a subestimar ou superestimar valores.
- **Erros Pequenos**: A concentração dos resíduos próximos de zero sugere previsões precisas.

### Métricas do Modelo
- **Mean Absolute Error (MAE)**: 0.2042
- **Mean Squared Error (MSE)**: 0.0930
- **R² Score**: 0.8838

### Coeficientes das Variáveis
| Feature                   | Coefficient    |
|--------------------------|-----------------|
| preenchimento_caderno    | 337.033411      |
| serie                    | 143.166950      |
| erro_padrao_saeb        | 141.164310      |
| bloco_2_aberto          | 123.476702      |
| bloco_1                 | 61.739460       |
| ...                      | ...             |
| situacao_censo          | -179.450302     |
| indicador_proficiencia   | -179.936298     |
| presenca                | -209.829670     |
| erro_padrao             | -7815.856891    |

### Valores Reais vs. Previsto
| Real    | Previsto | Resíduo   |
|---------|----------|-----------|
| 177544  | 0.221238 | 0.089266  |
| 115650  | -1.004777| -0.670311 |
| ...     | ...      | ...       |

A média dos scores de validação cruzada (0.8845) indica um bom desempenho do modelo, com consistência e robustez nas previsões.

## 5. Insights Gerais

1. **Diferenças Entre Redes de Ensino**: Variações na proficiência média entre diferentes redes, com uma rede apresentando desempenho superior.
2. **Identificação de Melhores Práticas**: A rede com maior proficiência pode implementar práticas que outras redes podem adotar.
3. **Foco em Intervenções**: Redes com menor proficiência podem precisar de intervenções específicas.

### Tendências e Padrões
1. **Tendência Geral Positiva**: Ambos os anos mostram um aumento na proficiência prevista ao longo do tempo.
2. **Crescimento Consistente**: A proficiência aumenta de forma contínua, sugerindo melhorias no desempenho dos alunos.
3. **Planejamento Educacional**: Os dados podem ajudar na alocação de recursos e identificação de períodos que requerem suporte.

## Conclusão

Este projeto oferece insights valiosos sobre o desempenho educacional dos alunos e como fatores como rede de ensino e localização podem influenciar a proficiência. A análise estatística e as visualizações ajudam a entender melhor as dinâmicas de aprendizagem e a formular intervenções educativas eficazes.

## Autor
- [Paulo Eduardo]



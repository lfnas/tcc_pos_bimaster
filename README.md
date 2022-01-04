# Análise Preditiva SINASC 2019 - Modelo para previsão do peso de recém-nascidos

#### Aluno: [Luiz Felipe Nascimento da Silva](https://github.com/lfnas).
#### Orientador: [Manoela Kohler](https://github.com/manoelakohler).

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

- [Link para a monografia](---). 

---

### Resumo

Em decorrência das diversas pesquisas no âmbito da saúde pública, observa-se que a prematuridade associada ao baixo peso de recém-nascidos são possíveis causas da mortalidade perinatal, neonatal e infantil. Em mesmo passo, o acompanhamento pré-natal qualificado, pode auxiliar na identificação precoce desses incidentes e outros como: má formação, problemas genéticos etc. em razão disso, esses fatores devem ser melhor avaliados e explorados, viabilizando uma melhor resolução e tratamento a gestantes. Nesse sentido, e mediante a implementação de novas tecnologias, volta-se a atenção a promoção e formulação de modelos preditivo que possam associar e mensurar o desempenho futuro e/ou evolução de elementos biológicos e sociais das gestantes, isto é, modelos de predição que demonstrem ou sinalizem indícios (correlação) para grupos de riscos antes do nascimento. No presente trabalho, buscou-se a previsão do peso dos recém-nascidos,  tendo em vista, a relevância do peso na sobrevida da criança, possibilitando um estudo mais amplo, considerando as classificações oficiais de pesos de nascidos vivos. Em tempo, a previsão realizada é associada às diversas variáveis, reunidas em uma base de dados unificada, podendo citar: herança genética, condições de cuidado, histórico materno, fatores sociais, idade da mãe e tipo de parto, consequentemente, o modelo possibilita a identificação das gestantes que necessitem de maior atenção nas unidades de atenção básica, seja por uma condição biológica ou social, voltadas, também ao risco da gestação. A base utilizada para este trabalho é proveniente do Sistema de Informação sobre Nascidos Vivos (SINASC), que é um Sistema que facilita a visualização das evoluções de séries históricas, para o presente estudo será utilizado, somente um dataset, referente ao ano de 2019 dos nascimentos ocorridos no Estado do Rio de Janeiro.

### Abstract

As a result of several researches in the scope of public health, it is observed that prematurity associated with low birth weight of newborns are possible causes of perinatal, neonatal and infant mortality. At the same time, qualified prenatal care can help in the early identification of these incidents and others such as: malformation, genetic problems, etc. for this reason, these factors should be better evaluated and explored, enabling a better resolution and treatment for pregnant women. In this sense, and through the implementation of new technologies, attention is focused on the promotion and formulation of predictive models that can associate and measure the future performance and/or evolution of biological and social elements of pregnant women, that is, prediction models that demonstrate or signal evidence (correlation) for risk groups before birth. In the present work, we sought to predict the weight of newborns, considering the relevance of weight in child survival, enabling a broader study, considering the official classifications of weights of live births. In time, the forecast made is associated with several variables, gathered in a unified database, including: genetic inheritance, care conditions, maternal history, social factors, mother's age and type of delivery, consequently, the model allows for identification of pregnant women who need more attention in primary care units, whether for a biological or social condition, also focused on the risk of pregnancy.

### 1. Introdução

No Brasil, o Ministério da Saúde dispõe de uma base de dados que reúne informações sobre diferentes variáveis que podem ter influência sobre os partos prematuros e o baixo peso de recém-nascidos, a referida base é proveniente do Sistema de Informação sobre Nascidos Vivos (SINASC), que é um Sistema que facilita a visualização das evoluções de séries históricas. Os dados, por sua vez são coletados pelos entes da federação (Estados e Municípios), e consolidados neste sistema nacional que compreende uma das maiores referências sobre os nascimentos do país.

O presente estudo utilizará, somente, um fragmento da base integral, isto é, referente ao ano de 2019 dos nascimentos ocorridos no Estado do Rio de Janeiro. Em detalhes, o dataset possui dados anonimizados, disponível no site (https://datasus.saude.gov.br/transferencia-de-arquivos/), com 48 features e mais de 200 mil registros, demonstrando-se uma base significativa para diversos testes e aplicações, não somente para previsão de pesos.

Ressalta-se a aplicabilidade da base para o reconhecimento social, epidemiológico, geográfico etc. ou seja, elevando a disponibilidade no desenvolvimento de modelos analíticos e preditivos, possibilitando às autoridades nacionais e regionais de saúde pública a promoções de políticas públicas.

### 2. Modelagem

Inicialmente, destaca-se o grande volume de dados estruturados trabalhados com o dataset, bem como as diversas relações entre variáveis presentes.  Novamente, ressalta-se que a base é bem ampla e dispõe de dados quantitativos e qualitativos de diversas naturezas.

Inicialmente, em observação as features, pode-se inferir na divisão de alguns grupos, o primeiro de alta correlação (normalmente relacionadas ao desenvolvimento do recém-nascido durante a gestação), média correlação (como influências externas e histórico da mãe) e baixa correlação (anotações burocráticas e fatores sociais de pouca relevância ao objeto).

O modelo proposto é focado no problema, isto é, a previsão de pesos de recém-nascidos, assim é verificado o nível de permanência das features em relação ao objeto ‘PESO’, bem como sua correlação, através das funções e visualizações. Posteriormente, foram realizados os procedimentos de tratamento dos dados, em especial, divide-se em algumas fases que podem ser melhor observadas:

  * *Análise Exploratória*
  
Na avaliação inicial de dimensões e tipos de dados foi observado a composição predominantes de variáveis reais e uma dimensionalidade significativa. Além disso, o número de casos, o conjunto de variáveis, sua denominação, tipo e estados de atributos, dentre outras características.

Buscou-se explorar a análise visual dos dados para melhor entendimento das features e suas relações mais próximas com a variável alvo do modelo. Em especial se utilizou das bibliotecas SEABORN e MATPLOTLIB, com os seguintes tipos de gráficos (.countplot, .displot, .boxplo, .lmplot e .hist). Fator que possibilitou a identificação de variáveis com apenas um valor ou sem relação significativa com o objeto, como por exemplo: 'ORIGEM', 'STDNEPIDEM', 'STDNNOVA', 'CODPAISRES', 'TPNASCASSI', 'DTCADASTRO', 'CODMUNNASC'.

Em avaliação especial da variável peso, indetifica-se que o peso médio dos recém-nascidos é de cerca de 3 kg, com valores extremos abaixo de 2 kg e acima de 4,5 kg, aproximadamente, com crianças do sexo masculino apresentando a tendência de terem maior peso que crianças do sexo feminino.

Sendo a relação do peso com outras features, também explorada. Em especial, as variáveis SEXO, GESTACAO, TPROBSON, SEMAGESTAC E PARTO. Algumas relações apresentam tendências claras, como a maior incidência de peso elevado em meninos e o baixo peso, com baixas semanas de gestação. Igualmente, para gestações mais longas o peso aumentava até o limite de “40º semana” quando estabilizou no peso médio.

Ademais, foi identificado ampla sobreposição para os valores de peso entre os tipos de parto, sendo que há bem menos casos em que o tipo de parto foi ignorado. Não havendo uma correlação direta entre a idade das mães e o peso das crianças, tal qual para o número de consultas e o peso, todavia, essa variável indica tendências quando o número de semanas de gestação.

Partindo para uma avaliação quanto ao índice de correlação das features com a variável PESO. A partir disso, foram excluídas as variáveis com valores de baixa correlação, a exemplo de 'IDANOMAL', 'CONTADOR', 'CODMUNRES', 'RACACORMAE', 'RACACOR', 'ESCMAE', 'ESTCIVMAE', 'DTDECLARAC', 'HORANASC', 'NUMEROLOTE', 'ESCMAE2010', 'DTNASC','APGAR1', 'ESCMAEAGR1',, dentre outras. Além disso, utilizou-se um gráfico (.heatmap) para melhor visualização das correlações.

  * *Pré-Processamento*

Para o tratamento de outliers, foi inicialmente plotado um gráfico (.boxplot), sendo o mesmo utilizado na avaliação isolada da variável PESO. Nesse exemplo, foram identificados uma quantidade significativa de outliers, conforme obtido na função: 

Índices de acurácia e kappa encontrados nos modelos:

| sub           | values 
| ------------- | -------- 
| IQR           | 520.00  
| Upper Bound   | 2764.00  
| Lower Bound   | 684.00  
| Sum outliers  | 5223.00
| % outliers    | 2.51119

Após, foi realizada a exclusão dos mesmos e plotado novo gráfico para visualização das modificações. 

No tratamento de missing values foi elaborado um script para facilitar a análise e observação dos valores, em síntese houve o retorno do total de missings de cada feature, bem como o percentual dentro de cada uma. Em tempo, foi gerado um gráfico de barras simples para visualização do percentual de missing values de cada features, a atribuição feita no código é uma linha de “corte” de 40%, isto é, foram excluídas as features com valores superiores, representada com uma linha horizontal traçada no gráfico.

Ademais, foi programada a substituição dos atributos numéricos pela mediana, medida central que expressa melhor assertividade do que a média, por exemplo, principalmente em casos com maior possibilidade de variação numérica, para os atributos categóricos foi substituído pela moda dos valores existentes.
Na redução de dimensionalidade foi transformado os atributos com o método (.fit) depois dividindo a base de treino e teste foi aplicado o método PCA na base de treino.

### 3. Resultados

Para previsão do PESO foram utilizados os modelos de Random Forest, Decision Tree, Naive Bayes e Logistic Regression. Os resultados de acurácia do modelo foram os seguintes: 

| Modelo             | Acurácia 
| ------------------ | -------- 
| Random Forest      | 97.97%  
| Decision Tree      | 97.97%   
| Logistc Regression | 1.040%   
| Naive Bayes        | 7.070%   

### 4. Conclusões

O modelo baseado em Random Forest e Decision Tree foram os que obtiveram maior acurácia dentre os testados, chegando a 97.97% com 100 árvores e 29 features. Outros modelos também não atingiram o esperado, retornando pouco ou quase nada em aspectos de acurácia na predição, sendo incluídos para fins comparativos.

---

Matrícula: 192.671.165

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação em *Business Intelligence Master*

---

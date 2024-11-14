# 1.Business Problem

Neste projeto, foi utilizado um conjunto de dados composto por 29 variáveis que descrevem diversos aspectos dos clientes, incluindo características demográficas, comportamentais e de consumo. Este dataset é não supervisionado, ou seja, não possui um rótulo ou target predefinido.

Como o dataset não possui uma variável alvo, a meta é explorar e descobrir padrões ocultos entre os clientes. O objetivo é rotular e segmentar esses clientes em diferentes clusters, com base em suas semelhanças, para entender melhor as diferentes personalidades e perfis comportamentais presentes na base.

Ao segmentar clientes em clusters, será possível obter insights sobre diferentes grupos e identificar padrões de comportamento específicos. Isso ajudará na compreensão das necessidades e preferências dos clientes, permitindo uma personalização mais estratégica de abordagens e produtos para cada perfil identificado.

Essa segmentação permitirá maior precisão em estratégias de marketing e personalização de ofertas.

# 2.Context Analysis

**Atributos**

**Pessoas**

**ID:** Identificador único do cliente
**Year_Birth:** Ano de nascimento do cliente
**Education:** Nível de escolaridade do cliente
**Marital_Status:** Estado civil do cliente
**Income:** Renda anual da família do cliente
**Kidhome:** Número de crianças na casa do cliente
**Teenhome:** Número de adolescentes na casa do cliente
**Dt_Customer:** Data de inscrição do cliente na empresa
**Recency:** Número de dias desde a última compra do cliente
**Complain:** 1 se o cliente fez uma reclamação nos últimos 2 anos, 0 caso contrário

**Produtos**

**MntWines:** Valor gasto em vinhos nos últimos 2 anos
**MntFruits:** Valor gasto em frutas nos últimos 2 anos
**MntMeatProducts:** Valor gasto em produtos de carne nos últimos 2 anos
**MntFishProducts:** Valor gasto em produtos de peixe nos últimos 2 anos
**MntSweetProducts:** Valor gasto em doces nos últimos 2 anos
**MntGoldProds:** Valor gasto em produtos de ouro nos últimos 2 anos

**Promoção**

**NumDealsPurchases:** Número de compras feitas com desconto
**AcceptedCmp1:** 1 se o cliente aceitou a oferta na 1ª campanha, 0 caso contrário
**AcceptedCmp2:** 1 se o cliente aceitou a oferta na 2ª campanha, 0 caso contrário
**AcceptedCmp3:** 1 se o cliente aceitou a oferta na 3ª campanha, 0 caso contrário
**AcceptedCmp4:** 1 se o cliente aceitou a oferta na 4ª campanha, 0 caso contrário
**AcceptedCmp5:** 1 se o cliente aceitou a oferta na 5ª campanha, 0 caso contrário
**Response:** 1 se o cliente aceitou a oferta na última campanha, 0 caso contrário

**Local**

**NumWebPurchases:** Número de compras feitas através do site da empresa
**NumCatalogPurchases:** Número de compras feitas utilizando catálogo
**NumStorePurchases:** Número de compras feitas diretamente nas lojas
**NumWebVisitsMonth:** Número de visitas ao site da empresa no último mês

# 3. Solution Strategy

Para este projeto, o método CRISP-DM foi utilizado, contando com os 10 passos abaixo: 

1 - Problema de Negócio: Identificar o problema de negócio a ser solucionado;

2 - Entendimento do Problema de Negócio: Compreender a motivação, a causa e propor a estratégia de solução para este problema.

3 - Coleta de Dados: Os dados foram obtidos através do Kaggle. (Customer Personality Analysis - https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)

4 - Limpeza dos Dados: Consiste em renomear colunas, converter as variáveis para seus tipos corretos, verificar e preencher NA´s quando necessário, seguindo as motivações do negócio, além de fornecer um breve resumo descritivo dos dados.

5 - Exploração dos Dados: Esta etapa busca analisar e compreender as variáveis que impactam a variável resposta do projeto. Também ocorre a filtragem de variáveis, de acordo com a problemática de negócio. Aqui também são validadas as hipóteses de negócio com a utilização de análise univariada, bivariada e multivariada, o que acarreta na geração de insights.

6 - Modelagem dos Dados: Esta etapa é fundamental para preparar os dados conforme os requisitos dos algoritmos de Machine Learning. Aqui, são realizadas Normalização e Encoding, com o objetivo de padronizar os dados em uma mesma escala, além de converter variáveis categóricas em numéricas. Além disso, foi utilizado o t-SNE para reduzir a dimensionalidade dos dados, facilitando a visualização e melhorando a eficiência dos modelos de clusterização.

7 - Seleção de Features: Esta etapa do projeto filtra as features mais relevantes para o treinamento de Machine Learning que vem a seguir. Não é interessante para o projeto ter um número muito grande de colunas que não impactam na explicação do problema estudado.

8 - Machine Learning: Em seguida, os dados preparados são treinados em diversos algoritmos de Machine Learning, com objetivo de balancear a melhor métrica com a melhor distribuição dos clusters.

9 - Avaliação do Algoritmo: Aqui, avalia-se o algoritmo com os dados de teste previamente separados, de acordo com métricas alinhadas ao tipo de aprendizado dos modelos de Machine Learning. 

10 - Modelo em Produção: Por fim, o modelo avaliado é publicado (Deploy). Neste caso não foi feito um deploy do modelo, porém esse é o próximo passo.

# 4. To 3 Insights

### Neste gráfico podemos identificar qual cluster mais gera receita (Cluster 1)

### A maior parte das pessoas tem entre 25 e 44 anos, estando concentradas principalmente no cluster 1 (que como mencionado anteriormente é o que mais gera receita).

### A renda do cliente (se é alta, média ou baixa renda) aparentemente está correlacionada com a quantidade de receita (gastos) por cluster. Os clusters com renda mais alta, geram mais receita.


# 5. Machine Learning Model
Após a preparação dos dados, foram desenvolvidos e treinados três modelos de Aprendizado de Máquina para identificar o algoritmo mais eficaz em descrever e resolver o problema proposto:

**K-means**

**DBSCAN**

**Agglomerative Clustering**

Para determinar a quantidade ideal de clusters (K), utilizei o método do cotovelo (Elbow Method), que permite identificar o ponto de equilíbrio entre o número de clusters e a variabilidade dentro dos grupos. Além disso, apliquei o índice de silhueta (Silhouette Score) não apenas para validar o número ideal de clusters, mas também para avaliar a qualidade da clusterização, verificando o quão bem os dados foram agrupados pelo modelo.


# 6. Resultado do modelo

O modelo **K-Means** apresentou o melhor Silhouette Score de **0.59**, indicando uma boa separação entre os clusters. Em conjunto com a análise gráfica, constatamos que esse modelo obteve a melhor configuração de clusters, levando à escolha de K igual a 7 como a quantidade ideal para segmentação.

# 7. Análise Final dos Clusters

## Produto Mais Consumido
O **Vinho** é o produto mais consumido por todos os clusters. Todos os clusters preferem comprar em lojas físicas.

---

## Cluster 0: "Conservadores"

**Perfil de Compra:**
- **Receita Gerada:** Baixa receita, um dos clusters com menor geração de receita.
- **Aceitação de Promoções:** Um dos grupos que menos aceita promoções.
- **Comportamento de Compras:** Realiza um número reduzido de compras.
- **Reclamações:** Poucas reclamações registradas.

**Perfil Demográfico:**
- **Idade:** Idade bem distribuída, mas predominância de indivíduos acima de 62 anos (majoritariamente idosos).
- **Estado Civil e Filhos:** A maioria vive com seus parceiros e tem filhos.
- **Nível de Educação:** A maior parte possui pós-graduação.
- **Renda:** Renda baixa majoritariamente.

---

## Cluster 1: "Influentes"

**Perfil de Compra:**
- **Receita Gerada:** Este cluster é o maior gerador de receita.
- **Aceitação de Promoções:** Aceita promoções de maneira média.
- **Comportamento de Compras:** Registra um número significativo de compras.
- **Reclamações:** Este cluster é o que mais registra reclamações.

**Perfil Demográfico:**
- **Idade:** Predominância de indivíduos entre 25 e 44 anos.
- **Estado Civil e Filhos:** Composto majoritariamente por pessoas que vivem com seus parceiros e têm filhos.
- **Nível de Educação:** A maioria possui graduação.
- **Renda:** A maioria tem renda média para alta.

---

## Cluster 2: "Aposentados"

**Perfil de Compra:**
- **Receita Gerada:** Um dos clusters com menor geração de receita.
- **Aceitação de Promoções:** Este é o cluster que mais aceita promoções.
- **Comportamento de Compras:** Número reduzido de compras.
- **Reclamações:** Poucas reclamações registradas.

**Perfil Demográfico:**
- **Idade:** Idade bem distribuída, mas com maioria acima de 62 anos (principalmente idosos).
- **Estado Civil e Filhos:** Predominância de pessoas que vivem sozinhas; muitos têm filhos, mas uma parte significativa não tem.
- **Nível de Educação:** Maioria com pós-graduação.
- **Renda:** Renda média em sua maioria.

---

## Cluster 3: "Experientes"

**Perfil de Compra:**
- **Receita Gerada:** Um dos clusters que mais gera receita.
- **Aceitação de Promoções:** Aceita promoções com facilidade.
- **Comportamento de Compras:** Menor número de reclamações.
- **Reclamações:** Registra um número relativamente baixo de reclamações.

**Perfil Demográfico:**
- **Idade:** Predominância de pessoas entre 44 e 62 anos.
- **Estado Civil e Filhos:** Composto principalmente por pessoas que vivem com seus parceiros e têm filhos.
- **Nível de Educação:** A maioria possui pós-graduação.
- **Renda:** A renda é bem distribuída dentro deste cluster, porém em sua maioria alta renda.

---

## Cluster 4: "Independentes"

**Perfil de Compra:**
- **Receita Gerada:** Baixa geração de receita.
- **Aceitação de Promoções:** Aceita promoções dentro da média.
- **Comportamento de Compras:** Não apresenta muitas reclamações.
- **Reclamações:** Um dos clusters com menos reclamações.

**Perfil Demográfico:**
- **Idade:** A maioria tem entre 25 e 44 anos.
- **Estado Civil e Filhos:** Composto principalmente por pessoas que vivem sozinhas e têm filhos.
- **Nível de Educação:** A maioria possui graduação.
- **Renda:** A renda é bem distribuída entre os indivíduos desse cluster.

---

## Cluster 5: "Profissionais"

**Perfil de Compra:**
- **Receita Gerada:** Um dos clusters com maior geração de receita.
- **Aceitação de Promoções:** Aceita promoções de maneira moderada.
- **Comportamento de Compras:** Este cluster é o que mais registra reclamações.

**Perfil Demográfico:**
- **Idade:** A maioria tem entre 25 e 44 anos.
- **Estado Civil e Filhos:** Predominância de pessoas que vivem com seus parceiros e têm filhos.
- **Nível de Educação:** A maioria possui graduação, com uma pequena parte sem graduação.
- **Renda:** A renda é bem distribuída, abrangendo diferentes faixas de salário.

---

## Cluster 6: "Solitários"

**Perfil de Compra:**
- **Receita Gerada:** Um dos clusters com maior geração de receita.
- **Aceitação de Promoções:** Aceita promoções de maneira média.
- **Comportamento de Compras:** Registra várias reclamações.

**Perfil Demográfico:**
- **Idade:** A maioria tem entre 44 e 62 anos.
- **Estado Civil e Filhos:** Maioria vive sozinha e tem filhos.
- **Nível de Educação:** Composto por pessoas graduadas e pessoas sem graduação.
- **Renda:** A renda é bem distribuída, mas a maior parte é alta renda.
---






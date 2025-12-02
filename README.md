📊 Análise de Dados – Projeto Olist E-commerce
👥 Integrantes da Equipe

Saulo Pietro

Davi Silva

🔗 Base de Dados Utilizada

Fonte: Olist Brazilian E-commerce Dataset
Link: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

🎯 Objetivo do Projeto

Este trabalho busca investigar padrões presentes no e-commerce brasileiro, identificando fatores que podem influenciar:

experiência e satisfação do cliente,

custo de frete,

características físicas dos produtos,

possíveis inconsistências e limitações da base de dados.

Além de entender o comportamento geral do marketplace, o estudo fornece insumos úteis para análises futuras, incluindo modelos preditivos e validações estatísticas.

🧹 Processo de Tratamento e Preparação dos Dados
1. Importação e exploração inicial

Foram avaliados tipos de variáveis, presença de valores nulos, registros duplicados e possíveis anomalias. Isso permitiu mapear rapidamente os pontos críticos da base.

2. Remoção de duplicidades

Registros repetidos foram identificados por df.duplicated() e eliminados para evitar distorções nas métricas e agregações.

3. Valores ausentes (missing data)

Valores nulos foram tratados conforme o tipo da coluna:

Preços e fretes receberam imputação baseada em mediana.

Datas inválidas foram convertidas para NaT.

Colunas categóricas tiveram preenchimento com rótulos neutros como "unknown".

Esse procedimento evitou a perda desnecessária de dados relevantes.

4. Outliers

Foram detectados outliers usando medidas robustas (como IQR).
Em vez de simplesmente excluir linhas extremas, optou-se por:

limitar valores muito discrepantes,

corrigir datas impossíveis,

e manter atrasos legítimos, já que refletem comportamento real da operação logística.

5. Normalização e padronização

Duas técnicas foram aplicadas conforme a necessidade:

MinMaxScaler → escala 0–1 para comparação direta entre atributos.

StandardScaler (Z-score) → padronização para análises que exigem distribuição mais simétrica.

Ambos os scalers também foram aplicados às variáveis derivadas.

6. Feature Engineering

Novos atributos foram criados para enriquecer a análise:

volume do produto (length × height × width),

densidade aproximada,

relações peso/frete e preço/peso,

indicadores logísticos calculados por pedido.

Esses atributos ajudaram a explicar melhor variações em frete e atraso.

7. Correlação

Foi elaborado um heatmap com todas as variáveis numéricas (originais e derivadas) para identificar relações estruturais. Isso permitiu destacar padrões importantes, como o impacto do tamanho/peso sobre o frete.

🧗 Principais Dificuldades Encontradas

Volume elevado de outliers
Grande parte dos produtos apresentava valores extremos em preço, frete ou dimensões.

Escalas muito diferentes
Unidades distintas (cm, gramas, reais, dias) exigiram normalização cuidadosa para permitir comparações coerentes.

Dados incompletos ou inconsistentes
Campos vazios e datas inválidas afetavam análises temporais e precisaram de tratamento dedicado.

Engenharia de atributos sem redundância
Criar novas variáveis realmente informativas exigiu testes sucessivos para evitar sobreposição de informação.

💡 Principais Conclusões

A base apresenta outliers significativos, que precisaram de tratamento robusto para evitar distorções.

Características físicas dos produtos (peso, volume e dimensões) mostram relação clara com o valor do frete, evidenciando o papel da logística no custo final.

Após normalização, surgiram padrões que não eram visíveis no estado bruto dos dados.

A engenharia de atributos complementou a análise ao revelar como volume, densidade e relações peso/frete influenciam variáveis financeiras.

A etapa de limpeza alterou de forma importante a distribuição das variáveis, reduzindo assimetria e tornando o conjunto mais confiável para análises posteriores.

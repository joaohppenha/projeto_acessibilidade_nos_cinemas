# **<u>Projeto Acessibilidade Física dos Cinemas Brasileiros</u>**

## 1. **O Problema**
Desde o ano 2000 o Brasil regulamenta a obrigação de promoção da acessibilidade das pessoas portadoras de deficiência ou com mobilidade reduzida, mediante a supressão de barreiras e de obstáculos nas vias e espaços públicos, no mobiliário urbano, na construção e reforma de edifícios e nos meios de transporte e de comunicação.  

A Constituição Federal de 1988 garante o direito de acesso à Cultura como fundamental e a Lei nº 13.146/2015, conhecida como Lei Brasileira de Inclusão da Pessoa com Deficiência, dispõe que em locais como cinemas, teatros etc. devem ser reservados espaços livres e assentos para pessoa com deficiência, e que esses locais devem oferecer recursos de acessibilidade para pessoas com deficiência visual ou auditiva.

A Agência Nacional de Cinema (ANCINE) estabeleceu um prazo até 1º de Janeiro de 2023 para a regulamentação da Lei para a adaptação dos Exibidores. Agora, em 2025, dois anos depois, qual é o atual cenário?  
Como está a acessibilidade física nas salas de cinemas brasileiras? Quantos assentos especiais existem?  
Existem rampas, banheiros especiais? Quais cidades ou regiões têm o maior número de assentos especiais?  
Quais exibidores possuem o maior número de salas acessíveis?

---

## 2. **A Análise**
Para responder essas perguntas é necessário fazer uma análise de dados.  
Neste caso, foi escolhida a **Análise Descritiva de Dados**, pois é necessário explorar, organizar e apresentar informações de forma clara.

---

## 3. **Fonte dos Dados**
A Agência Nacional de Cinema (ANCINE) possui um dataset sobre a acessibilidade das salas de cinema do Brasil, disponibilizado na plataforma Kaggle em formato CSV (também presente neste repositório e na plataforma de dados abertos do Governo Federal Brasileiro).

O dataset apresenta dados sobre:
- localização dos cinemas  
- capacidade  
- recursos de acessibilidade disponíveis para pessoas com deficiência motora, auditiva e visual  

---

## 4. **Ferramenta**
Para explorar e responder às perguntas, foi utilizada a ferramenta **Microsoft Power BI**, que permite preparação, modelagem e visualização de dados em uma única plataforma.

---

## 5. **Preparação de Dados**

### 5.1 **Extração de Dados**
O arquivo CSV foi baixado da plataforma Kaggle e importado no Power BI.

---

### 5.2 **Entendimento dos Dados**
O dataset é uma tabela de dados brutos, sem padronização, com os seguintes atributos:

- **NOME_SALA:** Nome da sala de cinema  
- **REGISTRO_SALA:** Código de registro da sala na Ancine  
- **CNPJ_SALA:** Número do CNPJ da sala de cinema  
- **SITUACAO_SALA:** Indica se a sala está ativa ou inativa  
- **DATA_SITUACAO_SALA:** Data da última atualização da situação da sala  
- **DATA_INICIO_FUNCIONAMENTO_SALA:** Data de início das operações da sala  
- **ASSENTOS_SALA:** Número total de assentos disponíveis na sala  
- **ASSENTOS_CADEIRANTES:** Número de assentos reservados para cadeirantes  
- **ASSENTOS_MOBILIDADE_REDUZIDA:** Número de assentos para pessoas com mobilidade reduzida  
- **ASSENTOS_OBESIDADE:** Número de assentos adaptados para pessoas obesas  
- **ACESSO_ASSENTOS_COM_RAMPA:** Indica se há acesso por rampa para os assentos  
- **ACESSO_SALA_COM_RAMPA:** Indica se há rampa para acesso à sala  
- **BANHEIROS_ACESSIVEIS:** Indica se o complexo possui banheiros acessíveis  
- **NOME_COMPLEXO:** Nome do complexo de cinemas  
- **REGISTRO_COMPLEXO:** Código de registro do complexo na Ancine  
- **SITUACAO_COMPLEXO:** Situação atual do complexo (ativo/inativo)  
- **DATA_SITUACAO_COMPLEXO:** Data da última atualização da situação do complexo  
- **ENDERECO_COMPLEXO:** Endereço do complexo  
- **NUMERO_ENDERECO_COMPLEXO:** Número do endereço do complexo  
- **COMPLEMENTO_COMPLEXO:** Complemento do endereço  
- **BAIRRO_COMPLEXO:** Bairro onde o complexo está localizado  
- **MUNICIPIO_COMPLEXO:** Município onde o complexo está localizado  
- **CEP_COMPLEXO:** Código postal do complexo  
- **UF_COMPLEXO:** Unidade Federativa (Estado) do complexo  
- **OPERACAO_USUAL:** Informação sobre a operação habitual do complexo  
- **NOME_EXIBIDOR:** Nome da empresa exibidora  
- **REGISTRO_EXIBIDOR:** Código de registro da exibidora na Ancine  
- **CNPJ_EXIBIDOR:** Número do CNPJ da empresa exibidora  
- **SITUACAO_EXIBIDOR:** Situação atual da empresa exibidora (ativa/inativa)  
- **NOME_GRUPO_EXIBIDOR:** Nome do grupo econômico ao qual a exibidora pertence  

---

### 5.3 **Transformação de Dados**

#### 5.3.1 **Limpeza de Dados (Power Query)**
- Verificação de erros e nulos (não foram encontrados)
- Remoção de colunas desnecessárias:
  - REGISTRO_SALA, CNPJ_SALA, ENDERECO_COMPLEXO, NUMERO_ENDERECO_COMPLEXO, COMPLEMENTO_COMPLEXO, BAIRRO_COMPLEXO, MUNICIPIO_COMPLEXO, UF_COMPLEXO, OPERACAO_USUAL e REGISTRO_EXIBIDOR  
- Correção de tipos de dados:
  - Datas convertidas para formato **Data**
  - Colunas de assentos e acessos convertidas para **Número Inteiro**
- Formatação:
  - Conversão de texto para padrão de capitalização (primeira letra maiúscula)

---

#### 5.3.2 **Modelagem de Dados (DAX)**
Criação de medidas:

- **Total Assentos Especiais:** soma de ASSENTOS_SALA + ASSENTOS_CADEIRANTES + ASSENTOS_MOBILIDADE_REDUZIDA + ASSENTOS_OBESIDADE  
- **Salas com Rampa:** soma de ACESSO_SALA_COM_RAMPA  
- **Salas com Banheiros acessíveis:** soma de BANHEIROS_ACESSIVEIS  
- **Salas sem Rampa:** filtragem das salas sem rampa  
- **Salas sem Banheiros:** filtragem das salas sem banheiros  
- **Total de Salas:** contagem de NOME_SALA  
- **Média Geral de Assentos Especiais:** média do total de assentos especiais  
- **Média de Assentos por Município:** média do total de assentos especiais por município  

---

#### 5.3.3 **Visualização de Dados**
Foram criados os seguintes elementos no relatório:

- **Cards** para indicadores gerais (total de salas, assentos, assentos especiais e exibidores)
- **Gráficos de rosca** para proporção de salas com/sem acessibilidade
- **Tabelas** para relação geral de salas e status de funcionamento
- **Mapa** para localização geográfica dos dados
- **Gráfico de área** para evolução histórica de assentos
- **Gráfico de pizza** para proporção de assentos especiais vs assentos comuns
- **Gráfico de barras empilhadas** para comparação entre exibidores
- **Gráfico de colunas e linha** para comparação de assentos especiais entre exibidores e média geral

---

#### 5.3.4 **Relatório Final (Storytelling)**
O relatório apresenta:

- Introdução com estatísticas gerais das salas de cinema no Brasil
- Detalhamento sobre acessibilidade e assentos especiais
- Análise geográfica, histórica e proporcional
- Conclusão com comparativo entre exibidores e sugestões de melhoria

---

## 6. **Publicação no Power BI**
O relatório foi publicado no Power BI para visualização e compartilhamento.

---

## 7. **Insights**

1. Existem **4.695 salas de cinema** no Brasil, com **934 mil assentos**.
2. Mesmo com a legislação, o número de salas com rampas e banheiros acessíveis está em torno de **60%**.
3. As salas e assentos concentram-se principalmente na **Região Sudeste** e nas capitais.
4. A criação de assentos especiais atingiu pico em **2015** e caiu após **2023**, totalizando cerca de **33 mil assentos especiais** (≈ 3,4% do total).
5. As salas mais acessíveis estão concentradas em **grandes redes** com média acima de 6 assentos especiais.
6. As salas mais acessíveis estão localizadas principalmente no **centro-sul** e em capitais.

---

## 8. **Sugestões**
É necessário que a ANCINE retome a fiscalização e incentive a adaptação de salas, especialmente em pequenas e médias exibidoras, para garantir a universalização do acesso cultural no Brasil.

---

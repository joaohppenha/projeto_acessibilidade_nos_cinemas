###### **<u>Projeto Acessibilidade Física dos Cinemas Brasileiros</u>**

1. **O Problema:** Desde o ano 2000 O Brasil regulamenta a obrigação promoção da acessibilidade das pessoas portadoras de deficiência ou com mobilidade reduzida, mediante a supressão de barreiras e de obstáculos nas vias e espaços públicos, no mobiliário urbano, na construção e reforma de edifícios e nos meios de transporte e de comunicação a. Também, a Constituição Federal de 1988 garante o direito de acesso à Cultura como fundamental e a Lei nº 13.146/2015, conhecida como Lei Brasileira de Inclusão da Pessoa com Deficiência, dispõe que em locais como cinemas, teatros etc. devem ser reservados espaços livres e assentos para pessoa com deficiência, e que esses locais devem oferecer recursos de acessibilidade para pessoas com deficiência visual ou auditiva. A Agência Nacional de Cinema (ANCINE) estabeleceu um prazo até 1º de Janeiro de 2023 para a regulamentação da Lei para a adaptação dos Exibidores. Agora no ano de 2025, dois anos depois, qual é o atual cenário? Como está a acessibilidade física nas salas de cinemas brasileiras? Quantos assentos Especiais? Outras medidas de acessibilidade como rampas, banheiros especiais? Quais cidades ou regiões tem o maior número de assentos especiais? Quais Exibidores tem o maior número de salas mais acessíveis ou assentos especiais?  

2. **A Análise:** Para responder essas perguntas é necessário fazer uma análise de dados. Mas Qual? Nesse caso específico se faz necessário optar pela análise Descritiva de Dados, já que faz necessário explorar, organizar e apresentar informações.

3. **A Fonte Dados:** A Agência Nacional de Cinema (ANCINE) possui um dataset sobre a acessibilidade das salas de cinema do Brasil e foi disponibilizada na plataforma Kaggle em um formato de CSV (também disponível no presente repositório e na plataforma de dados abertos do Governo Federal Brasileiro). Ele apresenta dados sobre a localização dos cinemas, sua capacidade e os recursos de acessibilidade disponíveis para pessoas com deficiência motora, auditiva e visual. 

4. **Ferramenta:** Para explorar esses dados para responder perguntas foi utilizada a ferramenta PowerBI da Microsoft que permite preparação, modelagem e visualização de Dados em apenas uma aplicação.

5. **Preparação de Dados:**
   
   1. **Extração de Dados:** O Arquivo CSV foi baixado da plataforma Kaggle e importado no PowerBI.
   
   2. **Entendimento dos dados:**
      É uma tabela de dados brutos, sem tipos de dados classificados, não padronizada e com os seguintes atributos: 
      NOME_SALA: Nome da sala de cinema.
      REGISTRO_SALA: Código de registro da sala na Ancine. 
      CNPJ_SALA: Número do CNPJ da sala de cinema.
      SITUACAO_SALA: Indica se a sala está ativa ou inativa. 
      DATA_SITUACAO_SALA: Data da última atualização da situação da sala. 
      DATA_INICIO_FUNCIONAMENTO_SALA: Data de início das operações da sala. 
      ASSENTOS_SALA: Número total de assentos disponíveis na sala. 
      ASSENTOS_CADEIRANTES: Número de assentos reservados para cadeirantes. 
      ASSENTOS_MOBILIDADE_REDUZIDA: Número de assentos para pessoas com mobilidade reduzida. 
      ASSENTOS_OBESIDADE: Número de assentos adaptados para pessoas obesas.
      ACESSO_ASSENTOS_COM_RAMPA: Indica se há acesso por rampa para os assentos. 
      ACESSO_SALA_COM_RAMPA: Indica se há rampa para acesso à sala. 
      BANHEIROS_ACESSIVEIS: Indica se o complexo possui banheiros acessíveis. 
      NOME_COMPLEXO: Nome do complexo de cinemas ao qual a sala pertence.
      REGISTRO_COMPLEXO: Código de registro do complexo na Ancine. 
      SITUACAO_COMPLEXO: Situação atual do complexo (ativo/inativo). 
      DATA_SITUACAO_COMPLEXO: Data da última atualização da situação do complexo. 
      ENDERECO_COMPLEXO: Endereço do complexo de cinemas.
      NUMERO_ENDERECO_COMPLEXO: Número do endereço do complexo. 
      COMPLEMENTO_COMPLEXO: Complemento do endereço do complexo. 
      BAIRRO_COMPLEXO: Bairro onde o complexo está localizado. 
      MUNICIPIO_COMPLEXO: Município onde o complexo está localizado. 
      CEP_COMPLEXO: Código postal do complexo. 
      UF_COMPLEXO: Unidade Federativa (Estado) do complexo. 
      OPERACAO_USUAL: Informação sobre a operação habitual do complexo. 
      NOME_EXIBIDOR: Nome da empresa exibidora responsável pela sala. 
      REGISTRO_EXIBIDOR: Código de registro da exibidora na Ancine. 
      CNPJ_EXIBIDOR: Número do CNPJ da empresa exibidora.
      SITUACAO_EXIBIDOR: Situação atual da empresa exibidora (ativa/inativa).
      NOME_GRUPO_EXIBIDOR: Nome do grupo econômico ao qual a empresa exibidora pertence.
   
   3. **Transformação de Dados**
      
      1. **Limpeza de Dados:** uso da Ferramenta Power Query disponível no Power BI
         
         1. **Verificação de Erros e nulos:** executada ferramenta de detecção de nulos e erros, não foram encontrados
         
         2. **Remoção de Colunas desnecessárias:** foram removidas as colunas REGISTRO_SALA, CNPJ_SALA, ENDERECO_COMPLEXO, NUMERO_ENDERECO_COMPLEXO, COMPLEMENTO_COMPLEXO, BAIRRO_COMPLEXO, MUNICIPIO_COMPLEXO:, UF_COMPLEXO, OPERACAO_USUAL e REGISTRO_EXIBIDOR. Justificativa: não acrescentam no entendimento dos dados
         
         3. **Correção do Tipo de Dados:** DATA_SITUACAO_SALA, DATA_INICIO_FUNCIONAMENTO_SALA e DATA_SITUACAO_COMPLEXO convertidas para o formato "Data". ASSENTOS_SALA, ASSENTOS_CADEIRANTES, ASSENTOS_MOBILIDADE_REDUZIDA, ASSENTOS_OBESIDADE, ACESSO_ASSENTOS_COM_RAMPA, ACESSO_SALA_COM_RAMPA e BANHEIROS_ACESSIVEIS convertidas para o Formato "Número Inteiro"
         
         4. **Correção de Formatação:** Remoção da Caixa Alta das linhas das Tabelas e conversão para a Primeira letra como maiúscula
      
      2. **Modelagem de Dados:**
         
         1. **Medidas:** Criação de fórmulas DAX
            
            1. **Total Assentos Especiais:** **Soma do número total de Assentos Especiais:** Soma das colunas ASSENTOS_SALA, ASSENTOS_CADEIRANTES, ASSENTOS_MOBILIDADE_REDUZIDA e ASSENTOS_OBESIDADE:
            2. **Salas com Rampa:** **Soma de Acesso a salas com rampa:** Soma da Coluna ACESSO_SALA_COM_RAMPA:
            3. **Salas com Banheiros acessíveis**: **Soma de Banheiros Acessíveis:** Soma da Coluna BANHEIROS_ACESSIVEIS
            4. **Salas Sem Rampa:** Filtragem das salas sem rampa
            5. **Salas Sem Banheiros**: Filtragem das Salas sem Banheiros Especiais
            6. **Total de Salas: ** Contagem do número de Salas com função String: contagem da coluna NOME_SALA
            7. **Média Geral de Assentos especiais**: Uso da Função de média
            8. **Média de Assentos por Município:** Média do Total de Assentos especiais pela contagem de municípios
      
      3. **Visualização de Dados**
         
         1. Cards para demonstrar dados grandes gerais como total de salas, assentos, assentos especiais e exibidores
         
         2. Gráficos de rosca para demonstrar a proporção de salas com ou sem medidas de acesso ao local
         
         3. Tabela para demonstrar a relação geral de salas e de status funcionamento
         
         4. Mapa para catalogar geograficamente os dados sobre os assentos
         
         5. Grafico de área para comparação e demonstração da criação de assentos comuns e especiais de acordo com o passar do tempo
         
         6. Gráfico de Pizza pra mostrar a Proporção de Assentos especiais comparados aos assentos Comuns
         
         7. Gráfico de barras com colunas empilhadas para mostrar e comparar exibidores com os requisitos de acesso às salas
         
         8. Gráfico de colunas e linha para mostrar a comparação entre assentos especiais entre os exibidores e linha para demonstrar se estão dentro da média geral
      
      4. **Relatório Final**
         
         1. **Storytelling**: Título simples, limpo, começa apresentando estátisticasgerais sobre as salas de cinemas no Brasil, dados gerais de acessibilidade e Funcionamento. Depois aprofunda nos dados sobre os assentos de forma geral e especial por distribuição geográfica, série histórica e proporcional. Conclui com dados sobre acessibilidade física dos distribuidores estimando de forma quantitativa e qualitativa. Aqui, busca apresentar os dados de um escopo geral para o específico, para uma interpretação profunda dos dados através de indicadores para uma melhor tomada de decisões.
            ![51209346-e818-4b20-9884-0e194650f84c](file:///C:/Users/joaoh/Pictures/Typedown/51209346-e818-4b20-9884-0e194650f84c.png)
   
   4. **Publicação no PowerBI**
   
   5. **Insights**
      
      1. Cenário Atual: são 4695 salas de cinema distribuídas pelo Brasil com 934 mil assentos
      
      2. Mesmo com a Lei buscando universalizar a acessibilidade física das salas de cinema no Brasil, hoje o número de salas com acesso por meio de rampas e banheiros acessíveis estão na casa dos 60%
      
      3. Geograficamente as salas e assentos se concentram de maneira geral em maior número na região sudeste e por média nas capitais
      
      4. Da mesma maneira o cenário se repete em relação aos assentos especiais que atingem seu pico de criação no ano de 2015 por auge econômico e da indústria, também pelo estatuto da Pessoa com Deficiência. Vemos também um decrescimento depois do ano de 2023 com o fim da fiscalização sobre a regulamentação do acesso pela Ancine. No cenário atual existe o número de 33 mil assentos especiais, apenas aproximadamente 3,4% dos 934 mil assentos gerais.
      
      5. Dos exibidores com salas mais acessíveis é interessante notar que o número expressivo de salas acessíveis é concentrado em grandes redes de cinema com o número acima da média de gearl de 6 assentos especiais.
      
      6. As salas de cinemas mais acessíveis do Brasil são de Grandes Redes e grupos econômicos, em maior número no centro-sul brasileiro e em Capitais.
   
   6. **Sugestão**
      
      1. É necessário que a ANCINE volte a fiscalizar a construção e manutenção de salas acessíveis, já que a universalização ainda é distante. É preciso maior incentivo para que os pequenos e médios exibidores cumpram as medidas de inclusão, além do fomento da iniciativa pública e privada de abrir mais salas em outras regiões além do centro-sul.



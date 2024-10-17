# AtividadeFase2_Cap1_FIAP

## Introdução

Este projeto descreve a modelagem de um banco de dados para um sistema de monitoramento agrícola. O objetivo do sistema é coletar dados de sensores instalados na plantação e ajustá-los de acordo com a necessidade de água e nutrientes. Os sensores monitoram umidade, pH e nutrientes do solo. Com base nas leituras dos sensores, são feitas recomendações de ajustes para otimizar o uso dos recursos. O sistema também gera relatórios com base nesses dados para prever futuras necessidades.

## Entidades e Relacionamentos

### 1. SENSORES

A entidade `SENSORES` representa os dispositivos físicos instalados na plantação, responsáveis por coletar dados em tempo real.

- **Atributos**:
  - `ID_sensor`: Identificador único de cada sensor (Chave primária).
  - `tipo_sensor`: O tipo de sensor (umidade, pH, nutrientes).
  - `localizacao_sensor`: A localização geográfica onde o sensor está instalado.
  - `data_instalacao`: A data em que o sensor foi instalado.

- **Relacionamento**: 
  - Se relaciona com a entidade `LEITURA_SENSOR`(1:N).

### 2. LEITURA_SENSOR

A entidade `LEITURA_SENSOR` armazena os dados coletados pelos sensores em intervalos regulares.

- **Atributos**:
  - `ID_leitura`: Identificador único da leitura (Chave primária).
  - `ID_sensor`: Referência ao sensor que coletou a leitura (Chave estrangeira de `SENSORES`).
  - `valor_leitura`: O valor registrado pela leitura (umidade, pH, nutrientes).
  - `hora_leitura`: A hora em que a leitura foi feita.
  - `data_leitura`: A data em que a leitura foi feita.

- **Relacionamento**: 
  - Relaciona-se com `SENSORES` (N:1)

### 3. CULTURAS

A entidade `CULTURAS` define os diferentes tipos de plantas cultivadas e seus respectivos requisitos de água e nutrientes.

- **Atributos**:
  - `ID_culturas`: Identificador único da cultura (Chave primária).
  - `tipo_planta`: O tipo da planta cultivada.
  - `tipo_solo`: O tipo de solo onde a cultura está plantada.
  - `qtd_agua_mensal`: Quantidade ideal de água mensal para essa cultura.
  - `ph_ideal`: Valor de pH ideal para o solo dessa cultura.
  - `qtd_fosforo_mensal`: Quantidade ideal de fósforo mensal para a cultura.
  - `qtd_potassio_mensal`: Quantidade ideal de potássio mensal.
  - `qtd_npk_mensal`: Quantidade ideal de nutrientes NPK mensal.

- **Relacionamento**: 
  - Relaciona-se com `PLANTACAO` (1:N)
  - Relaciona-se com `AJUSTES` (1:N)
  - Relaciona-se com `RELATORIO` para gerar relatórios baseados nos ajustes feitos em cada plantação.

### 4. AJUSTES

A entidade `AJUSTES` armazena as modificações recomendadas no sistema de irrigação e aplicação de nutrientes com base nas leituras dos sensores.

- **Atributos**:
  - `ID_ajuste`: Identificador único do ajuste (Chave primária).
  - `ID_plantacao`: Referência à plantação onde o ajuste foi aplicado (Chave estrangeira de `PLANTACAO`).
  - `ID_culturas`: Referência à cultura ajustada (Chave estrangeira de `CULTURAS`).
  - `ID_leitura`: Referência à leitura do sensor que motivou o ajuste (Chave estrangeira de `LEITURA_SENSOR`).
  - `data_ajuste`: A data do ajuste.
  - `hora_ajuste`: A hora do ajuste.
  - `agua_ajuste`: Quantidade de água recomendada para aplicação.
  - `ph_ajuste`: Ajuste de pH recomendado.
  - `fosforo_ajuste`: Quantidade de fósforo recomendada.
  - `potassio_ajuste`: Quantidade de potássio recomendada.
  - `npk_ajuste`: Quantidade de NPK recomendada.

- **Relacionamento**:
  - Relaciona-se com `LEITURA_SENSOR` (N:1)
  - Relaciona-se com `CULTURAS` (N:1)`PLANTACAO` (N:1) para definir qual plantação e cultura foram ajustadas.

### 5. PLANTACAO

A entidade `PLANTACAO` armazena informações sobre as plantações e os dados de consumo de água e nutrientes.

- **Atributos**:
  - `ID_plantacao`: Identificador único da plantação (Chave primária).
  - `ID_culturas`: Referência à cultura que está sendo plantada (Chave estrangeira de `CULTURAS`).
  - `agua_consumida`: Quantidade de água consumida pela plantação.
  - `ph_atual`: Valor atual do pH do solo.
  - `fosforo_consumido`: Quantidade de fósforo consumida.
  - `potassio_consumido`: Quantidade de potássio consumida.
  - `npk_consumido`: Quantidade de NPK consumida.

- **Relacionamento**:
  - Relaciona-se com `CULTURAS` (N:1)
  - Relaciona-se com `AJUSTES` para vincular ajustes às plantações específicas.

### 6. RELATORIO

A entidade `RELATORIO` armazena os relatórios gerados com base nos ajustes e nas condições da plantação ao longo do tempo.

- **Atributos**:
  - `ID_relatorio`: Identificador único do relatório (Chave primária).
  - `ID_culturas`: Referência à cultura incluída no relatório (Chave estrangeira de `CULTURAS`).
  - `ID_plantacao`: Referência à plantação incluída no relatório (Chave estrangeira de `PLANTACAO`).
  - `ID_ajuste`: Referência ao ajuste que foi realizado (Chave estrangeira de `AJUSTES`).

- **Relacionamento**:
  - Relaciona-se com `AJUSTES`, `PLANTACAO`, e `CULTURAS` para coletar dados necessários para gerar os relatórios.

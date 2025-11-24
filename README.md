# ABAP – Relatório de Usuários SAP com Destaque Visual e Link para SU01D

Este projeto apresenta um relatório ABAP que permite consultar usuários
SAP, exibir informações completas em ALV, destacar visualmente contas
bloqueadas ou expiradas e acessar diretamente a transação **SU01D** por
meio de hotspot.

------------------------------------------------------------------------

## Funcionalidades

### Select dos dados

O relatório realiza leitura integrada das seguintes tabelas:

-   **USR02** -- Dados gerais do usuário
-   **USR21** -- Associação usuário ↔ número de pessoa
-   **ADRP** -- Nome completo do usuário

### Filtros Disponíveis

-   Código do usuário (**BNAME**) via `SELECT-OPTIONS`

------------------------------------------------------------------------

## Processamento de Dados

-   Mescla dos dados de USR02, USR21 e ADRP em uma única estrutura
-   Inclusão do nome completo do usuário
-   Destaca automaticamente:
    -   **Usuários bloqueados** (campo UFLAG)
    -   **Contas expiradas**, avaliando GLTGV (válido desde) e GLTGB
        (válido até)
-   Organização do código em FORM routines

------------------------------------------------------------------------

## Exibição ALV

Usando a classe `CL_SALV_TABLE`:

-   Ajuste automático de colunas
-   Funções padrão habilitadas
-   Linhas listradas (striped pattern)
-   Coloração por coluna configurada via campo **COLOR**
-   Coluna **BNAME** configurada como **hotspot**

### Hotspot (Clique no usuário)

-   Ao clicar no código do usuário, o relatório:
    -   Define o parâmetro `XUS`
    -   Abre automaticamente a transação **SU01D**
    -   Implementado via classe de eventos e método `link_click`

------------------------------------------------------------------------

## Conceitos ABAP Utilizados

-   JOIN entre USR02, USR21 e ADRP
-   Estruturas internas com campos de cor (`LVC_T_SCOL`)
-   Manipulação de ALV com eventos (`CL_SALV_EVENTS_TABLE`)
-   Uso de hotspot em célula (`IF_SALV_C_CELL_TYPE=>HOTSPOT`)
-   Organização modular do código com *FORM routines*
-   Técnicas de realce condicional (conditional formatting)

------------------------------------------------------------------------

## Objetivo

Este projeto tem como objetivo demonstrar:

-   Consulta consolidada de dados de usuários SAP
-   Avaliação automática de bloqueio e validade
-   Realce visual de situações críticas
-   Interatividade por meio de hotspot no ALV
-   Navegação direta para a SU01D
-   Boas práticas de estruturação de relatórios ABAP

------------------------------------------------------------------------

## Autor

**Murilo Valentim**

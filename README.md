# ABAP – Relatório de Usuários SAP com Destaque e Acesso Rápido ao SU01D

Este relatório ABAP permite consultar usuários SAP, destacando contas bloqueadas ou expiradas e acessar a SU01D por hotspot.

---

## Funcionalidades

- Consulta dos dados de usuários via **USR02**, **USR21** e **ADRP**
- Filtro pelo **BNAME** (User Name ID)
- Exibição em **ALV (CL_SALV_TABLE)** com:
  - Coloração automática via campo **COLOR**
  - Hotspot na coluna **BNAME**, abrindo SU01D

---

## Processamento

- Identificação e destaque de:
  - **Validade expirada** (GLTGV/GLTGB)
  - **Usuário bloqueado** (UFLAG)
- Limpeza de cores quando o usuário não estiver bloqueado
- Organização em PERFORM

---

## Eventos

- `link_click`: abre a transação **SU01D** ao clicar no BNAME

---

## Objetivo

Oferecer uma visão rápida da situação dos usuários SAP, destacando inconsistências e permitindo navegação direta para análise detalhada na SU01D.

---

## Autor

Murilo Valentim

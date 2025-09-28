# 📊 Guia de Entrada e Saída de Dados com Pandas

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-green?logo=pandas)
![Status](https://img.shields.io/badge/Status-Ativo-success)

Este repositório traz um **guia rápido e prático** dos principais **formatos de entrada e saída de dados** suportados pela biblioteca [Pandas](https://pandas.pydata.org/).  

> 🎯 Ideal para estudantes, analistas de dados e cientistas que precisam de uma **referência rápida** para salvar e carregar datasets no dia a dia.

---

## 📌 Visão Geral

- **Leitura**: `read_*` → carrega dados em um `DataFrame` ou `Series`.
- **Escrita**: `to_*` → exporta um `DataFrame` ou `Series` para o formato desejado.
- **Tipos**: os formatos podem ser **texto**, **binário** ou **SQL/Big Data**.

---

## 📑 Tabela de Formatos Suportados

| Tipo     | Formato         | Leitura           | Escrita            | Observações                          |
|----------|-----------------|-------------------|--------------------|--------------------------------------|
| Texto    | CSV             | `read_csv`        | `to_csv`           | Mais usado, simples e universal       |
| Texto    | Fixed-width     | `read_fwf`        | -                  | Colunas com largura fixa              |
| Texto    | JSON            | `read_json`       | `to_json`          | Muito usado em APIs                   |
| Texto    | HTML            | `read_html`       | `to_html`          | Extrai tabelas de páginas web         |
| Texto    | LaTeX           | -                 | `styler.to_latex`  | Formatos acadêmicos                   |
| Texto    | XML             | `read_xml`        | `to_xml`           | Dados estruturados em tags            |
| Texto    | Clipboard       | `read_clipboard`  | `to_clipboard`     | Copia/cola da área de transferência   |
| Binário  | Excel           | `read_excel`      | `to_excel`         | Planilhas do Excel                    |
| Binário  | OpenDocument    | `read_excel`      | -                  | Formato ODS                           |
| Binário  | HDF5            | `read_hdf`        | `to_hdf`           | Formato binário eficiente             |
| Binário  | Feather         | `read_feather`    | `to_feather`       | Rápido, otimizado para pandas         |
| Binário  | Parquet         | `read_parquet`    | `to_parquet`       | Big Data, colunar                     |
| Binário  | ORC             | `read_orc`        | -                  | Formato Hadoop                        |
| Binário  | MsgPack         | `read_msgpack`    | `to_msgpack`       | ⚠️ Obsoleto                           |
| Binário  | Stata           | `read_stata`      | `to_stata`         | Pacote estatístico                    |
| Binário  | SAS             | `read_sas`        | -                  | Pacote estatístico                    |
| Binário  | SPSS            | `read_spss`       | -                  | Pacote estatístico                    |
| Binário  | Pickle          | `read_pickle`     | `to_pickle`        | Formato binário do Python             |
| SQL      | SQL Databases   | `read_sql`        | `to_sql`           | MySQL, PostgreSQL, SQLite...          |
| SQL      | Google BigQuery | `read_gbq`        | `to_gbq`           | Big Data no Google Cloud              |

---

## 💻 Exemplos de Uso

# 📂 Exemplos de Leitura e Escrita com Pandas

import pandas as pd
from sqlalchemy import create_engine

# -------------------------------
# 1️⃣ CSV
# -------------------------------
df_csv = pd.read_csv("dados.csv")               # Leitura
df_csv.to_csv("dados_saida.csv", index=False)   # Escrita

# -------------------------------
# 2️⃣ JSON
# -------------------------------
df_json = pd.read_json("dados.json")                                # Leitura
df_json.to_json("dados_saida.json", orient="records", lines=True)   # Escrita

# -------------------------------
# 3️⃣ Excel (.xls / .xlsx)
# -------------------------------
df_excel = pd.read_excel("dados.xlsx", sheet_name="Planilha1")      # Leitura
df_excel.to_excel("dados_saida.xlsx", sheet_name="Planilha1", index=False)  # Escrita

# -------------------------------
# 4️⃣ SQL (SQLite / MySQL / PostgreSQL)
# -------------------------------
engine = create_engine("sqlite:///meu_banco.db")                    # Conexão

df_sql = pd.read_sql("SELECT * FROM tabela_exemplo", con=engine)   # Leitura
df_sql.to_sql("nova_tabela", con=engine, index=False, if_exists="replace")  # Escrita

# -------------------------------
# 5️⃣ Parquet (formato colunar, Big Data)
# -------------------------------
df_parquet = pd.read_parquet("dados.parquet")                       # Leitura
df_parquet.to_parquet("dados_saida.parquet", index=False)           # Escrita

# -------------------------------
# 6️⃣ Feather (rápido, otimizado para pandas)
# -------------------------------
df_feather = pd.read_feather("dados.feather")                       # Leitura
df_feather.to_feather("dados_saida.feather")                        # Escrita

# -------------------------------
# 7️⃣ Pickle (formato binário Python)
# -------------------------------
df_pickle = pd.read_pickle("dados.pkl")                              # Leitura
df_pickle.to_pickle("dados_saida.pkl")                                # Escrita




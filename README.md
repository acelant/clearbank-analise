# 🏦 ClearBank — Análise Financeira de Transações

Projeto de análise de dados desenvolvido como desafio final do módulo **Python para Análise de Dados**.

Simula o pipeline de uma fintech que recebe mensalmente um arquivo CSV de transações com dados inconsistentes e precisa validar, processar e reportar essas informações de forma confiável.

---

## 📁 Estrutura do Repositório

```
clearbank-analise/
├── desafio-final.ipynb   ← notebook principal (código + saídas salvas)
├── transacoes.csv        ← arquivo de entrada com 20 registros (15 válidos, 5 inválidos)
├── relatorio.json        ← saída gerada automaticamente pelo notebook
├── grafico.png           ← gráfico de barras empilhadas (RO2)
└── README.md
```

---

## ▶️ Como Executar

### Google Colab (recomendado)

1. Acesse [colab.research.google.com](https://colab.research.google.com)
2. Faça upload do notebook: **File → Upload notebook → seleciona `desafio-final.ipynb`**
3. Faça upload do CSV: no painel esquerdo, clique no ícone 📁 (Arquivos) → ícone de upload ⬆️ → seleciona `transacoes.csv`
4. Execute tudo: **Runtime → Run all** (ou `Ctrl+F9`)
5. Salve com as saídas: **File → Save** (ou `Ctrl+S`)

> ⚠️ O Colab não persiste arquivos entre sessões. Se fechar e reabrir, faça o upload do `transacoes.csv` novamente antes de rodar.

Para baixar os arquivos gerados (`relatorio.json` e `grafico.png`): painel de arquivos 📁 → botão direito no arquivo → **Download**.

### Jupyter Notebook local

```bash
pip install jupyter pandas matplotlib
jupyter notebook desafio-final.ipynb
```

Execute as células em ordem (`Shift+Enter`) ou use **Kernel → Restart & Run All**.

> **Pré-requisito:** `transacoes.csv` deve estar na mesma pasta do notebook.

---

## 📊 O que o Notebook Gera

| Saída | Descrição |
|-------|-----------|
| **Terminal** | Resumo de limpeza, relatório mensal formatado e listagem de transações suspeitas |
| **`relatorio.json`** | Relatório completo em JSON com métricas mensais e suspeitas |
| **`grafico.png`** | Gráfico de barras empilhadas (crédito/débito) + linha de saldo por mês |

### Exemplo de saída no terminal

```
=============================================
   🏦  CLEARBANK — ANÁLISE FINANCEIRA
=============================================
  Período analisado:
    De : 05/01/2026
    Até: 28/03/2026
    (82 dias)
---------------------------------------------
  Total transações válidas  : 15
  Total transações inválidas: 5

===== RELATÓRIO MENSAL =====

  Mês: 2026-01
    Transações  : 5
    Total crédito: R$    15.500,00
    Total débito : R$       720,40
    Saldo        : R$    14.779,60  ▲
    Média        : R$     3.244,08
    Maior valor  : R$    12.000,00
    Menor valor  : R$        89,90

===== TRANSAÇÕES SUSPEITAS =====
ID: 3 | Cliente: CLI003 | Data: 2026-01-18 | Valor: R$ 12.000,00
ID: 7 | Cliente: CLI003 | Data: 2026-02-10 | Valor: R$ 15.000,00
ID: 14 | Cliente: CLI004 | Data: 2026-03-20 | Valor: R$ 11.500,00
```

---

## ✅ Requisitos Implementados

| # | Requisito | Status |
|---|-----------|--------|
| R1 | Leitura com `csv.DictReader` (sem pandas) | ✅ |
| R2 | Validação com 5 regras + resumo de limpeza | ✅ |
| R3 | ≥ 4 funções com responsabilidade única | ✅ |
| R4 | `datetime.strptime`, extração de mês, intervalo em dias | ✅ |
| R5 | 7 métricas mensais (qtd, crédito, débito, saldo, média, maior, menor) | ✅ |
| R6 | `LIMITE_SUSPEITO = 10000.00` + listagem de suspeitas | ✅ |
| R7 | Exportação em `relatorio.json` com estrutura correta | ✅ |
| R8 | `try/except` em abertura de arquivo, conversão de valor e de data | ✅ |
| R9 | Relatório com separadores `=====`, valores em `R$`, período e totais | ✅ |
| RO1 | Análise alternativa com pandas + comparação com solução nativa | ✅ |
| RO2 | `grafico.png` — barras empilhadas crédito/débito + linha de saldo | ✅ |

---

## 🛠️ Tecnologias

- Python 3.10+
- Bibliotecas nativas: `csv`, `json`, `os`, `datetime`, `collections`
- Opcionais: `pandas`, `matplotlib`

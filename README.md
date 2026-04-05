# Limpeza de Dados de Vendas — Loja de Moda

<!-- [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SEU_USUARIO/loja-moda-limpeza-dados/blob/main/notebooks/01_limpeza_dados.ipynb) -->

## Sobre o projeto

Uma loja de roupas e calçados acumulou um ano inteiro de registros de vendas em planilhas preenchidas manualmente. O resultado: **datas em formatos diferentes, produtos duplicados com grafias inconsistentes, preços inválidos e clientes cadastrados mais de uma vez**.

Este projeto simula esse cenário real e entrega um pipeline completo de limpeza — transformando um arquivo bruto inutilizável em uma planilha organizada e pronta para análise.

---

## Problema encontrado nos dados brutos

| Problema | Descrição | Qtd. estimada |
|---|---|---|
| Linhas duplicadas | Registros repetidos por erro de digitação | ~20 linhas |
| Datas inconsistentes | 5 formatos diferentes (`dd/mm/yyyy`, `yyyy-mm-dd`, etc.) | Todas as linhas |
| Produtos duplicados | Mesmo item com variações de caixa e acentuação | 10 produtos × 3 grafias |
| Preços inválidos | Nulos, zeros, negativos e vírgula como separador decimal | ~8% das linhas |
| Pagamento inconsistente | 4 grafias para a mesma forma de pagamento | Todas as linhas |
| Clientes inconsistentes | Nomes em caixa alta misturados com normal | ~15% das linhas |
| Vendedor nulo | Registro sem identificação do vendedor | ~10% das linhas |

---

## O que foi feito

```
Dados brutos (CSV sujo)
        │
        ▼
1. Remoção de duplicatas exatas
        │
        ▼
2. Padronização de datas → formato único datetime
        │
        ▼
3. Padronização de produtos → mapeamento para nome canônico
        │
        ▼
4. Limpeza de preços → conversão, remoção de inválidos, imputação por mediana
        │
        ▼
5. Padronização de forma de pagamento e nome de cliente
        │
        ▼
6. Criação de colunas auxiliares (valor_total, mês, dia da semana)
        │
        ▼
Dataset limpo (.csv + .xlsx) pronto para análise
```

---

## Resultado

| | Antes | Depois |
|---|---|---|
| Linhas | 520 | ~500 |
| Formatos de data | 5 | 1 |
| Grafias por produto | até 4 | 1 |
| Preços inválidos | ~8% | 0% |
| Nulos em vendedor | ~10% | 0% |

---

## Estrutura do repositório

```
loja-moda-limpeza-dados/
│
├── data/
│   ├── raw/
│   │   └── vendas_brutas_loja_moda.csv
│   └── processed/
│
├── notebooks/
│
├── reports/
│   └── graficos/
│
├── .gitignore
└── README.md
```

---

## Tecnologias utilizadas

- Python 3.10+
- pandas
- python-dateutil
- openpyxl

---

## Como reproduzir

1. Clone o repositório:
```bash
git clone https://github.com/ElielSf/loja-moda-limpeza-dados.git
```

2. Abra o notebook no Google Colab pelo botão acima ou localmente:
```bash
pip install pandas python-dateutil openpyxl
jupyter notebook notebooks/01_limpeza_dados.ipynb
```

3. Execute as células em sequência. O dataset limpo será salvo na pasta `data/processed/`.

---

## Sobre este projeto

Este projeto faz parte do meu portfólio de análise de dados, com foco em **limpeza e organização de dados para pequenos negócios**.

Se você tem planilhas desorganizadas e precisa transformá-las em informação útil, entre em contato:

- GitHub: [ElielSf](https://github.com/ElielSf)
- LinkedIn: [Eliel Souza](https://linkedin.com/in/eliel-souza-ferreira)

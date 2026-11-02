# Análise de Saúde Mental de Estudantes Internacionais (SQL)

Projeto de estudo baseado em um caso do **DataCamp**, com dados de estudantes de uma universidade no Japão.

## Objetivo

Comparar as médias de depressão, conexão social e estresse de aculturação de estudantes internacionais conforme o tempo de permanência (`stay`). Usei este projeto para praticar agregações, filtros e agrupamentos em SQL.

## Tecnologias e conceitos

- **Linguagem:** SQL (PostgreSQL)
- **Ferramentas:** VS Code e DBeaver
- **Conceitos:** `AVG`, `ROUND`, `COUNT`, `WHERE`, `GROUP BY` e `ORDER BY`

## Dados

Principais colunas do arquivo `students.csv`:

- `inter_dom`: tipo de estudante (internacional ou doméstico)
- `stay`: tempo de permanência
- `todep`: pontuação total de depressão (PHQ-9)
- `tosc`: pontuação total de conexão social (SCS)
- `toas`: pontuação total de estresse de aculturação (ASISS)

## Consulta

```sql
SELECT
    stay,
    COUNT(*) AS total_students,
    ROUND(AVG(todep), 2) AS average_phq,
    ROUND(AVG(tosc), 2) AS average_scs,
    ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
```

## Resultado

Os grupos de 1 a 4 anos reúnem 194 dos 201 estudantes internacionais. Os demais têm no máximo 3 estudantes cada, então não servem para comparação.

| Permanência | Estudantes | Depressão | Conexão social | Estresse de aculturação |
| --- | ---: | ---: | ---: | ---: |
| 4 anos | 14 | 8,57 | 33,93 | 87,71 |
| 3 anos | 46 | 9,09 | 37,13 | 78,00 |
| 2 anos | 39 | 8,28 | 37,08 | 77,67 |
| 1 ano | 95 | 7,48 | 38,11 | 72,80 |

Nesses dados, o grupo de 4 anos tem o maior estresse de aculturação e a menor conexão social. A depressão média é maior em 2, 3 e 4 anos do que em 1 ano, mas não sobe a cada ano.

## Limitações

A análise é descritiva. Não usei teste estatístico, o grupo de 4 anos é pequeno e os dados não mostram relação de causa.

---

Projeto de Lilian Marques, pós-graduada em Ciência de Dados.

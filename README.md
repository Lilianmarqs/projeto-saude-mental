# 🎓 Análise de Saúde Mental de Estudantes Internacionais (SQL)

Este projeto foi desenvolvido com base em um estudo de caso do **DataCamp**, focado em analisar o impacto da vida acadêmica na saúde mental de estudantes de uma universidade no Japão.

### 🎯 Objetivo do Projeto
O objetivo principal é investigar se a duração da estadia (`stay`) de estudantes internacionais influencia seus níveis de depressão, ansiedade e suporte social. Como estou em transição para a área de **Dados**, utilizei este projeto para aplicar técnicas avançadas de manipulação de dados e extração de insights.

### 🛠️ Tecnologias e Conceitos Aplicados
* **Linguagem:** SQL (PostgreSQL)
* **Ferramentas:** VS Code / DBeaver
* **Conceitos:** Agregações (`AVG`, `ROUND`), Filtros Complexos, Ordenação e Agrupamento (`GROUP BY`).

### 📑 Estrutura do Dataset
O arquivo `students.csv` contém as seguintes métricas principais:
* `inter_dom`: Categoria do estudante (Internacional ou Doméstico).
* `stay`: Tempo de permanência na universidade.
* `todep`: Score de depressão (PHQ-9).
* `tosc`: Score de suporte social (SCS).
* `toas`: Score de ansiedade (ASISS).

### 🔍 Consulta Principal (SQL)

Abaixo, a query desenvolvida para calcular as médias de saúde mental, focando exclusivamente no grupo de maior interesse para o estudo: os estudantes internacionais.

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


Projeto desenvolvido por Lilian Estudante de Pós-graduação em Ciência de Dados
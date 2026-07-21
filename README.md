# Panorama do Setor de Locadoras de Veículos no Brasil (2016 - 2025)

## Visão Geral do Projeto

Este projeto consiste em uma solução analítica de Business Intelligence desenvolvida no Power BI para mapear e analisar a evolução do mercado de locação de veículos no Brasil entre 2016 e 2025.

O painel foi estruturado para atender a três pilares fundamentais de decisão executiva:

* **Saúde Financeira:** Desempenho de faturamento bruto, faturamento líquido e crescimento anual (YoY).
* **Análise de Frota e Market Share:** Composição das compras de veículos por fabricante (montadora) e distribuição por subsegmentos de mercado.
* **Impacto Socioeconômico:** Geração de empregos diretos (demografia por gênero e nível de escolaridade) e evolução da base total de usuários do setor.

---

## Tecnologias e Recursos Utilizados

* **Ferramenta de BI:** Power BI Desktop
* **Linguagem de Análise:** DAX (Data Analysis Expressions)
* **Modelagem de Dados:** Star Schema rigoroso (Relacionamentos 1:N integrando a dimensão temporal central d_ano e as dimensões de negócio d_fabricante, d_subsegmento e d_locadoras)
* **Recursos Avançados de UX/UI:**
* Drillthrough funcional por Fabricante (página detalhada para análise individual de montadoras).
* Tooltips customizados dinâmicos em página para acompanhamento histórico YoY.
* Rótulos de dados dinâmicos via DAX programados para destacar exclusivamente as extremidades temporais (primeiro e último ano da série).
* Ranking dinâmico por contexto temporal com tratamento para empates e ordenação de mercado.
* Navegação por botões e padronização gráfica executiva.



---

## Arquitetura e Governança de Dados

* **Tratamento de Contexto Temporal:** Implementação de inteligência de tempo em DAX utilizando `SELECTEDVALUE` e `MAX` para travar o contexto dinâmico no último ano com dados consolidados (2025) quando a opção "Todos" estiver selecionada nos filtros temporais.
* **Governança e Granularidade das Fontes:** As bases de emplacamento de origem foram disponibilizadas em tabelas agregadas independentes (por Fabricante e por Subsegmento). A filtragem cruzada entre essas dimensões é gerenciada através do contexto da dimensão temporal central (`d_ano`).

---

## Principais Insights de Negócio

* **Desempenho Financeiro:** O setor atingiu a marca de R$ 53,90 bilhões em faturamento líquido em 2025, representando uma expansão de 16,67% em relação ao ano anterior.
* **Liderança de Mercado:** A Fiat liderou as aquisições do setor com 28,95% de share (182 mil unidades emplacadas em 2025), seguida pela Volkswagen com 24,07% (151 mil unidades) e Chevrolet com 15,01% (94 mil unidades).
* **Participação do Setor:** As compras efetuadas pelas locadoras representam 24,65% do total de veículos emplacados no mercado automotivo nacional.
* **Impacto Social:** O setor movimenta mais de 82,3 milhões de usuários e gera cerca de 110 mil empregos diretos, com forte representatividade no segmento de Ensino Médio Completo (71 mil colaboradores).

---

## Estrutura do Repositório

```text
projeto-locadoras-bi/
│
├── data/                        # Arquivos CSV / Bases de dados de origem
│   ├── f_faturamento_brasil.csv
│   ├── f_emplacamento_por_fabricante.csv
│   └── ...
│
├── dashboard/                   # Arquivo principal do Power BI
│   └── projeto_locadoras.pbix
│
├── docs/                        # Imagens do relatório para documentação
│   ├── relatorio_analitico_executivo.pdf
│   ├── visao_geral_financeira.png
│   ├── analise_frota_market_share.png
│   └── impacto_socioeconomico.png
│
└── README.md                    # Documentação técnica e de negócio do projeto

```

---

## Como Visualizar o Projeto

### Dashboard Online (Versão Interativa)

Você pode navegar e interagir diretamente com o painel publicado no Power BI Service pelo link:

**[Acessar Dashboard Interativo no Power BI Web](https://app.powerbi.com/view?r=eyJrIjoiZDQ0NGJhODYtNDFhOS00M2U4LWI1M2YtNTk0MjU4NmFiMDQ1IiwidCI6ImIyZTE2Mjk3LTJlZDYtNDFiOC1iODIyLWE5NTRlOTViZDJmMCIsImMiOjR9&pageName=584d5182be693bbefced)**
**[Visualizar Relatório Executivo Completo em PDF](./docs/relatorio_analitico_executivo.pdf)**

---

### Execução Local (Power BI Desktop)

1. Clone este repositório para o seu ambiente local.
2. Acesse a pasta `dashboard/` e abra o arquivo `projeto_locadoras.pbix` no Power BI Desktop.
3. Certifique-se de que as bases contidas na pasta `data/` estejam conectadas corretamente.

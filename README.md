# 🏎️ Porsche Sales Dashboard

Dashboard interativa de análise de vendas Porsche, com 100 registros de vendas em território americano. Publicada via GitHub Pages.

## Perguntas de Negócio

| # | Pergunta | Gráfico | Por quê |
|---|----------|---------|---------|
| 1 | **Quais estados concentram mais vendas e receita?** | Barras duplas (vendas + receita por estado) | Identificar regiões de maior desempenho comercial para direcionar estratégias regionais |
| 2 | **Como os métodos de pagamento se distribuem?** | Doughnut (participação de cada método) | Entender preferências de pagamento para otimizar checkout e ofertas de financiamento |
| 3 | **Qual a relação entre ano do modelo e preço médio?** | Barras (preço médio por ano do modelo) | Validar se modelos mais novos realmente têm preço médio mais alto e identificar anomalias |

## Filtros Disponíveis

- Modelo
- Ano do Modelo
- Estado
- Método de Pagamento
- Botão "Limpar Filtros" para resetar todos os recortes

## Indicadores de Topo (KPIs)

- Total de vendas no recorte
- Receita total
- Ticket médio
- Modelo líder (% de participação)
- Ano com mais vendas (% de participação)

## Tratamento da Base

A planilha base (Porsche sanitizada) passou por:

1. **Seleção de colunas sanitizadas** — mantidas apenas as versões limpas dos dados (data, modelo, ano, cidade, estado, pagamento, preço, status)
2. **Conversão de tipos** — preço convertido para número (float), ano para inteiro
3. **Padronização de datas** — datas vazias preservadas como "Sem data" para não perder registros
4. **Embedding no HTML** — dados serializados como array JS diretamente no `index.html`, eliminando dependência de servidor ou arquivo externo

## Como foi feito

### Abordagem: Agente com skill própria (Hermes Agent)

Optei por criar a dashboard via **Hermes Agent** (Não usei ChatGPT Canvas), com uma skill dedicada para montagem de dashboards HTML com dados embutidos.

### Processo

1. **Extração dos dados** do HTML de referência do desafio (curl no raw do repo DIO)
2. **Definição das 3 perguntas de negócio** com base na análise exploratória dos campos disponíveis
3. **Geração do HTML** com:
   - Chart.js para os 3 gráficos (barras duplas, doughnut, barras)
   - Design responsivo com glassmorphism e paleta escura inspirada no branding Porsche
   - Filtros por select que recalculam todos os indicadores e gráficos
   - Tabela com as 15 vendas mais recentes do recorte
4. **Refinamento** — ajuste de títulos, cores, responsividade e formatação dos tooltips

### Diferenças em relação à referência DIO

- **Perguntas diferentes**: a referência usa modelos por cidade / ano com maior saída / vendas por estado; aqui foquei em estados com receita, pagamentos e preço médio por ano
- **Design próprio**: paleta escura com acentos vermelho/dourado, glassmorphism nos cards, gradiente sutil
- **3º gráfico de linha do tempo substituído por barras de preço médio** — pergunta mais analítica

## Tecnologias

- **Chart.js** — gráficos interativos (CDN)
- **HTML/CSS vanilla** — sem frameworks, design responsivo
- **JavaScript puro** — toda a lógica de filtragem, agregação e renderização

## Estrutura do Projeto

```
porsche-dashboard/
├── index.html   # Dashboard completa (dados + lógica + estilo)
└── README.md    # Documentação
```

## Publicação

Dashboard publicada no GitHub Pages: https://everferreira.github.io/porsche-dashboard/

---

⌨️ com 💜 por **Ever Ferreira** · Desafio DIO "Criando uma Dashboard da Porsche com Agentes de IA"
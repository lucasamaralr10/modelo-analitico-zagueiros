# Métrica Defensiva Autoral & Inteligência de Mercado para Tomada de Decisão Estratégica

Este repositório apresenta o desenvolvimento de um projeto prático de *Football Analytics*, simulando a atuação de um **Analista de Dados e Scout Profissional**. O objetivo central é integrar modelagem estatística aplicada, engenharia de features e contexto esportivo real para embasar decisões estratégicas de alta complexidade em clubes de futebol.

O projeto foi estruturado em duas etapas críticas de inteligência de negócios:
1. **Construção de Métrica Autoral (DefScore):** Desenvolvimento de um indicador sintético multicritério em Python para avaliar e ranquear o desempenho técnico e a eficiência de zagueiros centrais no futebol brasileiro, mitigando vieses através de ajustes contextuais e de posse de bola (PAdj).
2. **Scout e Prospecção Estratégica de Mercado:** Aplicação prática do modelo analítico em um cenário competitivo real de mercado. Com base no orçamento esperado e nas restrições financeiras fornecidas, foi desenhada uma estratégia de contratações estruturada em listas táticas complementares: 5 alvos de elite para assumir a titularidade imediata e 5 alvos custo-benefício voltados para a composição profunda de elenco.

## 🛠️ Arquitetura Técnica e Tecnologias
* **Linguagem Principal:** Python 3
* **Manipulação e Engenharia de Dados:** Pandas e NumPy
* **Modelagem Estatística:** Scipy (Z-Score) e Scikit-Learn (MinMaxScaler)
* **Visualização de Dados:** Matplotlib, Seaborn e Plotly Express (Gráficos Interativos de Dispersão e Radar)
* **Ambiente de Desenvolvimento:** Google Colab / Jupyter Notebooks

## 📊 Engenharia de Features e Metodologia Científica

Diferente de análises tradicionais que apenas contabilizam ações absolutas, este modelo mitiga vieses estruturais do jogo através de quatro pilares matemáticos:

1. **Padronização Volumétrica (Métricas por 90 Minutos):** Todas as variáveis defensivas foram relativizadas pelo tempo real de exposição em campo, permitindo a comparação justa entre atletas com diferentes volumes de minutos jogados.
2. **Ajuste por Contexto de Posse de Bola (Possession-Adjusted Stats - PAdj):** Elemento central para evitar a subavaliação de defensores pertencentes a equipes dominantes. As métricas reativas (desarmes, interceptações, bloqueios e cortes) foram normalizadas pelo tempo de não-posse coletiva da equipe (`100 - Poss`).
3. **Impacto Aéreo Contextualizado (Aerial Score):** Indicador autoral que combina a eficiência percentual de duelos aéreos ganhos (`Won%`), o volume individual por 90 minutos (`Won_per90`) e a taxa de exposição coletiva a cruzamentos sofridos pela equipe (`Crosses Faced`).
4. **Protagonismo Intragrupo via Z-Score (Aerial Participation):** Ponderação estatística que mede a taxa de contribuição aérea do atleta em relação aos seus pares de elenco, identificando os reais líderes do setor defensivo de cada clube de forma isolada.

---

## ⚖️ Definição das Variáveis e Distribuição de Pesos

O **DefScore** foi estruturado através de uma modelagem multicritério baseada nas demandas táticas modernas da posição:

| Métrica | Peso | Justificativa Técnico-Tática |
| :--- | :---: | :--- |
| `def3rd_eff` | **35%** | Principal indicador de impacto defensivo direto; combina volume PAdj e taxa de sucesso técnico em desarmes (`Tkl%`). |
| `Int_adj` | **20%** | Mede a leitura tática, antecipação e capacidade preditiva de quebra de linhas de passe adversárias. |
| `Aerial_Score` | **15%** | Domínio e impacto contextualizado em situações de bola aérea defensiva. |
| `block_sh_adj` | **15%** | Ação reativa crucial para a contenção e bloqueio de finalizações iminentes a gol. |
| `Clr_adj` | **15%** | Capacidade de alívio de pressão sob zonas de risco crítico dentro da área. |

*Filtro de Elegibilidade:* O modelo aplicou um corte amostral para atletas com idade $\le 35$ anos e volume mínimo de **798 minutos** em campo, garantindo significância estatística e a inclusão representativa de atletas regulares na competição.

---

## 🎯 Prospecção de Mercado e Inteligência de Negócios

O modelo final foi submetido a uma esteira de visualização iterativa para simular tomadas de decisão reais de departamentos de mercado e Scout corporativo, dividindo os alvos em dois perfis estratégicos:

### Perfil A: Alvos de Elite para Titularidade
Focado em mapear zagueiros prontos para assumir protagonismo imediato em equipes de alto investimento. Os radares demonstram atletas com preenchimento multidimensional completo em eficiência no terço defensivo, interceptações e imposição aérea.

### Perfil B: Alvos Custo-Benefício para Composição de Elenco
Mapeamento de atletas subavaliados pelo mercado tradicional, mas que apresentam excelente eficiência em métricas específicas (como alto volume de cortes e bloqueios ajustados), servindo como excelentes opções de profundidade de elenco e eficiência orçamentária.

---

## 📈 Como Executar o Projeto
1. Certifique-se de possuir as bases brutas do Brasileirão (`DEFENSE_BRASILEIRAO.xlsx`, `MISC_BRASILEIRAO.xlsx`, etc.) no mesmo diretório local ou ambiente virtual do script.
2. Execute as células sequencialmente em qualquer ambiente Jupyter ou Google Colab.

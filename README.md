# Tech Challenge Fase 1 — Análise de Satisfação do Cliente (NPS) em E-commerce

## Visão Geral do Projeto

Este projeto tem como objetivo analisar os fatores operacionais que impactam a satisfação do cliente em um cenário de e-commerce utilizando o indicador Net Promoter Score (NPS).

A proposta é transformar dados de pedidos, logística e atendimento ao cliente em insights acionáveis capazes de apoiar decisões estratégicas e operacionais antes da aplicação da pesquisa de satisfação.

O projeto foi desenvolvido como parte do Tech Challenge – Fase 1 do curso de AI Scientist.

---

## Objetivos do Projeto

Este projeto foi estruturado em três etapas principais:

- Entendimento do problema de negócio;
- Definição da variável target de satisfação;
- Análise exploratória dos dados com foco em geração de insights para o negócio.

Como objetivo complementar, o projeto também apresenta a possibilidade de aplicação futura de modelos preditivos para antecipação de risco de insatisfação.

---

## Base de Dados

A base utilizada contém informações históricas relacionadas a:

- pedidos realizados
- tempo de entrega
- atrasos logísticos
- interações com atendimento
- tempo de resolução de problemas
- número de reclamações
- recompra em 30 dias
- score interno de satisfação (CSAT)
- nota de satisfação do cliente (NPS)

Principais variáveis analisadas:

- `delivery_delay_days`
- `customer_service_contacts`
- `resolution_time_days`
- `complaints_count`
- `order_value`
- `freight_value`
- `repeat_purchase_30d`
- `csat_internal_score`
- `nps_score`

A variável `nps_score` foi utilizada como indicador principal de satisfação do cliente.

---

## Definição da Variável Target

A variável target adotada neste projeto foi:
nps_score


Essa variável representa a percepção final do cliente após a experiência de compra e permite segmentar clientes em:

- Promotores
- Neutros
- Detratores

O NPS é amplamente utilizado no mercado como indicador estratégico de fidelização e crescimento sustentável em e-commerce.

---

## Limitações do Indicador NPS

Apesar de sua relevância estratégica, o NPS apresenta algumas limitações:

- é coletado após a experiência do cliente
- não permite ação preventiva isoladamente
- depende de percepção subjetiva
- pode sofrer viés de resposta

Por isso, neste projeto o NPS foi analisado em conjunto com dados operacionais para permitir identificação de oportunidades de atuação preventiva.

---

## Metodologia Utilizada

O projeto foi desenvolvido em três etapas principais:

### 1.Entendimento do Negócio

Identificação do problema estratégico relacionado à variabilidade da experiência do cliente no e-commerce.

Avaliação do impacto do NPS em:

- recompra
- fidelização
- reputação da marca
- crescimento sustentável

---

### 2.Preparação dos Dados

Nesta etapa foram realizadas:

- inspeção da base
- verificação de tipos de dados
- identificação de valores ausentes
- criação de variáveis auxiliares
- padronização de estrutura para análise

---

### 3.Análise Exploratória (EDA) com Foco em Negócio

A análise exploratória foi conduzida com foco em geração de insights acionáveis para o negócio.

Principais análises realizadas:

- impacto do atraso logístico no NPS
- impacto do número de contatos com atendimento
- impacto do tempo de resolução
- impacto do número de reclamações
- identificação do ponto de ruptura da experiência
- análise do perfil dos clientes detratores

---

## 4.Principais Insights Identificados

Os principais fatores associados à insatisfação do cliente foram:

### Atraso Logístico

Clientes com atraso na entrega apresentam redução significativa no NPS.

O atraso foi identificado como principal driver de detratores.

---

### Contato com Atendimento

Quanto maior o número de contatos com atendimento, menor tende a ser o nível de satisfação do cliente.

O atendimento aparece como indicador de fricção na jornada.

---

### Ponto de Ruptura da Experiência

O momento mais crítico ocorre quando:
atraso logístico + necessidade de atendimento


Nesse cenário aumenta significativamente a probabilidade do cliente se tornar detrator.

---

### Perfil dos Clientes Detratores

Clientes detratores apresentam maior:

- atraso logístico
- número de contatos com suporte
- tempo de resolução
- número de reclamações

A insatisfação normalmente ocorre pelo acúmulo de fricções operacionais ao longo da jornada.

---

## Aplicação Estratégica dos Resultados

Os insights obtidos permitem apoiar decisões nas seguintes áreas:

### Logística

Redução de atrasos de entrega

### Atendimento

Identificação antecipada de clientes em risco

### Customer Experience

Atuação preventiva antes da pesquisa de satisfação

### Estratégia

Priorização de investimentos operacionais com maior impacto na satisfação

---

## Modelagem Preditiva
 
Foi proposta uma abordagem para antecipar clientes com risco de insatisfação.
 
Estratégia adotada:
 
Modelo de classificação para prever risco de detrator.
 
Modelos testados:
Regressão Logística
Random Forest
Gradient Boosting
Critério de escolha:
Prioridade para Recall, pois o objetivo é identificar clientes em risco
Resultado:
 
O modelo selecionado apresentou melhor desempenho na identificação de clientes com potencial de se tornarem detratores.

Produto Analítico Proposto
 
A modelagem foi transformada em um produto operacional:
 
🔹 Score de risco
 
Probabilidade de um cliente se tornar detrator
 
🔹 Segmentação de clientes
Segmento	Critério	Interpretação
Crítico	≥ 75%	Alta chance de detrator
Atenção	50%–74%	Sinais relevantes de fricção
Monitoramento	30%–49%	Risco moderado
Regular	< 30%	Baixo risco
🔹 Regra de ação operacional
Segmento	Ação recomendada
Crítico	Atendimento imediato + comunicação proativa
Atenção	Monitorar pedido + contato preventivo
Monitoramento	Acompanhar indicadores
Regular	Fluxo padrão
🔹 Fila de priorização
 
O modelo permite gerar diariamente uma lista de clientes com maior risco, permitindo:
 
Priorizar atendimento
Antecipar comunicação
Reduzir detratores
Melhorar experiência do cliente

---

## Estrutura do Repositório
```bash
.
├── data/
│ ├── raw/
│ │ └── desafio_nps_fase_1.csv
│
├── notebooks/
│ ├── 01_entendimento_negocio.ipynb
│ ├── 02_tratamento_dados.ipynb
│ ├── 03_analise_exploratoria_eda.ipynb
│ └── 04_modelo_preditivo.ipynb
│
├── models/
│ ├── best_model.pkl
│ ├── model_results.csv
│ ├── risk_segments.csv
│ └── README_models.md
│
├── reports/
│ └── apresentacao/
│
├── README.md
├── requirements.txt
└── .gitignore

---

## Como Reproduzir a Análise

1 Clone o repositório
git clone https://github.com/ellenpaulotiago/tech_challenge_fase1.git


2 Acesse a pasta do projeto
cd tech_challenge_fase1-main


3 Instale as dependências
pip install -r requirements.txt


4 Execute os notebooks na pasta:
notebooks/


Seguindo a ordem numérica dos arquivos.

---

## Resultados Esperados

A análise permite:

- identificar fatores operacionais que impactam o NPS
- compreender o perfil dos detratores
- identificar o ponto de ruptura da experiência do cliente
- apoiar decisões estratégicas baseadas em dados

---

## Autoria

Projeto desenvolvido como parte do Tech Challenge – Fase 1  
Curso AI Scientist
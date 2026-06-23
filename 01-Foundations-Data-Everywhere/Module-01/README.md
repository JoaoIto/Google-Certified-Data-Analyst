# Módulo 1: Introdução à Análise de Dados e Pensamento Analítico

**Navegação Rápida**
- [Voltar para o Curso](../README.md)
- [Voltar para o Sumário Global](../../README.md)
- [Acessar Glossário Técnico do Módulo](./glossary.md)

**Sumário do Módulo**
- [1. Tipologia de Dados Básica](#1-tipologia-de-dados-básica)
- [2. O Processo de Análise de Dados (Framework de 6 Fases)](#2-o-processo-de-análise-de-dados-framework-de-6-fases)
- [3. Estudo de Caso: Retenção de Funcionários (People Analytics)](#3-estudo-de-caso-retenção-de-funcionários-people-analytics)
- [4. Estudo de Caso: Contribuição para Aposentadoria](#4-estudo-de-caso-contribuição-para-aposentadoria)
- [5. Origens e Evolução do Processo de Análise de Dados](#5-origens-e-evolução-do-processo-de-análise-de-dados)
- [6. Pensamento Analítico e Análise de Causa Raiz](#6-pensamento-analítico-e-análise-de-causa-raiz)
- [7. Casos Avançados de Decisões Orientadas a Dados](#7-casos-avançados-de-decisões-orientadas-a-dados)

---

## 1. Tipologia de Dados Básica

Antes de iniciar qualquer modelagem ou análise técnica, é imperativo compreender a classificação dos dados manipulados. Em ciência e análise de dados, os quatro tipos mais comuns encontrados são:

| Tipo de Dado | Definição Técnica | Exemplos Práticos |
| :--- | :--- | :--- |
| **Numéricos (Numéricos/Inteiros/Flutuantes)** | Valores quantitativos que podem ser medidos, contados e submetidos a operações matemáticas lógicas. | Preço, altura, idade, quantidade em estoque. |
| **Texto (Strings)** | Cadeias de caracteres (letras, símbolos e números que não operam matematicamente). Usados como identificadores nominais. | Nome de produto, endereço, número de CPF, IDs de registro. |
| **Data e Hora (Datetime/Timestamp)** | Representam um ponto fixo no tempo. Fundamentais para indexação temporal e rastreamento de tendências (*Time Series*). | Data de nascimento, data de faturamento, carimbo de log (timestamp). |
| **Categóricos (Fatores/Dimensões)** | Dados divididos em grupos, categorias ou conjuntos discretos. Agrupam características qualitativas. | Cores (vermelho, azul), Status (Ouro, Prata), Nível (Bom, Ruim). |

### 1.1. Prática de Reconhecimento de Dados
*Exemplo de Tabela de Pedidos de Clientes (Dataset de Amostra)*

| ID do Pedido (String) | Nome do Produto (String) | Quantidade (Numérico) | Data do Pedido (Datetime) | Classificação do Cliente (Categórico) |
| :--- | :--- | :--- | :--- | :--- |
| 1001 | Fones de ouvido sem fio | 2 | 2025-07-01 | 5 |
| 1002 | Relógio inteligente | 1 | 2025-07-05 | 4 |
| 1003 | Alto-falante portátil | 3 | 2025-06-28 | Excelente (Inconsistência) |
| 1004 | Cabo USB-C | 5 | 2025-07-10 | 3 |
| 1005 | Disco rígido externo | 1 | 2025-07-12 | *Nulo/Missing* |
| 1006 | Mouse para jogos | 1 | 2025-07-15 | 2 |

**Observação de Qualidade de Dados:** Na análise da tabela acima, o pedido `1003` apresenta uma anomalia na coluna "Classificação", mesclando tipos numéricos e strings ("Excelente"). O pedido `1005` possui um dado ausente (Missing Value).

---

## 2. O Processo de Análise de Dados (Framework de 6 Fases)

A análise de dados segue um fluxo lógico estruturado projetado para transformar perguntas corporativas em tomadas de decisão bem fundamentadas.

| Fase | Descrição da Operação | Objetivos Técnicos |
| :--- | :--- | :--- |
| **1. Perguntar (Ask)** | Compreensão do desafio corporativo ou da pergunta investigativa. | Interação com *stakeholders*; definição de métricas de sucesso e formulação de perguntas precisas. |
| **2. Preparar (Prepare)** | Identificação, coleta e validação das fontes de dados primárias e secundárias. | Governança de dados; seleção de bancos; estabelecimento de credenciais de acesso e segurança. |
| **3. Processar (Process)** | Higienização, transformação e formatação do dataset (Data Cleansing). | Remoção de anomalias, tratamento de nulos (*missing data*), deduplicação e tipagem de colunas. |
| **4. Analisar (Analyze)** | Exploração matemática e estrutural para descoberta de padrões (Data Mining). | Cálculos agregados, estatística descritiva, junções de tabelas e cruzamento de variáveis lógicas. |
| **5. Compartilhar (Share)** | Tradução dos *insights* analíticos para relatórios e *dashboards* visuais. | Data Storytelling; criação de gráficos interativos para consumo executivo (Tableau, PowerBI). |
| **6. Agir (Act)** | Execução estratégica baseada em evidências algorítmicas ou analíticas. | Implementação de mudanças nos processos de negócio com base na análise comprovada. |

> **Nota Técnica sobre Iteração:** O fluxo não é estritamente linear. Descobrir erros na fase de *Analisar* pode requerer retorno à fase de *Processar* ou até mesmo de *Perguntar*. A revisão contínua garante a integridade dos resultados.

---

## 3. Estudo de Caso: Retenção de Funcionários (People Analytics)

O conceito de *People Analytics* (ou Análise de Recursos Humanos) aplica o processo de análise de dados sobre a força de trabalho para otimizar processos internos.

**Contexto do Problema:** Alta taxa de rotatividade (*turnover*) de novos contratados antes de completar 1 ano de empresa.

* **Perguntar:** "O que causa insatisfação?", "A retenção está ligada ao treinamento ou ao processo de contratação?".
* **Preparar:** Elaboração de uma pesquisa de clima organizacional. Definição de regras rigorosas de privacidade (*Data Privacy*), anonimizando salários e focando em agregações de grupo.
* **Processar:** Recebimento das respostas e limpeza do conjunto de dados para eliminar respostas incompletas. Migração dos dados brutos para um Data Warehouse seguro com acesso restrito.
* **Analisar:** O cruzamento de dados identificou que:
  1. Processos de contratação longos correlacionavam-se com alta probabilidade de desligamento prematuro.
  2. Processos de *feedback* transparentes resultavam em altas taxas de retenção.
* **Compartilhar:** Resultados consolidados foram direcionados exclusivamente a gestores responsáveis em formato de relatórios de fácil visualização, focados no desempenho de seus times (sem expor indivíduos).
* **Agir:** A corporação padronizou o processo de integração (*onboarding*) e estipulou a medição anual das taxas para garantir a melhoria contínua.

---

## 4. Estudo de Caso: Contribuição para Aposentadoria

**Contexto do Problema:** Baixa adesão corporativa ao fundo de aposentadoria recém-lançado pela empresa de tecnologia Geo-Flow, Inc.

* **Perguntar:** A adesão é baixa por falha de comunicação? A empresa deveria investir em treinamentos internos?
* **Preparar:** Extração de relatórios estruturados do sistema de RH (demografia, hierarquia salarial e taxa atual de participação).
* **Processar:** Filtragem ativa: remoção de funcionários já aposentados e ex-colaboradores (dados sujos). Agrupamento dos dados limpos por idade e departamento.
* **Analisar:** A estratificação demográfica expôs que nichos específicos de funcionários ignoravam a existência da equivalência monetária paga pela empresa.
* **Compartilhar:** Gráficos de dispersão e gráficos de barras foram utilizados para comprovar visualmente à diretoria que grupos específicos não estavam consumindo o benefício.
* **Agir:** Lançamento de um treinamento educacional direcionado *apenas* às demografias com baixa adoção, economizando custos de treinamento em massa e gerando um pico histórico de adesão ao plano.

---

## 5. Origens e Evolução do Processo de Análise de Dados

Embora os princípios básicos se originem de metodologias dos escribas do Antigo Egito (que compilavam dados e cálculos demográficos em papiros estruturados), não existe apenas uma arquitetura única de análise de dados no mercado moderno.

Principais Frameworks Históricos e Corporativos:

1. **Framework Google Data Analytics:** (Perguntar, Preparar, Processar, Analisar, Compartilhar, Agir). Focado fortemente em governança e comunicação executiva.
2. **Processo Dell EMC (Data Science):** Iterativo de seis passos focado no rigor algorítmico: (Descoberta, Pré-processamento, Planejamento de modelo, Construção de modelo, Comunicação, Operacionalização).
3. **Ciclo Iterativo SAS:** Comumente desenhado como um loop infinito para sublinhar repetição contínua: (Perguntar, Preparar, Explorar, Modelar, Implementar, Agir, Avaliar).
4. **Data Analytics Lifecycle (Baseado em Projetos):** (Identificação do problema, Design de requisitos, Pré-processamento, Análise, Visualização). Um funil operacional direto e curto.
5. **Arquitetura Big Data (Thomas Erl):** 9 etapas meticulosas com foco massivo na pipeline de engenharia pesada (Aquisição, Filtragem, Extração, Validação, Agregação, Representação, etc).

## 6. Pensamento Analítico e Análise de Causa Raiz

O **Pensamento Analítico** envolve a decomposição de problemas complexos em estruturas gerenciáveis. Analistas de dados seniores dominam a transição fluida entre o pensamento criativo (geração de hipóteses inovadoras) e o crítico (validação lógica e algorítmica rigorosa).

### 6.1. Os 5 Pilares do Pensamento Analítico
| Pilar | Definição Prática na Análise |
| :--- | :--- |
| **Visualização** | Mapeamento mental e representação gráfica da informação bruta. |
| **Estratégia** | Planejamento da abordagem analítica para atingir metas de negócios. |
| **Orientação a Problemas** | Foco metodológico direcionado à resolução sistemática do gargalo central. |
| **Correlação** | Identificação técnica de relações lógicas de causa e efeito entre variáveis. |
| **Visão Geral e Detalhe** | Capacidade de transitar do macro (*Big Picture*) para a granularidade do microdado. |

### 6.2. Análise de Causa Raiz (The Five Whys)
A causa raiz é a origem primária e estrutural de um evento ou anomalia corporativa. O framework iterativo dos **Cinco Porquês (Five Whys)** exige perguntar "Por quê?" até esgotar as causas superficiais (sintomas) e chegar à falha sistêmica central.

**Casos de Aplicação Técnica:**
1. **Otimização Logística (Mercearia):** Entregas danificadas -> Embalagem inadequada -> Falta de treinamento prático -> Novos funcionários atuando prematuramente -> *Causa Raiz:* O RH desativou o módulo de treinamento padrão para uma atualização de arquitetura de software, deixando os novos contratados com documentação obsoleta.
2. **Engenharia de Qualidade (Bombas de Água):** Aumento de defeitos de fábrica -> Máquinas com falha de calibração -> Manutenção programada incorreta -> Método de calibração incompatível -> *Causa Raiz:* Atualização de *firmware* do sistema instalada sem sincronização com as especificações de calibração dos técnicos operacionais.

### 6.3. Análise de Lacunas (Gap Analysis)
Metodologia utilizada para investigar déficits de processo. A arquitetura envolve mapear quantitativamente ou processualmente o **Estado Atual (As-Is)** contra o **Estado Futuro Desejado (To-Be)**, identificando o hiato e definindo o plano de execução exato para preenchê-lo.

---

## 7. Casos Avançados de Decisões Orientadas a Dados

O impacto do *Data-Driven Decision Making* transcende bases de dados puras e atinge o planejamento comportamental de companhias inteiras.

### 7.1. Validação de Liderança (Google HR Analytics)
**Hipótese Central Administrativa:** "Gerentes intermediários são um custo redundante e as equipes operariam melhor apenas com colaboradores individuais."
**Abordagem Analítica Técnica:**
1. **Mineração:** Extração massiva de dados de avaliações de desempenho anuais e pesquisas de clima (*surveys*).
2. **Segmentação Estatística:** Organização e partição da amostra de dados em quartis (Q1 a Q4).
3. **Descoberta Quantitativa:** Equipes do Quartil Superior (reportando aos melhores gestores) exibiram correlações exponenciais com altos níveis de produtividade e retenção.
4. **Iteração Qualitativa:** Desenvolvimento de *pipelines* de feedback interno (ex: ferramentas de premiação/indicação) para extrair os comportamentos específicos que estruturavam um bom gestor, transformando hipóteses em documentação de treinamento padrão.

### 7.2. Jornalismo de Dados e Setor Não Lucrativo
**Objetivo de Negócio:** Mensurar com precisão a conversão de leitura editorial em impacto social tangível.
**Abordagem Analítica Técnica:**
* Emprego de ferramentas avançadas de *web tracking* para isolar métricas granulares: retenção por parágrafo, cliques em links externos, tráfego redirecionado e engajamento social.
* Cruzamento do tráfego segmentado de publicações de mídia com a volumetria de doações financeiras e inscrições voluntárias nos bancos de dados de ONGs parceiras.
* **Resultado:** Calibração técnica de modelos de publicação para garantir que os esforços jornalísticos fossem alocados estruturalmente para gerar o máximo de conscientização e conversão filantrópica.

[Voltar ao topo](#módulo-1-introdução-à-análise-de-dados-e-pensamento-analítico)
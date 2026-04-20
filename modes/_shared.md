# Contexto Compartilhado -- career-ops (Portugues BR)

<!-- ============================================================
     THIS FILE IS AUTO-UPDATABLE. Don't put personal data here.
     
     Your customizations go in modes/_profile.md (never auto-updated).
     This file contains system rules, scoring logic, and tool config
     that improve with each career-ops release.
     ============================================================ -->

## Fontes da Verdade (SEMPRE ler antes de cada avaliacao)

| Arquivo | Caminho | Quando |
|---------|---------|--------|
| cv.md | `cv.md` (raiz do projeto) | SEMPRE |
| article-digest.md | `article-digest.md` (se existir) | SEMPRE (proof points detalhados) |
| profile.yml | `config/profile.yml` | SEMPRE (identidade e vagas-alvo) |
| _profile.md | `modes/_profile.md` | SEMPRE (arquetipos, narrativa, negociacao do usuario) |

**REGRA: NUNCA fazer hardcode de metricas de proof points.** Leia-as de `cv.md` e `article-digest.md` no momento da avaliacao.
**REGRA: Para metricas de artigos/projetos, `article-digest.md` tem prioridade sobre `cv.md`** (`cv.md` pode conter numeros desatualizados).
**REGRA: Leia `_profile.md` DEPOIS deste arquivo. As personalizacoes do usuario em `_profile.md` sobrescrevem os valores padrao aqui.**

---

## Sistema de Pontuacao

A avaliacao usa 6 blocos (A-F) com uma nota global de 1-5:

| Dimensao | O que mede |
|----------|------------|
| Match com CV | Habilidades, experiencia, alinhamento de proof points |
| Alinhamento North Star | Quao bem a vaga encaixa nos arquetipos-alvo do usuario (de `_profile.md`) |
| Remuneracao | Salario vs mercado (5=quartil superior, 1=bem abaixo) |
| Sinais culturais | Cultura da empresa, crescimento, estabilidade, politica de trabalho remoto |
| Red flags | Bloqueadores, alertas (ajustes negativos) |
| **Global** | Media ponderada dos itens acima |

**Interpretacao da nota:**
- 4.5+ → Match forte, recomendado aplicar imediatamente
- 4.0-4.4 → Bom match, vale a pena aplicar
- 3.5-3.9 → Razoavel mas nao ideal, aplicar apenas se houver motivo especifico
- Abaixo de 3.5 → Recomendado nao aplicar (veja Ethical Use no CLAUDE.md)

## North Star -- Vagas-Alvo

O skill trata TODAS as vagas-alvo com o mesmo cuidado. Nenhuma e primaria ou secundaria — qualquer uma e uma vitoria, desde que a remuneracao e a perspectiva de crescimento estejam adequadas:

| Arquetipo | Eixos tematicos | O que estao comprando |
|-----------|-----------------|----------------------|
| **Backend Engineer** | APIs, microservices, bancos de dados, sistemas distribuidos, performance | Alguem que constroi sistemas server-side confiaveis e escalaveis |
| **AI/ML Engineer** | RAG, LLMs, ML pipelines, deploy de modelos, embeddings, agentes | Alguem que coloca modelos de IA/ML em producao com metricas reais |
| **Software Engineer (Full Stack)** | Desenvolvimento end-to-end, web apps, system design, arquitetura limpa | Alguem que entrega features completas do frontend a infra |
| **AI Backend Engineer** | APIs com IA, inference serving, vector DBs, integracao de LLMs | Alguem que constroi sistemas backend com IA no core |
| **Platform / DevOps Engineer** | CI/CD, infra cloud, observability, containers, IaC | Alguem que faz times entregarem mais rapido e com mais confiabilidade |
| **Data Engineer** | Data pipelines, ETL, streaming, modelagem de dados, infra de analytics | Alguem que constroi a fundacao de dados para produtos e IA |

### Framing Adaptativo por Arquetipo

> **Metricas concretas: ler de `cv.md` e `article-digest.md` no momento da avaliacao. NUNCA fazer hardcode aqui.**

| Se a vaga e... | Enfatizar no candidato... | Fontes de Proof Points |
|----------------|--------------------------|------------------------|
| Backend | Experiencia em Java/Python/TS backend, APIs, microservices, bancos de dados | cv.md |
| AI/ML | RAG pipelines, sistemas de chatbot, embeddings, deploy de modelos | cv.md + article-digest.md |
| Software (Full Stack) | Entrega end-to-end, React Native, Firebase, projetos full-stack | cv.md |
| AI Backend | Servicos backend com IA, integracao de vector DB, APIs de inferencia | cv.md + article-digest.md |
| Platform / DevOps | CI/CD, deploys em cloud, automacao de infra | cv.md |
| Data Engineering | Data pipelines, processos ETL, modelagem de dados | cv.md |

<!-- [PERSONALIZAR] Mapeie seus projetos/artigos concretos para os arquetipos acima -->

### Narrativa de Transicao (usar em TODOS os framings)

<!-- [PERSONALIZAR] Substitua pela sua propria narrativa. Exemplos:
     - "Construi e vendi minha propria SaaS em 5 anos. Agora foco total em IA aplicada no Enterprise."
     - "Lead de engenharia em uma Series-B durante crescimento 10x. Buscando o proximo desafio."
     - "Transicao de consultoria para produto. Buscando vagas com alta responsabilidade."
     Lido de config/profile.yml -> narrative.exit_story -->

Use a narrativa de transicao de `config/profile.yml` para enquadrar TODO o conteudo:
- **Em PDF Summaries:** Construir a ponte do passado para o futuro — "Aplico as mesmas [habilidades] agora em [dominio do JD]."
- **Em historias STAR:** Referenciar proof points de `article-digest.md`.
- **Em respostas rascunho (Bloco G):** A narrativa de transicao vai na primeira resposta.
- **Quando a vaga menciona "empreendedor", "ownership", "builder", "end-to-end":** Esse e o diferencial numero 1. Aumentar peso de match.

### Vantagem Transversal

Enquadrar o perfil como **"Engenheiro full-stack com experiencia real em IA em producao"**, adaptando o framing a vaga:
- Para Backend: "Engenheiro que constroi APIs e microservices escalaveis com foco em performance"
- Para AI/ML: "Engenheiro que coloca modelos de IA em producao com RAG, embeddings e metricas reais"
- Para Software: "Engenheiro que entrega features completas end-to-end, do frontend a infra"
- Para AI Backend: "Engenheiro que integra IA no backend com APIs robustas e vector DBs"
- Para Platform: "Engenheiro que automatiza infra e melhora a velocidade de entrega do time"
- Para Data: "Engenheiro que constroi pipelines de dados confiaveis para alimentar produtos e modelos"

Posicionar "Builder" como sinal profissional — nao como "hobbyista". Proof points reais tornam isso credivel.

### Portfolio como Proof Point (usar em candidaturas de alto valor)

<!-- [PERSONALIZAR] Se voce tem uma demo ao vivo, dashboard ou projeto publico, configure aqui.
     Exemplo:
     dashboard:
       url: "https://seudominio.dev/demo"
       password: "demo-2026"
       when_to_share: "LLMOps, AI-Platform, vagas de Observability"
     Lido de config/profile.yml -> narrative.proof_points e narrative.dashboard -->

Quando o candidato tem uma demo ao vivo / dashboard (verificar `profile.yml`), oferecer acesso em candidaturas relevantes.

### Inteligencia de Remuneracao (Comp Intelligence)

<!-- [PERSONALIZAR] Pesquise faixas salariais para suas vagas-alvo e ajuste os valores -->

**Orientacoes gerais:**
- WebSearch para dados atuais de mercado (Glassdoor, Levels.fyi, Blind)
- Enquadrar por titulo da vaga, nao por skills — titulos definem as faixas salariais
- Taxas de freelance geralmente ficam 30-60% acima da hora bruta de CLT (encargos, ferias, FGTS, INSS, contador)
- Geo-arbitragem funciona em vagas remotas: custo de vida menor = melhor liquido

### Mercado Brasileiro -- Especificidades (IMPORTANTE)

Em vagas e negociacoes brasileiras, existem termos e praticas que nao aparecem nos mercados EN/ES/DE. Eles DEVEM ser avaliados corretamente:

| Termo | Significado | Impacto na Avaliacao |
|-------|-------------|----------------------|
| **CLT** (Consolidacao das Leis do Trabalho) | Contrato formal com carteira assinada | Inclui FGTS, INSS, ferias, 13o, aviso previo. Na comparacao, considerar o custo total empregador |
| **PJ** (Pessoa Juridica) | Contratacao como prestador de servicos (nota fiscal) | Valor mensal mais alto, mas sem beneficios CLT. Calcular equivalente CLT para comparacao justa |
| **13o Salario** | Pagamento extra obrigatorio para CLT | Comp CLT = salario x 13 (ou 13,33 com 1/3 de ferias). NUNCA esquecer na comparacao |
| **FGTS** (Fundo de Garantia) | 8% do salario depositado pelo empregador | Beneficio CLT, nao aparece no contra-cheque mas e remuneracao real |
| **Vale-Refeicao / Vale-Alimentacao** | Beneficio alimentacao (iFood, Sodexo, Alelo) | Comum em vagas CLT, pode chegar a R$ 1.500+/mes. Incluir na comp total |
| **PLR** (Participacao nos Lucros e Resultados) | Bonus atrelado a resultados da empresa | Pode ser 1-3 salarios extras/ano. Variavel — ponderar com cautela |
| **Stock Options / VSOP** | Equity em startups | Comum em startups brasileiras. Avaliar vesting, cliff e liquidez |
| **Periodo de Experiencia** | 45+45 dias (CLT) ou conforme contrato (PJ) | Padrao de mercado, nao e red flag |
| **Aviso Previo** | 30 dias (CLT) + 3 dias por ano trabalhado | Planejar data de inicio conforme vinculo atual |
| **Plano de Saude** | Beneficio medico (Amil, SulAmerica, Bradesco Saude) | Muito valorizado no Brasil. Sem plano = red flag em vagas CLT |
| **Cooperativa / MEI** | Formas alternativas de contratacao | Avaliar com cautela — pode indicar precarizacao trabalhista |

### Scripts de Negociacao

<!-- [PERSONALIZAR] Adapte para sua situacao -->

**Pretensao salarial (framework geral):**
> "Com base em dados atuais de mercado para essa vaga, minha expectativa esta na faixa de [FAIXA do profile.yml]. Tenho flexibilidade na estrutura — o que importa e o pacote total e a perspectiva de crescimento."

**Pushback contra desconto geografico:**
> "As vagas em que estou concorrendo sao orientadas a resultados, nao a localizacao. Meu track record nao muda com o CEP."

**Quando a oferta esta abaixo do alvo:**
> "Estou comparando com ofertas na faixa de [faixa mais alta]. [Empresa] me atrai por [motivo]. E possivel chegarmos em [valor-alvo] juntos?"

**CLT vs PJ:**
> "Para comparar de forma justa, preciso entender a composicao completa: salario-base, 13o, ferias, FGTS, vale-refeicao, plano de saude e PLR. Se for PJ, qual o valor mensal equivalente considerando esses itens?"

### Politica de Localizacao (Location Policy)

<!-- [PERSONALIZAR] Adapte para sua situacao. Lido de config/profile.yml -> location -->

**Em formularios:**
- Perguntas binarias "Voce pode trabalhar presencialmente?": responder conforme disponibilidade real de `profile.yml`
- Em campos de texto livre: informar fuso horario e disponibilidade explicitamente

**Em avaliacoes (Scoring):**
- Dimensao remoto em hibrido fora do seu estado/pais: Score **3.0** (nao 1.0)
- Score 1.0 apenas se a vaga diz explicitamente "deve estar presencial 4-5 dias/semana, sem excecoes"

### Prioridade Time-to-Offer
- Demo funcional + metricas > perfeicao
- Aplicar mais rapido > aprender mais
- Abordagem 80/20, tudo com prazo definido

---

## Deteccao de Arquetipo

Classificar cada vaga em um destes tipos (ou hibrido de 2):

| Arquetipo | Sinais-chave no JD |
|-----------|-------------------|
| Backend Engineer | "API", "microservices", "database", "distributed systems", "REST", "GraphQL" |
| AI/ML Engineer | "ML pipeline", "RAG", "LLM", "embeddings", "model deployment", "inference" |
| Software Engineer | "full-stack", "web application", "system design", "architecture", "end-to-end" |
| AI Backend Engineer | "AI-powered API", "vector database", "LLM integration", "inference serving" |
| Platform / DevOps | "CI/CD", "infrastructure", "Kubernetes", "observability", "IaC", "cloud" |
| Data Engineer | "data pipeline", "ETL", "streaming", "data warehouse", "analytics" |

Apos detectar o arquetipo, ler `modes/_profile.md` para o framing e proof points especificos do usuario para aquele arquetipo.

---

## Legitimidade da Vaga (Bloco G)

O Bloco G avalia se uma vaga provavelmente e real e ativa. NAO afeta a nota global 1-5 — e uma avaliacao qualitativa separada.

**Tres niveis:**
- **Alta Confianca** — Vaga real e ativa (maioria dos sinais positivos)
- **Prosseguir com Cautela** — Sinais mistos, vale observar (algumas preocupacoes)
- **Suspeita** — Multiplos indicadores de ghost job, investigar antes de investir tempo

**Sinais-chave (ponderados por confiabilidade):**

| Sinal | Fonte | Confiabilidade | Notas |
|-------|-------|----------------|-------|
| Idade da vaga | Snapshot da pagina | Alta | Menos de 30d=bom, 30-60d=misto, 60d+=preocupante |
| Botao Apply ativo | Snapshot da pagina | Alta | Fato diretamente observavel |
| Especificidade tecnica no JD | Texto do JD | Media | JDs genericos correlacionam com ghost postings |
| Realismo dos requisitos | Texto do JD | Media | Contradicoes sao sinal forte |
| Noticias de demissoes recentes | WebSearch | Media | Considerar departamento, timing e tamanho da empresa |
| Padrao de repostagem | scan-history.tsv | Media | Mesma vaga repostada 2+ vezes em 90 dias e preocupante |
| Transparencia salarial | Texto do JD | Baixa | Depende da jurisdicao |
| Fit vaga-empresa | Qualitativo | Baixa | Subjetivo, usar apenas como sinal de apoio |

**Enquadramento etico (OBRIGATORIO):**
- Isso ajuda usuarios a priorizar tempo em oportunidades reais
- NUNCA apresentar achados como acusacoes de desonestidade
- Apresentar sinais e deixar o usuario decidir
- Sempre notar explicacoes legitimas para sinais preocupantes

---

## Regras Globais

### NUNCA

1. Inventar experiencia ou metricas
2. Modificar `cv.md` ou arquivos do portfolio
3. Enviar candidaturas em nome do candidato
4. Compartilhar numero de telefone em mensagens geradas
5. Recomendar remuneracao abaixo do mercado
6. Gerar PDF sem ter lido a descricao da vaga antes
7. Usar jargao corporativo ou "corporates"
8. Ignorar o tracker (toda vaga avaliada e registrada)

### SEMPRE

0. **Carta de apresentacao:** Se o formulario permite anexar ou escrever uma carta, SEMPRE inclua uma. PDF no mesmo design visual do curriculo. Conteudo: citacoes da descricao da vaga mapeadas para proof points, links para case studies relevantes. Maximo 1 pagina.
1. Ler `cv.md`, `_profile.md` e `article-digest.md` (se existir) antes de avaliar qualquer vaga
1b. **Na primeira avaliacao de cada sessao:** Executar `node cv-sync-check.mjs` via Bash. Se houver avisos, informar o candidato antes de continuar
2. Detectar o arquetipo da vaga e adaptar o framing conforme `_profile.md`
3. Ao fazer matching, citar linhas exatas do curriculo
4. Usar WebSearch para dados de remuneracao e empresa
5. Registrar no tracker apos cada avaliacao
6. Gerar conteudo na lingua da descricao da vaga (PT-BR padrao)
7. Ser direto e pratico — sem enrolacao
8. Ao gerar texto em portugues (PDF summaries, bullets, mensagens LinkedIn, historias STAR): portugues tech natural, nao traducao literal. Frases curtas, verbos de acao, evitar voz passiva. Termos tecnicos (stack, pipeline, deployment, embedding) nao precisam ser traduzidos
8b. **URLs de case studies no PDF Professional Summary:** Se o PDF menciona case studies ou demos, as URLs DEVEM aparecer ja no primeiro paragrafo (Professional Summary). Recrutadores frequentemente so leem o resumo. Todos os URLs no HTML com `white-space: nowrap`
9. **Entradas no tracker como TSV** — NUNCA editar `applications.md` diretamente para novos registros. Escrever TSV em `batch/tracker-additions/`, `merge-tracker.mjs` cuida do merge
10. **Incluir `**URL:**` em todo header de report** — entre Score e PDF

### Tools

| Tool | Uso |
|------|-----|
| WebSearch | Pesquisa de remuneracao, tendencias, cultura da empresa, contatos LinkedIn, fallback para descricoes de vagas |
| WebFetch | Fallback para extrair descricoes de vagas de paginas estaticas |
| Playwright | Verificar se vagas ainda estao ativas (browser_navigate + browser_snapshot), extrair descricoes de SPAs. **CRITICO: NUNCA iniciar 2+ agentes com Playwright em paralelo — eles compartilham a mesma instancia do navegador** |
| Read | cv.md, _profile.md, article-digest.md, cv-template.html |
| Write | HTML temporario para PDF, applications.md, reports .md |
| Edit | Atualizar tracker |
| Bash | `node generate-pdf.mjs` |

# Modo: pdf — Geração de PDF Otimizado para ATS

## Pipeline completo

1. Lê `cv.md` como fonte da verdade
2. Pede ao usuário o JD se não estiver no contexto (texto ou URL)
3. Extrai 15-20 keywords do JD
4. Detecta idioma do JD → idioma do CV (EN default)
5. Detecta localização da empresa → formato de papel:
   - US/Canada → `letter`
   - Resto do mundo → `a4`
6. Detecta arquétipo do cargo → adapta framing
7. Reescreve Professional Summary injetando keywords do JD + exit narrative bridge
8. Seleciona top 3-4 projetos mais relevantes para a vaga
9. Reordena bullets de experiência por relevância ao JD
10. Constrói competency grid a partir dos requisitos do JD (6-8 keyword phrases)
11. Injeta keywords naturalmente em conquistas existentes (NUNCA inventa)
12. Gera HTML completo a partir do template + conteúdo personalizado
13. Lê `name` de `config/profile.yml` → normaliza para kebab-case lowercase (ex: "Igor David Morais" → "igor-david-morais") → `{candidate}`
14. Escreve HTML em `/tmp/cv-{candidate}-{company}.html`
15. Executa: `node generate-pdf.mjs /tmp/cv-{candidate}-{company}.html output/cv-{candidate}-{company}-{YYYY-MM-DD}.pdf --format={letter|a4}`
16. Reporta: caminho do PDF, nº de páginas, % de cobertura de keywords

## Regras ATS (parsing limpo)

- Layout single-column (sem sidebars, sem colunas paralelas)
- Headers padrão: "Professional Summary", "Work Experience", "Education", "Skills", "Certifications", "Projects"
- Sem texto em imagens/SVGs
- Sem info crítica em headers/footers do PDF (ATS os ignora)
- UTF-8, texto selecionável (não rasterizado)
- Sem tabelas aninhadas
- Keywords do JD distribuídas: Summary (top 5), primeiro bullet de cada cargo, Skills section

## Design do PDF

- **Fonts**: Space Grotesk (headings, 600-700) + DM Sans (body, 400-500)
- **Fonts self-hosted**: `fonts/`
- **Header**: nome em Space Grotesk 24px bold + linha gradiente `linear-gradient(to right, hsl(187,74%,32%), hsl(270,70%,45%))` 2px + linha de contato
- **Section headers**: Space Grotesk 13px, uppercase, letter-spacing 0.05em, cor cyan primary
- **Body**: DM Sans 11px, line-height 1.5
- **Nomes de empresa**: cor accent purple `hsl(270,70%,45%)`
- **Margens**: 0.6in
- **Background**: branco puro

## Ordem das seções (otimizado "6-second recruiter scan")

1. Header (nome grande, gradiente, contato, link portfólio)
2. Professional Summary (3-4 linhas, keyword-dense)
3. Core Competencies (6-8 keyword phrases em flex-grid)
4. Work Experience (cronológico reverso)
5. Projects (top 3-4 mais relevantes)
6. Education & Certifications
7. Skills (idiomas + técnicos)

## Estratégia de keyword injection (ético, baseado em verdade)

Exemplos de reformulação legítima:
- JD diz "RAG pipelines" e CV diz "LLM workflows with retrieval" → mudar para "RAG pipeline design and LLM orchestration workflows"
- JD diz "MLOps" e CV diz "observability, evals, error handling" → mudar para "MLOps and observability: evals, error handling, cost monitoring"
- JD diz "stakeholder management" e CV diz "collaborated with team" → mudar para "stakeholder management across engineering, operations, and business"

**NUNCA adicionar skills que o candidato não tem. Apenas reformular experiência real com o vocabulário exato do JD.**

## Template HTML

Usar o template em `templates/cv-template.html`. Substituir os placeholders `{{...}}` com conteúdo personalizado:

| Placeholder | Conteúdo |
|-------------|----------|
| `{{LANG}}` | `en`, `pt`, ou idioma do JD |
| `{{PAGE_WIDTH}}` | `8.5in` (letter) ou `210mm` (A4) |
| `{{NAME}}` | (de profile.yml) |
| `{{EMAIL}}` | (de profile.yml) |
| `{{LINKEDIN_URL}}` | (de profile.yml) |
| `{{LINKEDIN_DISPLAY}}` | (de profile.yml) |
| `{{PORTFOLIO_URL}}` | (de profile.yml) |
| `{{PORTFOLIO_DISPLAY}}` | (de profile.yml) |
| `{{LOCATION}}` | (de profile.yml) |
| `{{SECTION_SUMMARY}}` | Professional Summary / Resumo Profissional |
| `{{SUMMARY_TEXT}}` | Summary personalizado com keywords |
| `{{SECTION_COMPETENCIES}}` | Core Competencies / Competências-Chave |
| `{{COMPETENCIES}}` | `<span class="competency-tag">keyword</span>` × 6-8 |
| `{{SECTION_EXPERIENCE}}` | Work Experience / Experiência Profissional |
| `{{EXPERIENCE}}` | HTML de cada trabalho com bullets reordenados |
| `{{SECTION_PROJECTS}}` | Projects / Projetos |
| `{{PROJECTS}}` | HTML dos top 3-4 projetos |
| `{{SECTION_EDUCATION}}` | Education / Formação |
| `{{EDUCATION}}` | HTML de educação |
| `{{SECTION_CERTIFICATIONS}}` | Certifications / Certificações |
| `{{CERTIFICATIONS}}` | HTML de certificações |
| `{{SECTION_SKILLS}}` | Skills / Habilidades |
| `{{SKILLS}}` | HTML de skills |

## Geração via Canva CV (opcional)

Se `config/profile.yml` tem `canva_resume_design_id` definido, oferecer ao usuário uma escolha antes de gerar:
- **"HTML/PDF (rápido, otimizado para ATS)"** — fluxo existente acima
- **"Canva CV (visual, preserva design)"** — fluxo Canva

Se o usuário não tem `canva_resume_design_id`, pular este prompt e usar o fluxo HTML/PDF.

### Workflow Canva

#### Passo 1 — Duplicar o design base
a. `export-design` do design base → get download URL
b. `import-design-from-url` usando a URL → cria novo design editável (a cópia)

#### Passo 2 — Ler a estrutura do design
a. `get-design-content` no novo design → retorna todos os elementos de texto
b. Mapear elementos para seções do CV por conteúdo

#### Passo 3 — Gerar conteúdo personalizado
Mesma geração de conteúdo do fluxo HTML (Passos 1-11 acima).

**IMPORTANTE — Regra de orçamento de caracteres:** Cada texto de substituição DEVE ter aproximadamente o mesmo comprimento do texto original (±15% de contagem de caracteres).

#### Passo 4 — Aplicar edições
a. `start-editing-transaction` no design duplicado
b. `perform-editing-operations` com `find_and_replace_text`
c. **Refluxo de layout após substituição de texto**
d. **Verificar layout antes de commitar**
e. `commit-editing-transaction` para salvar (SOMENTE após aprovação do usuário)

#### Passo 5 — Exportar e baixar PDF
a. `export-design` como PDF
b. **IMEDIATAMENTE** baixar o PDF via Bash
c. Verificar o download
d. Reportar: caminho do PDF, tamanho, URL do design Canva

## Pós-geração

Atualizar tracker se a vaga já está registrada: mudar PDF de ❌ para ✅.

# Plano de Construcao

Status: concluido
Ultima atualizacao: 2026-04-17 00:55

## Decisoes fixas

- Subagents reais via Task tool, nao personas inline
- 1 advogado por area (apenas civil no MVP)
- Idioma: PT-BR em tudo (estrutura, codigo, conteudo, conversa)
- Fontes oficiais: planalto.gov.br, scon.stj.jus.br, portal.stf.jus.br, sumulas STJ/STF
- Indexacao: INDICE.md por pasta + frontmatter YAML por arquivo
- Curadoria inicial manual; WebFetch sob demanda nas skills
- Workflow canonico do caso: intake -> triagem -> pesquisa -> tese -> peca -> revisao

## Fases

### Fase 0 - Setup minimo (sequencial)

- [x] CLAUDE.md raiz criado (regras, idioma PT-BR, disclaimer legal explicito, ponteiros)
- [x] PLANO.md criado
- [x] .gitignore criado (ignora casos/reais/** mesmo que ainda nao exista)

### Fase 1 - Scaffold (4 trilhas paralelas via Task tool)

- [x] 1a: arvore completa de pastas + INDICE.md vazios em cada pasta de referencia/KB
- [x] 1b: CLAUDE.md em base-conhecimento-geral/, referencias-geral/, referencias-civil/, casos/
- [x] 1c: template do subagent advogado em .claude/agents/advogados/_TEMPLATE.md + perfil humano em agentes-advogados/_TEMPLATE.md
- [x] 1d: schema do INDICE.md documentado formalmente em referencias-geral/CLAUDE.md com exemplo

### Fase 2 - Conteudo seed (3 trilhas paralelas via Task tool)

- [x] 2a: base-conhecimento-geral/ populado (constitucional/cf-essencial.md, processual/cpc-visao-geral.md, organizacao-judiciaria/estrutura-judiciario-br.md)
- [x] 2b: referencias-civil/ populado (leis, sumulas, jurisprudencia/_README, INDICE)
- [x] 2c: advogado civil concreto criado (.claude/agents/advogados/civil.md + agentes-advogados/civil.md)

### Fase 3 - Skills (5 trilhas paralelas via Task tool)

- [x] 3a: caso-novo
- [x] 3b: caso-triagem
- [x] 3c: caso-pesquisa
- [x] 3d: caso-reuniao
- [x] 3e: caso-peca

### Fase 4 - Integracao e smoke test

- [x] 4a: slash command /caso-criar em .claude/commands/caso-criar.md
- [x] 4b: caso-exemplo sintetico em casos/exemplos/contrato-locacao-inadimplemento/ executando o fluxo completo end-to-end

### Fase 5 - Verificacao independente (obrigatoria)

- [x] Spawnar subagent Explore/general-purpose com checklist isolado
- [x] Salvar relatorio em VERIFICACAO.md
- [x] Corrigir gaps ate zero
- [x] Marcar Fase 5 concluida somente apos zero gaps

## Log de progresso

- 2026-04-16 23:22 - PLANO.md criado, inicio da Fase 0
- 2026-04-16 23:30 - Fase 0 concluida (CLAUDE.md raiz, PLANO.md, .gitignore)
- 2026-04-16 23:45 - Fase 1 concluida (scaffold de pastas, CLAUDE.md em subpastas, templates, schema formal em referencias-geral)
- 2026-04-17 00:10 - Fase 2 concluida (base-conhecimento-geral populada, referencias-civil populadas, advogado civil concreto)
- 2026-04-17 00:25 - Fase 3 concluida (5 skills: caso-novo, caso-triagem, caso-pesquisa, caso-reuniao, caso-peca)
- 2026-04-17 00:45 - Fase 4 concluida (slash command /caso-criar + smoke test contrato-locacao-inadimplemento)
- 2026-04-17 00:55 - Fase 5 concluida (auditoria independente: 10/10 PASS, 4/4 bonus, zero gaps bloqueantes)

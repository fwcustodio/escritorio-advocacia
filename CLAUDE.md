# CLAUDE.md - Escritorio de Advocacia Simulado

Ambiente de apoio a decisao em casos juridicos reais, comecando por Direito Civil. O cliente humano (Fernando) esta no loop; os "advogados" sao subagents Claude Code com persona, formacao e especialidade, invocados via Task tool para reunioes multi-agente.

## DISCLAIMER LEGAL (OBRIGATORIO)

Referencias (leis, sumulas, jurisprudencia) devem ser sempre reverificadas nas fontes oficiais antes de qualquer uso real: planalto.gov.br, scon.stj.jus.br, portal.stf.jus.br.

## Regras gerais

- Idioma: PT-BR em tudo (estrutura de pastas, conteudo, codigo, conversa do agente com o cliente).
- Sem emojis em qualquer artefato (codigo, markdown, commits, mensagens).
- Sem referencia a IA/Claude/Anthropic em commits, comentarios, Swagger ou textos externos.
- Fontes primarias preferidas: Planalto, STJ, STF, TJs oficiais. Doutrina por links curados apenas.
- Tipagem forte: quando houver codigo, proibido any/object/Function/{} em producao. Ver global CLAUDE.md.
- Nenhum arquivo de caso real sera commitado. casos/reais/\*\* esta no .gitignore.

## Workflow canonico de um caso

1. intake: cliente descreve o caso em linguagem livre (skill caso-novo).
2. triagem: o sistema identifica area(s) juridica(s) envolvidas e monta o time de advogados (skill caso-triagem). No MVP, apenas civil.
3. pesquisa: alimenta a base de conhecimento do caso seguindo a hierarquia base-conhecimento-geral/ -> referencias-geral/ -> referencias-{area}/ -> WebFetch oficial (skill caso-pesquisa).
4. tese: reuniao com o(s) subagent(s) advogado(s), cliente humano participa, tese juridica e registrada (skill caso-reuniao).
5. peca: minuta de peca processual e gerada a partir da KB consolidada (skill caso-peca).
6. revisao: cliente humano revisa, faz perguntas de volta, itera.

Cada passo gera artefatos versionaveis em casos/<slug>/.

## Estrutura de pastas (referencia)

- agentes-advogados/: perfis humanos legiveis dos advogados (bio, cidade, faculdade, OAB ficticia).
- .claude/agents/advogados/: subagents funcionais invocaveis via Task tool.
- .claude/skills/: skills de workflow (caso-novo, caso-triagem, caso-pesquisa, caso-reuniao, caso-peca).
- .claude/commands/: slash commands (/caso-criar orquestrador).
- base-conhecimento-geral/: KB comum a todas as areas (constitucional, processual, organizacao judiciaria).
- referencias-geral/: referencias transversais (schema do INDICE.md, convencoes).
- referencias-civil/: leis, sumulas, jurisprudencia e doutrina civis.
- casos/: casos ativos. \_TEMPLATE/ e o esqueleto; exemplos/ tem casos ficticios para smoke test; reais/ fica fora do git.

## Convencoes

- Toda pasta de referencia/KB tem INDICE.md listando seus arquivos com uma linha cada: `- [arquivo.md](arquivo.md) - tipo - ano - resumo curto`.
- Todo arquivo de referencia tem frontmatter YAML com: tipo, fonte (URL canonica), jurisdicao, data, ano, area, tags, resumo. Schema completo em referencias-geral/CLAUDE.md.
- Ao adicionar um novo arquivo em referencia/KB, atualizar INDICE.md da pasta.
- Casos seguem template em casos/\_TEMPLATE/.

## Ponteiros

- Base de conhecimento geral: base-conhecimento-geral/CLAUDE.md
- Referencias transversais: referencias-geral/CLAUDE.md
- Referencias civis: referencias-civil/CLAUDE.md
- Casos: casos/CLAUDE.md
- Plano de construcao: PLANO.md
- Relatorio de verificacao: VERIFICACAO.md (gerado na Fase 5)

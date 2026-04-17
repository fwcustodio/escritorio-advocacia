# CLAUDE.md - Casos

Todos os casos do escritorio simulado: ativos, exemplos ficticios e arquivados.

## DISCLAIMER LOCAL

Casos reais so sao trabalhados em `casos/reais/`, que esta FORA DO GIT via `.gitignore`. Nada produzido nesta pasta constitui parecer juridico formal; e apoio a decisao gerado por subagents simulados (ver disclaimer completo no CLAUDE.md raiz).

## Subpastas

- `_TEMPLATE/`: esqueleto de um caso novo. Copiado pela skill `caso-novo` ao iniciar cada caso.
- `exemplos/`: casos ficticios usados em smoke test e documentacao. Versionados no git.
- `reais/`: casos reais do cliente. IGNORADO pelo git. Nenhum arquivo aqui deve ser commitado.

## Estrutura interna de um caso

Baseada em `_TEMPLATE/`:

- `descricao.md`: intake inicial do cliente em linguagem livre (skill `caso-novo`).
- `triagem.md`: area(s) juridica(s) identificada(s) e time de advogados (subagents) escalado (skill `caso-triagem`).
- `base-conhecimento/`: KB especifica do caso. Contem `INDICE.md` proprio, com links para arquivos locais e para referencias externas reutilizadas.
- `reunioes/YYYY-MM-DD-titulo.md`: atas de reuniao com os subagents advogados e o cliente humano (skill `caso-reuniao`). Um arquivo por reuniao.
- `tese.md`: tese juridica consolidada apos reunioes, com fundamentos, riscos e linha de argumentacao.
- `pecas/`: minutas de pecas processuais geradas a partir da tese e da KB (skill `caso-peca`).
- `linha-do-tempo.md`: eventos do caso em ordem cronologica (prazos, protocolos, decisoes).

## Convencao de nomenclatura

- Slug do caso em kebab-case, sem acentos, descritivo da materia.
- Exemplos: `contrato-locacao-inadimplemento`, `acao-alimentos-revisional`, `usucapiao-extrajudicial-imovel-urbano`.
- Nunca usar nome real de parte ou CPF no slug, mesmo em `reais/`.

## Fluxo canonico

intake -> triagem -> pesquisa -> tese -> peca -> revisao. Cada etapa e dirigida por uma skill especifica e deixa artefato versionado dentro do caso.

## Ponteiros

- Workflow e disclaimer geral: `../CLAUDE.md`
- Skills de workflow:
  - `caso-novo`: cria novo caso a partir de `_TEMPLATE/`.
  - `caso-triagem`: identifica area e monta time.
  - `caso-pesquisa`: alimenta `base-conhecimento/` do caso.
  - `caso-reuniao`: conduz reuniao com subagents advogados.
  - `caso-peca`: minuta peca processual a partir da KB e da tese.

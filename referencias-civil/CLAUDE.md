# CLAUDE.md - Referencias de Direito Civil

Referencias especificas de Direito Civil: leis, sumulas, jurisprudencia e doutrina. Complementa (nao substitui) `base-conhecimento-geral/`.

## Proposito

Indexar o material normativo e jurisprudencial civel utilizado pelas skills de pesquisa e pelos subagents advogados da area civel. Conteudo aqui e especifico; fundamentos transversais (processo civil geral, CF, organizacao judiciaria) ficam em `base-conhecimento-geral/`.

## Estrutura

- `leis/`: Codigo Civil (Lei 10.406/2002), Codigo de Defesa do Consumidor (Lei 8.078/1990), Lei do Inquilinato (Lei 8.245/1991), Lei de Registros Publicos (Lei 6.015/1973), Estatuto da Crianca e do Adolescente (parte civel), Lei de Alimentos, entre outras. Frontmatter com `tipo: lei`.
- `sumulas/`: sumulas do STJ e STF com conteudo civel. Frontmatter com `tipo: sumula`.
- `jurisprudencia/`: acordaos relevantes e repetitivos (Temas do STJ, Teses do STF em materia civel). Frontmatter com `tipo: jurisprudencia`.
- `doutrina/`: APENAS links curados para doutrina acessivel online (artigos, pareceres publicos). Nao transcrever livro. Frontmatter com `tipo: doutrina`.

Cada subpasta tem seu proprio `INDICE.md`.

## Workflow ao adicionar uma nova referencia

1. Criar o arquivo markdown com frontmatter YAML COMPLETO (ver schema em `../referencias-geral/CLAUDE.md`).
2. Atualizar o `INDICE.md` da subpasta (linha: `- [arquivo.md](arquivo.md) - tipo - ano - resumo curto`).
3. Campo `fonte` do frontmatter deve apontar para URL oficial:
   - Leis: `https://www.planalto.gov.br/...`
   - Sumulas/jurisprudencia STJ: `https://scon.stj.jus.br/...`
   - Jurisprudencia STF: `https://portal.stf.jus.br/...`
4. NUNCA transcrever o texto integral da lei/acordao. Indexar, resumir e linkar.
5. Conteudo do arquivo: resumo curado (artigos-chave, ementa, pontos controvertidos, aplicacao pratica), nao copia.

## Convencoes locais

- Nome de arquivo em kebab-case, sem acentos (ex: `cc-art-186-responsabilidade-civil.md`, `sumula-297-stj.md`).
- Quando um artigo de lei for referenciado por multiplas sumulas/acordaos, manter o arquivo principal em `leis/` e linkar de `sumulas/` e `jurisprudencia/`.
- Atualizacoes de jurisprudencia: registrar `data` e `ano` do acordao/tese no frontmatter; acrescentar `ultima-verificacao` quando revalidado.

## Ponteiros

- Schema de frontmatter e convencoes de metadados: `../referencias-geral/CLAUDE.md`
- Base de conhecimento transversal (processual, constitucional): `../base-conhecimento-geral/CLAUDE.md`
- CLAUDE.md raiz: `../CLAUDE.md`

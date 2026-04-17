# CLAUDE.md - Base de Conhecimento Geral

Base de conhecimento transversal a TODAS as areas juridicas. Conteudo aqui nao deve ser duplicado em referencias-{area}/.

## Proposito

Centralizar fundamentos que sustentam qualquer analise juridica, independente da area (civil, penal, trabalhista, tributario etc.). Esta pasta e a PRIMEIRA consultada pela skill caso-pesquisa, antes das referencias especificas de cada area.

## Estrutura

- `constitucional/`: Constituicao Federal de 1988, principios constitucionais, direitos e garantias fundamentais, divisao de poderes, controle de constitucionalidade.
- `processual/`: Codigo de Processo Civil (CPC/2015), teoria geral do processo, procedimento comum, pressupostos processuais, partes e procuradores, atos processuais, tutela provisoria, recursos.
- `organizacao-judiciaria/`: estrutura do Judiciario brasileiro. STF, STJ, TJs estaduais, TRFs, Justica do Trabalho, Justica Eleitoral, Juizados Especiais (JEC/JECrim), competencia em razao da materia, do valor e territorial.

Cada subpasta tem seu proprio `INDICE.md`.

## Convencoes locais

- Todo arquivo markdown aqui deve ter frontmatter YAML conforme schema definido em `referencias-geral/CLAUDE.md`.
- Ao adicionar um novo arquivo, atualizar o `INDICE.md` da pasta correspondente (linha no formato: `- [arquivo.md](arquivo.md) - tipo - ano - resumo curto`).
- Conteudo e CURADO: resumos, esquemas, fluxogramas, pontos-chave. Nunca copia integral de lei ou acordao.
- Toda referencia a texto legal deve apontar para fonte oficial (planalto.gov.br, scon.stj.jus.br, portal.stf.jus.br).
- Nome de arquivo em kebab-case, sem acentos (ex: `principio-contraditorio.md`, `competencia-jec.md`).

## Uso pelas skills

A skill `caso-pesquisa` consulta esta pasta ANTES de `referencias-civil/` (ou qualquer outra referencia especifica). O fluxo e:

1. `base-conhecimento-geral/` (fundamentos transversais)
2. `referencias-geral/` (convencoes e metadados)
3. `referencias-{area}/` (especifico da area triada)
4. `WebFetch` em fonte oficial (ultimo recurso, com citacao)

## Escopo MVP

No MVP apenas Direito Civil esta ativo. Ainda assim, esta KB ja comporta fundamentos que serao reaproveitados em outras areas futuras (penal, trabalhista, tributario). Nao incluir conteudo especifico de area aqui.

## Ponteiros

- Schema de frontmatter e convencoes de metadados: `../referencias-geral/CLAUDE.md`
- CLAUDE.md raiz (workflow canonico, disclaimer legal): `../CLAUDE.md`

---
name: caso-pesquisa
description: Alimenta a base de conhecimento especifica de um caso (casos/<slug>/base-conhecimento/) seguindo a hierarquia base-conhecimento-geral -> referencias-geral -> referencias-{area} -> WebFetch nas fontes oficiais (Planalto, STJ, STF). Usar apos caso-triagem, antes de caso-reuniao.
---

# Skill: caso-pesquisa

## Quando usar

Apos triagem indicar as areas. Ou quando cliente pede "pesquise jurisprudencia", "buscar sumulas", "qual a base legal".

## Pre-requisitos

- `casos/<slug>/triagem.md` existe e indica areas.
- `casos/<slug>/base-conhecimento/` existe (mesmo que vazio).

## Hierarquia de pesquisa OBRIGATORIA (nesta ordem, parar assim que achar)

1. `casos/<slug>/base-conhecimento/` - se o caso ja tem material pesquisado anteriormente.
2. `base-conhecimento-geral/` - KB transversal (CF, CPC, organizacao judiciaria).
3. `referencias-geral/` - referencias transversais.
4. `referencias-{area}/` - referencias da area (ex: `referencias-civil/`).
5. WebFetch em fontes oficiais, SO SE os passos anteriores nao cobrirem:
   - Planalto (https://www.planalto.gov.br/) para leis federais.
   - STJ scon (https://scon.stj.jus.br/) para sumulas e acordaos.
   - STF portal (https://portal.stf.jus.br/) para sumulas vinculantes e acordaos.
   - CNJ (https://www.cnj.jus.br/) para resolucoes.
   - TJ do estado competente apenas para acordaos estaduais.

## Passos

1. **Ler `triagem.md`** e extrair areas-primaria/secundarias, tese proposta, riscos.

2. **Formular perguntas de pesquisa** concretas (3-7). Cada pergunta deve ser responsavel por um dispositivo, sumula, tese repetitiva ou precedente. Exemplo:
   - "Qual o prazo prescricional para acao de indenizacao por dano moral em relacao de consumo?"
   - "Existe sumula do STJ sobre responsabilidade objetiva da instituicao financeira por fraude a cartao clonado?"
   - "O CDC se aplica a locacao residencial celebrada entre pessoas fisicas?"

3. **Para cada pergunta**, executar a hierarquia (1-5):
   - Ler arquivos relevantes via Read/Grep/Glob.
   - Extrair: dispositivo (art./lei/ano), sumula (n/orgao/texto), acordao (classe/n/relator/orgao/data/ementa/ratio).
   - Se nenhuma fonte local cobre E tem confianca baixa, usar WebFetch nas URLs oficiais.

4. **Registrar resultados** em `casos/<slug>/base-conhecimento/` como arquivos discretos:
   - Preferir copiar/referenciar arquivos ja existentes em `referencias-*` (ex: criar um arquivo `leis-aplicaveis.md` que LINKA para `referencias-civil/leis/codigo-civil.md`).
   - NAO duplicar o conteudo. Apenas sintetizar o que e relevante para ESTE caso, e linkar.
   - Frontmatter YAML em cada arquivo de sintese (`tipo: sintese`, `fonte`: caminho relativo ou URL, `data`, `area`, `tags`, `resumo`).

5. **Arquivos-sintese tipicos**:
   - `leis-aplicaveis.md` - dispositivos diretamente invocaveis, com citacao e link.
   - `sumulas-aplicaveis.md` - sumulas relevantes, com enunciado e ratio.
   - `jurisprudencia-aplicavel.md` - acordaos de cada tribunal, organizados por tese.
   - `doutrina-relevante.md` - links para artigos/livros curados.
   - `precedentes-vinculantes.md` - IRDR, IAC, REsp repetitivos, RE repercussao geral, sumulas vinculantes.
   - `questoes-abertas.md` - pontos onde pesquisa nao encontrou resposta e que precisam de atencao humana.

6. **Atualizar `casos/<slug>/base-conhecimento/INDICE.md`** com os arquivos criados.

7. **Atualizar `linha-do-tempo.md`**: `YYYY-MM-DD - pesquisa concluida - N arquivos de sintese gerados`.

8. **Atualizar status** em `descricao.md`: de `triado` para `pesquisado`.

9. **Resumo ao cliente**: bullet list (5-10 items) com as principais fundamentacoes encontradas e quaisquer gaps/riscos.

## Regras

- SEMPRE citar a fonte (art./sumula/acordao + URL canonica).
- NUNCA inventar sumulas, artigos ou acordaos. Se nao encontrar, declarar explicitamente no arquivo `questoes-abertas.md`.
- Reverificar datas e numeros em fontes oficiais antes de registrar.
- WebFetch so em ultimo caso; tentar esgotar KB local primeiro.

## Nao fazer

- Nao redigir peca.
- Nao convocar subagent advogado.
- Nao alterar `referencias-*` ou `base-conhecimento-geral/` globais (a pesquisa e LOCAL ao caso).

## Ponteiros

- Anterior: `caso-triagem`.
- Proxima: `caso-reuniao`.
- Hierarquia e fontes: `CLAUDE.md` raiz.

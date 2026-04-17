---
name: caso-peca
description: Gera uma minuta de peca processual (peticao inicial, contestacao, impugnacao, replica, alegacoes finais, recurso de apelacao, embargos de declaracao, REsp, RE etc.) a partir da KB consolidada do caso e da tese definida em reuniao. Salva em casos/<slug>/pecas/YYYY-MM-DD-<tipo-peca>.md. Usar apos caso-reuniao.
---

# Skill: caso-peca

## Quando usar

- Apos `caso-reuniao` ter consolidado tese.
- Ou quando cliente pede "redija a inicial", "minute a contestacao", "prepare apelacao", "minuta de recurso".

## Pre-requisitos

- `tese.md` existe e esta atualizada.
- `base-conhecimento/` populado.
- Tipo de peca definido pelo cliente OU inferido do status processual.

## Tipos suportados (MVP)

- `peticao-inicial` (polo ativo, rito comum)
- `contestacao` (polo passivo)
- `impugnacao-contestacao` / `replica`
- `alegacoes-finais` (memoriais)
- `recurso-apelacao`
- `embargos-declaracao`
- `recurso-especial`
- `recurso-extraordinario`
- `peticao-simples` (requerimento, manifestacao, juntada)

## Passos

1. **Confirmar tipo de peca** e polo (autor/reu/apelante/apelado/recorrente/recorrido).

2. **Reunir contexto**. Ler:
   - `descricao.md` (fatos e partes)
   - `triagem.md` (areas, riscos)
   - `base-conhecimento/*.md` (leis, sumulas, jurisprudencia, precedentes)
   - `tese.md` (tese consolidada com teses subsidiarias)
   - `reunioes/<ultima>.md` (decisoes tomadas)

3. **Estrutura da peca** (adaptar ao tipo). Para peticao inicial (exemplo):
   - Enderecamento (juizo competente).
   - Qualificacao das partes (completa conforme CPC art. 319, II).
   - Fatos (narrativa cronologica, com documentos indicados).
   - Fundamentos juridicos (por tese, com citacao de artigos + sumulas + jurisprudencia).
   - Tutela provisoria (se aplicavel) com requisitos art. 300 ou 311 CPC.
   - Dos pedidos (rol especifico e determinado - art. 322 CPC).
   - Valor da causa (art. 291-293 CPC).
   - Requerimento de provas (art. 319, VI CPC).
   - Requerimentos finais (beneficios, audiencia de conciliacao etc.).

   Para contestacao: preliminares (art. 337 CPC), merito, pedidos.
   Para recursos: requisitos de admissibilidade (tempestividade, preparo, interesse, legitimidade, cabimento), razoes de reforma.

4. **Redigir a minuta** em estilo formal, linguagem juridica, em PT-BR culto. Usar:
   - Citacoes com art. / lei / ano.
   - Sumulas e acordaos mencionados sempre com orgao e numero.
   - Evitar prolixidade. Fundamentacao densa mas sintetica.
   - Placeholders [ENTRE COLCHETES MAIUSCULOS] para dados que o cliente precisa preencher (valores exatos, datas precisas, qualificacao completa, enderecos).

5. **Nao inventar**:
   - Se nao souber a comarca exata, deixar `[COMARCA DO FORO COMPETENTE]`.
   - Se nao souber a qualificacao completa, deixar placeholders.
   - Se um ato processual ainda nao ocorreu (ex: intimacao), deixar placeholders de data.

6. **Salvar em `casos/<slug>/pecas/YYYY-MM-DD-<tipo-peca>.md`** com frontmatter:

   ```yaml
   ---
   tipo: peca
   slug-caso: <slug>
   tipo-peca: peticao-inicial | contestacao | apelacao | ...
   polo: autor | reu | apelante | apelado | ...
   data-minuta: YYYY-MM-DD
   status: minuta | revisada | protocolada
   base-tese: <caminho para tese.md>
   ---
   ```

7. **Incluir nota final na peca**:

   > DISCLAIMER: Minuta gerada por sistema de apoio a decisao. NAO substitui revisao por advogado habilitado na OAB. Placeholders [...] devem ser preenchidos com dados reais. Toda fundamentacao deve ser reverificada nas fontes oficiais antes do protocolo.

8. **Atualizar `linha-do-tempo.md`**: `YYYY-MM-DD - minuta de <tipo-peca> gerada`.

9. **Atualizar status** em `descricao.md` para `peca-minuta`.

10. **Apresentar ao cliente**: resumo da peca em 5-8 linhas (enderecamento, teses, pedidos principais, placeholders pendentes).

## Regras

- Nunca protocolar. A skill so gera minuta.
- Nunca inventar jurisprudencia/sumulas; usar apenas da KB do caso ou das referencias-*.
- Preservar rigorosamente o CPC (competencia, prazos, formalidades).
- Peca deve refletir a tese principal da `tese.md`; teses subsidiarias podem aparecer em secao "subsidiariamente".

## Nao fazer

- Nao alterar KB global.
- Nao submeter para tribunal, nao enviar por email, nao mexer em sistema externo.
- Nao apagar minutas anteriores (versionar criando novo arquivo YYYY-MM-DD).

## Ponteiros

- Anterior: `caso-reuniao`.
- CPC visao geral: `base-conhecimento-geral/processual/cpc-visao-geral.md`.

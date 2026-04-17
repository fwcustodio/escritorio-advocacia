---
description: Orquestra o fluxo completo de abertura de caso - executa caso-novo, caso-triagem, caso-pesquisa em sequencia. Apos conclusao, sugere ao usuario acionar caso-reuniao.
argument-hint: [descricao livre do caso - opcional]
---

# /caso-criar - Orquestrador de abertura de caso

Executa o fluxo canonico ate a pesquisa juridica concluida. Tres skills encadeadas. O cliente humano decide entre as etapas.

## Argumentos

`$ARGUMENTS` - descricao livre do caso. Pode vir vazia; neste caso, perguntar ao cliente em linguagem natural os campos de intake.

## Fluxo

### Etapa 1 - Intake (skill caso-novo)

1. Se `$ARGUMENTS` esta vazio, perguntar ao cliente (em uma unica mensagem) os 7 campos de intake: partes/polo, fatos+datas, documentos, pretensao, urgencia, jurisdicao, valor.
2. Aguardar resposta do cliente.
3. Invocar a logica da skill caso-novo (ler `.claude/skills/caso-novo.md` e executar os passos) para gerar slug, criar pasta casos/exemplos/<slug>/ ou casos/reais/<slug>/ conforme decisao do cliente, e preencher descricao.md + esqueleto.
4. Ao final, mostrar ao cliente: slug, caminho, arquivos criados.
5. Pausa curta - perguntar se segue para triagem ou se quer revisar descricao.md antes.

### Etapa 2 - Triagem (skill caso-triagem)

1. Com autorizacao do cliente, executar a logica de `.claude/skills/caso-triagem.md`.
2. Ler descricao.md, mapear areas, avaliar complexidade e riscos, montar time (MVP: [advogado-civil]), sugerir 1-3 estrategias.
3. Gerar triagem.md.
4. Apresentar resumo ao cliente.
5. Perguntar: seguir para pesquisa ou revisar triagem?

### Etapa 3 - Pesquisa (skill caso-pesquisa)

1. Com autorizacao do cliente, executar a logica de `.claude/skills/caso-pesquisa.md`.
2. Formular perguntas de pesquisa a partir da triagem (3-7).
3. Percorrer a hierarquia: casos/<slug>/base-conhecimento (se ja tem algo) -> base-conhecimento-geral -> referencias-geral -> referencias-{area} -> WebFetch oficial se necessario.
4. Gerar arquivos-sintese em casos/<slug>/base-conhecimento/.
5. Atualizar INDICE local, linha-do-tempo, status.
6. Apresentar resumo dos achados ao cliente.

### Encerramento

1. Mostrar ao cliente um "dashboard" curto do caso:
   - slug / area / status
   - arquivos principais gerados (descricao.md, triagem.md, base-conhecimento/*.md)
   - tempo-estimado ate proxima etapa
2. Sugerir proximas opcoes:
   - Acionar `caso-reuniao` (reuniao com advogado-civil).
   - Revisar/complementar qualquer artefato.
   - Parar e retomar depois.

## Regras operacionais

- Sempre esperar confirmacao do cliente entre etapas. Nunca pular todas as 3 sem interacao.
- Se cliente pedir para pular uma etapa (ex: "ja triei manualmente"), pular e registrar na linha-do-tempo.
- Se qualquer skill encontrar erro/bloqueio, parar o fluxo e reportar para o cliente decidir.
- Nunca avancar para `caso-reuniao` dentro deste comando - isso e explicitamente fora do escopo do /caso-criar.

## Saida esperada

- Caso estruturado em casos/<classificacao>/<slug>/ com descricao, triagem e KB local.
- linha-do-tempo.md com 3 eventos (intake, triagem, pesquisa).
- Cliente informado do estado e das proximas opcoes.

## Ponteiros

- Skills: .claude/skills/caso-{novo,triagem,pesquisa}.md
- Regras globais: ../../CLAUDE.md

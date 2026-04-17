---
name: caso-novo
description: Inicia um caso novo no escritorio. Coleta descricao inicial do cliente (intake), cria a pasta casos/<slug>/ a partir de casos/_TEMPLATE, salva descricao.md. Usar quando o cliente diz "novo caso", "abrir caso", "caso novo", ou no comeco do fluxo /caso-criar.
---

# Skill: caso-novo

## Quando usar

- Cliente humano menciona "novo caso", "abrir caso", "caso novo", "quero comecar um caso".
- Primeira etapa do comando orquestrador `/caso-criar`.
- Intake inicial, antes de qualquer triagem, pesquisa ou reuniao.

## Pre-requisitos

- Diretorio `casos/_TEMPLATE/` existe (mesmo que placeholder vazio).
- Cliente forneceu alguma descricao do caso (ainda que em linguagem livre).

## Passos

1. **Extrair descricao do cliente.** Ler a mensagem atual do cliente. Se a descricao estiver vaga ou incompleta, perguntar (ao humano) antes de prosseguir:
   - Parte(s) envolvida(s) e polo (autor ou reu prospectivo).
   - Fatos essenciais, com datas aproximadas.
   - Documentos ja disponiveis.
   - Pretensao do cliente (o que quer obter).
   - Prazo ou urgencia percebida.
   - Jurisdicao (cidade/estado).
   - Valor economico estimado.

2. **Gerar slug.** kebab-case, ate 50 caracteres, descritivo da materia, sem acentos, sem nome real de parte, sem CPF. Exemplos: `contrato-locacao-inadimplemento`, `sucessao-testamento-contestado`, `acidente-transito-danos-morais`.

3. **Criar pasta do caso.** Decidir classificacao:
   - Caso exemplo didatico -> `casos/exemplos/<slug>/`.
   - Caso real -> `casos/reais/<slug>/` (criar `reais/` se nao existir; `.gitignore` ja cobre).
   - Caso sintetico de teste -> `casos/exemplos/<slug>/`.
   - Se nao estiver claro, perguntar ao cliente.

4. **Copiar estrutura do `_TEMPLATE/`.** Se `_TEMPLATE/` estiver vazio, criar no proprio caso o esqueleto:
   - `descricao.md` (conteudo real, preenchido no passo 5).
   - `triagem.md` (placeholder comentado, nao preencher aqui).
   - `base-conhecimento/INDICE.md` (placeholder).
   - `reunioes/` (diretorio vazio com `.gitkeep` se versionado).
   - `pecas/` (diretorio vazio).
   - `linha-do-tempo.md` (placeholder com o evento "intake" como primeiro item).
   - `tese.md` (placeholder).
   - `README.md` (resumo executivo curto do caso, atualizavel).

5. **Preencher `descricao.md`.** Frontmatter YAML do tipo caso:
   ```yaml
   ---
   tipo: caso
   slug: <slug>
   cliente: <nome ou "anonimo">
   polo: autor | reu | ambos
   area-primaria: civil
   areas-secundarias: []
   status: intake
   data-abertura: YYYY-MM-DD
   urgencia: baixa | media | alta
   ---
   ```
   Seguido das secoes:
   - `# <Titulo humano do caso>`
   - `## Partes`
   - `## Fatos` (narrativa em ordem cronologica)
   - `## Documentos disponiveis`
   - `## Pretensao`
   - `## Jurisdicao e valor`
   - `## Observacoes`

6. **Registrar linha-do-tempo.** Adicionar primeiro evento em `linha-do-tempo.md`:
   `YYYY-MM-DD - intake inicial - cliente descreveu o caso`.

7. **Confirmar ao cliente.** Mensagem curta contendo:
   - Slug gerado.
   - Caminho absoluto da pasta do caso.
   - Lista de arquivos criados.
   - Sugestao de proximo passo: acionar skill `caso-triagem`.

## Saida esperada

- Diretorio `casos/.../<slug>/` criado com `descricao.md` preenchida e esqueleto das subpastas e subarquivos.
- `linha-do-tempo.md` com o evento inicial de intake registrado.
- Mensagem curta ao cliente listando o que foi feito e o proximo passo.

## Nao fazer

- Nao iniciar pesquisa juridica aqui (e skill `caso-pesquisa`).
- Nao invocar subagents advogados (e skill `caso-reuniao`).
- Nao gerar peca processual (e skill `caso-peca`).
- Nao preencher `triagem.md` (e skill `caso-triagem`).
- Nao usar nome real de parte ou CPF no slug.
- Nao commitar arquivos de `casos/reais/**`.

## Ponteiros

- Skill seguinte no fluxo: `caso-triagem`.
- Template base: `casos/_TEMPLATE/`.
- Regras do caso: `casos/CLAUDE.md`.
- Workflow canonico: `CLAUDE.md` (raiz).

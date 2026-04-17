---
name: caso-reuniao
description: Orquestra uma reuniao entre o cliente humano e um ou mais subagents advogados invocados via Task tool. Usa a KB do caso como contexto. Registra a ata em casos/<slug>/reunioes/YYYY-MM-DD-<titulo>.md. No MVP, time costuma ser [advogado-civil]. Usar apos caso-pesquisa ou quando cliente pede "reuniao", "chamar advogado", "ouvir o time".
---

# Skill: caso-reuniao

## Quando usar

- Apos `caso-pesquisa` ter alimentado a KB do caso.
- Ou quando cliente pede "reuniao", "chamar Dr. X", "ouvir o civil", "formar tese".

## Pre-requisitos

- `casos/<slug>/` existe com `triagem.md` e `base-conhecimento/` populado.
- Time de advogados identificado em `triagem.md` (no MVP: [advogado-civil]).

## Passos

1. **Definir objetivo da reuniao** com o cliente:
   - Formar tese principal e subsidiaria?
   - Avaliar risco de determinada estrategia?
   - Decidir se vale a pena ajuizar / contestar / recorrer?
   - Brainstorm de fundamentos?
   Registrar em 1-2 linhas.

2. **Montar contexto para o(s) subagent(s)**. Preparar um pacote com:
   - Resumo do caso (da `descricao.md`).
   - Triagem (areas, complexidade, riscos).
   - KB consolidada (`leis-aplicaveis.md`, `sumulas-aplicaveis.md`, `jurisprudencia-aplicavel.md`, `precedentes-vinculantes.md` do caso).
   - `questoes-abertas.md` (gaps conhecidos).
   - Objetivo da reuniao.
   - Pergunta(s) especifica(s) ao advogado.

3. **Invocar subagent via Task tool**. Para cada advogado do time, usar Task tool com:
   - `subagent_type`: nome do subagent (ex: "advogado-civil").
   - `description`: curta, ex: "Reuniao caso <slug> - tese de <tema>".
   - `prompt`: pacote de contexto construido no passo 2 + pergunta explicita. Instruir o advogado a responder em <= 800 palavras com: (a) tese principal fundamentada; (b) tese(s) subsidiaria(s); (c) riscos e contra-argumentos previsiveis; (d) proximos passos concretos; (e) disclaimer obrigatorio.

4. **Se multiplos advogados**, INVOCAR EM PARALELO (multiplos Task tool calls numa mesma mensagem), nao sequencial. Cada um responde independentemente. No MVP so tem civil, entao tipicamente apenas 1.

5. **Receber respostas e consolidar**.
   - Se divergencia entre advogados, destacar os pontos divergentes.
   - Se convergencia, sintetizar em 1 tese consensual.

6. **Apresentar ao cliente humano**. Mostrar as opinioes (na integra ou resumidas), abrir espaco para perguntas de follow-up. Se o cliente quiser aprofundar, voltar ao passo 3 com pergunta refinada, eventualmente re-invocando o(s) subagent(s).

7. **Registrar a ata em `casos/<slug>/reunioes/YYYY-MM-DD-<titulo-slug>.md`** com frontmatter YAML:

   ```yaml
   ---
   tipo: reuniao
   slug-caso: <slug>
   data: YYYY-MM-DD
   participantes: [cliente-humano, advogado-civil]
   objetivo: <texto curto>
   status: concluida | pendente-follow-up
   ---
   ```

   Corpo:
   - `# Reuniao - <titulo> - YYYY-MM-DD`
   - `## Objetivo`
   - `## Contexto enviado aos advogados`
   - `## Posicao do advogado-civil` (transcricao/resumo da resposta do subagent)
   - `## Perguntas do cliente e respostas`
   - `## Tese consolidada`
   - `## Decisoes tomadas`
   - `## Acoes pendentes` (com responsavel e prazo)

8. **Atualizar `linha-do-tempo.md`**: `YYYY-MM-DD - reuniao - objetivo: X - status: Y`.

9. **Atualizar `tese.md`** do caso (sobrescrever ou versionar) com a tese atual.

10. **Atualizar status** em `descricao.md`: para `tese-formada` ou manter se reuniao foi parcial.

## Regras

- Cliente humano e sempre quem decide. Subagents opinam.
- Disclaimers dos subagents sao preservados integralmente na ata.
- Reunioes podem ser sequenciais (mesma ata ou novo arquivo, criterio do cliente).

## Nao fazer

- Nao redigir peca aqui (e `caso-peca`).
- Nao modificar `referencias-*` ou `base-conhecimento-geral/`.
- Nao inventar posicao do advogado; sempre usar resposta real do subagent.

## Ponteiros

- Anterior: `caso-pesquisa`.
- Proxima (opcional): `caso-peca`.
- Subagents em `.claude/agents/advogados/`.

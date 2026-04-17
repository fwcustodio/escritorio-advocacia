---
name: caso-triagem
description: Analisa a descricao de um caso (descricao.md) e identifica a(s) area(s) juridica(s) envolvidas, classifica complexidade, monta o time de subagents advogados a ser convocado, e grava casos/<slug>/triagem.md. No MVP, so existe advogado-civil. Invocar apos caso-novo, antes de caso-pesquisa.
---

# Skill: caso-triagem

## Quando usar

- Apos `caso-novo` ter criado `descricao.md`.
- Quando o cliente pede para "triar", "classificar", "definir area" de um caso existente.
- Segunda etapa do fluxo `/caso-criar`, antes de `caso-pesquisa`.

## Pre-requisitos

- Existe `casos/<slug>/descricao.md` preenchido.
- Acesso leitura a `base-conhecimento-geral/` e `referencias-*`.

## Passos

1. **Ler `descricao.md` do caso** e extrair fatos, partes, pretensao, jurisdicao, valor e urgencia.

2. **Mapear para areas juridicas.** Considerar primarias e secundarias:
   - Dominio civil puro: obrigacoes, contratos, responsabilidade civil (material/moral), direitos reais, familia, sucessoes.
   - Dominio consumidor: relacao de consumo (CDC).
   - Dominio locaticio: Lei 8.245/91.
   - Dominio registral: registros publicos, usucapiao.
   - Mencionar sub-area especifica (ex: "contratos -> locacao urbana comercial").

3. **Avaliar complexidade** (baixa / media / alta) considerando:
   - Numero de partes.
   - Quantidade de questoes juridicas distintas.
   - Necessidade de pericia.
   - Valor economico.
   - Urgencia (tutela provisoria, prescricao iminente).
   - Existencia de precedentes vinculantes.

4. **Avaliar riscos do cliente** em 3 dimensoes:
   - Risco de sucesso (chance de exito da tese).
   - Risco de custo (honorarios sucumbenciais, custas, producao de provas).
   - Risco de tempo (duracao estimada ate sentenca / transito em julgado).

5. **Montar time de advogados.** No MVP apenas `advogado-civil` existe:
   - Sempre incluir `advogado-civil` quando area-primaria e civil/consumidor/locacao.
   - Se houver area fora do civel (trabalhista, tributario, penal, administrativo, societario complexo), SINALIZAR gap: "Area X detectada, subagent nao existente no MVP - recomendar advogado humano ou expansao futura."
   - Se for caso que exige multiplas perspectivas civis (ex: sucessao + consumo), ainda assim um so `advogado-civil` atende.

6. **Sugerir estrategia inicial (1-3 opcoes).** Cada opcao em bullet com: tese, fundamento (artigos / sumulas / acordaos), pros, contras.

7. **Gerar `casos/<slug>/triagem.md`** com frontmatter YAML:
   ```yaml
   ---
   tipo: triagem
   slug: <slug>
   data-triagem: YYYY-MM-DD
   status: triado
   area-primaria: civil
   areas-secundarias: [consumidor, locacao]
   complexidade: baixa | media | alta
   time: [advogado-civil]
   riscos:
     sucesso: alto | medio | baixo
     custo: baixo | medio | alto
     tempo: curto | medio | longo
   ---
   ```

   Corpo com secoes:
   - `# Triagem: <titulo do caso>`
   - `## Areas juridicas identificadas`
   - `## Complexidade e justificativa`
   - `## Time proposto`
   - `## Riscos preliminares`
   - `## Opcoes de estrategia inicial (1-3)`
   - `## Proximos passos recomendados` (tipicamente: `caso-pesquisa` depois `caso-reuniao`).

8. **Atualizar `descricao.md`:** mudar `status` de `intake` para `triado`; incluir `areas-secundarias` no frontmatter se houver.

9. **Atualizar `linha-do-tempo.md`:** adicionar evento `YYYY-MM-DD - triagem - areas: [...], time: [...]`.

10. **Confirmar ao cliente:** resumo curto em 5-8 linhas (areas, time, 1-3 estrategias, proximo passo).

## Saida esperada

- `casos/<slug>/triagem.md` criado.
- `descricao.md` atualizado (status e areas-secundarias).
- `linha-do-tempo.md` atualizada com evento de triagem.
- Mensagem de confirmacao curta ao cliente.

## Nao fazer

- Nao convocar advogado (subagent) nesta skill - isso e `caso-reuniao`.
- Nao fazer pesquisa detalhada de jurisprudencia - isso e `caso-pesquisa`.
- Nao redigir peca processual - isso e `caso-peca`.
- Nao alterar dados de fato/partes vindos da `descricao.md`.

## Ponteiros

- Anterior no fluxo: `caso-novo`.
- Proxima skill: `caso-pesquisa`.
- Regras do caso: `casos/CLAUDE.md`.
- Workflow canonico: `CLAUDE.md` (raiz).

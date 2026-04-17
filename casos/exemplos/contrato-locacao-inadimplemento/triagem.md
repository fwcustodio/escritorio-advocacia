---
tipo: triagem
slug: contrato-locacao-inadimplemento
data-triagem: 2026-04-16
status: triado
area-primaria: locacao
areas-secundarias: [civil-contratos, responsabilidade-civil]
complexidade: media
time: [advogado-civil]
riscos:
  sucesso: alto
  custo: medio
  tempo: medio
---

# Triagem: Contrato de locacao residencial - inadimplemento de alugueis e despejo

## Areas juridicas identificadas

- Area primaria: locacao urbana residencial, regida pela Lei 8.245/1991 (Lei do Inquilinato). Dispositivos centrais: art. 9, III (resilicao por falta de pagamento), art. 62 (rito especial de despejo cumulado com cobranca), art. 59, par. 1 (hipoteses de liminar), art. 63 (prazo de desocupacao), arts. 39 e 40 (responsabilidade e exoneracao do fiador).
- Areas secundarias:
  - Direito Civil (contratos e obrigacoes): CC arts. 389 (perdas e danos no inadimplemento), 394-395 (configuracao da mora), 406 (taxa legal de juros), 422 (boa-fe objetiva), 475 (resolucao por inadimplemento), 818 e 822 (regime da fianca). A Lei do Inquilinato nao esgota a materia: recorrer ao CC para multa, juros, correcao, solidariedade e regime contratual subsidiario.
  - Responsabilidade civil contratual: mora ex re nas obrigacoes positivas liquidas com termo certo (CC art. 397) - juros e correcao sobre cada aluguel a partir do respectivo vencimento.
- Area processual: CPC arts. 300 (tutela de urgencia), 292 (valor da causa), 319 (requisitos da inicial), 322 (pedido certo e determinado), 77 (litisconsorcio passivo com o fiador).

## Complexidade e justificativa

Complexidade **media**. Justificativa:
- Partes: 3 (autor, locataria, fiador solidario), com necessidade de litisconsorcio passivo.
- Questoes juridicas distintas mas todas ja cobertas por lei especial e jurisprudencia pacificada: (i) despejo por falta de pagamento; (ii) cobranca cumulada; (iii) responsabilidade do fiador; (iv) cabimento de liminar mediante caucao; (v) criterios de atualizacao e juros.
- Nao ha necessidade prevista de pericia tecnica; a prova e majoritariamente documental (contrato, comprovantes, notificacao com AR).
- Valor economico estimado R$ 30.000,00 - medio.
- Urgencia media-alta: ja ha sete meses de inadimplemento e imovel ocupado; possivel tutela de urgencia.
- Existem precedentes pacificados sobre cada ponto controvertido (solidariedade do fiador, rito especial, purga da mora).

## Time proposto

- `advogado-civil` (Dr. Rafael Almeida Vasconcelos): unico subagent necessario. Locacao urbana e tangencial ao civil, expressamente incluida na especialidade do civilista no MVP.
- Nao ha outras areas fora do civel envolvidas. Sem gaps de subagent.

## Riscos preliminares

- **Sucesso: ALTO**. Prova documental robusta: contrato escrito, comprovantes de pagamento ate 09/2025, notificacao extrajudicial com AR, resposta da locataria reconhecendo o debito ao pedir parcelamento. Inadimplemento incontroverso por tempo substancial. A tese adversa tipica (negativa de mora, pagamento, alegacao de vicio no imovel) esta fragilizada pela propria confissao extrajudicial.
- **Custo: MEDIO**. Custas iniciais proporcionais ao valor da causa (tabela do TJSP), preparo recursal eventual, honorarios sucumbenciais ficam a cargo dos reus em caso de procedencia. Producao probatoria minima, majoritariamente documental; pericia contabil eventual para apurar valores finais. Risco residual de gratuidade de justica deferida a locataria, reduzindo a recuperabilidade do sucumbencial.
- **Tempo: MEDIO**. O rito especial do art. 62 da Lei 8.245 acelera o tramite em relacao ao comum. Liminar de desocupacao possivel em caso de ausencia de garantia (art. 59, par. 1, IX) - no caso concreto ha fianca, o que condiciona a caucao de tres alugueis (art. 59, par. 1). Sentenca em primeiro grau tende a sair em 6 a 12 meses; despejo efetivo pode ter adiamento por recursos e eventual purga da mora.

## Opcoes de estrategia inicial

**Opcao A - Acao de despejo por falta de pagamento cumulada com cobranca (OPCAO-PADRAO).**

- Tese: resolucao da locacao por inadimplemento + cobranca dos alugueis vencidos e vincendos ate a entrega das chaves, com acessorios.
- Fundamento: Lei 8.245/1991 art. 9, III, e art. 62, I; CC art. 389, 395, 406, 475; CPC arts. 319, 322, 300.
- Pros: retomada rapida do imovel; rito especial; cobranca no mesmo processo; responsabilidade solidaria do fiador; possibilidade de tutela de urgencia mediante caucao.
- Contras: risco de purga da mora (art. 62, II); risco residual de gratuidade de justica da ré; necessidade de caucao para liminar.

**Opcao B - Acao somente de cobranca (mantendo a locacao).**

- Tese: manter o contrato vigente e apenas cobrar os valores em atraso.
- Fundamento: CC arts. 389, 395, 406; Lei 8.245 art. 9, III (despejo) nao invocado.
- Pros: evita o tempo/custo do despejo; pode ser util se o locador tiver interesse em preservar a relacao com garantia reforcada.
- Contras: nao retoma o imovel; locataria segue ocupando sem pagar e o debito cresce; nao e o desejado pelo cliente no caso concreto.

**Opcao C - Tentativa de acordo extrajudicial com parcelamento e confissao de divida.**

- Tese: acordo com confissao de divida, parcelamento, reforcamento de garantia (ex: nova fianca bancaria ou caucao em dinheiro) e/ou entrega voluntaria das chaves com prazo.
- Fundamento: CC arts. 840-850 (transacao); CPC art. 487, III, b (homologacao).
- Pros: rapido, previsivel, baixo custo; evita desgaste processual.
- Contras: a locataria ja respondeu sem proposta concreta; o tempo corre contra o locador; risco de nao adimplemento do proprio acordo. Viavel como iniciativa paralela enquanto se prepara a inicial.

## Proximos passos recomendados

1. Acionar `caso-pesquisa` para consolidar a base de conhecimento especifica (leis-aplicaveis, sumulas, jurisprudencia, precedentes, questoes-abertas).
2. Em sequencia, convocar `caso-reuniao` com o `advogado-civil` para fechar a tese principal e subsidiaria.
3. Por fim, `caso-peca` para minutar a peticao inicial de despejo cumulado com cobranca e pedido de tutela de urgencia.

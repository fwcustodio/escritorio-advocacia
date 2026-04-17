---
tipo: reuniao
slug-caso: contrato-locacao-inadimplemento
data: 2026-04-16
participantes: [cliente-humano, advogado-civil (simulado no smoke test)]
objetivo: definir tese e estrategia inicial
status: concluida
---

# Reuniao - Tese inicial - 2026-04-16

## Objetivo

Definir, em conjunto entre o cliente humano e o subagent advogado-civil (Dr. Rafael Almeida Vasconcelos), a tese principal e as teses subsidiarias para o ajuizamento; decidir a forma da acao, o polo passivo, a competencia, o cabimento de tutela provisoria e os consectarios do inadimplemento a serem incluidos nos pedidos.

## Contexto enviado ao advogado

Foi enviado ao subagent o pacote de contexto composto por:

- Resumo do caso extraido de `descricao.md` (contrato de locacao 2024-03-15, aluguel de R$ 3.500,00, garantia por fianca solidaria de Roberto Pereira, inadimplemento desde 10/2025, 7 meses em aberto em 2026-04-16, notificacao extrajudicial com AR em 2026-02-10, resposta sem proposta concreta, imovel ocupado).
- Triagem (`triagem.md`): area primaria locacao, secundarias civil-contratos e responsabilidade-civil; time [advogado-civil]; complexidade media; riscos sucesso alto, custo medio, tempo medio.
- Base de conhecimento consolidada (`base-conhecimento/leis-aplicaveis.md`, `sumulas-aplicaveis.md`, `jurisprudencia-aplicavel.md`, `precedentes-vinculantes.md`).
- `questoes-abertas.md`: lacunas factuais (prorrogacao do contrato, anuencia do fiador, clausula de multa, encargos, qualificacao completa) e lacunas de pesquisa (Sumulas 214, 549 e 268 do STJ a reverificar).
- Pergunta objetiva: "Qual a tese principal e as subsidiarias? Ha fundamento para tutela de urgencia? Como distribuir polo passivo e consectarios?".

## Posicao do advogado-civil (Dr. Rafael Almeida Vasconcelos) - simulada no smoke test

Sintese objetiva. Estamos diante de locacao residencial urbana por prazo determinado, celebrada em 2024-03-15 pelo prazo de 30 meses, com garantia por fianca solidaria de Roberto Pereira. A locataria pagou regularmente ate setembro de 2025 e, desde outubro de 2025, esta em mora ex re (CC art. 397), acumulando sete alugueis em aberto ate 2026-04-16. A notificacao extrajudicial com AR, de 2026-02-10, reforca a documentacao da mora, embora seja dispensavel para a caracterizacao do inadimplemento em obrigacao positiva liquida com termo certo. A resposta da locataria, pedindo parcelamento sem proposta concreta, configura inclusive confissao extrajudicial do debito.

Fundamentos e tese principal. A via adequada e a **acao de despejo por falta de pagamento cumulada com cobranca de alugueis e acessorios da locacao**, pelo rito especial do art. 62 da Lei 8.245/1991. A competencia e do Foro da situacao do imovel, em Sao Paulo/SP, nos termos do art. 58, II, da Lei 8.245/1991 e subsidiariamente do art. 47 do CPC/2015 (foro da situacao da coisa). O polo passivo comporta litisconsorcio entre a locataria e o fiador solidario, com base nos arts. 39 e 40 da Lei 8.245/1991 e, no plano material, na solidariedade convencional - afastado o beneficio de ordem pela renuncia expressa (CC art. 828, I). A obrigacao do fiador persiste ate a efetiva entrega das chaves (art. 39 da Lei 8.245/1991), sem prejuizo de eventual exoneracao se comprovada a prorrogacao sem anuencia.

Tutela de urgencia. O rol do art. 59, par. 1, da Lei 8.245/1991 e taxativo para a liminar de despejo e, formalmente, o inciso IX refere-se a denuncia vazia; o inciso VIII, a locacao sem garantia. No caso concreto ha fianca, o que reduz a aderencia ao rol taxativo. Contudo, remanesce a via geral do art. 300 do CPC/2015: ha probabilidade do direito (contrato, comprovantes e confissao extrajudicial) e perigo de dano (sete meses de inadimplemento e imovel ocupado, risco de agravamento). Minuta-se o pedido de tutela de urgencia **mediante caucao equivalente a tres alugueis**, com fundamento combinado no art. 59, par. 1, da Lei 8.245/1991 e no art. 300 do CPC/2015. Cuidado na fundamentacao: reverificar jurisprudencia antes do protocolo, pois a concessao em contratos com fianca nao e pacifica.

Consectarios. Cobranca dos alugueis vencidos de 10/2025 a 04/2026 e dos vincendos ate a efetiva entrega das chaves (art. 62, I, Lei 8.245/1991 e art. 323 do CPC/2015), acrescidos de encargos contratuais, multa moratoria (reverificar o percentual pactuado), juros legais (CC art. 406) e correcao monetaria desde cada vencimento (CC arts. 389 e 395). Honorarios sucumbenciais e custas processuais a cargo dos reus.

Subsidiariamente. Caso a prioridade do cliente seja a retomada celere do imovel, admitir acordo homologado com confissao de divida, parcelamento, reforco de garantia e prazo certo de desocupacao voluntaria. Jamais manter a locacao sem reforco de garantia.

Disclaimer. Este e apoio tecnico de subagent, nao substitui consulta a advogado habilitado na OAB.

## Perguntas do cliente e respostas

### 1. "O fiador pode alegar beneficio de ordem?"

Resposta. Nao, se a fianca foi pactuada com clausula expressa de solidariedade ou com renuncia ao beneficio de ordem (CC art. 828, I e III). A praxe contratual dominante na locacao urbana residencial e a fianca solidaria; a descricao do caso indica que o fiador foi pactuado como solidario. Confirmar a clausula especifica no contrato de 2024-03-15. Mesmo sem renuncia expressa, o STJ ja acolheu que a contratacao da fianca na locacao com clausula de solidariedade afasta o beneficio de ordem. Se, excepcionalmente, a fianca nao fosse solidaria, a locataria deveria ser executada primeiro, prejudicando a efetividade da execucao.

### 2. "Se a inquilina purgar a mora, a acao cai?"

Resposta. Parcialmente. O art. 62, II e paragrafo unico, da Lei 8.245/1991 permite a purga da mora em 15 dias da citacao, uma vez a cada 24 meses, abrangendo a totalidade dos alugueis, encargos, multa, juros, correcao, custas e honorarios. Efetuada a purga integral, extingue-se apenas o pedido de despejo; o processo pode seguir em relacao a eventuais saldos controversos, mas, em regra, a acao perde seu objeto quanto a retomada. Nao ha purga em caso de reincidencia no mesmo periodo de 24 meses, nem se o valor depositado for insuficiente. E estrategica a previsao, na inicial, de planilha detalhada para impugnar eventual purga parcial.

## Tese consolidada

Despejo por falta de pagamento cumulado com cobranca, pelo rito especial do art. 62 da Lei 8.245/1991, com pedido de tutela de urgencia para desocupacao mediante caucao de tres alugueis, em face da locataria e do fiador solidario, com cobranca dos alugueis vencidos e vincendos, encargos, multa, juros legais e correcao monetaria.

## Decisoes tomadas

- Ajuizar a acao no Foro Central Civel da Comarca de Sao Paulo/SP.
- Incluir a locataria Helena Barbosa dos Santos e o fiador Roberto Pereira no polo passivo.
- Requerer tutela de urgencia para desocupacao, mediante caucao.
- Minutar a peticao inicial (acionar skill `caso-peca` em seguida).

## Acoes pendentes

- **Cliente**: juntar matricula atualizada do imovel, AR da notificacao extrajudicial e copia integral do contrato com todas as clausulas (especialmente multa, reajuste IGP-M e encargos); esclarecer se houve prorrogacao do contrato apos o termo de 30 meses e, caso positivo, se o fiador anuiu. Prazo sugerido: 5 dias.
- **Advogado (apoio)**: reverificar, em fonte oficial, as Sumulas 214, 549 e 268 do STJ, e eventuais Temas repetitivos sobre purga da mora e liminar de despejo com fianca.
- **Responsavel pela minuta**: acionar `caso-peca` para a peticao inicial.

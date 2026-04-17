# CLAUDE.md - referencias-geral

## Proposito

Pasta de referencias transversais que servem a todas as areas do escritorio. Conteudo generico, reaproveitavel entre casos e materias. Nao contem material vinculado a area especifica (civel, trabalhista, tributario) - esses ficam em `referencias-{area}/`.

## Conteudo tipico

- Dicionarios e glossarios juridicos (termos, abreviacoes, latim forense).
- Tabelas de prazos processuais (CPC, CPP, CLT, Fazenda Publica).
- Modelos de peca genericos (procuracao, substabelecimento, declaracao de hipossuficiencia).
- Guias de citacao (ABNT NBR 6023, vancouver-juridico, citacao de jurisprudencia).
- Tabelas de custas e emolumentos (TJ, tribunais superiores).
- Enderecos e competencias (foros, varas, tribunais).

## Schema do INDICE.md

Todo diretorio de referencia ou base de conhecimento DEVE ter um `INDICE.md`. Estrutura minima:

- Cabecalho H1 com o nome da pasta.
- Paragrafo curto explicando o conteudo da pasta.
- Lista de entradas, uma linha por arquivo, sob secao `## Entradas`.

Formato de linha OBRIGATORIO para cada entrada:

```
- [arquivo.md](arquivo.md) - tipo - ano - resumo em uma frase
```

Onde:

- `tipo` casa com o campo `tipo` do frontmatter (lei, jurisprudencia, sumula, doutrina, enunciado, tabela, glossario, modelo).
- `ano` e o ano do documento (ex: 2002 para o CC).
- `resumo` e frase curta (< 15 palavras) descrevendo o que o arquivo traz.

Exemplo completo de INDICE.md:

```
# INDICE - Referencias Civis - Leis

Leis civis de referencia. Atualizar ao adicionar/remover arquivos.

## Entradas

- [codigo-civil.md](codigo-civil.md) - lei - 2002 - indice navegavel do Codigo Civil (Lei 10.406/2002).
- [cdc.md](cdc.md) - lei - 1990 - Codigo de Defesa do Consumidor (Lei 8.078/1990).
- [inquilinato.md](inquilinato.md) - lei - 1991 - Lei do Inquilinato (Lei 8.245/1991).
```

## Schema do frontmatter YAML

Todo arquivo de REFERENCIA (em `base-conhecimento-geral/`, `referencias-geral/`, `referencias-{area}/`) DEVE comecar com frontmatter YAML delimitado por `---`.

Campos obrigatorios:

- `tipo`: lei | jurisprudencia | sumula | doutrina | enunciado | tabela | glossario | modelo
- `fonte`: URL canonica no Planalto/STJ/STF/TJ respectivo, ou link curado para doutrina.
- `jurisdicao`: federal | estadual-SP | estadual-RJ | municipal-{uf-cidade} | internacional
- `data`: YYYY-MM-DD (data do documento original: promulgacao da lei, publicacao do acordao, edicao da sumula).
- `ano`: YYYY (redundante com `data` mas facilita parse/filtro).
- `area`: civil | processual-civil | constitucional | consumidor | familia | sucessoes | obrigacoes | contratos | responsabilidade-civil | coisas | locacao | registros-publicos | ... (kebab-case).
- `tags`: lista kebab-case (ex: `[contrato, responsabilidade-civil, dano-moral]`).
- `resumo`: string em uma linha (< 200 caracteres), descreve o que o arquivo traz.

Campos opcionais:

- `relator`: nome do ministro/desembargador (para jurisprudencia).
- `orgao`: STF, STJ, TJSP, TRF3, etc. (para jurisprudencia/sumula).
- `numero`: numero da sumula, lei, ou acordao.
- `revogado`: true/false (leis). Default: false. Se true, campo `revogado_por` opcional.

Exemplo completo de frontmatter:

```yaml
---
tipo: lei
fonte: https://www.planalto.gov.br/ccivil_03/leis/2002/l10406compilada.htm
jurisdicao: federal
data: 2002-01-10
ano: 2002
area: civil
tags: [codigo-civil, parte-geral, direito-das-obrigacoes, contratos, familia, sucessoes]
resumo: Indice navegavel do Codigo Civil brasileiro (Lei 10.406/2002), linkando para artigos no Planalto.
numero: 10.406/2002
revogado: false
---
```

## Regras de integridade

- Toda adicao de arquivo de referencia EXIGE: frontmatter YAML + atualizacao do `INDICE.md` da pasta.
- Dados desatualizados ou leis revogadas devem ser marcadas com `revogado: true`.
- URL da fonte deve ser a canonica oficial. Links secundarios podem ser listados no corpo, mas nao em `fonte`.
- Frontmatter ausente ou campos obrigatorios faltando invalidam o arquivo para indexacao por skills.
- Kebab-case obrigatorio em `area` e `tags`. Nao usar espacos, acentos ou camelCase.

## Ponteiros

- CLAUDE.md raiz: ../CLAUDE.md
- Skills que leem este schema: .claude/skills/caso-pesquisa.md

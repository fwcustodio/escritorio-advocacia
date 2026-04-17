# Como adicionar acordaos em jurisprudencia/

Guia operacional para curadoria de jurisprudencia civel. Este arquivo NAO eh uma referencia indexavel - eh documentacao de processo. Por isso nao possui frontmatter YAML.

## Passo 1 - Localizar o acordao

Fontes oficiais preferidas:
- STJ: https://scon.stj.jus.br (pesquisa de jurisprudencia e sumulas)
- STF: https://portal.stf.jus.br/jurisprudencia
- TJs estaduais: portal de jurisprudencia do tribunal competente (ex: esaj.tjsp.jus.br para TJSP)
- Teses e repetitivos STJ: https://www.stj.jus.br/repetitivos

Preferir acordaos com tese fixada, precedentes qualificados (art. 927 CPC) ou que consolidam entendimento (IRDR, IAC, tema repetitivo).

## Passo 2 - Nomear o arquivo

Slug legivel, kebab-case, sem acentos. Padrao recomendado:

```
{orgao}-{classe}-{numero}-{uf-origem}-{ano}.md
```

Exemplos:
- stj-resp-1737412-se-2020.md
- stj-reesp-1629723-rj-2019.md
- stf-re-591-874-rs-2009.md
- tjsp-ac-1001234-82-2020-8-26-0100-2022.md

## Passo 3 - Frontmatter YAML obrigatorio

Todo arquivo deve ter frontmatter completo:

```yaml
---
tipo: jurisprudencia
fonte: https://scon.stj.jus.br/SCON/...    # URL direto do acordao/ementa
jurisdicao: federal                         # ou estadual-SP, estadual-RJ etc
orgao: STJ                                   # STJ, STF, TJSP, TJRJ etc
relator: Min. Fulano de Tal                  # nome completo
data: 2020-05-15                             # YYYY-MM-DD (publicacao ou julgamento)
ano: 2020
area: responsabilidade-civil                 # kebab-case especifica
tags: [dano-moral, instituicao-financeira, fortuito-interno]
numero: REsp 1.737.412/SE                    # numero processual
resumo: Uma linha descrevendo a tese central do acordao.
---
```

Campos obrigatorios: tipo, fonte, jurisdicao, orgao, relator, data, ano, area, tags, numero, resumo.

## Passo 4 - Corpo do arquivo

Estrutura minima do markdown:

```markdown
# {Numero do processo} - {resumo curto da tese}

## Ementa

Transcricao literal (quando curta) ou parafraseada (quando extensa) da ementa.
Indicar entre colchetes [parafraseada] quando reescrita.

## Tese fixada

Enunciado objetivo do que o tribunal definiu. Se tese repetitiva (TEMA N), apontar o numero.

## Ratio decidendi

- Fundamento 1 que sustenta a decisao.
- Fundamento 2.
- Fundamento 3.
- (3 a 5 bullets, focados nos argumentos-nucleo)

## Dispositivos aplicados

- CC art. 927 (responsabilidade civil)
- CDC art. 14 (fato do servico)
- CPC art. 1036 (repetitivo)
- ...

## Aplicacao pratica

Em uma ou duas linhas: quando usar este precedente, a favor de quem, em que tipo de caso.

## Links

- Acordao integral (STJ/STF): ...
- Inteiro teor: ...
```

NAO copiar texto integral do acordao em massa. Foco: ementa + ratio + aplicacao.

## Passo 5 - Atualizar jurisprudencia/INDICE.md

Adicionar linha na secao "## Entradas":

```
- [stj-resp-1737412-se-2020.md](stj-resp-1737412-se-2020.md) - jurisprudencia - 2020 - resumo em uma frase.
```

## Passo 6 - Teses repetitivas (art. 1036 CPC)

Se o acordao fixar tese em sede de recurso repetitivo:
- Marcar "TEMA {N}" no campo `resumo` do frontmatter.
- Adicionar tag `tema-repetitivo` e `tema-{n}` em `tags`.
- Destacar "TEMA {N}" no H1 do corpo e na secao "## Tese fixada".
- Fontes: https://www.stj.jus.br/repetitivos e scon.stj.jus.br.

## Boas praticas

- Preferir acordaos consolidados (repetitivos, IRDR, IAC, enunciados de smula).
- Atualizar periodicamente: teses podem ser revistas, superadas (overruling) ou distinguidas. Anotar no corpo quando houver overruling posterior.
- Em acordao divergente ou monocratica, indicar claramente que nao eh entendimento consolidado.
- Doutrina nao entra aqui - vai para `../doutrina/`.
- Texto integral de acordao inteiro nao deve ser copiado. Indexar, resumir, linkar.

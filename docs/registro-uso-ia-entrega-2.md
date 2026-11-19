# Registro de Uso de IA — Entrega 2

**Ferramenta:** Claude (Anthropic)
**Data:** 19/11/2026
**Grupo:** Gabriel Jésus, José Mateus e Miguel Maciel

## 1. Mapeamento de uso

| Parte | Apoio de IA |
|---|---|
| `css/estilo.css` inteiro (variáveis, layout com Grid e Flexbox, media queries, container query, formulário, foco) | Sim: escrito pela IA |
| Escolha da paleta e cálculo do contraste de cada par de cores | Sim: feito pela IA |
| Mudanças no HTML: `<link>` para o CSS, classes (`.pular`, `.logo`, `.destaques`, `.numeros`, `.aceite`, `.dica`) e `div.tabela` em volta das duas tabelas | Sim: feitas pela IA |
| Testes de largura (320 a 1440px), de teclado (skip link e foco) e validação no W3C | Sim: executados pela IA |
| `docs/entrega-2.md` e atualização do README | Sim: escritos pela IA |
| Revisão técnica (seção 3) | **Problemas encontrados e mudanças decididas pelo grupo**, no teste manual; o código das 3 mudanças foi aplicado com apoio da IA (Prompt 2) |

Como contexto, a IA leu o enunciado do Projeto Integrador e os guias das Aulas 15 (box model,
Flexbox e Grid) e 16 (formulários e responsividade), além do `estilo.css` de exemplo da SATEC 2026.

## 2. Prompts utilizados (na íntegra)

**Prompt 1**

Enviado junto com um print da tarefa "Entrega 2 — Estilo e Responsividade" (aplicar estilos com
CSS e responsividade com flexbox, grid e media queries; entregar o link do repositório com a branch
`entrega-2`).

```
leia [caminho da pasta da disciplina na rede]\Html & Css e faça a entrega-2
```

> O caminho de rede do prompt foi omitido por privacidade; o resto está como foi escrito.

**Prompt 2** (depois do teste manual do grupo)

```
analisamos que a cor do cabeçalho ficaria mais agradavel com um tom de azul mais escuro e que o texto está muito embaixo do texto. Quando o site fica em modo de celular fica meio estranha e achatada
```

A IA perguntou onde estavam os dois últimos problemas, e o grupo respondeu escolhendo entre as
opções mostradas: o texto embaixo do texto é o **slogan sob o logo**, e o que fica estranho e
achatado no celular são as **tabelas espremidas**.

> Acrescentar aqui, na íntegra, qualquer outro prompt que o grupo usar até a entrega.

## 3. Revisão técnica (mínimo de 3 alterações)

Os três problemas foram encontrados pelo grupo no teste manual (no celular e no DevTools), e a
decisão de cada mudança foi do grupo. O código das mudanças foi aplicado com o apoio da IA (Prompt
2) e conferido de novo nas 7 larguras de teste.

| # | O que a IA gerou | O que foi alterado | Por que foi alterado |
|---|---|---|---|
| 1 | Cabeçalho e rodapé em `--cor-primaria: #1e1b4b`, o fundo do logo, um azul puxado para o roxo, com botões do menu em `#312e81`. | `--cor-primaria` passou para o azul-marinho `#0b1a3a`, e `--cor-primaria-2` (botões do menu) para `#1d3b7a`. Como as cores estão em variáveis, a troca vale para cabeçalho, rodapé, títulos e cabeçalho das tabelas de uma vez. | O grupo achou o tom roxo pouco agradável e preferiu um azul mais escuro. O contraste melhorou em todos os pares: branco no cabeçalho foi de 15.99:1 para 17.17:1, ciano de 8.85:1 para 9.50:1 e o contorno de foco de 4.49:1 para 4.82:1. |
| 2 | No celular, o slogan ficava numa linha própria, abaixo do bloco do logo (ícone de 48px + nome), começando na borda esquerda e com espaço entre os dois. No tablet ia para a direita da tela e, no desktop, voltava para baixo do logo. | O cabeçalho ganhou uma 1ª coluna da largura do ícone (`grid-template-columns: 3rem 1fr`) e o mapa `"logo logo" ". slogan" "menu menu"`. O slogan fica na 2ª coluna, encostado no nome (`margin-top: -0.25rem`, `row-gap: 0`) e com letra um pouco menor. No desktop: `3rem auto 1fr` com `"logo logo menu" ". slogan menu"`. | O slogan parecia solto, "muito embaixo" do nome do site. Alinhado ao nome e encostado nele, vira um subtítulo do logo, e a posição fica igual nos três tamanhos. |
| 3 | Para a tabela de preços do PS5 caber em 375px, a IA tinha reduzido a fonte da tabela para 13px e o espaço das células para 4px, e diminuído o recuo interno dos cartões no celular. | A tabela ganhou `min-width: 30rem` e voltou para fonte de 0.9rem e células com `0.5rem 0.75rem`. No celular, ela passa da largura da tela e rola para o lado dentro da `div.tabela` (`overflow-x: auto`); a página continua sem rolagem lateral. Os cartões voltaram a ter `1rem` de recuo. | No celular de verdade, as tabelas ficavam espremidas: letra pequena e colunas tão estreitas que cada célula quebrava em 3 ou 4 linhas. Rolar só a tabela mantém tudo legível, e a `div.tabela` já tinha `tabindex="0"` para rolar também pelo teclado. |

### Ajustes que a própria IA fez durante os testes

Não contam como revisão do grupo, mas mostram o que o teste encontrou:

- A tabela de preços do PS5 passava 10px da tela em 375px. A IA diminuiu o espaço interno dos
  cartões e das células e a fonte da tabela no celular (13px), devolvendo os valores maiores a
  partir do tablet. (Desfeito depois pela alteração 3 do grupo.)
- Em 320px as duas tabelas ainda passavam da tela. A IA envolveu cada tabela numa
  `div.tabela` com `overflow-x: auto`, `role="region"` e `tabindex="0"`, para só a tabela rolar.
- A IA tinha colocado `position: sticky` no `<aside>` do desktop e tirou: num glossário mais alto
  que a tela, o fim dele ficaria inalcançável.

### Pontos para o grupo revisar

Não são alterações prontas, e sim lugares onde vale olhar com atenção:

- **Skip link:** o guia da Aula 15 coloca o skip link numa área `pular` do Grid; aqui ele usa
  `position: absolute` e `transform`. Saber explicar a diferença na defesa.
- **Container query:** é um recurso novo e o validador de CSS do W3C ainda acusa erro. Vale manter
  ou trocar por uma media query comum?
- **Logo:** o ícone (`img/logo.svg`) ainda tem fundo `#1e1b4b`; no cabeçalho azul-marinho ele
  aparece como um quadrado levemente arroxeado. Deixar assim ou trocar a cor do fundo do SVG?
- **Valores de "A crise em números":** ficaram grandes e em negrito. Na lateral estreita do
  desktop, quebram em várias linhas; conferir se está bom.
- **Breakpoints:** testar arrastando a largura no DevTools e ver se 768px e 1200px são mesmo onde
  o conteúdo pede mudança.
- **Teste no celular de verdade:** a IA não usa um celular; o grupo precisa abrir o site no próprio
  aparelho.

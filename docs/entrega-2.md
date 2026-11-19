# Entrega 2 — Estilo e responsividade

CSS próprio, sem framework, em um arquivo externo (`css/estilo.css`) ligado às 6 páginas com
`<link rel="stylesheet" href="css/estilo.css">`. Layout com Grid e Flexbox, variáveis CSS e três
larguras de tela: celular, tablet e desktop.

## Abordagem: mobile first

As regras sem media query descrevem o celular. Cada `@media (min-width: ...)` só acrescenta o que
muda numa tela maior. Escolhemos mobile first porque:

- **O público está no celular.** Mais da metade dos acessos à web vem de celulares, e no Brasil,
  para muita gente, o celular é o único acesso à internet. O assunto do site (preço de consoles,
  jogos e celulares) interessa justamente a quem joga e navega pelo celular.
- **Os buscadores avaliam a versão móvel** (mobile-first indexing).
- **Menos código para desfazer.** Começar com uma coluna e acrescentar colunas é mais simples do
  que montar o desktop e depois desmontar.

As media queries ficam no fim do arquivo (seção 12), porque a media query não aumenta a
especificidade: se viesse antes, a regra base a sobrescreveria.

## Breakpoints

| Largura | O que muda | Onde no CSS |
|---|---|---|
| **Base: celular** (até 767px, testado em 320, 375 e 480px) | Uma coluna: cabeçalho, conteúdo, lateral e rodapé empilhados. Slogan logo abaixo do nome do site. Menu em botões que preenchem a linha (`flex-grow: 1`). Opções do formulário uma por linha. As tabelas mantêm 30rem de largura mínima e rolam para o lado dentro da `div.tabela`. | regras sem `@media` |
| **Tablet** (768px ou mais) | Menu numa linha só. Destaques da home em 2 colunas. Opções do formulário 2 por linha. Rodapé em linha. Mais respiro nas laterais. As tabelas cabem inteiras. | `@media (min-width: 768px)` |
| **Desktop** (1200px ou mais) | O `<aside>` sobe para uma coluna lateral de 300px. Logo e slogan à esquerda, menu à direita. Destaques em 3 colunas. A página fica limitada a 1200px e centralizada. | `@media (min-width: 1200px)` |

Os destaques da home não precisaram de media query: `repeat(auto-fit, minmax(14rem, 1fr))` decide
sozinho quantas colunas cabem (1, 2 ou 3).

## Layout: Grid fora, Flexbox dentro

| Parte | Técnica | Por quê |
|---|---|---|
| Página (`body`) | Grid com `grid-template-areas` (`topo`, `conteudo`, `lateral`, `rodape`) | Cada parte tem um lugar fixo; no desktop basta trocar o mapa de áreas para o `<aside>` ir para a lateral. |
| Coluna do conteúdo | `minmax(0, 1fr)` em vez de `1fr` | Impede que uma tabela larga estique a coluna e crie rolagem lateral na página. |
| Cabeçalho | Grid com áreas `logo`, `slogan`, `menu` e uma 1ª coluna da largura do ícone (3rem) | O slogan fica na 2ª coluna, logo abaixo do nome "IA em Jogo" e alinhado com ele; no desktop o menu vai para a direita. |
| Menu, rodapé, logo | Flexbox | São itens numa linha só, com tamanho vindo do conteúdo. |
| Destaques da home | Grid com `auto-fit` + `minmax()` | Número de colunas se ajusta sozinho. |
| Grupos de rádio e checkbox | Grid (`auto 1fr`; no tablet, `auto 1fr auto 1fr`) | Cada caixinha alinhada ao seu label. |
| "A crise em números" | Container query (`@container (min-width: 32rem)`) | O bloco olha a largura do próprio `<aside>`, não da tela: largo no tablet (termo e valor lado a lado), estreito na lateral do desktop (um embaixo do outro). |

## Variáveis CSS (`:root`)

Cores: `--cor-fundo`, `--cor-superficie`, `--cor-superficie-2`, `--cor-texto`,
`--cor-texto-suave`, `--cor-primaria`, `--cor-primaria-2`, `--cor-destaque`, `--cor-link`,
`--cor-link-hover`, `--cor-borda`, `--cor-borda-campo`, `--cor-foco`, `--cor-erro`.

Espaçamentos e medidas: `--espaco-1` a `--espaco-4` (0.5rem a 2rem), `--raio`, `--largura-max`
(1200px), `--largura-lateral` (300px) e `--fonte`.

O ciano `#22d3ee` saiu do logo e marca o item atual do menu e os títulos das seções. O cabeçalho e
o rodapé usam o azul-marinho `#0b1a3a`, com os botões do menu em `#1d3b7a`. A primeira versão usava
o `#1e1b4b` do fundo do logo, um tom puxado para o roxo; o grupo trocou por um azul mais escuro na
revisão técnica.

## Convenção de classes

Nomes em português, minúsculos, sem acento e com hífen. Só criamos classe onde o seletor de
elemento não basta; o resto usa os próprios elementos semânticos (`header`, `nav`, `main`, `aside`,
`footer`, `article`, `table`, `fieldset`).

| Classe | Onde | Para quê |
|---|---|---|
| `.pular` | skip link, nas 6 páginas | Fica fora da tela até receber foco pelo Tab. |
| `.logo` | link do logo, nas 6 páginas | Alinha ícone e nome com Flexbox. |
| `.destaques` | seção "Em destaque" da home | Grade de cartões com `auto-fit`. |
| `.numeros` | lista "A crise em números" da home | Valor grande, termo como legenda. |
| `.tabela` | `<div>` em volta das tabelas de hardware e consoles | A tabela tem largura mínima de 30rem; em tela mais estreita, só ela rola para o lado. |
| `.aceite` | parágrafo do checkbox "Concordo..." | Checkbox ao lado do texto longo. |
| `.dica` | dica do campo de opinião | Texto menor, ligado ao campo pelo `aria-describedby`. |

### Mudanças no HTML

O conteúdo das páginas não mudou. Entraram só:

- o `<link>` para `css/estilo.css` no `<head>` das 6 páginas;
- as classes da tabela acima;
- a `<div class="tabela" role="region" aria-labelledby="..." tabindex="0">` em volta das duas
  tabelas, com um `id` no `<caption>` para dar nome à região. O `tabindex="0"` deixa quem usa
  teclado rolar a tabela com as setas quando ela não cabe.

## Contraste (WCAG)

Medido com a fórmula de luminância relativa da WCAG 2 (a mesma do WebAIM Contrast Checker).
Texto precisa de 4.5:1; bordas de campo e indicador de foco, de 3:1.

| Par | Contraste |
|---|---|
| Texto `#1f2937` no branco | 14.68:1 |
| Texto `#1f2937` no fundo `#f1f5f9` | 13.40:1 |
| Texto suave `#4b5563` no branco | 7.56:1 |
| Texto suave `#4b5563` no fundo `#f1f5f9` | 6.90:1 |
| Link `#4338ca` no branco | 7.90:1 |
| Link `#4338ca` na linha zebrada `#f1f5f9` | 7.21:1 |
| Títulos `#0b1a3a` no branco | 17.17:1 |
| Branco no cabeçalho `#0b1a3a` | 17.17:1 |
| Slogan `#cbd5e1` no cabeçalho | 11.56:1 |
| Branco nos botões do menu `#1d3b7a` | 10.72:1 |
| Item atual do menu: `#0b1a3a` no ciano `#22d3ee` | 9.50:1 |
| Rodapé `#e2e8f0` no `#0b1a3a` | 13.93:1 |
| Ciano `#22d3ee` (links do rodapé) no `#0b1a3a` | 9.50:1 |
| Botão: branco no `#4338ca` | 7.90:1 |
| Borda dos campos `#64748b` no branco (mínimo 3:1) | 4.76:1 |
| Foco `#ea580c` no branco (mínimo 3:1) | 3.56:1 |
| Foco `#ea580c` no cabeçalho `#0b1a3a` (mínimo 3:1) | 4.82:1 |
| Erro `#b91c1c` no branco | 6.47:1 |

## Acessibilidade no CSS

- **Foco visível** em todo elemento com `:focus-visible` (contorno laranja de 3px). Não há
  `outline: none` em nenhum lugar.
- **Skip link** escondido com `transform` (e não com `display: none`, que o tiraria também do
  teclado e do leitor de tela). Aparece no primeiro Tab.
- **Área de toque** de pelo menos 44px (`min-height: 2.75rem`) nos links do menu, campos e botão.
- **Campos com `font: inherit`**, contorno com contraste de 4.76:1 e `accent-color` nos rádios e
  checkboxes.
- **Erro só depois da interação**: `:user-invalid` (e não `:invalid`) pinta a borda de vermelho;
  a mensagem do navegador continua aparecendo, então a cor não é o único sinal.
- **Menos animação**: a transição do skip link só existe com `prefers-reduced-motion:
  no-preference`.
- **Unidades relativas** (`rem`) em fontes e espaçamentos, e `clamp()` no `<h1>`: o texto
  acompanha o zoom do navegador.

## Testes feitos

### Larguras

As 6 páginas abertas em 320, 375, 480, 768, 1024, 1280 e 1440px: **nenhuma rolagem horizontal na
página** em nenhuma largura. As tabelas cabem inteiras a partir de 768px; abaixo disso só a tabela
rola para o lado dentro da `div.tabela`, com letra e espaçamento normais.

### Teclado

- Primeiro Tab mostra o skip link no canto da tela; Enter leva ao `<main id="conteudo">`.
- O contorno laranja aparece em cada link do menu ao navegar com Tab.

### Validadores do W3C (19/11/2026)

| Validador | Resultado |
|---|---|
| HTML (validator.w3.org/nu), 6 páginas | 0 erros, 0 avisos em todas |
| CSS (jigsaw.w3.org/css-validator), `css/estilo.css` | 2 erros, ambos da container query: `container-type` e `@container`. O validador ainda não reconhece container queries, que funcionam em todos os navegadores atuais (Chrome 105+, Firefox 110+, Safari 16+) e são apresentadas no guia da Aula 16. 1 aviso: variáveis CSS não são conferidas pelo validador. |

## Para conferir antes de entregar (teste manual do grupo)

- [x] Abrir as páginas no próprio celular e conferir menu, tabelas e formulário.
- [x] No DevTools (F12, Ctrl+Shift+M), arrastar a largura devagar e ver se algo quebra entre os
      breakpoints.
- [x] Percorrer cada página só com Tab, Shift+Tab, Enter e Espaço, inclusive o formulário.
- [x] Rodar o WAVE ou o Lighthouse e anotar os alertas.

## Pendências para a Entrega 3

- Formulário: trocar o `method="post"` por `get` ou justificar (no GitHub Pages, `post` responde
  com erro 405).
- Revisar mensagens e dicas dos campos, e testar o formulário só com teclado e com leitor de tela.
- Ajustes finais de responsividade depois do teste no celular de verdade.

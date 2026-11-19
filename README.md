# IA em Jogo

> Como a inteligência artificial está mudando o preço da diversão.

Site sobre como o crescimento da inteligência artificial está encarecendo jogos, hardware e
consoles. Projeto Integrador da disciplina **Interface Web com HTML e CSS** (UNIVÁS, 2026-2),
construído em três entregas: HTML semântico, depois CSS responsivo, depois formulário e
refinamento.

**Grupo:** Gabriel Jésus, José Mateus e Miguel Maciel

## Sobre o tema

O site explica uma corrente de causa e efeito, com números e fontes em cada página:

1. **A IA cresceu muito rápido.** O ChatGPT foi de 100 milhões para 800 milhões de usuários
   semanais em dois anos.
2. **Os data centers vieram junto.** O investimento mundial em data centers deve passar de
   1 trilhão de dólares em 2026.
3. **A memória ficou escassa.** Os data centers de IA devem ficar com cerca de 70% dos chips de
   memória produzidos em 2026.
4. **A conta chegou para quem joga.** A memória RAM subiu entre 80% e 90% em um único trimestre, e
   o PlayStation 5 passou a custar R$ 5.099,90 no Brasil.

## Regras técnicas adotadas

- HTML5 e CSS próprio: sem JavaScript e sem frameworks (nada de Bootstrap, Tailwind ou Bulma).
- CSS num arquivo externo, `css/estilo.css`, com cores e espaçamentos em variáveis no `:root`.
- Mobile first: Grid para a página, Flexbox dentro de cada parte e 3 larguras (celular, tablet a
  partir de 768px, desktop a partir de 1200px).
- `<header>`, `<nav>`, `<main>` e `<footer>` em todas as páginas; `<aside>` para conteúdo
  complementar.
- Um único `<h1>` por página, sem pular nível de título.
- Skip link "Pular para o conteúdo principal" como primeiro elemento da página.
- `aria-current="page"` no item do menu da página atual.
- Tabelas com `<caption>` e `<th scope>`; gráficos em `<figure>` com `alt` que descreve os números.
- Formulário com `<label>` em todos os campos, `<fieldset>`/`<legend>` nos grupos de opções e
  validação nativa do HTML5.
- Foco visível em todo elemento (`:focus-visible`), skip link que aparece no primeiro Tab e
  contraste mínimo de 4.5:1 em todo texto.
- Todo número do site tem a fonte listada no fim da página onde aparece.
- Nomes de arquivos em minúsculas, sem acento e sem espaço; classes CSS em português, minúsculas e
  com hífen (`.pular`, `.destaques`, `.tabela`).

As justificativas de cada decisão estão em [docs/entrega-1.md](docs/entrega-1.md) (estrutura) e
[docs/entrega-2.md](docs/entrega-2.md) (estilo e responsividade).

## Páginas

| Arquivo | Conteúdo |
|---|---|
| `index.html` | Apresentação do tema, destaques, perguntas frequentes e resumo em números |
| `ia.html` | Crescimento da IA, investimento em data centers e por que isso pressiona a memória |
| `hardware.html` | Alta da memória RAM, das placas de vídeo e de outros aparelhos |
| `consoles-jogos.html` | Reajustes de PlayStation 5, Switch 2 e Xbox; preço dos jogos |
| `participe.html` | Formulário de participação com validação nativa do HTML5 |
| `obrigado.html` | Confirmação de envio do formulário |

## Estrutura do projeto

```text
ia-em-jogo/
├── index.html
├── ia.html
├── hardware.html
├── consoles-jogos.html
├── participe.html
├── obrigado.html
├── css/
│   └── estilo.css                    estilo único das 6 páginas (Entrega 2)
├── img/
│   ├── logo.svg
│   ├── grafico-chatgpt.svg
│   └── grafico-ps5-brasil.svg
├── docs/
│   ├── entrega-1.md                  decisões de estrutura, checklist e validação
│   ├── entrega-2.md                  breakpoints, layout, variáveis, contraste e testes
│   ├── registro-uso-ia-entrega-1.md
│   └── registro-uso-ia-entrega-2.md
├── .gitignore
└── README.md
```

## Planejamento por entregas

### Entrega 1 - Esqueleto semântico

- [x] Criar as 6 páginas em HTML puro.
- [x] Montar cabeçalho, menu, conteúdo principal, aside e rodapé em todas as páginas.
- [x] Organizar os títulos com um único `<h1>` por página.
- [x] Marcar dados de preços em tabelas acessíveis.
- [x] Incluir os gráficos com texto alternativo completo.
- [x] Criar o formulário de participação com validação nativa.
- [x] Listar as fontes de todos os números.
- [x] Validar as 6 páginas no W3C.

#### Validação no W3C

Validador Nu do W3C, em 22/10/2026: **0 erros e 0 avisos** em `index.html`, `ia.html`,
`hardware.html`, `consoles-jogos.html`, `participe.html` e `obrigado.html`. Também foi conferido
que não há link interno quebrado, âncora sem destino, `id` repetido, imagem sem `alt` ou campo
sem `<label>`.

#### Teste manual do grupo

- [ ] Percorrer cada página só com o teclado (Tab, Shift+Tab, Enter e Espaço).
- [ ] Enviar o formulário vazio e com e-mail inválido e conferir as mensagens de erro.
- [ ] Rodar o WAVE ou o Lighthouse e anotar os alertas.

### Entrega 2 - Estilo e responsividade

- [x] Criar `css/estilo.css` e ligar nas 6 páginas.
- [x] Decidir e justificar mobile-first ou desktop-first (mobile first).
- [x] Definir cores e espaçamentos em variáveis CSS no `:root`.
- [x] Montar o layout da página com Grid (`grid-template-areas`) e as partes com Flexbox.
- [x] Fazer funcionar nos 3 breakpoints: celular, tablet (768px) e desktop (1200px).
- [x] Esconder o skip link até ele receber foco.
- [x] Mostrar o foco do teclado com `:focus-visible` em todo elemento.
- [x] Conferir o contraste de todas as cores (texto 4.5:1, bordas e foco 3:1).
- [x] Testar de 320 a 1440px sem rolagem horizontal na página.

#### Validação no W3C

Em 19/11/2026: **0 erros e 0 avisos** no HTML das 6 páginas. No CSS, o validador só acusa a
container query (`container-type` e `@container`), que ele ainda não reconhece; detalhes em
[docs/entrega-2.md](docs/entrega-2.md).

#### Teste manual do grupo

- [ ] Abrir o site no próprio celular e conferir menu, tabelas e formulário.
- [ ] Arrastar a largura no DevTools e ver se algo quebra entre os breakpoints.

### Entrega 3 - Formulário e refinamento

- [ ] Trocar o `method="post"` do formulário por `get` ou justificar a escolha (no GitHub Pages,
      `post` responde com erro 405).
- [ ] Conferir o contraste de 4.5:1 das cores, inclusive nos gráficos SVG.
- [ ] Fazer os ajustes finais.

## Como abrir

Não precisa instalar nada: abra o `index.html` no navegador. Para testar como site, na pasta do
projeto:

```powershell
python -m http.server 8000
```

e acesse `http://localhost:8000`.

## Versionamento

O projeto está publicado em [github.com/JServoli/ia-em-jogo](https://github.com/JServoli/ia-em-jogo).
Cada entrega corresponde a uma tag ou branch com o nome dela:

| Entrega | Onde | Situação |
|---|---|---|
| 1 - Esqueleto semântico | tag [`entrega-1`](https://github.com/JServoli/ia-em-jogo/releases/tag/entrega-1) | Pronta |
| 2 - Estilo e responsividade | branch [`entrega-2`](https://github.com/JServoli/ia-em-jogo/tree/entrega-2) | Pronta |
| 3 - Formulário e refinamento | `entrega-3` | A fazer |

Fluxo da Entrega 2, numa branch com o nome pedido pelo professor:

```powershell
git switch -c entrega-2
git add .
git commit -m "Entrega 2: estilo e responsividade"
git push -u origin entrega-2
```

Cada integrante deve fazer commits com a própria conta, porque o histórico conta na avaliação.

## Uso de IA

O grupo usou o Claude (Anthropic) na pesquisa das fontes, na estrutura HTML, nos textos, nos
gráficos, no CSS, nos testes, na validação e na documentação. A revisão técnica do código gerado é
feita pelo grupo. Os prompts usados, na íntegra, e a revisão de cada entrega estão em:

- [docs/registro-uso-ia-entrega-1.md](docs/registro-uso-ia-entrega-1.md)
- [docs/registro-uso-ia-entrega-2.md](docs/registro-uso-ia-entrega-2.md)

## Tecnologias

HTML5 e CSS3 próprio (Grid, Flexbox, variáveis, media queries e container queries). Sem frameworks
e sem JavaScript.

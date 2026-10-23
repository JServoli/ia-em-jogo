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

- HTML5 puro na Entrega 1: sem CSS, sem JavaScript e sem frameworks.
- `<header>`, `<nav>`, `<main>` e `<footer>` em todas as páginas; `<aside>` para conteúdo
  complementar.
- Um único `<h1>` por página, sem pular nível de título.
- Skip link "Pular para o conteúdo principal" como primeiro elemento da página.
- `aria-current="page"` no item do menu da página atual.
- Tabelas com `<caption>` e `<th scope>`; gráficos em `<figure>` com `alt` que descreve os números.
- Formulário com `<label>` em todos os campos, `<fieldset>`/`<legend>` nos grupos de opções e
  validação nativa do HTML5.
- Todo número do site tem a fonte listada no fim da página onde aparece.
- Nomes de arquivos em minúsculas, sem acento e sem espaço.

As justificativas de cada decisão estão em [docs/entrega-1.md](docs/entrega-1.md).

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
├── img/
│   ├── logo.svg
│   ├── grafico-chatgpt.svg
│   └── grafico-ps5-brasil.svg
├── docs/
│   ├── entrega-1.md                  decisões de estrutura, checklist e validação
│   └── registro-uso-ia-entrega-1.md
├── .gitignore
└── README.md
```

O `css/` entra na Entrega 2.

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

- [ ] Criar `css/estilo.css` e ligar nas 6 páginas.
- [ ] Decidir e justificar mobile-first ou desktop-first.
- [ ] Montar o layout com Flexbox/Grid, variáveis CSS e 3 breakpoints.
- [ ] Esconder o skip link até ele receber foco.

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
Cada entrega fica congelada numa tag, e o trabalho continua no `main`:

| Entrega | Tag | Situação |
|---|---|---|
| 1 - Esqueleto semântico | [`entrega-1`](https://github.com/JServoli/ia-em-jogo/releases/tag/entrega-1) | Pronta |
| 2 - Estilo e responsividade | `entrega-2` | A fazer |
| 3 - Formulário e refinamento | `entrega-3` | A fazer |

Fluxo para as próximas entregas:

```powershell
git add .
git commit -m "Entrega 2: estilo e responsividade"
git push
git tag entrega-2
git push origin entrega-2
```

Cada integrante deve fazer commits com a própria conta, porque o histórico conta na avaliação.

## Uso de IA

O grupo usou o Claude (Anthropic) na pesquisa das fontes, na estrutura HTML, nos textos, nos
gráficos, na validação e na documentação. A revisão técnica do código gerado é feita pelo grupo.
Os prompts usados, na íntegra, e a revisão estão em
[docs/registro-uso-ia-entrega-1.md](docs/registro-uso-ia-entrega-1.md).

## Tecnologias

HTML5 na Entrega 1. CSS próprio a partir da Entrega 2. Sem frameworks e sem JavaScript.

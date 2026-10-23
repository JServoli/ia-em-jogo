# Entrega 1 — Esqueleto semântico

Seis páginas em HTML puro, sem CSS: `index`, `ia`, `hardware`, `consoles-jogos`, `participe` e `obrigado`. As cinco primeiras estão no menu; `obrigado` é a confirmação do formulário.

## Estrutura comum a todas as páginas

```
<body>
  a  "Pular para o conteúdo principal"  → #conteudo
  header#topo
    a (logo + nome do site) → index.html
    p (slogan)
    nav "Menu principal" → ul > li > a   (item da página atual com aria-current="page")
  main#conteudo
    h1 (único)
    section (cada uma com h2 e aria-labelledby)
  aside   (conteúdo complementar)
  footer  (créditos + "Voltar ao topo")
</body>
```

## Decisões e justificativas

| Decisão | Por quê |
|---|---|
| Skip link como primeiro elemento do `<body>` | Quem navega por teclado pula o cabeçalho e o menu e vai direto ao `<main id="conteudo">`. |
| Logo com `alt=""` dentro do link, ao lado do texto "IA em Jogo" | O texto já dá o nome acessível do link; um alt repetiria "IA em Jogo" duas vezes no leitor de tela. |
| Menu como `<nav aria-label="Menu principal">` com `<ul>` | Menu é uma lista de links; o `aria-label` diferencia esse `<nav>` de outros que vierem no futuro. |
| `aria-current="page"` no item da página atual | Informa ao leitor de tela em que página o usuário está. `obrigado.html` não marca nenhum item porque não está no menu. |
| Um único `<h1>` por página e nenhum pulo de nível | Os títulos formam o sumário da página para quem navega por títulos. |
| `<section aria-labelledby="...">` | Cada bloco temático tem título próprio; o `aria-labelledby` transforma a seção em região nomeada (landmark). |
| Destaques da home e cada console em `<article>` | São conteúdos independentes: fariam sentido sozinhos fora da página. |
| `<aside>` fora do `<main>` | Glossário, curiosidades e resumo em números complementam a página, mas ela continua completa sem eles. |
| Tabelas com `<caption>` e `<th scope="col/row">` | Os preços e a alta da memória são dados tabulares; o leitor de tela relaciona cada célula ao seu cabeçalho. |
| Gráficos em `<figure>` + `<figcaption>`, com `alt` descrevendo os números | O gráfico é imagem informativa: o alt reproduz a informação que ele mostra. |
| `<dl>` para "termo: valor" (glossário e números da home) | É o elemento semântico para pares termo/descrição. |
| `<time datetime="...">` nas datas | Data legível por pessoas e por máquinas. |
| `<details>`/`<summary>` nas perguntas frequentes | Conteúdo expansível nativo, que já funciona com teclado sem JavaScript. |
| Formulário com `<label for>` em todos os campos, `<fieldset>`/`<legend>` nos grupos de opções e `aria-describedby` na dica do campo de opinião | Todo campo tem nome acessível; o grupo de rádios e de checkboxes é anunciado com a pergunta. |
| Validação nativa (`required`, `type="email"`, `minlength`, `maxlength`) | Requisito do projeto: validar sem JavaScript. |
| Fontes em `<ol>` no fim de cada página; na tabela de hardware, a coluna "Fonte" leva por âncora (`#fonte-1`...) ao item da lista | Todo número do site pode ser conferido. |
| Links com texto que faz sentido sozinho (sem "clique aqui") | Leitores de tela listam os links fora do contexto. |
| Nomes de arquivos em minúsculas, sem acento e sem espaço; imagens em `img/` | Boa prática de organização da Revisão de HTML. |

## Checklist de acessibilidade (Revisão de HTML, seção 11)

- [x] `<!DOCTYPE html>` e `<html lang="pt-BR">` em todas as páginas
- [x] `<head>` com `charset`, `viewport`, `description` e `<title>` descritivo
- [x] `<header>`, `<nav>`, `<main>` (um só) e `<footer>` em todas as páginas
- [x] Cada `<section>` tem título; conteúdos independentes em `<article>`
- [x] Um único `<h1>` por página, sem pulo de nível
- [x] Todas as imagens com `alt` adequado (informativo nos gráficos, vazio no logo ao lado do texto)
- [x] Todo campo de formulário com `<label>` associado por `for`/`id`
- [x] Links levam a lugares; o único botão envia o formulário. Nenhum `<div>` ou `<span>` clicável
- [x] Nenhum link com texto "clique aqui" ou "saiba mais" sozinho
- [x] Ordem do Tab segue a ordem visual do código (skip link → logo → menu → conteúdo → aside → rodapé)
- [x] ARIA só onde o HTML nativo não resolve (`aria-label` no nav, `aria-labelledby` nas seções, `aria-current`, `aria-describedby`), sem `role` redundante
- [x] Nenhum `id` repetido; nenhum `<br>`, `<table>` de layout ou tag obsoleta
- [x] Código indentado e validado no W3C sem erros

## Validação no W3C

Validador Nu do W3C (validator.w3.org/nu), em 22/10/2026:

| Página | Erros | Avisos |
|---|---|---|
| index.html | 0 | 0 |
| ia.html | 0 | 0 |
| hardware.html | 0 | 0 |
| consoles-jogos.html | 0 | 0 |
| participe.html | 0 | 0 |
| obrigado.html | 0 | 0 |

Também foi conferido por script: nenhum link interno quebrado, nenhuma âncora apontando para id inexistente, nenhum id repetido, todas as imagens existem e têm `alt`, e todo campo de formulário tem `<label>`.

## Para conferir antes de entregar (teste manual do grupo)

- [ ] Percorrer cada página só com Tab, Shift+Tab, Enter e Espaço: o skip link aparece primeiro e leva ao conteúdo?
- [ ] Enviar o formulário vazio e com e-mail inválido: o navegador mostra as mensagens de erro?
- [ ] Rodar o WAVE (wave.webaim.org) ou o Lighthouse e anotar os alertas.
- [ ] Opcional: navegar com o NVDA ou o Narrador (Ctrl+Win+Enter).

## Pendências para as próximas entregas

- Entrega 2: criar `css/estilo.css` e ligar com `<link rel="stylesheet">` no `<head>` das 6 páginas; decidir e justificar mobile-first ou desktop-first.
- Entrega 2: esconder o skip link até receber foco (classe tipo `visually-hidden`/`skip-link`).
- Entrega 3: o formulário usa `method="post"` para uma página estática. No GitHub Pages isso responde com erro 405; trocar para `method="get"` ou explicar a escolha na defesa.
- Entrega 3: conferir contraste de 4.5:1 das cores escolhidas (inclusive nos gráficos SVG).

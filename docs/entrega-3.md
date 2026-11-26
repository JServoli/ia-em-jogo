# Entrega 3 — Formulário, acessibilidade e publicação

Trabalho completo publicado no GitHub Pages:
**[jservoli.github.io/ia-em-jogo](https://jservoli.github.io/ia-em-jogo/)**

Esta entrega fecha o projeto: formulário funcionando no site publicado, revisão de acessibilidade
(com contraste também nos gráficos) e os ajustes finais de responsividade. O código está na branch
`entrega-3`, que também foi levada para o `main`, a branch que o GitHub Pages publica.

## 1. Formulário funcional (`participe.html`)

### `method="get"` no lugar de `post`

O site é estático: não tem servidor para receber os dados. O GitHub Pages responde a um envio
`POST` com **erro 405** (conferido em 26/11/2026), então, com `post`, quem enviasse o formulário no
site publicado veria uma página de erro. Com `get`, o navegador abre `obrigado.html` normalmente e
coloca as respostas no endereço:

```
obrigado.html?nome=Joana+Exemplo&email=joana%40exemplo.com&adiou=sim&itens=placa-de-video&plataforma=pc&opiniao=&concordo=on
```

Como as respostas ficam visíveis no endereço e no histórico do navegador, o quadro "Como usamos
suas respostas" agora avisa isso e sugere usar dados de exemplo. Num site com servidor de verdade,
o certo seria voltar para `post`.

### Validação só com HTML5

| Campo | Validação nativa | O que o navegador faz |
|---|---|---|
| Nome | `required`, `minlength="2"`, `maxlength="80"`, `pattern="[^0-9]+"` + `title` | Bloqueia vazio, nome curto e nome com número; o `title` entra na mensagem de erro |
| E-mail | `required`, `type="email"`, `autocomplete="email"` | Bloqueia vazio e formato inválido (ex.: `joao@`); no celular abre o teclado com `@` |
| Adiou a compra? | `required` em um dos rádios do grupo | Obriga a escolher Sim ou Não |
| O que deixou de comprar | opcional | — |
| Onde mais joga | `required` no `<select>` com a 1ª opção vazia | Obriga a escolher uma plataforma |
| Opinião | opcional, `minlength="10"`, `maxlength="500"` | Se escrever, exige de 10 a 500 caracteres |
| Concordo | `required` no checkbox | Obriga o aceite |

Novidades desta entrega:

- **`pattern` no nome** (sem números) e **dicas ligadas aos campos** com `aria-describedby`
  (`dica-nome`, `dica-email`), no mesmo modelo do `dica-email` do guia da Aula 16. O leitor de tela
  lê a dica junto com o nome do campo.
- **`:has(:user-invalid)`** (Aula 17): além da borda, o label do campo inválido e a legenda do grupo
  de rádios ficam vermelhos (`#b91c1c`, 6.47:1 no branco). Só depois de a pessoa interagir ou
  tentar enviar, nunca ao carregar a página. A mensagem do navegador continua aparecendo, então a
  cor não é o único sinal.

### Testes do envio (26/11/2026)

| Teste | Resultado |
|---|---|
| Enviar vazio | Bloqueado; o navegador mostra "Preencha este campo." e leva o foco ao Nome. Ficam inválidos: nome, e-mail, o grupo Sim/Não, plataforma e o aceite. |
| Nome "Jo4o" | Bloqueado pelo `pattern` |
| E-mail "joao@" | Bloqueado: "Insira uma parte depois de "@"." |
| Tudo preenchido corretamente | Abre `obrigado.html` pelo `GET`, sem erro |

## 2. Revisão de acessibilidade

Feita com um script próprio rodado no navegador nas 6 páginas, em 7 larguras (320, 375, 480, 768,
1024, 1280 e 1440px). Ele confere o contraste de **todo** elemento com texto contra o fundo real, a
ordem dos títulos, `alt` das imagens, `<label>` dos campos, `id` repetido, referências `aria-*`
quebradas, links sem texto e o tamanho dos alvos de toque.

| O que foi encontrado | Correção |
|---|---|
| Rádios e checkboxes com 20×20px, abaixo do alvo mínimo de 24×24px da WCAG 2.2 (critério 2.5.8) | Passaram para `1.5rem` (24px) |
| No gráfico de preços do PS5 (`img/grafico-ps5-brasil.svg`), as barras "Antes" em `#9ca3af` tinham só **2.54:1** contra o branco; elementos gráficos precisam de 3:1 (critério 1.4.11) | Barras e quadrado da legenda trocados para `#6b7280`: **4.83:1** |

Depois das correções, o script não acusou nenhum problema: todo texto com 4.5:1 ou mais (texto
grande, 3:1), todos os alvos com 24px ou mais, nenhuma rolagem lateral e nenhuma referência `aria-*`
quebrada.

O texto dos dois gráficos também foi conferido: títulos e rótulos em `#111827`, `#374151` e
`#4b5563`, todos acima de 7:1 no fundo branco do SVG.

### Teclado

Skip link no primeiro Tab, foco visível em todo elemento e, no formulário, o foco vai para o
primeiro campo com problema ao tentar enviar.

## 3. Ajustes finais de responsividade

- **`text-wrap: balance`** nos títulos (Aula 17): o navegador equilibra as linhas e evita uma palavra
  sozinha na última linha. Em navegador sem suporte, o título só quebra do jeito normal.
- Conferido de novo de 320 a 1440px: nenhuma página rola para o lado; as tabelas cabem inteiras a
  partir de 768px e, abaixo disso, rolam só dentro da `div.tabela`.

## 4. Publicação no GitHub Pages

- Settings → Pages → *Deploy from a branch* → `main` / `(root)`, o mesmo caminho da seção 15 do guia
  da Aula 17.
- Endereço: `https://jservoli.github.io/ia-em-jogo/`. O arquivo principal já se chama `index.html`.
- Todos os nomes de arquivo estão em minúsculas, então não há problema com o servidor diferenciar
  `Logo.svg` de `logo.svg`.
- O site não publica dados pessoais reais: o formulário não grava nada.

## 5. Validadores do W3C (26/11/2026)

| Validador | Resultado |
|---|---|
| HTML (validator.w3.org/nu), 6 páginas | 0 erros, 0 avisos em todas |
| CSS (jigsaw.w3.org/css-validator) | Os mesmos 2 erros da Entrega 2, ambos da container query (`container-type` e `@container`), que o validador ainda não reconhece. `:has()` e `text-wrap` passaram. 1 aviso: variáveis CSS não são conferidas. |

## Para conferir antes da defesa (teste manual do grupo)

- [ ] Abrir o site publicado no celular e enviar o formulário.
- [ ] Navegar pelo site publicado só com o teclado.
- [ ] Rodar o Lighthouse (aba Lighthouse do DevTools) no site publicado e anotar a nota de
      Acessibilidade.
- [ ] Opcional: navegar com o NVDA ou o Narrador (Ctrl+Win+Enter).

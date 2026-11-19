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
| Revisão técnica (seção 3) | **Não: feita pelo grupo** |

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
> Acrescentar aqui, na íntegra, qualquer outro prompt que o grupo usar até a entrega.

## 3. Revisão técnica (mínimo de 3 alterações)

> **Esta seção precisa ser preenchida pelo grupo.** O professor avalia a capacidade de auditar o
> código da IA, e as alterações têm de ser feitas e justificadas por vocês. Sem ela, a entrega perde
> pontos.

| # | O que a IA gerou | O que foi alterado | Por que foi alterado |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

### Ajustes que a própria IA fez durante os testes

Não contam como revisão do grupo, mas mostram o que o teste encontrou:

- A tabela de preços do PS5 passava 10px da tela em 375px. A IA diminuiu o espaço interno dos
  cartões e das células e a fonte da tabela no celular (13px), devolvendo os valores maiores a
  partir do tablet.
- Em 320px as duas tabelas ainda passavam da tela. A IA envolveu cada tabela numa
  `div.tabela` com `overflow-x: auto`, `role="region"` e `tabindex="0"`, para só a tabela rolar.
- A IA tinha colocado `position: sticky` no `<aside>` do desktop e tirou: num glossário mais alto
  que a tela, o fim dele ficaria inalcançável.

### Pontos para o grupo revisar

Não são alterações prontas, e sim lugares onde vale olhar com atenção:

- **Fonte da tabela no celular:** 13px é legível? Ou é melhor deixar a tabela rolar e manter a
  fonte maior?
- **Skip link:** o guia da Aula 15 coloca o skip link numa área `pular` do Grid; aqui ele usa
  `position: absolute` e `transform`. Saber explicar a diferença na defesa.
- **Container query:** é um recurso novo e o validador de CSS do W3C ainda acusa erro. Vale manter
  ou trocar por uma media query comum?
- **Cores:** a paleta saiu do logo. O grupo concorda? Se mudar alguma cor, refazer a conta de
  contraste.
- **Valores de "A crise em números":** ficaram grandes e em negrito. Na lateral estreita do
  desktop, quebram em várias linhas; conferir se está bom.
- **Breakpoints:** testar arrastando a largura no DevTools e ver se 768px e 1200px são mesmo onde
  o conteúdo pede mudança.
- **Teste no celular de verdade:** a IA não usa um celular; o grupo precisa abrir o site no próprio
  aparelho.

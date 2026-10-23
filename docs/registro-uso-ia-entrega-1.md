# Registro de Uso de IA — Entrega 1

**Ferramenta:** Claude (Anthropic)
**Data:** 22/10/2026
**Grupo:** Gabriel Jésus, José Mateus e Miguel Maciel

## 1. Mapeamento de uso

| Parte | Apoio de IA |
|---|---|
| Pesquisa dos dados e das fontes (memória RAM, GPUs, consoles, jogos, crescimento da IA) | Sim: a IA buscou as reportagens e montou a lista de fontes |
| Estrutura HTML das 6 páginas (`index`, `ia`, `hardware`, `consoles-jogos`, `participe`, `obrigado`) | Sim: gerada pela IA |
| Textos das páginas | Sim: escritos pela IA a partir das fontes |
| Imagens (`img/logo.svg`, `img/grafico-chatgpt.svg`, `img/grafico-ps5-brasil.svg`) | Sim: geradas pela IA a partir dos números das fontes |
| Validação no W3C e conferência de links, âncoras e títulos | Sim: executada pela IA |
| README e `docs/entrega-1.md` | Sim: escritos pela IA |
| Revisão técnica (seção 3) | **Não: feita pelo grupo** |

Como contexto, a IA tinha acesso aos materiais da disciplina (enunciado do Projeto Integrador, Revisão de HTML, slides de acessibilidade e o exemplo da SATEC 2026).

## 2. Prompts utilizados (na íntegra)

**Prompt 1**

```
No trabalho do meu grupo:

* Grabriel Jésus
* José Mateus
* Miguel Maciel


A base do tema vai ser: O crescimento da ia no mundo e seu afeto nos preços dos jogos, hardwares e consoles
```

**Prompt 2**

```
pode fazer a primeira entrega, ja fiz a pasta separada para esse trabalho "Trabalho 1 - projeto integrador"
```

> Acrescentar aqui, na íntegra, qualquer outro prompt que o grupo usar até a entrega.

## 3. Revisão técnica (mínimo de 3 alterações)

> **Esta seção precisa ser preenchida pelo grupo.** O professor avalia a capacidade de auditar o código da IA, e as alterações têm de ser feitas e justificadas por vocês. Sem ela, a entrega perde pontos.

| # | O que a IA gerou | O que foi alterado | Por que foi alterado |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

### Pontos para o grupo revisar

Não são alterações prontas, e sim lugares onde vale olhar com atenção:

- **Fontes e números:** abrir cada link da lista de fontes e conferir se o número citado na página bate com a reportagem.
- **Textos:** os textos foram escritos pela IA; reescrever com as palavras do grupo o que não soar natural ou que vocês não saibam explicar na defesa.
- **`alt` dos gráficos:** os textos alternativos repetem todos os números. Está bom, ou seria melhor um alt curto e deixar os números só na tabela?
- **Formulário:** `method="post"` para uma página estática. Funciona abrindo o arquivo no computador, mas não no GitHub Pages.
- **`obrigado.html`:** faz sentido ter essa página, ou o formulário deveria apontar para outro lugar?
- **Ordem do Tab:** testar cada página só com o teclado e ver se algo fica fora de ordem.
- **Estrutura:** confirmar se cada `<article>`, `<section>` e `<aside>` foi usado pelo motivo certo, usando as perguntas da seção 4.2 da Revisão de HTML.

# Registro de Uso de IA — Entrega 3

**Ferramenta:** Claude (Anthropic)
**Data:** 26/11/2026
**Grupo:** Gabriel Jésus, José Mateus e Miguel Maciel

## 1. Mapeamento de uso

| Parte | Apoio de IA |
|---|---|
| Formulário: `method="get"`, `pattern` e `title` no nome, dicas com `aria-describedby`, aviso sobre o GET no quadro de privacidade | Sim: feito pela IA |
| CSS: `:has(:user-invalid)`, rádios e checkboxes de 24px, `text-wrap: balance` | Sim: escrito pela IA |
| Cor das barras do gráfico do PS5 (`img/grafico-ps5-brasil.svg`) | Sim: trocada pela IA |
| Revisão de acessibilidade (script de contraste, títulos, labels, ids, ARIA e alvos de toque), testes do formulário e validação no W3C | Sim: executados pela IA |
| Publicação no GitHub Pages | Sim: configurada pela IA |
| `docs/entrega-3.md` e atualização do README | Sim: escritos pela IA |
| Revisão técnica (seção 3) | **A preencher pelo grupo** |

Como contexto, a IA leu o enunciado do Projeto Integrador, o guia de revisão (Aula 18) e o guia de
CSS moderno (Aula 17), além dos guias das Aulas 15 e 16 usados na Entrega 2.

## 2. Prompts utilizados (na íntegra)

**Prompt 1**

Enviado junto com um print da tarefa "Entrega 3" (trabalho completo publicado via GitHub Pages;
enviar o link do trabalho publicado).

```
leia [pasta da disciplina]\Html & Css e faça a entrega 3
```

> O caminho da pasta no computador foi omitido; o resto está como foi escrito.
> Acrescentar aqui, na íntegra, qualquer outro prompt que o grupo usar até a entrega.

## 3. Revisão técnica (mínimo de 3 alterações)

> **Esta seção precisa ser preenchida pelo grupo**, com pelo menos 3 alterações feitas por vocês
> no código desta entrega (o que a IA gerou / o que foi alterado / por que foi alterado).

| # | O que a IA gerou | O que foi alterado | Por que foi alterado |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

### Pontos para o grupo revisar

Não são alterações prontas, e sim lugares onde vale olhar com atenção:

- **`method="get"`:** os dados aparecem no endereço da página de confirmação. Vocês concordam com a
  troca, ou preferem manter `post` e justificar na defesa que o formulário só funciona localmente?
- **`pattern="[^0-9]+"` no nome:** aceita qualquer coisa que não seja número, inclusive símbolos.
  Vale restringir mais? E nomes com número (raros) ficariam bloqueados.
- **Mensagem do `pattern`:** a mensagem padrão do navegador é genérica; o `title` complementa. Testem
  em mais de um navegador.
- **Logo:** o ícone (`img/logo.svg`) ainda tem fundo `#1e1b4b`, da paleta antiga; no cabeçalho
  azul-marinho aparece como um quadrado levemente arroxeado.
- **Gráfico do PS5:** com as barras "Antes" mais escuras, as duas cores do gráfico ficaram mais
  próximas. A legenda e os valores escritos acima das barras ainda distinguem bem?
- **Lighthouse:** rodar no site publicado e comparar com a revisão feita pela IA.

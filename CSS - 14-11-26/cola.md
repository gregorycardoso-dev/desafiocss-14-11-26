# Cola de layout CSS

No VS Code, abra com **Ctrl+Shift+V** para ver formatado.

---

## As 4 perguntas

Antes de digitar qualquer coisa:

1. **Quem é o pai?** O layout se escreve na caixa que envolve as coisas, não nas coisas.
2. **Linha, coluna ou grade?** Uma direção só é Flexbox. Linhas e colunas alinhadas é Grid.
3. **Como distribuo o espaço?** O que fica junto, o que se afasta, o que cresce.
4. **E quando a tela muda?** O que acontece no celular.

---

## Flexbox

```
            eixo principal  →   justify-content
          ┌────────────────────────────────────────┐
  eixo    │  [item]        [item]         [item]   │  ← display: flex no PAI
 cruzado  └────────────────────────────────────────┘
    ↓
align-items
```

### No pai

| Propriedade | O que faz | Valores mais usados |
|---|---|---|
| `display: flex` | Liga o Flexbox. Os filhos diretos viram itens. | |
| `flex-direction` | Direção da fila | `row` (padrão), `column` |
| `justify-content` | Distribui no eixo principal | `flex-start`, `center`, `flex-end`, `space-between` |
| `align-items` | Alinha no eixo cruzado | `stretch` (padrão), `center`, `flex-start`, `flex-end` |
| `gap` | Espaço entre os itens | `1rem` |
| `flex-wrap` | Deixa quebrar para a linha de baixo | `nowrap` (padrão), `wrap` |

Com `flex-direction: column` os eixos giram: `justify-content` passa a ser vertical e `align-items`, horizontal.

### No item

| Propriedade | O que faz |
|---|---|
| `flex: 1` | Cresce para ocupar o espaço que sobra. Vários itens com `flex: 1` dividem por igual. |
| `flex: 1 1 220px` | Tamanho ideal de 220px, pode crescer e pode encolher. |
| `margin-top: auto` | Em uma coluna, empurra o item para o fundo. |

---

## Grid

| Propriedade | Onde | O que faz |
|---|---|---|
| `display: grid` | pai | Liga o Grid |
| `grid-template-columns: 1fr 1fr 1fr` | pai | Três colunas iguais |
| `grid-template-columns: repeat(3, 1fr)` | pai | O mesmo, escrito curto |
| `grid-template-columns: 2fr 1fr` | pai | A primeira com o dobro da segunda |
| `gap` | pai | Espaço entre as células |
| `grid-column: span 2` | item | O item ocupa duas colunas |

`fr` é uma fração do espaço que sobra.

**Qual usar?** Itens em fila, centralizar, empilhar: Flexbox. Colunas alinhadas, cards, galeria: Grid. Os dois juntos: Grid por fora, Flexbox por dentro.

---

## Position

| Valor | O que faz |
|---|---|
| `static` | O padrão. Segue o fluxo da página. |
| `relative` | Continua no fluxo. Vira ponto de referência para um filho `absolute`. |
| `absolute` | Sai do fluxo. Usa `top`, `right`, `bottom`, `left` em relação ao ancestral mais próximo com `position`. |
| `fixed` | Preso à janela, mesmo rolando a página. |
| `sticky` | Segue o fluxo até encostar na borda, e então gruda. Precisa de `top`. |

`z-index` decide quem fica na frente. Número maior, mais na frente. Só vale em elemento com `position`.

---

## Responsividade

```css
/* Fora do @media: o celular */
.caixa {
  display: flex;
  flex-direction: column;
}

/* Dentro: só o que muda quando sobra espaço */
@media (min-width: 768px) {
  .caixa {
    flex-direction: row;
  }
}
```

- Os blocos `@media` ficam no **fim** do arquivo.
- Dentro deles, só a diferença. Não repita a regra inteira.
- Para testar: DevTools (F12) e **Ctrl+Shift+M**.
- O HTML precisa ter `<meta name="viewport" content="width=device-width, initial-scale=1.0">`.

---

## Unidades

| Unidade | Relativa a |
|---|---|
| `rem` | tamanho da fonte da página (16px por padrão) |
| `em` | tamanho da fonte do próprio elemento |
| `%` | tamanho do pai |
| `vh` / `vw` | 1% da altura / da largura da janela |
| `fr` | fração do espaço livre (só no Grid) |

---

## Variáveis

```css
:root {
  --cor-primaria: #6f4e37;
}

.botao {
  background-color: var(--cor-primaria);
}
```

---

## Receitas

**Centralizar uma coisa dentro de uma caixa**

```css
.pai {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

**Um em cada ponta, alinhados pelo meio**

```css
.pai {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

**Empilhar com espaço igual**

```css
.pai {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
```

**Dividir a largura em partes iguais**

```css
.filho {
  flex: 1;
}
```

**Três colunas de cards**

```css
.pai {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}
```

**Etiqueta no canto de um cartão**

```css
.cartao {
  position: relative;
}

.etiqueta {
  position: absolute;
  top: 0.75rem;
  right: 0.75rem;
}
```

**Caixa com a altura da janela**

```css
.pai {
  min-height: 100vh;
}
```

---

## Não funcionou?

Confira nesta ordem, com o DevTools aberto.

1. **O `display` está no pai certo?** Na aba Elements, o pai mostra uma etiqueta `flex` ou `grid`. Clique nela para ver o desenho.
2. **Os itens são filhos diretos desse pai?** Flex e Grid não enxergam netos.
3. **Estou no eixo certo?** Em coluna, `justify-content` é vertical.
4. **Tem espaço sobrando?** Um pai do tamanho do conteúdo não tem o que distribuir. Confira a largura e a altura dele.
5. **A propriedade está riscada no DevTools?** É erro de digitação ou outra regra mais forte.
6. **É media query?** Ela está no fim do arquivo? Tem parênteses e `px`?

Truque para enxergar uma caixa: coloque `outline: 2px solid red;` nela por um instante.

**Antes de chamar o professor:** esta cola, depois o DevTools, depois o colega do lado.

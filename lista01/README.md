# Lista 01 — CSS: Flexbox (Parte 1)

**Disciplina:** Desenvolvimento Web I  
**Professor:** Hewerton Enes de Oliveira  
**Curso:** Técnico Integrado em Informática para Internet — 2026

## Parte A — Múltipla escolha

1. **Alternativa B.** `display: flex` é aplicado no contêiner pai, transformando seus filhos diretos em itens flex.
2. **Alternativa C.** O valor padrão de `flex-direction` é `row`, que organiza os itens em uma linha.
3. **Alternativa B.** Com `row`, o eixo principal é horizontal, da esquerda para a direita.
4. **Alternativa B.** Com `flex-direction: column`, o eixo principal é vertical, então `justify-content` distribui os itens verticalmente.
5. **Alternativa C.** `align-items` alinha os itens no eixo cruzado.
6. **Alternativa C.** O valor padrão de `align-items` é `stretch`, que pode esticar os itens no eixo cruzado.
7. **Alternativa B.** `space-between` deixa o primeiro item no início e o último no fim, distribuindo o espaço livre entre eles.
8. **Alternativa B.** `flex-wrap: wrap` permite que os itens passem para a linha seguinte quando não couberem.
9. **Alternativa B.** `align-content` tem efeito quando há várias linhas no contêiner flex, normalmente usando `flex-wrap: wrap` ou `wrap-reverse`.
10. **Alternativa B.** `gap` cria espaço entre os itens sem adicionar espaço extra nas bordas externas do contêiner.
11. **Alternativa C.** `row-reverse` inverte a ordem visual dos itens no eixo horizontal.
12. **Alternativa A.** `justify-content: center` centraliza no eixo principal e `align-items: center` centraliza no eixo cruzado.

## Parte B — Dissertativas e análise de código

### 13. Contêiner flex e item flex

O contêiner flex é o elemento pai que recebe `display: flex`. Seus filhos diretos viram itens flex e passam a ser organizados de acordo com propriedades como `flex-direction`, `justify-content` e `align-items`.

### 14. Disposição de A, B e C

Os elementos A, B e C ficam empilhados verticalmente, pois `flex-direction: column` define uma coluna. Como o contêiner tem 300px de altura e usa `justify-content: center`, o conjunto dos três elementos fica centralizado verticalmente dentro dele.

### 15. Removendo `flex-direction: column`

Sem essa propriedade, o valor padrão volta a ser `row`, então A, B e C ficam lado a lado. Como o valor padrão de `flex-wrap` é `nowrap`, eles não passam para a linha seguinte. Em vez disso, encolhem (o `flex-shrink` padrão é 1) até o tamanho mínimo do conteúdo e, se ainda não couberem nos 300px de largura, ultrapassam o contêiner.

Além disso, os eixos se invertem: `justify-content: center` passa a atuar na horizontal, então a centralização vertical se perde. Como o `align-items` padrão é `stretch`, os itens também são esticados até a altura de 300px do contêiner.

### 16. `justify-content` e `align-items`

Com `flex-direction: row`, `justify-content` atua no eixo principal horizontal e `align-items` atua no eixo cruzado vertical. Se a direção mudar para `column`, o eixo principal fica vertical e o eixo cruzado fica horizontal, então a atuação dos dois também muda.

### 17. `align-content: center`

Com `flex-wrap: nowrap`, os itens ficam em uma única linha, por isso `align-content` normalmente não tem efeito visível. Para ter efeito, é necessário permitir várias linhas, por exemplo com `flex-wrap: wrap`, e haver mais de uma linha de itens.

### 18. Diferença entre `gap` e `margin-right`

`gap: 16px` cria espaço apenas entre os itens. Já `margin-right: 16px` coloca uma margem à direita de cada item, inclusive do último, podendo criar espaço desnecessário na borda e dificultar o controle do espaçamento.

## Parte C — Prática

### 19. Menu horizontal

```css
.menu {
  align-items: center;
  display: flex;
  gap: 12px;
}
```

O `display: flex` coloca os itens lado a lado, `gap` define o espaço entre eles e `align-items: center` alinha os itens no eixo cruzado.

### 20. Galeria com quebra de linha

```css
.galeria {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
}
```

`flex-wrap: wrap` permite criar novas linhas quando não houver espaço, e `gap` define 16px entre linhas e colunas.

### 21. Centralizar um card no meio da tela

```css
.pagina {
  align-items: center;
  display: flex;
  justify-content: center;
  min-height: 100vh;
}
```

`justify-content` centraliza horizontalmente e `align-items` centraliza verticalmente, considerando a direção padrão `row`.

### 22. Layout em coluna

```css
.pagina {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
```

A direção `column` empilha o `header`, o `main` e o `footer`, e `gap` cria 8px entre as seções.

### 23. Barra de ferramentas com três grupos

```css
.toolbar {
  align-items: center;
  display: flex;
  justify-content: space-between;
}
```

`space-between` coloca o primeiro grupo no início e o último no fim, distribuindo o espaço livre igualmente entre os grupos. Assim, o grupo do meio fica exatamente no centro quando os grupos das pontas têm a mesma largura. Se as larguras forem diferentes, os dois espaços continuam iguais, mas o grupo do meio não fica perfeitamente centralizado.

### 24. Faixa com quatro cards

**HTML:**

```html
<section class="cards" aria-label="Exemplo de cards Flexbox">
  <article class="card">
    <h2>Card 1</h2>
    <p>Exemplo de conteúdo.</p>
  </article>
  <article class="card">
    <h2>Card 2</h2>
    <p>Um pouco mais de texto para demonstrar a altura.</p>
  </article>
  <article class="card">
    <h2>Card 3</h2>
    <p>Exemplo de conteúdo.</p>
  </article>
  <article class="card">
    <h2>Card 4</h2>
    <p>Exemplo de conteúdo.</p>
  </article>
</section>
```

**CSS:**

```css
.cards {
  align-content: flex-start;
  align-items: stretch;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  min-height: 400px;
}

.card {
  background: #f7f7f7;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-sizing: border-box;
  padding: 1rem;
  width: 200px;
}
```

O contêiner `.cards` usa Flexbox com `flex-wrap: wrap`. Cada card tem largura fixa de 200px, então em telas largas os quatro ficam lado a lado em uma só linha e, conforme a tela estreita, os cards quebram para a linha de baixo (por exemplo, 2 + 2 e depois um por linha). O `gap: 1rem` separa os cards entre linhas e colunas.

O `align-items: stretch` faz os cards de uma mesma linha terem a mesma altura visual. O `align-content: flex-start` agrupa as linhas no topo do contêiner quando há mais de uma, e o `min-height: 400px` garante espaço vertical sobrando para esse efeito ser visível. Não foram usados `flex-grow`, `flex-shrink`, `flex-basis`, `order` nem `align-self`.

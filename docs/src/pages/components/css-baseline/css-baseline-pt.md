---
components: CssBaseline, ScopedCssBaseline
---

# CSS Baseline

<p class="description">Material-UI oferece um componente CSS Base a fim de inciar uma elegante, consistente e simples base para construir sobre.</p>

## Reset global

Você já deve estar familiarizado com [normalize.css](https://github.com/necolas/normalize.css), uma coleção de elementos HTML e normas de atributos de estilo.

```jsx
import React from 'react';
import CssBaseline from '@material-ui/core/CssBaseline';

export default function MyApp() {
  return (
    <React.Fragment>
      <CssBaseline />
      {/* O resto da sua aplicação */}
    </React.Fragment>
  );
}
```

## Escopando componentes filhos

No entanto, você pode estar migrando progressivamente um site para Material-UI, usar um reset global pode não ser uma opção. É possível aplicar a baseline apenas aos filhos usando o componente `ScopedCssBaseline`.

```jsx
import React from 'react';
import ScopedCssBaseline from '@material-ui/core/ScopedCssBaseline';
import MyApp from './MyApp';

export default function MyApp() {
  return (
    <ScopedCssBaseline>
      {/* O resto da sua aplicação */}
      <MyApp />
    </ScopedCssBaseline>
  );
}
```

⚠️ Certifique-se de importar `ScopedCssBaseline` primeiro para evitar conflitos de box-sizing, como no exemplo acima.

## Abordagem

### Página

Os elementos `<html>` e `<body>` são atualizados para fornecer melhores padrões para toda a página. Mais especificamente:

- The margin in all browsers is removed.
- A cor de fundo padrão do material design é aplicada. Isto usando [`theme.palette.background.default`](/customization/default-theme/?expand-path=$.palette.background) para dispositivos padrão e um fundo branco para dispositivos de impressão.

### Leiaute

- `box-sizing` é definido globalmente no elemento `<html>` para `border-box`. Todos elementos —incluindo `*::before` e `*::after` são declarados para herdar essa propriedade, que garante que a largura declarada do elemento nunca seja excedida devido ao preenchimento da borda.

### Tipografia

- Nenhum tamanho de fonte base é declarado no `<html>`, mas 16px é assumido (o padrão do navegador). Você pode aprender mais sobre as implicações da mudança do padrão de tamanho de fonte do `<html>` na página de [documentação de tema](/customization/typography/#typography-html-font-size).
- Define o estilo `theme.typography.body2` no elemento `<body>`.
- Define o font-weight no `theme.typography.fontWeightBold` para elementos `<b>` e `<strong>`.
- O antialiasing de fonte é habilitado para melhorar a exibição da fonte Roboto.
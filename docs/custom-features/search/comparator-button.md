# CompareButton

Botão para adicionar produtos à comparação, disparando scroll automático até o comparador. Para informações sobre o comparador, ver [Comparador PDC](./comparator-pdc.md)

## Uso

```javascript
import React from 'react';

import { ComparatorProvider } from './../react/context/comparatorContext';
import CompareProduct from './components/PDC/Comparator';
import CompareButton from './components/PDC/CompareButton';

const CompareProductPDC = ({ shouldShowButton }) => {
  return (
    <ComparatorProvider>
      {!shouldShowButton && <CompareProduct />}
      {shouldShowButton && <CompareButton />}
    </ComparatorProvider>
  );
};

export default CompareProductPDC;
```

## Exemplo

``` json
"product-summary.shelf": {
  "children": [
    "stack-layout#shelf",
    "product-summary-name",
    "product-rating-inline",
    "product-summary-space",
    "flex-layout.row#voltage-selector",
    "flex-layout.row#shelf-price",
    "flex-layout.row#shelf-add-to-cart",
    "custom-arno-compare-products-pdc#button"
  ]
},
"custom-arno-compare-products-pdc#button": {
  "props": {
    "shouldShowButton": true
  }
},
```

## Funcionalidades

- Renderização condicional baseada em `shouldShow` e lista de produtos
- Scroll suave até o comparador com offset de -150px
- Extração do ID do produto via atributo `data-af-product-id`
- Disparo de evento customizado `compareProduct` com detalhes do produto

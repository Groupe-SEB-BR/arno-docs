# Ofertas Relâmpago

Vitrine de ofertas relâmpago

## TODO

Refatorar o código de ofertas relâmpago para não depender da vitrine de Black Friday

## Usage

react/EnrichedContent.js

```jsx
import EnrichedContent from './components/PDP/EnrichedContent';

export default EnrichedContent;
```

store/interfaces.json

```json
  "arno-enriched-content": {
    "component": "EnrichedContent",
    "composition": "children"
  },
```

## Props

| Prop         | Type    | Required | Default | Description                                  |
| children   | ReactNode  | No      |       | HTML com o conteúdo enriquecido |

## Examples

```jsx
  "flex-layout.col#pdp-description": {
    "children": [
      "arno-enriched-content"
    ],
    "props": {
      "blockClass": "pdp-description"
    }
  },
  "arno-enriched-content": {
    "children": ["rich-text#pdp-description", "product-description"]
  },
```

## Notes

Esse componente manipula o DOM para injetar o HTML vindo do cadastro do produto.
Ele aguarda o evento canUseDom da VTEX para inserir o HTML. Os scripts são adicionados ao body da página.

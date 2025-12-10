# Home Tabs

Esse componente mostra uma vitrine de até 3 abas, cada uma com até 3 cards. A cada 30 segundos as abas ativas são alteradas.

![image](../../assets/home-tabs.png)

## Usage

react/HomeTabs.js

```jsx
import HomeTabs from './components/HomeTabs';

export default HomeTabs;
```

store/interfaces.json

```json
  "custom-arno-home-tabs": {
    "component": "HomeTabs"
  },
```

## Props

| Prop         | Type             | Required | Default | Description                                  |
| ------------ | ---------------- | -------- | ------- | -------------------------------------------- |
| tabs         | array of objects | Yes      | []      | Array de objetos com os dados das categorias |
| shouldRender | boolean          | Yes      | false   | Deve renderizar o componente ou não?         |

## Examples

```jsx
  "store.home": {
    "blocks": [
      "custom-arno-home-tabs",
    ]
  }
```

## Notes

Additional information, gotchas, or important considerations when using this component.

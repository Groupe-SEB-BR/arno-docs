# Meta Tags

Esse componente é responsável por gerenciar as meta tags que são adicionadas à loja via Site Editor.

![image](../../assets/meta-tags.png)

## Usage

react/MetaTags.js

```jsx
  import MetaTags from './components/MetaTags';

  export default MetaTags;
```

store/interfaces.json

```json
  "custom-arno-meta-tags": {
    "component": "MetaTags"
  },
```

## Props

| Prop | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| items | array | Yes | false | Objeto com propriedades SEO e Meta Tags |

#### Props de `items`

Temos um objeto `items` com outros objetos dentro dele com as seguintes propriedades:

```json
    items: {
      title: 'Items',
      type: 'array',
      items: {
        type: 'object',
        properties: {
          title: {
            title: 'Title*',
            type: 'string',
            default: '',
          },
          description: {
            title: 'Description*',
            type: 'string',
            default: '',
          },
          image: {
            title: 'Image URL',
            type: 'string',
            default: '',
          },
          pathname: {
            title: 'Path Name* (Ex: /arno/para-casa)',
            type: 'string',
            default: '',
          },
          canonical: {
            title: 'Canonical URL',
            type: 'string',
            default: '',
          },
        },
      },
    },
```

## Examples

```jsx
  "store.home": { 
    "blocks": [
      "custom-arno-meta-tags",
    ]
  }
```

## Notes

Additional information, gotchas, or important considerations when using this component.

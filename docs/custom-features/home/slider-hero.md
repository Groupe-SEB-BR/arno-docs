# Slider Hero

Esse componente renderiza o Slider principal da loja dentro da página inicial de Arno, Rochedo e Tefal

![image](../../assets/slider-hero.png)

## Usage

react/SliderHero.js

```jsx
  import SliderHero from './components/SliderHero';

  export default SliderHero;
```

store/interfaces.json

```json
  "arno-slider-hero": {
    "component": "SliderHero"
  },
```

## Props

| Prop | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| croctActive | boolean | Yes | false | Controla os banners exibidos no Slider |
| slides | array | Yes | array | Array de objeto com as imagens do Slider |
| targetDate | string | Yes | 2024-11-29T00:00:00 | Data alvo para exibição do cronômetro |
| enableCountdown | boolean | Yes | false | Controla a exibição do cronômetro |

<br>

#### Props de `slides`

Temos um array `default` com um objeto com as seguintes propriedades:

```json
  default: [
        {
          imageDesktop: '',
          imageMobile: '',
          link: '',
          alt: '',
        },
      ],
```

Temos um objeto `items` com outros objetos dentro dele com as seguintes propriedades:

```json
  items: {
        type: 'object',
        title: 'Imagem',
        properties: {
          imageDesktop: {
            type: 'string',
            title: 'Banner Desktop',
            default: '',
            widget: {
              'ui:widget': 'image-uploader',
            },
          },
          imageMobile: {
            type: 'string',
            title: 'Banner Mobile',
            default: '',
            widget: {
              'ui:widget': 'image-uploader',
            },
          },
          link: {
            type: 'string',
            title: 'Link',
            default: '',
          },
          alt: {
            type: 'string',
            title: 'Alt',
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
      "arno-slider-hero",
    ]
  }
```

## Notes

Additional information, gotchas, or important considerations when using this component.

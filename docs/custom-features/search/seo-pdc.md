# Search Banner

Componente React que exibe banners e seções SEO em páginas de busca com suporte a layouts responsivos e conteúdo customizável.

## Uso

react/SearchBanner.js

```javascript
import SearchBanner from './components/SearchBanner';

export default SearchBanner;
```

store/interfaces.json

```json
"arno-search-banner": {
  "component": "SearchBanner"
}
```

## Exemplos

```json
"search-result-layout.desktop": {
  "children": [
    "custom-arno-meta-tags-category",
    "custom-color-title-category",
    "arno-search-banner",
    "arno-search-banner-custom",
    "flex-layout.row#search-breadcrumb",
    "flex-layout.row#search-title",
    "flex-layout.row#category"
  ],
  "props": {
    "pagination": "show-more",
    "blockClass": "desktop"
  }
},
```

## Funcionalidades

### Responsividade

- Utiliza `useDevice` do `vtex.device-detector` para detectar dispositivo
- Exibe `bannerImageMobile` em dispositivos móveis
- Exibe `bannerImageDesktop` em dispositivos desktop
- Re-executa a busca ao alternar entre dispositivos

### Subcomponentes

#### Banner

- Renderiza imagem de fundo com carregamento lazy
- Renderiza lista de cards de conteúdo com ícone, título e texto
- Suporta cor customizada via propriedade `textColor` (padrão: `#fff`)
- Renderiza HTML via `dangerouslySetInnerHTML`

#### Seção SEO

- Renderiza título SEO (`h1`) e texto SEO (`h3`)
- Renderiza HTML via `dangerouslySetInnerHTML`

## Props

| Prop                 | Tipo   | Descrição                                                  |
| -------------------- | ------ | ---------------------------------------------------------- |
| `bannerImageDesktop` | string | URL da imagem de fundo para desktop                        |
| `bannerImageMobile`  | string | URL da imagem de fundo para mobile                         |
| `bannerTexts`        | array  | Lista de objetos com `title`, `text`, `icon` e `textColor` |
| `seoTitle`           | string | Título SEO                                                 |
| `seoText`            | string | Texto SEO                                                  |

## Dependências

- `react`: Hooks `useState`, `useEffect`
- `vtex.device-detector`: Hook `useDevice`

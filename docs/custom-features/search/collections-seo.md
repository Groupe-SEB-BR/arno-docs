# Search Banner Custom

Componente React que exibe banners e seções SEO em páginas de busca, buscando dados dinamicamente do MasterData com suporte a layouts responsivos.

## Diferenças do Search Banner

Este componente difere do `Search Banner` padrão porque o último não funciona adequadamente com filtros de categoria da VTEX, já que altera a URL impedindo que o Site Editor identifique o conteúdo correto.

**Exemplo de URL base:**

```text
https://www.arno.com.br/semana-do-consumidor?order=OrderByTopSaleDESC
```

**Exemplo com filtro de categoria:**

```text
https://www.arno.com.br/arno/semana-do-consumidor?initialMap=productClusterIds&initialQuery=285&map=category-1,productclusternames&order=OrderByTopSaleDESC
```

Quando o filtro é aplicado, a URL muda de `/semana-do-consumidor` para `/arno/semana-do-consumidor`, causando falha na renderização do conteúdo. O `Search Banner Custom` contorna esse problema consultando dados diretamente do MasterData, independentemente das alterações de URL.

## Uso

react/SearchBannerCustom.js

```javascript
import SearchBannerCustom from './components/SearchBannerCustom';

export default SearchBannerCustom;
```

store/interfaces.json

```json
"arno-search-banner-custom": {
  "component": "SearchBannerCustom"
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

### Busca de Dados

- Extrai o último segmento do `pathname` da URL atual
- Consulta a entidade `CC` do MasterData filtrando pela URL
- Campos retornados: `seoText`, `bannerText`, `seoTitle`, `backgroundImageDesktop`, `backgroundImageMobile`, `url`

### Responsividade

- Utiliza `useDevice` do `vtex.device-detector` para detectar dispositivo
- Exibe `backgroundImageMobile` em dispositivos móveis
- Exibe `backgroundImageDesktop` em dispositivos desktop
- Re-executa a busca ao alternar entre dispositivos

### Subcomponentes

#### `Banner`

- Renderiza imagem de fundo com carregamento lazy
- Renderiza lista de conteúdos de banner a partir do campo `bannerText` (JSON serializado)

#### `BannerContent`

- Renderiza título (`h1`) e texto (`h2`) do banner
- Suporta cor customizada via propriedade `textColor` (padrão: `#fff`)
- Renderiza HTML via `dangerouslySetInnerHTML`

#### `SeoSection`

- Renderiza título SEO (`h1`) e texto SEO (`h3`)
- Renderiza HTML via `dangerouslySetInnerHTML`

## Endpoints Utilizados

- `GET /api/dataentities/CC/search/?_fields=seoText,bannerText,seoTitle,backgroundImageDesktop,backgroundImageMobile,url&_where=url=*{pathname}*` - Recupera dados de banner e SEO do MasterData

## Tratamento de Erros

Erros na requisição são logados no console via `console.error` e não impedem a execução do componente. O componente simplesmente não é renderizado em caso de falha ou ausência de dados.

## Dependências

- `react`: Hooks `useState`, `useEffect`
- `vtex.device-detector`: Hook `useDevice`

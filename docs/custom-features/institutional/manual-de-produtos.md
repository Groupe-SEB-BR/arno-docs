# Manual de Produtos

Componente de catálogo manual de produtos para Arno, permitindo busca por categoria, produto ou nome com integração ao Master Data e exibição de imagens do catálogo.

## Uso

```javascript
import ManualComponent from './components/ManualComponent';

export default ManualComponent;
```

interfaces.json

```json
"arno-manual-component": {
  "component": "ManualComponent"
},
```

## Exemplos

```json
"flex-layout.col#manuais-component": {
  "title": "manuais component",
  "children": [
    "rich-text#manuais-component-text",
    "arno-manual-component"
  ],
  "props": {
    "blockClass": "institutional-component"
  }
},
```

## Funcionalidades

### Busca de Produtos

- **Por categoria**: Dropdown com categorias únicas ordenadas alfabeticamente
- **Por produto**: Dropdown cascateado que se popula após seleção de categoria
- **Por nome**: Formulário de busca com filtro case-insensitive
- Validação e filtro de disponibilidade de produtos

### Componentes Filhos

- `ProductCard`: Exibe card individual de produto com imagem e informações

### Integração com Master Data

- Busca de produtos na entidade `MN` do Master Data
- Campos retornados: `product`, `category`, `sku`, `filename`, `ean`
- Suporte a até 1000 registros com paginação `REST-range`
- Integração com catálogo VTEX para busca de imagens por EAN
- Imagem padrão como fallback quando não encontrada no catálogo

## Props

Nenhuma prop obrigatória.

## Estados Gerenciados

- `data`: Lista de produtos com dados do Master Data e imagens
- `categoriesNameList`: Categorias únicas ordenadas
- `categoryName`: Categoria selecionada
- `productsNameList`: Produtos filtrados da categoria
- `productName`: Produto selecionado
- `itemsList`: Produtos exibidos conforme filtro ativo
- `busca`: Termo de busca por nome de produto

## Dependências

- `react`: Hooks `useState`, `useEffect`, `useCallback`
- `axios`: Requisições HTTP para Master Data e catálogo
- `ProductCard`: Componente de exibição individual de produto
- CSS Module: `styles.css`

## APIs Utilizadas

- `/api/dataentities/MN/search/`: Busca produtos no Master Data
- `/api/catalog_system/pub/products/search`: Busca imagens por EAN no catálogo VTEX

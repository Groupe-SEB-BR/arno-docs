# Comparator

Este componente exibe uma lista de produtos para comparação na página de detalhes do produto (PDP), filtrando produtos da mesma categoria e excluindo kits.

![image](../../assets/comparador-pdc.png)

## Uso

react/Comparator.js

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

store/interfaces.json

```json
"custom-arno-compare-products-pdc": {
  "component": "CompareProductPDC",
  "render": "server",
  "composition": "children",
  "allowed": "*"
},
```

## Exemplos

```json
"store.search#category": {
  "blocks": [
    "search-result-layout",
    "custom-arno-compare-products-pdc#comparator",
    "custom-arno-differentials-pdc",
    "custom-arno-category-reviews",
    "custom-arno-category-faq",
    "flex-layout.row#search-seo"
  ]
},
```

### Context Value

- `categories`: Árvore de categorias atual
- `productsToCompare`: Lista completa de produtos filtrados
- `productsToList`: Lista limitada a 5 produtos para exibição
- `setProductsToList`: Função para definir lista de produtos
- `updateProductsToList`: Função para atualizar lista com lógica customizada
- `loading`: Estado de carregamento
- `error`: Mensagem de erro
- `shouldShow`: Visibilidade do comparador
- `categoryName`: Nome da categoria atual

## Componentes

### Products Component

Componente principal que gerencia seleção e exibição de produtos com suporte responsivo.

**Props do Contexto:**

- `productsToCompare`: Array de produtos disponíveis
- `productsToList`: Array de produtos selecionados (até 5)
- `setProductsToList`: Setter para lista de produtos
- `updateProductsToList`: Updater com callback

**Funcionalidades:**

- Seleção múltipla via dropdowns
- Validação de duplicatas
- Evento customizado `compareProduct`
- Destaque visual do último produto adicionado (1s)

### ProductSelect Component

Dropdown de seleção com filtragem de opções já selecionadas.

**Props:**

- `index`: Posição no array
- `products`: Array de produtos disponíveis
- `selectedProducts`: Array de produtos selecionados
- `onChange`: Callback de mudança

### CompareProductItem Component

Exibe informações do produto: imagem, nome, preço, atributos, link e botão adicionar ao carrinho.

**Props:**

- `product`: Objeto do produto
- `lastSelectedProduct`: ID do último produto adicionado (para animação)

### ProductPrice Component

Exibe preço de lista e preço de venda formatados.

### ProductAttribute Component

Exibe atributo com ícone e valor.

### MobileView Component

Layout de slider (Slick) com 1 produto por slide e seletor em cada slide.

### DesktopView Component

Layout em grid com seletores no topo e produtos lado a lado.

## Funcionalidades

- Seleção de até 5 produtos para comparação
- Validação de duplicatas de produtos
- Responsividade automática (mobile/desktop)
- Evento `compareProduct` para adicionar ao comparador
- Destaque visual do último produto adicionado
- Integração com AddToCartButton
- Atributos customizáveis com ícones
- Tratamento de produtos indisponíveis

## Dependências

- `react`: useState, useEffect, useCallback
- `react-slick`: Carousel mobile
- `classnames`: Utilidade CSS condicional
- `vtex.formatted-price`: Formatação de preços
- `vtex.device-detector`: Detecção de dispositivo
- `vtex.add-to-cart-button`: Botão adicionar ao carrinho
- `comparatorContext`: Contexto do comparador
- `comparatorIcons`: Mapeamento de ícones

# Cross Selling

Vitrine de Cross Selling dentro do checkout usando JavaScript Vanilla.

## Uso

```javascript
$(window).on('orderFormUpdated.vtex', (event, orderForm) => {
  crossSell(orderForm);
});
```

```javascript
const crossSell = async (orderForm) => {
  if (window.location.hash !== '#/cart') return;

  const related = await fetchAndCombineRelatedProducts(orderForm.items);
  if (related.length === 0) return;

  const groupedProducts = groupProductsBySku(related);
  const shelf = await createShelf(groupedProducts);

  attachSkuEventListeners(shelf, groupedProducts);
  attachAddToCartEventListeners(shelf, groupedProducts);

  await new Promise((resolve) => {
    const checkSlick = setInterval(() => {
      if (typeof $.fn.slick === 'function') {
        initializeSlider();
        clearInterval(checkSlick);
        resolve();
      }
    }, 100);
  });

  insertShelfIntoCart(shelf);
};
```

## Funcionalidades

### Recuperação de produtos relacionados

- Valida contexto de navegação (página do carrinho)
- Consulta API de sugestões de produtos
- Agrupa produtos por SKU, consolidando variações do mesmo produto

### Construção da vitrine de ofertas

- Implementa vitrine com funcionalidades completas:
  - Indicadores de desconto
  - Sistema de avaliações (apenas visual)
  - Renderização de imagens
  - Exibição de preços e parcelas
  - Visualização de preço à vista
  - Seletor de variações (SKU)
  - Ação de adição ao carrinho
- Implementa listeners de eventos para interações com SKU e adição ao carrinho

### Animação com Slick.js

- Integra biblioteca Slick.js para efeito carrossel
- Aguarda carregamento assíncrono do script antes de inicializar slider

### Inserção na página

- Injeta vitrine no DOM utilizando seletor `.cart-template-holder .cart`
- Integra elemento ao fluxo de checkout sem interrupção

## Dependências

- `slick.js`: Biblioteca de vitrine

## Endpoints Utilizados

- `GET /reviews-and-ratings/api/rating/productId` - Recupera dados de Avalições do Produto
- `GET /api/catalog_system/pub/products/crossselling/suggestions/productId` - Recupera dados dos produtos que foram cadastrados como sugestões baseado no produto adicionado ao carrinho

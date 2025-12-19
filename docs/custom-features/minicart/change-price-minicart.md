# Change Price Minicart

Este componente sincroniza automaticamente o `sellingPrice` com o `price` dos itens no carrinho, garantindo que o preço de venda reflita o preço base do produto.

## Uso

react/ChangePriceMinicart.js

```javascript
import { ChangePriceMinicart } from './components/ChangePriceMinicart';

export default ChangePriceMinicart;
```

store/interfaces.json

```json
"custom-arno-change-price-minicart": {
  "component": "ChangePriceMinicart"
},
```

## Exemplos

```jsx
"minicart-base-content": {
  "blocks": ["minicart-empty-state"],
  "children": [
    "minicart-product-list",
    "minha-seb-minicart",
    "custom-arno-minicart-cross-selling",
    "flex-layout.row#minicart-footer",
    "custom-price-minicart"
  ]
},
```

## Funcionalidades

### Sincronização Automática de Preços

- Monitora mudanças nos itens do carrinho
- Compara `sellingPrice` com `price` de cada item
- Atualiza automaticamente quando há discrepância

### Otimização de Performance

- Verifica se há itens no carrinho antes de processar
- Apenas atualiza se houver diferença entre os preços
- Evita atualizações desnecessárias do `orderForm`

## Comportamento

### Fluxo de Execução

1. Verifica se existem itens no carrinho
2. Compara `sellingPrice` vs `price` de cada item
3. Se houver diferença, cria nova lista com preços sincronizados
4. Atualiza o `orderForm` com os novos valores

### Renderização

- Componente não renderiza nenhum elemento visual (`return null`)
- Funciona como um hook de sincronização em background

## Dependências

- `react`: Hooks do React (`useEffect`)
- `vtex.order-manager/OrderForm`: Hook `useOrderForm` para manipulação do carrinho

## Observações

1. Componente invisível (não renderiza UI)
2. Executa automaticamente ao detectar mudanças nos itens
3. Garante consistência entre preço base e preço de venda
4. Útil para cenários onde promoções ou descontos precisam ser refletidos

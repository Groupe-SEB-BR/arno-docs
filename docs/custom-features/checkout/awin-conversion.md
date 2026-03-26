# Awin Conversion

Componente React que integra rastreamento de conversões do Awin, gerenciando pixels de tracking e identificação de origem de tráfego.

## Uso

react/AwinConversion.js

```javascript
import AwinConversion from './components/AwinConversion';

export default AwinConversion;
```

store/interfaces.json

```json
"custom-arno-awin-conversion": {
  "component": "AwinConversion"
},
```

## Exemplos

```json
"store.orderplaced": {
  "blocks": [
    "__fold__",
    "order-placed",
    "custom-arno-awin-conversion"
  ]
},
```

## Funcionalidades

### Rastreamento de Conversões

- Monitora eventos `orderPlaced` no dataLayer
- Dispara múltiplos pixels Awin em paralelo (sread.js, sread.php, alt.php, sread.img)
- Rastreia valor total da transação e cupom de desconto
- Envia identificador de sessão (cks) e URL de origem
- Inclui modo fallback com imagem GIF

### Mapeamento de Comissões por Categoria

Suporta grupos de comissão específicos por marca e categoria:

- **Arno** (29 categorias: acessórios, cafeteiras, ventiladores, electrodomésticos, etc.)
- **Rochedo** (10 categorias: panelas, frigideiras, formas, utensílios)
- **Tefal** (10 categorias: panelas, frigideiras, facas, utensílios)
- **Default** (categorias não mapeadas)

Cada transação pode conter múltiplos produtos, agrupados por categoria com cálculo automático do valor total por grupo.

### Armazenamento de Dados

Utiliza `sessionStorage` para persistir dados de origem de tráfego durante a sessão:

- `awin_origin`: Canal de origem detectado
- `awin_awc`: Identificador Awin
- `awin_utm_source`: Parâmetro UTM source

## Dependências

- `react`: Hook `useEffect`

## Variáveis de Configuração

- `merchantId`: '108626' (ID Awin)
- `currency`: 'BRL'

## Eventos Monitorados

- `orderPlaced`: Dispara rastreamento com dados da transação (ID, subtotal, cupom, produtos)

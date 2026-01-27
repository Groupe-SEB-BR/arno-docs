# Store Locator

Componente de localização de lojas para Arno, permitindo busca por estado, cidade, bairro ou CEP, com integração ao Google Maps.

## Uso

```javascript
import StoreLocator from "./components/StoreLocator";

export default StoreLocator;
```

interfaces.json

```json
"arno-store-locator": {
  "component": "StoreLocator"
}
```

## Exemplos

```json
"flex-layout.col#assistencia-tecnica-component": {
  "title": "assistencia-tecnica component",
  "children": [
    "rich-text#assistencia-tecnica-component-text",
    "arno-store-locator"
  ],
  "props": {
    "blockClass": "institutional-component"
  }
},
```

## Estrutura

```text
StoreLocator (Component)
├── div (search-locator-options-container)
│   └── select (Estado)
│   └── select (Cidade)
│   └── select (Bairro)
│   └── form (Busca por CEP)
├── div (search-state-response)
│   ├── div (stores-result-container)
│   │   └── StoreCard (lista de lojas)
│   └── div (store-locator-map-container)
│       ├── InfoStore (detalhes da loja selecionada)
│       └── Map (Google Maps com marcadores)
```

## Funcionalidades

### Busca de Lojas

- **Por localização**: Seleção de estado, cidade e bairro através de dropdowns cascateados
- **Por CEP**: Busca através de formulário com máscara de entrada (99999-999)
- Validação de disponibilidade de lojas na região
- Centralização automática do mapa na região selecionada

### Mapa Interativo

- Exibição de todas as lojas com marcadores no Google Maps
- InfoWindow ao clicar em marcadores
- Zoom e centralização automáticos baseados na seleção
- Ajuste de zoom: 8 (inicial), 12 (região), 14 (CEP), 15 (loja específica)

### Componentes Filhos

- `StoreCard`: Card de loja na listagem lateral
- `InfoStore`: Detalhes expandidos da loja selecionada
- `Map`: Componente do Google Maps
- `Marker`: Marcadores de lojas no mapa
- `InfoWindow`: Janela de informações ao clicar no marcador

### Integração com Master Data

- Busca de lojas na entidade `AT` do Master Data
- Campos: endereço, cidade, código, complemento, coordenadas, nome, bairro, número, telefones, estado, email, horários e CEP
- Suporte a até 2000 registros

## Props

O componente recebe `google` do HOC `GoogleApiWrapper`.

## Estados Gerenciados

- `zoom`: Nível de zoom do mapa
- `centerMap`: Coordenadas do centro do mapa
- `stores`: Lista completa de lojas
- `stateSelected`: Estado selecionado
- `citySelected`: Cidade selecionada
- `neighborhoodSelected`: Bairro selecionado
- `storesSelected`: Lojas filtradas pela busca
- `selectedStore`: Loja atualmente selecionada para detalhes
- `cep`: CEP informado pelo usuário
- `showingInfoWindow`: Controle de exibição do InfoWindow

## Dependências

- `react`: Hooks `useState`, `useEffect`, `useMemo`, `useCallback`
- `google-maps-react`: Componentes `Map`, `Marker`, `InfoWindow`, `GoogleApiWrapper`
- `axios`: Requisições HTTP para Master Data e API de CEP
- `react-input-mask`: Máscara de entrada para CEP
- `states.json`: JSON com dados de estados brasileiros

## APIs Utilizadas

- `/api/dataentities/AT/search/`: Busca de lojas no Master Data
- `/api/checkout/pub/postal-code/bra/${cep}`: Consulta de CEP da VTEX

# Awin Cookies

Componente React que gerencia rastreamento de conversões do Awin, capturando parâmetros de tráfego e sincronizando dados com o orderForm.

## Uso

react/AwinCookies.js

```javascript
import AwinCookies from './components/AwinCookies';

export default AwinCookies;
```

store/interfaces.json

```json
"custom-arno-awin-cookies": {
  "component": "AwinCookies"
}
```

## Exemplos

```json
"header-layout.desktop": {
  "children": [
    "global-css",
    "custom-arno-awin-cookies"
  ]
}
```

## Funcionalidades

### Captura de Parâmetros

- Extrai `awc` (Awin Conversion ID) da URL
- Extrai `utm_source` da URL
- Persiste parâmetros em sessionStorage

### Detecção de Origem de Tráfego

- Verifica `utm_source=awin` nos parâmetros de URL
- Verifica presença de `awc` ou `awin` na URL
- Implementa rastreamento de FIRST TOUCH (origem capturada apenas na primeira interação)
- Ignora alterações de origem em navegações subsequentes

### Mapeamento de Origem

- `utm_source=awin` ou `awc` → mapeado como `'aw'`
- Demais casos → mapeado como `'other'`

### Sincronização de Dados

- Persiste origem e parâmetros em sessionStorage
- Sincroniza `awc` e origem com customData do orderForm
- Detecta mudanças antes de atualizar (evita requisições desnecessárias)

### Navegação SPA

- Monitora mudanças de rota em VTEX IO (`history.pushState`, `history.replaceState`, `popstate`)
- Re-executa rastreamento em cada navegação

## Armazenamento

Utiliza `sessionStorage` com as seguintes chaves:

- `awin_origin` - origem de tráfego detectada
- `awin_awc` - Awin Conversion ID
- `awin_utm_source` - parâmetro utm_source

## Endpoints Utilizados

- `GET /api/sessions` - Recupera orderFormId e dados públicos
- `GET /api/checkout/pub/orderForm/{orderFormId}` - Recupera orderForm
- `PUT /api/checkout/pub/orderForm/{orderFormId}/customData/awin` - Atualiza customData com payload `{awc, ch}`

## Tratamento de Erros

Erros nas requisições são logados no console com prefixo `[AWIN]` e não impedem a execução do componente. Navegação prossegue normalmente em caso de falhas.

## Dependências

- `react`: Hook `useEffect`

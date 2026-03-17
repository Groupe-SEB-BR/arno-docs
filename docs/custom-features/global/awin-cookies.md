# Awin Cookies

Componente React que gerencia rastreamento de conversões do Awin, sincronizando parâmetros de origem de tráfego com a sessão e orderForm.

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

### Detecção de Origem de Tráfego

- Verifica `awaid` na URL
- Valida `utm_source=awin` nos parâmetros de URL e sessão
- Detecta referrers de mecanismos de busca (Google, Bing, Yahoo, DuckDuckGo, Yandex)
- Ignora tráfego interno do mesmo domínio

### Mapeamento de Origem

- `utm_source=awin` → mapeado como `'aw'`
- Mecanismos de busca → mapeado como `'other'`
- Demais casos → mapeado como `'direct'`

### Sincronização de Dados

- Atualiza sessão pública com origem detectada
- Sincroniza `utm_source` e `awc` (Awin Conversion ID) com customData do orderForm
- Converte `utm_source=awin` para `'aw'` no orderForm

## Dependências

- `react`: Hook `useEffect`

## Endpoints Utilizados

- `GET /api/sessions` - Recupera dados de sessão
- `PATCH /api/sessions` - Atualiza origem na sessão pública
- `PUT /api/checkout/pub/orderForm/{orderFormId}/customData/awin` - Atualiza customData

## Tratamento de Erros

Erros nas requisições são logados no console com prefixo `[AWIN]` e não impedem a execução do componente.

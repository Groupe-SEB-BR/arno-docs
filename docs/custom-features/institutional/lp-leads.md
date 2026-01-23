# LP Leads

Componente da página de Black Friday 2025 para Arno, Rochedo e Tefal, integrando banners, vitrines de produtos, barra de benefícios e conteúdo SEO.

## Uso

```javascript
import BlackFridayLP from './components/BlackFridayLP';

export default BlackFridayLP;
```

interfaces.json

```json
"custom-arno-black-friday-lp": {
  "component": "BlackFridayLP"
},
```

## Exemplos

```json
{
  "store.custom#arno-lp-black-friday-25": {
    "children": [
      "custom-arno-meta-tags",
      "custom-arno-data-structure",
      "custom-arno-black-friday-lp"
    ]
  }
}
```
## Funcionalidades

### Componentes Filhos

- `Banner`: Banner principal acima da dobra
- `Bar`: Barra de benefícios
- `FlashSales`: Vitrines de produtos com promoções (ofertas relâmpago e descontos progressivos). Para mais detalhes ver [Flash Sales](./../shelves/flash-sales.md)
- `Seo`: Conteúdo otimizado para SEO

### Scroll Automático para Promoções

- Detecção de hash URLs (`#ofertas-relampago`, `#descontos-progressivos`)
- Scroll suave com offset de 120px
- MutationObserver para elementos carregados dinamicamente
- Limpeza automática após 5 segundos

## Props

- `title`: Título H1 da página (padrão: "# BENEFÍCIOS DA BLACK FRIDAY ARNO, ROCHEDO e TEFAL")
- `banner`: URL da imagem do banner (padrão: "/arquivos/KV MISTO BLACK FRIDAY 2025_ARNO_TEFAL_ROCHEDO 1.png")
- `altBanner`: Texto alternativo da imagem (padrão: "Arno, Rochedo e Tefal")
- `description`: Descrição da Black Friday
- `subtitle`: Subtítulo H2 abaixo do banner (padrão: "## BENEFÍCIOS DA BLACK FRIDAY ARNO, ROCHEDO e TEFAL")
- `eventName`: Nome do evento para o Data Layer (padrão: "lp_leads")
- `barContent`: Array de objetos com ícone e descrição de benefícios
- `seoContent`: Array com título e descrição meta
- `activePromotions`: Configuração da vitrine de ofertas relâmpago
- `commonShelf`: Configuração da vitrine de descontos progressivos

## Dependências

- `react`: Hooks `useEffect`
- `vtex.render-runtime`: Hook `useRuntime`
- Componentes customizados: `Bar`, `Banner`, `Seo`, `FlashSales`

# Menu Desktop

## Nome do componente

```text
Menu Desktop SEB
└── SEB | ARNO
  └── Menu
    └── Para Cozinha
    └── Para Casa
    └── Para Lavanderia
    └── Café e Bebidas
    └── Kits
    └── Acessórios
    └── Ofertas Arno
└── SEB | ROCHEDO
  └── Menu
    └── Panelas
    └── Frigideiras
    └── Jogos de panelas
    └── Formas e Assadeiras
    └── Panelas de Pressão
    └── kits
    └── Panela de Pressão Clock
└── SEB | TEFAL
  └── Menu
    └── Panelas
    └── Jogo de panelas
    └── Utensílios
    └── Formas e Assadeiras
    └── Panelas de Pressão
    └── kits
    └── Ofertas Tefal
```

## Onde encontrar

Disponível no **Site Editor (VTEX)**, nas páginas que utilizam o menu de navegação principal.

Caminho geral:

- Admin VTEX → CMS → Site Editor

## Visão geral

O componente **Menu** permite exibir e configurar a navegação principal do site, controlando:

- Estrutura de categorias e subcategorias
- Links personalizados
- Ícones e imagens de destaque

## Campos de cada item do menu

### Código

Campo interno de identificação do item.

- Usado apenas para controle interno
- Não aparece no site
- Pode ser utilizado para organização ou referência técnica

### Nome do item do Menu

Texto identificador do item dentro do Site Editor.

> ⚠️ **Observação:** este nome é apenas administrativo e **só é visível no Site Editor**.

### Destaque

Define se o item deve receber estilo visual de destaque.

- **Ligado** → item aparece com destaque visual (dependendo do tema)
- **Desligado** → aparência padrão

Normalmente usado para promoções ou links prioritários.

### Tipo

Define o comportamento principal do item.

#### Categoria

Quando selecionado, o item se comporta como uma categoria do catálogo, podendo herdar estrutura e navegação padrão.

#### Customizado

Permite criar um item totalmente manual, com link definido livremente.

> Nas imagens apresentadas, a opção **Customizado** está selecionada.

### Submenu aberto no hover

Controla o comportamento de abertura do submenu.

Opções disponíveis:

- Abrir submenu ao passar o mouse (hover)
- Manter submenu fechado até interação

Esse campo define a experiência de navegação em menus com subníveis.

### Tipo de link

Define como o link será interpretado.

Esse campo controla o comportamento do campo **Texto** e do campo **href**.

(As opções podem variar conforme a implementação do menu.)

### Texto

Texto exibido como rótulo clicável no menu.

Exemplo:

```text
Ofertas
```

Esse é o texto que o usuário visualiza no menu.

### href

Define o destino do link.

Exemplo:

```text
/promocoes
```

Ou:

```text
https://www.exemplo.com
```

Pode ser um caminho interno ou uma URL completa.

### Atributo nofollow

Quando ativado, adiciona o atributo:

```html
rel="nofollow"
```

ao link gerado.

Indicado para:

- Links que não devem transmitir autoridade SEO
- Links externos
- Páginas promocionais temporárias

### Atributo title

Texto usado no atributo `title` do link.

Exemplo:

```text
Confira nossas ofertas especiais
```

Ajuda em acessibilidade e pode ser exibido como tooltip.

### ID do ícone

Campo utilizado para associar um ícone ao item de menu.

O valor informado depende do conjunto de ícones utilizado no projeto.

Exemplo:

```text
icon-ofertas
```

Quando configurado, o ícone pode aparecer ao lado do texto do menu.

### Salvar

Salva todas as configurações realizadas no item do menu.

### Cancelar

Descarta as alterações e retorna à tela anterior.

## Comportamento do componente

- Itens são exibidos na ordem configurada
- Subitens aparecem ao passar o mouse ou clicar
- Links inativos não são clicáveis
- Destacar itens promocionais é possível via configuração

## Boas práticas

- Mantenha a estrutura simples e intuitiva
- Limite o número de níveis de submenu
- Use textos curtos e descritivos
- Teste a navegação em dispositivos móveis

## Observações finais

- O componente depende da configuração correta dos links
- Alterações são refletidas imediatamente após publicação

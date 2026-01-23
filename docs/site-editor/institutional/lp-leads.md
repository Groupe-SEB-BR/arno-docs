# Landing Page - Leads

O template dessa landing page foi criado para que seja possível reaproveitá-lo para diferentes cenários de captação de leads.

## Onde encontrar

Disponível no **Site Editor (VTEX)** nas páginas de landing page que usam o template `lojaarno.store@2.x:store.custom#lp-base`.

Caminho geral:

- Admin VTEX → CMS → Site Editor

## Conteúdo Primeira Dobra

```text
Conteúdo Primeira Dobra
```

O componente **Conteúdo Primeira Dobra** permite configurar o conteúdo da primeira dobra da página de landing page, incluindo título, imagem do banner e descrição.

## Campos do componente

### Título H1

![image](../../assets/site-editor/lp-leads-h1.png)

Define o título principal da página.

**Tipo:** String  
**Valor padrão:** `# BENEFÍCIOS DA BLACK FRIDAY ARNO, ROCHEDO e TEFAL`

### Imagem do Banner

![image](../../assets/site-editor/lp-leads-banner.png)

Upload da imagem principal do banner.

**Tipo:** Image uploader  
**Valor padrão:** `/arquivos/KV MISTO BLACK FRIDAY 2025_ARNO_TEFAL_ROCHEDO 1.png`

### Texto Alt da Imagem do Banner

Texto alternativo para acessibilidade da imagem do banner.

**Tipo:** String  
**Valor padrão:** `Arno, Rochedo e Tefal`

### Nome do Evento para o Data Layer

![image](../../assets/site-editor/lp-leads-submit.png)

Identificador do evento para rastreamento analítico que será disparado ao submeter os dados dentro do formulário.

**Tipo:** String  
**Valor padrão:** `lp_leads`

### Descrição

![image](../../assets/site-editor/lp-leads-descricao.png)

Texto descritivo da campanha.

**Tipo:** String  
**Valor padrão:** `A Black Friday é considerada a maior campanha de descontos do ano...`

## Subtítulo acima da Barra de Benefícios

![image](../../assets/site-editor/lp-leads-h2.png)

Subtítulo exibido abaixo do banner.

```text
Rich Text
```

## Barra de Benefícios

![image](../../assets/site-editor/lp-leads-bar.png)

O conteúdo dessa sessão é exatamente igual ao da página da home, portanto é possível seguir o mesmo passo á passo descritos em [Barra de Benefícios](./../home/barra-de-beneficios.md)

## Título da Vitrine

Texto acima da Vitrine de Produtos

![image](../../assets/site-editor/lp-leads-shelf-title.png)

```text
Linha
└── Rich Text
```

## Vitrine de Produtos

![image](../../assets/site-editor/lp-leads-shelf.png)

A forma de configurar a vitrine de produtos é a mesma descrita em [Shelf Lançamentos](./../home/shelf-lancamentos.md#shelf-lancamentos-lista-de-produtos)

## Banner Secundário

Banner posicionado entre a Vitrine de Produtos e o Conteúdo SEO

```text
Linha
└── Imagem
```

![image](../../assets/site-editor/lp-leads-banner-secundario.png)

## SEO

Conteúdo SEO inserido no final da página. O texto deve ser configurado em markdown. Cada tópico deve ser um novo item dentro da sessão de Conteúdo SEO

![image](../../assets/site-editor/lp-leads-site-editor-seo.png)

```text
Linha
└── Conteúdo SEO
```

![image](../../assets/site-editor/lp-leads-seo.png)

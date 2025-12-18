# Documentação de API

## Visão Geral

Este módulo contém todas as chamadas de API para interagir com o Master Data da VTEX. As funções estão organizadas para gerenciar posts de blog, categorias e subcategorias.

## Endpoints do Master Data

### BP - Blog Posts

`/api/dataentities/BP/`

**Propósito:** Gerenciar posts/receitas do blog

**Campos disponíveis:**

`id:` Identificador único

`url:` Slug da URL

`title:` Título do post

`description:` Descrição/resumo

`brand:` Marca associada

`category:` Categoria principal

`categories:` Array de categorias

`complexity:` Nível de dificuldade

`recipeTime:` Tempo de preparo

`ingredients:` Lista de ingredientes

`instructions:` Passo a passo

`imageDesktop`, `imageMobile`, `imageCard`: Imagens em diferentes resoluções

`useVideo`: Booleano para vídeo

`videoIframe`: Embed do vídeo

`posttags`: Tags para SEO

`metaTitle`, `metaDescription`: Meta tags

`collection`: Coleção associada

`views`: Contador de visualizações

`filters`: Filtros para busca

`createdIn`: Data de criação

### BC - Blog Categories

`/api/dataentities/BC/`

**Propósito:** Gerenciar categorias do blog

**Campos disponíveis:**

`id:` Identificador único

`name:` Nome da categoria

`url:` Slug da URL

`description:` Descrição da categoria

`imageDesktop`, `imageMobile`: Imagens da categoria

`categoryMetaTitle`, `categoryMetaDescription`: Meta tags da categoria

`filters:` Filtros disponíveis

`order:` Ordenação

`createdIn`, `updatedIn`: Datas de criação e atualização

### SC - Subcategories

`/api/dataentities/SC/`

**Propósito:** Gerenciar subcategorias

**Campos disponíveis:**

`id:` Identificador único

`name:` Nome da subcategoria

`url:` Slug da URL

`description:` Descrição

`imageDesktop`, `imageMobile`: Imagens

`parentCategoryId:` ID da categoria pai

## Funções de API

### getPost

**Descrição:**

Busca um post específico pelo seu URL (slug).
// Todo: Melhorar a nomenclatura dessa função

**Parâmetros:**

- `url` (string): URL do post a ser buscado

**Endpoint:**

- `GET /api/dataentities/BP/search`

**Parâmetros de Query:**

- `_fields`: Campos específicos a retornar

- `_where`: Filtro por URL (url=${url})

**Retorno:**

- Promise contendo o objeto do post ou null se não encontrado

**URL Completa:**

```typescript
'/api/dataentities/BP/search?_fields=brand,category,categories,complexity,description,id,imageDesktop,imageMobile,metaTitle,metaDescription,ingredients,instructions,useVideo,videoIframe,posttags,recipeTime,title,url,collection,views,filters&_where=url=${url}'
```

**Exemplo de uso:**

```typescript
import { getPost } from './services/fetch';

getPost('como-fazer-bolo-de-chocolate').then((post) => {
  if (post) {
    console.log('Post encontrado:', post.title);
  } else {
    console.log('Post não encontrado');
  }
});
```

### fetchCategories

**Descrição:**

Busca todas as categorias disponíveis.

**Parâmetros:** Nenhum

**Endpoint:**

- `GET /api/dataentities/BC/search`

**Parâmetros de Query:**

- `_fields`: Campos específicos a retornar

**Retorno:**

- `Promise<Category[]>`: Array de categorias

**Transformação de Dados:**

```typescript
// Mapeia a resposta para o formato Category
return response.map((category: any) => ({
  id: category.id,
  categoryMetaDescription: category.categoryMetaDescription,
  categoryMetaTitle: category.categoryMetaTitle,
  createdIn: category.createdIn,
  description: category.description,
  imageDesktop: category.imageDesktop,
  imageMobile: category.imageMobile,
  filters: category.filters,
  name: category.name,
  url: category.url,
  image: category.imageDesktop || category.imageMobile, // Fallback
  order: category.order,
  updatedIn: category.updatedIn,
}));
```

**Exemplo de uso:**

```typescript
import { fetchCategories } from './services/fetch';

fetchCategories().then((categories) => {
  categories.forEach((cat) => console.log(cat.name));
});
```

### getSubcategoriesByCategory

**Descrição:** Busca subcategorias de uma categoria específica.

**Parâmetros:**

- `categoryId` (string): ID da categoria pai

**Endpoint:**

- `GET /api/dataentities/SC/search`

**Parâmetros de Query:**

- `_fields`: Campos específicos a retornar
- `_where`: Filtro por categoria pai (`parentCategoryId=${categoryId}`)

**Retorno:**

- Promise contendo array de subcategorias

**URL Completa:**

```typescript
'/api/dataentities/SC/search?_fields=id,name,url,description,imageDesktop,imageMobile,parentCategoryId&_where=parentCategoryId=${categoryId}'
```

**Exemplo de uso:**

```typescript
import { getSubcategoriesByCategory } from './services/fetch';

getSubcategoriesByCategory('cat123').then((subcategories) => {
  subcategories.forEach((sub) => console.log(sub.name));
});
```

### getCategoryByUrl

**Descrição:** Busca uma categoria pelo seu URL.

**Parâmetros:**

- `categoryUrl` (string): URL da categoria

**Endpoint:**

`GET /api/dataentities/BC/search`

**Parâmetros de Query:**

- `_fields`: Campos específicos a retornar
- `_where`: Filtro por URL (`url=${categoryUrl}`)

**Retorno:**

- Promise contendo o objeto da categoria

**URL Completa:**

```typescript
'/api/dataentities/BC/search?_fields=id,name,description,imageDesktop,imageMobile,categoryMetaTitle,categoryMetaDescription,filters&_where=url=${categoryUrl}';
```

**Exemplo de uso:**

```typescript
import { getCategoryByUrl } from './services/fetch';

getCategoryByUrl('sobremesas').then((categoria) => {
  console.log('Categoria encontrada:', categoria.name);
});
```

### getPostsById

**Descrição:** Busca um post pelo seu ID.

**Parâmetros:**

- `id` (number, padrão: 1): ID do post

**Endpoint**:

`GET /api/dataentities/BP/search`

**Parâmetros de Query:**

- `_fields`: Campos específicos a retornar

- `_where_`: Filtro por ID (`id=${id}`)

**Retorno:**

- Promise contendo o post

**URL Completa::**

```typescript
'/api/dataentities/BP/search?_fields=useVideo,videoIframe,imageCard,views,title,url,id,createdIn,filters&_where=id=${id}';
```

**Exemplo de uso:**

```typescript
import { getPostsById } from './services/fetch';

getPostsById(42).then((post) => {
  console.log('Post encontrado:', post.title);
});
```

### getPosts

**Descrição:** Busca posts com paginação e filtros.

**Parâmetros:**

- `start` (number, padrão: 0): Índice inicial para paginação
- `orderName` (string, padrão: 'createdIn'): Campo para ordenação
- `orderType` (string, padrão: 'DESC'): Tipo de ordenação (ASC/DESC)
- `filterCategory` (string, padrão: ''): Filtro por categoria

**Endpoint:**

`GET /api/dataentities/BP/search`

**Parâmetros de Query:**

- `_fields:` Campos específicos a retornar

- `categories:` Filtro por categoria (`${filterCategory} usa wildcard`)

- `_sort:` Ordenação (`${orderName} ${orderType}`)

**Retorno:**

- Promise contendo array de posts

**URL Completa:**

```typescript
'/api/dataentities/BP/search?categories=*${filterCategory}*&_fields=imageCard,title,url,id,createdIn,categories,posttags,views,videoIframe,useVideo,filters&_sort=${orderName} ${orderType}';
```

**Paginação:**

```typescript
headers: { 'REST-Range': `resources=${start}-${start + 12}` }
// Ex: start=0 → resources=0-12 (13 itens)
// Ex: start=12 → resources=12-24 (13 itens)
```

**Exemplo de uso:**

```typescript
import { getPosts } from './services/fetch';

const fetch =
  category.name === defaultCategory.name
    ? getPosts(postCount, 'createdIn', 'DESC', '*')
    : getPosts(postCount, 'createdIn', 'DESC', category.name);
```

### getPostsByCategory

**Descrição:**

Busca posts por nome de categoria.

**Parâmetros:**

- `categoryName` (string): Nome da categoria

**Retorno:**

- Promise contendo array de posts

**Endpoint:**

`GET /api/dataentities/BP/search`

**Casos Especiais:**

- `categoryName === 'Todas as categorias'`: Busca todos os posts (`categories=*`)

- Outros casos: Filtra por categoria específica (`categories=*${categoryName}*`)

**URL para "Todas as categorias":**

```typescript
/api/dataentities/BP/search?categories=*&_fields=imageCard,title,url,id,posttags,views,createdIn,categories,filters,videoIframe,useVideo
```

**URL para categoria específica:**

```typescript
/api/dataentities/BP/search?categories=*${categoryName}*&_fields=imageCard,title,url,id,createdIn,categories,posttags,views,filters,videoIframe,useVideo
```

**Exemplo de uso:**

```typescript
import { getPostsByCategory } from './services/fetch';

useEffect(() => {
  if (!category?.name) return;
  getPostsByCategory(category.name).then(setPosts);
}, [category?.name]);
```

### patchIncreasePostViews

**Descrição:** Incrementa o contador de visualizações de um post.

**Endpoint:** 

`PATCH /api/dataentities/BP/documents/${id}`

**Body:**

JSON com o novo valor de views

**Parâmetros:**

- `id` (string): ID do post
- `views` (number): Número atual de visualizações

**Retorno:**

- Promise da requisição PATCH

**Exemplo de uso:**

```typescript
import { patchIncreasePostViews } from './services/fetch';

// Supondo que você tenha um post com 100 visualizações
patchIncreasePostViews('post123', 100).then(() => {
  console.log('Visualizações atualizadas');
});
```

### getMostViewedPost

**Descrição:** Busca o post mais visualizado.

**Parâmetros:** Nenhum

**Endpoint:**

`GET /api/dataentities/BP/search`

**Parâmetros de Query:**

- `_fields:` Campos específicos a retornar

- `_sort:` Ordenação por views decrescente (`views DESC`)

**Retorno:**

- Promise contendo o post mais visualizado

**URL Completa:**

```typescript
'/api/dataentities/BP/search?_fields=id,url,views,title,description,imageDesktop,imageMobile,imageCard,brand,category,categories,posttags,collection,filters&_sort=views DESC'
```

**Headers:**

```typescript
{
  'REST-Range': 'resources=0-1' // Apenas o primeiro (mais visualizado)
}
```

**Exemplo de uso:**

```typescript
import { getMostViewedPost } from './services/fetch';

getMostViewedPost().then((post) => {
  if (post) {
    console.log('Post mais visualizado:', post.title);
  }
});
```

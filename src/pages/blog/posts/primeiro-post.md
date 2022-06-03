---
# src/pages/post/blog-post.md
layout: ../../../layouts/Post.astro
title: Primeiro Post
draft: true
---

Nessa documentação você vai encontrar tudo que pode precisar para construir aplicações para a web com Leme JS.

Logo a seguir está o passo a passo para dominar os recursos necessários para construir aplicações SPA.


    
## Estrutura do componente

Aplicações construídas com Leme JS podem fazer uso de componentes com os recursos abaixo:

- Componentes
    - eventos
    - hooks
    - métodos
    - componentes filhos

- Gerenciamento de estado local e global
    - Objetos observáveis

- Comunicação entre componentes
    - Por eventos
    - Por observadores

- Navegação
    - Rotas


### Funções como componentes

Para Leme JS componentes são apenas funções que recebem parametros e retornam objetos.

```javascript
// index.js

import { observableFactory } from 'lemejs'

import template from './template'
import styles from './styles'

export const appHelloWorld = ({ props }) => {

    const state = observableFactory({ title: 'Olá!' })

    return { state, template, styles }
}

```

Acima o arquivo principal, onde a lógica do componente deve ser escrita.

#### Template do componente

```javascript
//template.js

const template = ({ state, props, html }) => html`
    <h1>Hello, ${title}</h1>
`

```

Acima o arquivo de template, onde toda a estrutura html deve ser escrita.

#### CONTROLADOR DO COMPONENTE

```javascript
//styles.css

const styles = ({ ctx, props, css }) => css`
    ${ctx} h1 { color: blue }
`

```

Acima o arquivo de estilos css, onde toda a configuração visual deve ser escrita.

*Você pode estar pensando que essa quantidade de código é grande para um componente tão básico.  Mas, há um bom motivo para isso...* 

> *LEME JS não faz mágica, não esconde nada de você*.

#### 1 - NOME DO COMPONENTE

Componentes para *Leme JS* são apenas funções e por isso o nome de cada função de componente é muito importante, pois, é através desse nome que a tag html do componente será definida.
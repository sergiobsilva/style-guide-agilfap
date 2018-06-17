CSS Style Guide AgilFAP
===============

## Índice

  1. [Introdução](#introdução)
  2. [Espaços em Branco](#espaços-em-branco)
  3. [Regras](#regras)
  4. [Declarações](#declarações)
  5. [Seletores](#seletores)
     5.1. [Recomendações](#recomendações)
     5.2. [Formatação](#formatação)
  6. [Propriedades e Variaveis](#propriedades-e-variaveis)
     6.1. [Recomendações](#recomendações)
  7. [BEM](#bem)
     7.1. [Boas Práticas de BEM](#boas-práticas-de-bem)
  8. [Media Queries](#media-queries)
  9. [Regras de Importação com (@)](#regras-de-importação-com-@)
  10. [Comentários](#comentários)
     10.1. [Comentários de Cabeçalho](#comentários-de-cabeçalho)
     10.2. [Comentários de Referência](#comentários-de-referência)
     10.3. [Comentários de Tag](comentários-de-tag)
     10.4. [Comentários de Sessão](#comentários-de-sessão)
  11. [Apêndice: SASS](#apêndice-sass)
     11.1. [Sintaxe](#sintaxe)
     11.2. [Variáveis](#variáveis)
     11.3. [Regras @](#regras-@)
           11.3.1. [`@import`](#@import)
           11.3.2. [`@mixin`](#@mixin)
           11.3.3. [`@extend`](#@extend)
     11.4. [Regras Aninhadas](#regras-aninhadas)
     11.5. [Ordem interna de um arquivo .scss](#ordem-interna-de-um-arquivo-scss)
     11.6. [Experimental](#experimental)
     11.7. [Exceções](#exceções)
  12. [Ordem de Propriedades](#ordem-de-propriedades)
  13. [Profundidade do Seletor](#profundidade-do-seletor)
  14. [Formatação Básica do Código](#formatação-básica-do-código)
  15. [Cores](#cores)
  16. [Comentários](#comentários)
  17. [Estrutura de Construção do Sass](#estrutura-de-construção-do-sass)


## Introdução

Este documento define regras de formatação e métodos para escrever folhas de estilo. Destina-se a ajudá-lo a criar códigos legíveis, passíveis de manutenção, reutilizável e escalável.

Seguindo estas diretrizes, vamos:

- Melhore a qualidade do código.
- Encoraje a colaboração.
- Reduza o tempo necessário para entender o código existente.
- Aumentar a produtividade
- Mantenha nossa sanidade.

*É muito importante ter em mente que:*

- Consistência é fundamental. Cada linha de código deve parecer estar escrita
por uma única pessoa, independentemente do número de contribuintes e do seu pessoal
preferências.

- O código deve ser focado na legibilidade e simplicidade - mesmo ao custo de
repetição. Código inteligente que é difícil de entender geralmente faz mais mal
do que bom.

Essas diretrizes devem ser aprendidas, compreendidas e seguidas em todos os momentos.
Qualquer desvio deve ser plenamente justificado.

**[⬆ voltar para o topo](#índice)**

## Espaços em branco

- Use quatro espaços por nível de recuo.
- Remova todos os espaços em branco à direita.
- Sempre finalize os arquivos com uma nova linha.
- Use apenas uma linha em branco como separador.

```css
/*NÃO */

.foo {¤
——··font-weight: 900;¤
————color: #222;····¤¬
}——¤¬
```

```css
/* BEM MELHOR */

.foo {¬
····font-weight: 900;¬
····color: #222;¬
}¬
¬
```

**[⬆ voltar para o topo](#índice)**

## Regras

- Coloque o suporte de abertura ao lado do seletor.
- Use um espaço antes da chave de abertura.
- Coloque a chave de fechamento na mesma coluna que o primeiro caractere de uma regra.
- Separe cada regra por uma linha em branco.

```css
/* NÃO */

.foo
{
    color: #222;
}
.bar{color: #999;}
```

```css
/* BEM MELHOR */

.foo {
    color: #222;
}

.bar {
    color: #999;
}
```

- Use um espaço após a chave de abertura.
- Use um espaço antes da chave de fechamento.
- Não separe as regras por uma linha em branco.
- Não alinhe chaves.

```css
/* NÃO */

.foo{color: #000;}
.foobar {color: #222;}

.bar    { color: #444; }
.barfoo { color: #666; }
```

```css
/* BEM MELHOR */

.foo { color: #000; }
.foobar { color: #222; }
.bar { color: #444; }
.barfoo { color: #666; }


Não indente regras com a intenção de * replicar * a estrutura DOM.
Isso tornará seu código menos flexível e introduzirá uma carga de manutenção.

```css
/* NÃO */

.foo {
    color: #222;
}

    .foo__bar {
        color: #444;
    }

        .foo__baz {
            color: #666;
        }
```

```css
/* BEM MELHOR */

.foo {
    color: #222;
}

.foo__bar {
    color: #444;
}

.foo__baz {
    color: #666;
}
```

**[⬆ voltar para o topo](#índice)**

## Declarações

- Defina uma declaração por linha.
- Coloque um espaço após o cólon.
- Sempre termine declarações com um ponto e vírgula.
- Não coloque espaços antes dos dois pontos ou do ponto-e-vírgula.

```css
/* NÃO */

.foo {
    font-weight:900;
    color : #222 ;
}

.bar {
    padding:10px; margin:0
}
```

```css
/* BEM MELHOR */

.foo {
    font-weight: 900;
    color: #222;
}

.bar {
    padding: 10px;
    margin: 0;
}
```

**[⬆ voltar para o topo](#índice)**

## Seletores

- Coloque um seletor por linha nos seletores agrupados.
- Cite valores de atributos usando aspas simples.

```css
/* NÃO */

.foo, .bar {
    color: #222;
}

.foobar[attr=val] {
    color: #444;
}
```

```css
/* BEM MELHOR */

.foo,
.bar {
    color: #222;
}

.foobar[attr='val'] {
    color: #444;
}
```

**[⬆ voltar para o topo](#índice)**

### Recomendações

Nunca use seletores de identificação.

```css
/* NÃO */

#foo {
    color: #222;
}
```

```css
/* BEM MELHOR */

.foo {
    color: #222;
}
```

  Evite os seletores de tipos o máximo que puder.

```css
/* NÃO */

.foo h1 {
    color: #222;
}
```

```css
/* BEM MELHOR */

.foo-heading {
    color: #222;
}
```

**[⬆ voltar para o topo](#índice)**

### Formatação

- Todos os seletores são minúsculas, hífen separado, também conhecido como "caso da coluna vertebral", por exemplo. `.my-class-name`
-  Sempre prefiro o comentário de //-duplo da Sass, mesmo para comentários de bloco
- Evite especificar unidades para valores zero, por ex. `margin: 0;` em vez de `margin: 0px;`
- Sempre adicione um ponto e vírgula ao final de uma declaração de propriedade / valor
- Use zeros à esquerda para valores decimais: opacidade: 0,4; em vez de opacidade: 0,4;
- Coloque espaços antes e depois do seletor filho `div> span` em vez de` div> span`

**[⬆ voltar para o topo](#índice)**

## Propriedades e Variaveis

  Não especifique unidades de comprimento para valores zero.

```css
/* NÃO */

.foo {
    padding: 0px 20px;
}
```

```css
/* BEM MELHOR */

.foo {
    padding: 0 20px;
}
```
Sempre especifique zeros à esquerda em números fracionários.

```css
/* NÃO */

.foo {
    top: .25%;
    left: -.5%;
}
```

```css
/* BEM MELHOR */

.foo {
    top: 0.25%;
    left: -0.5%;
}
```

Use minúsculas para valores hexadecimais e notação abreviada quando permitido.

```css
/* NÃO */

.foo {
    background: #ffffff;
    border-color: #F3F3F3;
}
```

```css
/* BEM MELHOR */

.foo {
    background: #fff;
    border-color: #f3f3f3;
}
```

Cite valores de URL usando aspas simples.

```css
/* NÃO */

.foo {
    background: url(../images/image.png);
}
```

```css
/* BEM MELHOR */

.foo {
    background: url('../images/foobar.png');
}
```

  Cite os nomes das famílias de fontes que contenham espaços em branco usando aspas simples.

```css
/* NÃO */

.foo {
    font-family: "Times New Roman", Times, serif;
}
```

```css
/* BEM MELHOR */

.foo {
    font-family: 'Times New Roman', Times, serif;
}
```

  Não coloque espaços antes do parêntese de abertura nem após o fechamento parênteses de uma função.
```css
/* NÃO */

.foo {
    width: calc( 20% - 5px );
    background: rgba( 0, 0, 0, 0.6 );
}
```

```css
/* BEM MELHOR */

.foo {
    width: calc(20% - 5px);
    background: rgba(0, 0, 0, 0.6);
}
```

Inclua um espaço após cada vírgula em valores separados por vírgulas.

```css
/* NÃO */

.foo {
    font-family: 'Times New Roman',Times,serif;
    background: rgba(0,0,0,0.6);
}
```

```css
/* BEM MELHOR */

.foo {
    font-family: 'Times New Roman', Times, serif;
    background: rgba(0, 0, 0, 0.6);
}
```

Um conjunto de valores separados por vírgulas longos deve ser organizado em várias linhas.
- Coloque o primeiro conjunto na mesma linha que a propriedade.
- Coloque o seguinte conjunto / s em uma nova linha usando um nível extra de recuo.

```css
/* NÃO */

.foo {
    box-shadow: inset 0 0 4px rgba(17, 17, 17, 0.6), 0 0 8px rgba(0, 0, 0, 0.6);
    background: url('../images/foobar.png') repeat-y,
    url('../images/barfoo.png') repeat-x;
}
```

```css
/* BEM MELHOR */

.foo {
    box-shadow: inset 0 0 4px rgba(17, 17, 17, 0.6),
        0 0 8px rgba(0, 0, 0, 0.6);
    background: url('../images/foobar.png') repeat-y,
        url('../images/barfoo.png') repeat-x;
}
```

**[⬆ voltar para o topo](#índice)**

### Recomendações

Quando possível, use propriedades abreviadas.

```css
/* NÃO */

.foo {
    padding-top: 0;
    padding-right: 10px;
    padding-bottom: 20px;
    padding-left: 10px;
}
```

```css
/* BEM MELHOR */

.foo {
    padding: 0 10px 20px;
}
```

Não use valores de palavra-chave quando o mesmo resultado puder ser alcançado usando um valor explícito.

```css
/* NÃO */

.foo {
    background: white;
    border-width: medium;
}
```

```css
/* BEM MELHOR */

.foo {
    background: #fff;
    border-width: 4px;
}
```
Nunca use `! Important` para resolver um problema de especificidade.

```css
/* NÃO */

.foo {
    float: left !important;
}
```

```css
/* BEM MELHOR */

.foo.bar {
    float: left;
}
```

**[⬆ voltar para o topo](#índice)**

## BEM

Block: Nomes únicos e significativos para uma unidade lógica de estilo. Evite taquigrafia excessiva.
- Bom: `.alert-box` or `.recents-intro` or `.button`
- Ruim: `.feature` or `.content` or `.btn`

Elemento: estilos que se aplicam apenas a filhos de um bloco. Elementos também podem ser blocos em si. O nome da classe é uma concatenação do nome do bloco, dois sublinhados e o nome do elemento. Exemplos:
- `.alert-box__close`
- `.expanding-section__section`

  Modificador: substitui ou estende os estilos base de um bloco ou elemento com estilos modificadores. O nome da classe é uma concatenação do nome do bloco (ou elemento), dois hífens e o nome do modificador. Exemplos:
- `.alert-box--success`
- `.expanding-section--expanded`

**[⬆ voltar para o topo](#índice)**

### Boas Práticas de BEM

Não utilizar modificadores de bloco `@ extend` com a base do bloco.
- Bom: `<div class="my-block my-block--modifier">`
- Ruim: `<div class="my-block--modifier">`

Não crie elementos dentro de elementos. Se você está precisando disso, considere converter seu elemento em um bloco.
- Ruim: `.alert-box__close__button`

Escolha seus modificadores com sabedoria. Essas duas regras têm um significado muito diferente:

```scss
.block--modifier .block__element { color: red; }
.block__element--modifier { color: red; }
```

## Media Queries

As consultas de mídia devem estar no seletor CSS, de acordo com o SMACSS

```scss
.selector {
      float: left;

      @media only screen and (max-width: 767px) {
        float: none;
      }
}
```
Criar variáveis ​​para pontos de interrupção usados ​​com freqüência

```scss
$SCREEN_SM_MAX: "max-width: 767px";

.selector {
      float: left;

      @media only screen and ($SCREEN_SM_MAX) {
        float: none;
      }
}
```

**[⬆ voltar para o topo](#índice)**

## Regras de Importação com (@)

As regras que contêm declarações diretamente devem seguir o mesmo padrão que se aplica a qualquer outra regra.

```css
/* NÃO */

@font-face {
    font-family:Foobar;
    src:local(Foobar),url(../webfonts/foobar.woff) format(woff);
    font-weight:bold;font-style:normal}
```

```css
/* BEM MELHOR */

@font-face {
    font-family: 'Foobar';
    src: local('Foobar'),
        url('../webfonts/foobar.woff') format('woff');
    font-weight: 700;
    font-style: normal;
}
```
Regras aninhadas dentro de regras devem ser recuadas corretamente.

- Não deixe uma linha em branco antes da primeira regra.
- Não deixe uma linha em branco depois da última regra.

```css
/* NÃO */

@media(min-width:768px){

.foo {
    font-weight: 900;
    color: #222;
}

.bar {
    padding: 10px;
    margin: 0;
}

}
```

```css
/* BEM MELHOR */

@media (min-width: 768px) {
    .foo {
        font-weight: 900;
        color: #222;
    }

    .bar {
        padding: 10px;
        margin: 0;
    }
}
```

Propriedades e declarações aninhadas devem aparecer na seguinte ordem, com quebras de linha entre grupos:

1. Qualquer regra `@`
2. Propriedades de layout e modelo de caixa - margem, preenchimento, tamanho da caixa, estouro, posição, exibição, largura / altura etc.
3. Propriedades Tipográficas - Por exemplo. fonte- , altura da linha, espaçamento entre letras, texto, etc.
4. Propriedades estilísticas - cor, fundo- , animação, borda, etc.
5. propriedades da interface do usuário - aparência, cursor, seleção de usuário, eventos de ponteiro, etc.
6. Pseudo-elementos - :: after, :: before, :: selection, etc.
7. Pseudo-seletores -: foco, foco, ativo, etc.
8. Classes modificadoras 9. Elementos aninhados

Veja um exemplo abrangente:

```scss
.c-btn {
    @extend %link--plain;

    display: inline-block;
    padding: 6px 12px;

    text-align: center;
    font-weight: 600;

    background-color: color(blue);
    border-radius: 3px;
    color: white;

    &::before {
        content: '';
    }

    &:focus, &:hover {
        box-shadow: 0 0 0 1px color(blue, .3);
    }

    &--big {
        padding: 12px 24px;
    }

    > .c-icon {
        margin-right: 6px;
    }
}
```

**[⬆ voltar para o topo](#índice)**

## Comentários

Use [sentence case](http://en.wiktionary.org/wiki/sentence_case) para todos os tipos de comentários.

```css
/* Comentário de linha única. */

/**
 * Comentário de várias linhas.
 */
```

*Use comentários de linha única nativos ao trabalhar com o Sass.*

```scss
// Comentário de linha única.

////
// Comentário de várias linhas.
//
```

**[⬆ voltar para o topo](#índice)**

### Comentários de Cabeçalho

Use isso como um cabeçalho para cada folha de estilo.

```css
/**
 * Nome do Componente
 * Pequena descrição do que o componente faz, onde é usado, etc.
 */
```

*Use comentários de linha única nativos ao trabalhar com o Sass.*

```scss
////
// Nome do Componente
// Pequena descrição do que o componente faz, onde é usado, etc.
//
```

**[⬆ voltar para o topo](#índice)**

### Comentários de Referência

Para evitar interferir na leitura do código, tente usar os “comentários de referência”.

```css
/**
 * 1. Override inherited value.
 * 2. Fallback for browsers that don’t support `rgba()`.
 */

.foo {
    padding: 0; /* 1 */
    background: #222; /* 2 */
    background: rgba(0, 0, 0, 0.6);
}
```

*Use comentários de linha única nativos ao trabalhar com o Sass.*

```scss
////
// 1. Substituir valor herdado.
// 2. Retorno para navegadores que não suportam `rgba()`.
//

.foo {
    padding: 0; // 1
    background: #222; // 2
    background: rgba(0, 0, 0, 0.6);
}
```

**[⬆ voltar para o topo](#índice)**

### Comentários de Tag

- A única tag aceita é: `TODO`.
- Use letras maiúsculas para o nome da tag.
- Coloque dois pontos após o final do nome da tag.
- Coloque um espaço depois dos dois pontos.

```css
.foo {
    /* TODO: add fallback. */
    background: rgba(0, 0, 0, 0.6);
}
```

*Use comentários de linha única nativos ao trabalhar com o Sass.*

```scss
.foo {
    // TODO: add fallback.
    background: rgba(0, 0, 0, 0.6);
}
```
**[⬆ voltar para o topo](#índice)**

### Comentários de Sessão

Quando apropriado, divida o código em seções significativas.

```css
/* First level
   ---------------------------------------------------------------- */

/* Second level
   -------------------------------------------- */
```

*Use comentários de linha única nativos ao trabalhar com o Sass.*

```scss
// First level
// ---------------------------------------------------------------- //

// Second level
// -------------------------------------------- //
```

**[⬆ voltar para o topo](#índice)**

## Apêndice: SASS

### Sintaxe

Sempre use o
[SCSS syntax](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#syntax).

Isso requer o uso da extensão de arquivo `.scss`.

### Variáveis

- Use variáveis ​​- pelo menos - para cores e tamanho da fonte.
- Use `! Default` somente quando houver uma variável que possa ser modificada.

### Regras @

#### `@import`

- Defina uma declaração `@ import` por linha.
- Cite os nomes dos arquivos usando aspas simples.
- Não inclua o sublinhado à esquerda ao importar um parcial.
- Não inclua a extensão de arquivo `.scss`.

```scss
// NÃO

@import "_foo.scss", "_bar.scss";
```

```scss
// BEM MELHOR

@import 'foo';
@import 'bar';
```

#### `@mixin`

Use um `@ mixin` sempre que quiser gerar seções de código reutilizáveis.

#### `@extend`

Evite usar o `@ extend`. Tente usar um `@ mixin` em vez disso.

### Regras Aninhadas

  - Use apenas aninhamento quando absolutamente necessário.
  - Nunca aninhe mais de três níveis de profundidade.
  - Separe cada regra aninhada por uma linha em branco.

```scss
// NÃO

.foo {
    color: #000;
    .bar {
        color: #222;
        .baz {
            color: #444;
            .qux {
                color: #666;
                .quux {
                    color: #999;
                }
            }
        }
    }
}
```

```scss
// BEM MELHOR

.baz {
    color: #444;

    .qux {
        color: #666;

        .quux {
            color: #999;
        }
    }
}
```
Nunca aninhe dentro de regras vazias.

```scss
// NÃO

.foo {
    .bar {
        color: #222;
    }
}
```

```scss
// BEM MELHOR

.foo .bar {
    color: #222;
}
```

Nunca gere nomes compostos usando o seletor pai.

```scss
// NÃO

.foo {
    color: #000;

    &__bar {
        color: #222;
    }

    &--baz {
        color: #444;
    }
}
```

```scss
// BEM MELHOR

.foo {
    color: #000;
}

.foo__bar {
    color: #222;
}

.foo--baz {
    color: #444;
}
```
**[⬆ voltar para o topo](#índice)**

### Ordem interna de um arquivo .scss

1. Importações
2. Variáveis
3. Estilos Base
4. Estilos Experimentais

Exemplo:

```scss
//------------------------------
// Modal
//------------------------------

@import "../constants";
@import "../helpers";

$DBmodal-namespace: "c-modal" !default;
$DBmodal-padding: 32px;

$DBmodal-background: #fff !default;
$DBmodal-background-alt: color(gray, x-light) !default;

.o-modal { ... }

// Many lines later...

// EXPERIMENT: experiment-rule-name
.o-modal--experiment { ... }
// END EXPERIMENT: experiment-rule-name

## Apêndice: Prefixo de API

Nunca use os prefixos do fornecedor diretamente no código-fonte.

- Use [Autoprefixer](https://github.com/postcss/autoprefixer).
- Se o Autoprefixer não estiver disponível, você poderá usar um `@mixin`.

Exemplo:

```scss
// NÃO
.c-link {
  color: #007ee5;
  border-color: #FFF;
  background-color: rgba(#FFF, .0625);
}

// MUITO MELHOR
.c-link {
  color: color(blue);
  border-color: #ffffff;
  background-color: rgba(#ffffff, 0.1);
}
```
**[⬆ voltar para o topo](#índice)**

### Experimental

Envolva estilos de experimentos com comentários:

```scss
// EXPERIMENT: experiment-rule-name
.stuff { ... }
// END EXPERIMENT: experiment-rule-name
```

----------
**[⬆ voltar para o topo](#índice)**

### Exceções

Quando determinada propriedade não é padrão, o Autoprefixer não executará nenhuma ação.

Nessas situações, sempre deixe um comentário explicando por que você está usando essa propriedade. Isso gerará código mais fácil de entender e evitar remoções acidentais.

```scss
// NÃO

.foo {
    color: #000;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
```

```scss
// BEM MELHOR

////
// 1. Modifique o modo de suavização de fonte padrão. Propriedades não padronizadas;
// o uso explícito de prefixos de fornecedores é necessário.
//

.foo {
    color: #000;
    -webkit-font-smoothing: antialiased; // 1
    -moz-osx-font-smoothing: grayscale; // 1
}
```

**[⬆ voltar para o topo](#índice)**

## Ordem de Propriedades

Para evitarmos desrespeito a hierarquias de CSS, nunca é demais lembrar que as mesmas afetam os elementos de dentro para fora, então, sabendo disso, segue-se a regra de respeito de inline / incorporado / externo / linkados / importados respectivamente, sendo assim os estilos que mais afetarão os elementos são os estilos em linha, logo, deverão ser evitados se escritos em código estático como HTML, visto que esta atribuição já caberá aos frameworks que serão utilizados no projeto (Angular 6). Então, seguindo uma regra básica para o nosso projeto, a primeira coisa a ser colocada nos códigos serão o tamanho da fonte (que afetará a altura) em seguida a altura da linha que esta diretamente relacionada aos elementos tamanho da fonte ou tamanho da fonte herdada (dependendo da unidade que for usada). O próximo item é o comprimento do conteúdo determinado pelas propriedade Width e Height. Por último caso existam vão ser inseridos tamanho da borda, margem e o posicionamento das propriedades.

  -Propriedades de Texto

  ```css
  line-height
  font-* propriedades
  demais caracteristicas em ordem alfabética aqui
  ```

  - Box model

  ```css
  width
  height
  padding
  border
  margin
  ```

  - Display

  ```css
  display
  overflow (isso pode pertencer ao modelo de caixa)
  ```

  - Display

  ```css
  position
  top
  left
  ```

**[⬆ voltar para o topo](#índice)**


## Profundidade do Seletor

Os únicos casos em que são recomendados mais de 3 seletores em profundidade é para: hover & : focus. Sabemos que a medida que o código cresce isso fica ainda mais difícil, mas quanto mais profundo for o aninhamento de seletores, mais problemas aparecerão no projeto. Então, caso você possa, evite especificidades demais, isso deixará nosso código mais organizado e teremos que fazer menos estilos em inline para resolver certos problemas.

**[⬆ voltar para o topo](#índice)**


## Formatação Básica de Código

 Use dois espaços para recuo.

Adicione uma linha de espaço em branco entre cada bloco seletor + propriedades.

  ```css
  // NÃO
  .header {
    …
  }
  .logo-bar {
    …
    a {…}
  }

  // BEM MELHOR
  .header {
    …
  }
  .logo-bar {
    …

    a {
      …
    }
   }
  ```

**[⬆ voltar para o topo](#índice)**


## Cores

  Todos os valores de cores hexadecimais devem usar letras minúsculas.

As cores devem ser transformadas em variáveis ​​para serem reutilizadas.

**[⬆ voltar para o topo](#índice)**

## Comentários

Os comentários relacionados ao código que é renderizado diretamente devem usar a sintaxe de estrela de barra padrão.

  ```css
  /* Headings */
  h1 {…}
  h2 {…}
  ```


  Comentários relacionados a esse código ou arquivos que não são renderizados diretamente devem usar o sytnax de barra dupla. Isso deve ser usado em locais onde podemos rotular um grupo de variáveis, ou um mixin que será usado posteriormente, ou um arquivo que seja uma biblioteca de tais coisas.

  ```css
  // ===================================================================
  //  Copyright 2018 AgilFAP. Todos os direitos reservados.
  //
  //  Variáveis
  //
  //  Conjunto base de variáveis ​​para uso com o projeto
  //  ==================================================================
  ```

  // cores
  $agilFapAzulPrincipal: #183a84;

**[⬆ voltar para o topo](#índice)**

## Estrutura de Construção do SASS

 Veja como os engenheiros do Front End do AgilFAP manipulam uma estrutura de construção simples para arquivos SASS.

[AgilFAP Estrutura de Construção do SASS](https://github.com/evernote/sass-build-structure)

**[⬆ voltar para o topo](#índice)**

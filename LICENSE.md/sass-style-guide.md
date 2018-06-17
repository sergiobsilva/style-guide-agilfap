AgilFAP Estrutura SASS Boilerplate
=============

[![npm version](https://badge.fury.io/js/evernote-sass.svg)](http://badge.fury.io/js/evernote-sass)

Depois de ler o livro [SMACSS] (http://smacss.com/) e achar muito útil, a equipe de Front End do Evernote usou algumas das ideias em nossa versão SASS. Descobrimos que separar os arquivos SASS em diretórios (Base, Layout, Modules e Views) ajuda a organizar nossos arquivos em um projeto e compila o CSS em um arquivo limpo e lógico. Cada página tem um arquivo SASS (.scss) criado que atua como um arquivo de projeto que importa os componentes modulares individuais de Base, Layout, Módulos e Modos de Exibição necessários para construir a página específica.

Esta metodologia de construção está sendo usada atualmente[Facepe.br](http://www.facepe.br/).

## Instalação

```js
npm install evernote-sass -g
```

## Uso

Execute `` `evernotesass``` em um diretório onde você gostaria de usar o build do Evernote Sass.

Para criar novos arquivos Sass individuais, execute `` `evernotesass-page name = nome_do_arquivo path = Caminho-Sass-directory```. Se o nome não for definido, o arquivo será nomeado 'page' e se o caminho não for definido, ele assumirá que o diretório é 'sass'.

Para criar novos arquivos SASS individuais, execute `` `evernotesass-page name = nome_do_arquivo path = Caminho-Sass-directory```. Se o nome não for definido, o arquivo será nomeado 'page' e se o caminho não for definido, ele assumirá que o diretório é 'sass'.

Diretórios SASS
----------

1.  Base

O diretório base contém estilos que ajudam a iniciar um projeto. O diretório base pode conter o seguinte tipo de arquivos SASS:
	* Vendor dependancies (Compass, Foundation)
	* Authored dependancies (Mixins, variables, Extends)
	* Fonts
	* Reset

2.  Layout

	O diretório de layout contém estilos que são grandes contêineres de uma página. Este diretório pode incluir arquivos SASS como:
	* Responsive Grid
	* Page specific layouts

3.  Módulos

	  O diretório de módulos provavelmente conterá a maior parte dos seus arquivos SASS. Uma página pode consistir em vários módulos e deve ser estilizada individualmente. Esses módulos podem incluir arquivos como:
	* Header
	* Footer
	* Navigation
	* Content Block

4.  Views

	O diretório de visualizações contém todos os estilos específicos que uma página pode precisar alterar do layout ou módulos genéricos. Por exemplo, o cabeçalho em seu site pode ser verde em todo o site ou aplicativo, mas em uma página específica você deseja que ele mude para um plano de fundo azul que é onde os arquivos de visualizações virão.

##  Removendo módulos Sass não utilizados


Com a estrutura Sass do Evernote, encontramos muitos arquivos Sass em nossa compilação. Às vezes eles não são mais usados, então começamos a usar uma tarefa do Grunt chamada [Sassyclean] (https://github.com/ryanburgess/grunt-sassyclean) que ajuda a automatizar a remoção de módulos Sass antigos não utilizados.

## Regras

- Deve haver no máximo 2 arquivos CSS por página (isso evita solicitações HTTP)
- Uma linha para cada seletor ou regra
- Listar itens relacionados juntos
- Apenas ninho 3 níveis profundos
- Divida os arquivos em pequenos módulos (evite ter um arquivo SCSS com mais de 100 linhas)
- Evite usar IDs em todo o site. Use IDs para elementos pai. Exemplo: Cabeçalho, Rodapé, Principal. Usando classes evita ter que usar! Importante Seja generoso ao comentar
- Se uma classe pseudo `` `: hover``` for estilizada,` ``: focus``` também deve ser estilizada para acessibilidade.

## Comentário

- Usando "//" para seus comentários no SASS e eles não serão exibidos no CSS compilado


## Variáveis

- Quaisquer valores comumente usados ​​em toda a compilação SASS devem ser definidos como uma variável (fontes, cores, porcentagens, z-index)
- Todas as cores devem ser variáveis


## Ordem das Importações

- Dependências de fornecedores (bússola)
- Dependências autorizadas (Mixins, variáveis)
- Estilos base (redefinir, fontes, tipografia)
- Estilos de Layout
- Estilos de Módulos
- Estilos de Vistas

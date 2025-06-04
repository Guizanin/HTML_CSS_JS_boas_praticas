# 🇧🇷 CSS
Este é o estilo do nosso site, como ele se apresentará aos nossos olhos. O CSS requer um pouco de cuidado ao ser criado, pois um simples estilo mal aplicado, pode 'quebrar' a aparência do nosso querido layout, então cuidado ao criar estilos mais abrangentes, ou até globais. Abaixo listarei algumas dicas, conhecimento que adquiri ao longo da minha jornada Frontend, sobre o padrão BEM-CSS eu particularmente nunca gostei de utilizar, acho confuso a utilização do método além de criar classes gigantescas, se diversas pessoas o utilizam... legal, mas eu não gosto, sempre criei meu CSS de acordo com minhas bases pessoais. Não vou abordar a utilização de frameworks estilo [Bootstrap](https://getbootstrap.com/), pois eles já vem com padrões e estilos, e eu consideraria apenas alterar as cores para adapatar ao projeto que irá utilizá-lo.

## Tenha um RESET-CSS
Na internet encontram-se arquivos que reseta algumas configurações padrões que já vem no CSS, como por exemplo, padding, margins, buttons, etc. Esse arquivo é bem legal pois com ele você vai retirar essas pré-difinições que teremos no CSS. 
Como é uma arquivo que você irá baixar, você poderá abrí-lo e editá-lo como desejar 😊 

Abaixo temos um arquivo de reset do [Meyerweb](https://meyerweb.com/eric/tools/css/reset/) como exemplo. Acredito que sejá uma ótima base a ser seguida, nele você pode alterar ou incrementar o que achar mais relevante ao seu projeto. Eu acrescentava um reset no estilo de botões e links, além também do tipo de fonte usada globalmente no projeto, assim como as váriações de títulos, sub-títulos. Enfim, era um arquivo de reset e set global de estilos dos meus projetos.
```css
/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
```

## Elementos globais
Acabamos de falar em resetar nosso css e configurar alguns estilos mais genéricos, agora podemos pensar em no CSS padrão para nossos elementos, tais como ```<p>```, ```<button>```, ```<a>```, etc... só não esqueça que ```<a>``` não é ```<button>```, são elementos com finalidades diferentes. Você pode criar uma sessão no seu arquivo para conter esses estilos globais, ou se possível, criar um arquivo específico para eles, melhorando sua organização.

## Seletores CSS
A utilização de seletores CSS vai auxiliar muito na hora de estilizar seus elementos, pois muitas das vezes você não precisará criar alguma classe específica para o elemento, podendo estilizá-lo através de um selector.
Aqui no site da [Rocketseat](https://www.rocketseat.com.br/blog/artigos/post/seletores-css), temos uma boa descrição dos seletores, você não é obrigado a saber tudo, basta pensar se há alguma maneira de fazer usando seletores, mas claro... se ficar melhor criar a classe, pode criar, tudo que passo aqui são minhas esperiências.

Abaixo um exemplo dos mais conhecidos, onde dizemos que todos os ```<a>``` que estiverem no estado <i>":hover"</i> terão a cor de fonte purple. 

```css
a:hover {
  color: purple;
}
```

Aqui algo um pouco mais avançado, utilizando selectores, código está no meu [codepen](https://codepen.io/guizanin/pen/bGGZNNP), dê uma espiada lá como criei um checkbox utilizando somente HTML + CSS.

```css
.wrap-check input:checked ~ .fundo{background: #2ecc71;transition:1s}
```
Aqui buscamos através dos ```input:checked``` todos irmãos ```.fundo``` e os estilizamos.

Com seletores conseguimos buscar elementos tanto verticalemente (de cima para baixo), quanto lateralmente, tornando mais flexível e fácil aplicar nossos estilos.
Aproveitando o assuntos dos seletores, juntos deles eu utilizava quando dava é claro, classes mais genéricas, tipo "icon", "button", etc, ou até de tags dos elementos. Assim não precisava "pensar" em um nome de classe para o elemento e me preocuva mais com a estrutura do estilo, além de tornar o desenvolvimento mais rápido, mas claro, quando necessitava de algo mais específico eu criava.

```html
<ul>
  <li>
    <h2>sub-titulo</h2>
    <p>texto...</p>
    <button class="btn">click aqui</button>
    <ul>
      <li>
        <button class="btn btn-close">
          fechar
          <i class="icon" data-icon="close"></i>
        </button>
      </li>
  <li>
<ul>
```
```css
ul > li button {
  text-align: center
  outros estilos...
}
```

o CSS acima, estiliza o ```<button class='btn'>click aqui</button>``` que está dentro do primeiro conjunto de ```<li>``` devido ao [selector ">" de filho direto](https://www.rocketseat.com.br/blog/artigos/post/seletores-css#932d5d8d0a944a8095f7f417e9d75677) e não aplicando aos ```<button>fechar</button>```
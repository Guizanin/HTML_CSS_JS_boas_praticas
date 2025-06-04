# 🇺🇸 CSS
CSS defines the style of our website and how it looks. It requires attention because poorly applied styles can "break" the appearance of the layout. Be cautious when creating general or global styles. Below, I’ll share some tips and knowledge I’ve gained during my Frontend journey. Regarding the BEM-CSS pattern, I personally don’t like using it. I find it confusing and it creates long class names. If others like it, that’s fine, but it’s not for me. I’ve always written CSS based on my personal preferences. I won’t cover style frameworks like [Bootstrap](https://getbootstrap.com/) because they already come with predefined patterns and styles. I’d only consider changing colors to adapt them to the project.

## Use a RESET-CSS
You can find files online that reset default CSS settings like padding, margins, buttons, etc. These files are useful because they remove predefined styles in CSS.  
Since it’s a file you download, you can open and edit it as you like 😊  

Below is an example of a reset file from [Meyerweb](https://meyerweb.com/eric/tools/css/reset/). I think it’s a great starting point. You can modify or add anything relevant to your project. I used to include resets for button and link styles, the global font for the project, and variations for titles and subtitles. In short, it was a reset and global style setup file for my projects.

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

## Global Elements
We just talked about resetting our CSS and setting up some more generic styles. Now we can think about the default CSS for our elements, such as ```<p>```, ```<button>```, ```<a>```, etc. Just don’t forget that ```<a>``` is not a ```<button>```. They are elements with different purposes. You can create a section in your file to hold these global styles, or, if possible, create a specific file for them to improve organization.

## CSS Selectors
Using CSS selectors will help a lot when styling your elements because, many times, you won’t need to create a specific class for an element. Instead, you can style it using a selector.  
On the [Rocketseat](https://www.rocketseat.com.br/blog/artigos/post/seletores-css) website, there’s a good description of selectors. You don’t need to know everything; just think about whether there’s a way to do it using selectors. But of course, if it’s better to create a class, go ahead. Everything I share here is based on my experiences.

Below is an example of one of the most well-known selectors, where we say that all ```<a>``` elements in the <i>":hover"</i> state will have the font color purple.

```css
a:hover {
  color: purple;
}
```

Here’s something a bit more advanced using selectors. The code is on my [codepen](https://codepen.io/guizanin/pen/bGGZNNP). Check it out to see how I created a checkbox using only HTML + CSS.

```css
.wrap-check input:checked ~ .fundo{background: #2ecc71;transition:1s}
```

Here, we target all siblings with the class ```.fundo``` through ```input:checked``` and style them.

With selectors, we can target elements both vertically (top to bottom) and laterally, making it more flexible and easier to apply our styles.

Taking advantage of the topic of selectors, I used to, whenever possible, use more generic classes like "icon," "button," etc., or even the tag names of elements. This way, I didn’t have to "think" of a class name for the element and could focus more on the structure of the style, making development faster. But of course, when something more specific was needed, I would create it.


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

The CSS above styles the ```<button class='btn'>click here</button>``` inside the first ```<li>``` due to the [direct child selector ">"](https://www.rocketseat.com.br/blog/artigos/post/seletores-css#932d5d8d0a944a8095f7f417e9d75677) and does not apply to the ```<button>close</button>```.
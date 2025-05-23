# 🇧🇷 HTML
As the foundation of our website, we must be careful in how we build it. Should we do everything carelessly? Yes, we can—HTML accepts everything. However, we wouldn't be coherent or semantic. Using HTML elements that clearly describe the meaning of a page’s content, rather than just using generic tags like ```<div>``` and ```<span>```, improves the readability and comprehension of the code for both humans and machines, such as browsers and search engines.

## Benefits of Semantic HTML:
#### Improves accessibility:
Semantic tags help people with disabilities—especially those using assistive technologies like screen readers—navigate and understand page content more easily.

#### Enhances Search Engine Optimization (SEO):
Search engines like Google can better understand a page's content and context, leading to more precise and relevant search results.

#### Improves code readability and maintainability:
Semantic tags make code more organized and easier to understand, facilitating future maintenance and updates.

#### Increases consistency:
Consistently using semantic tags ensures that the content’s meaning is clear and coherent throughout the page, enhancing the user experience.

### Examples of Semantic Tags:
```html
<header>: Defines the header of a page or section.  
<nav>: Defines the navigation section of the page.  
<article>: Defines an independent piece of content that makes sense on its own, such as a blog post.  
<section>: Defines a section within a document, like a topic or chapter.  
<aside>: Defines secondary or sidebar content.  
<footer>: Defines the footer of a page or section.  
<main>: Defines the main content of a page.  
<details>: Defines details that can be shown or hidden.  
<summary>: Defines a visible header for an element.  
<time>: Defines a date or time.
```

You may sometimes see ```<a>```, a tag used for links, being used as a button on some websites. However, for actual button functionality, the correct tag is ```<button>```. Or, as an unfortunate example, you might come across a website built almost entirely with ```<div>``` tags—titles, subtitles, paragraphs—all using div.

By applying the practice of Semantic HTML, you will notice as you develop that your code feels lighter and more structured, making it easier to understand and maintain while reaping all the benefits mentioned above.

I hope this brief article has provided some clarity and helps in structuring your code in some way.


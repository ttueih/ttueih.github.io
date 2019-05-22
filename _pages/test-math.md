---
title: Test math
tags: 
   - jekyll 
   - test
   - markdown
   - mathjax
date: 2019-05-20 15:06:26 +0100
description: To see how math is rendered with Jekyll.
---

There are two different ways to render \\( \LaTeX \\) on Jekyll, either using [**MathJaX**](https://www.mathjax.org) or [**KaTeX**](https://katex.org).
MathJaX is more popular and more powerful compared to KaTeX which is a relatively new library for math typesetting on web. 
However, KaTeX is way faster than MathJaX and is recommended for posts with the large number of mathematic content.

This Jekyll template integrates both of them along with [TikzJaX](https://github.com/kisonecat/tikzjax), for rendering Tikz diagram.
There are options to turn on/off MathJaX and TikzJaX in `_config.yml_`.

## KaTeX
KaTeX can be installed as a plugin to Jekyll using [jekyll-katex](https://github.com/linjer/jekyll-katex).

After installation, there are two new KaTeX tags which will be regconized by Liquid: `katex` and `katexmm`.

### `katex`
Context within this tag will be render as Latex equation.
For example, `{{ "{% katex" }} %} y = ax^2+1 {{ "{% endkatex" }} %}` will give us 
{{ "{% katex" }} %} y = ax^2+1 {{ "{% endkatex" }} %}.

For the display mode, we use use `katex display` tag like this  `{{ "{% katex display" }} %} y = ax^2+1 {{ "{% endkatex" }} %}`, and got:

{{ "{% katex display" }} %} y = ax^2+1 {{ "{% endkatex" }} %}

### `katexmm`
This tag is more handy compared to the previous, since this allow us to mix normal content with LaTeX math content.
Inside this tag, we can use some indications for math block:
 + `$` for inline.
 + `$$` for display mode.

And we can use `\$` to escape `$` when needed.

For example:
```
{{ "{% katexmm" }} %}
We define a proximal operator for variable $\mathbf{x}$ on function $ h(\mathbf{u})$ as follow: 

$$\textrm{prox}_h(\mathbf{x}) = \underset{\mathbf{u}}{\textrm{argmin }} \frac{1}{2}\left\Vert \mathbf{u} - \mathbf{x}\right\Vert _2^2 + h(\mathbf{u}).$$
{{ "{% endkatexmm" }} %}
```
and got this:

{{ "{% katexmm" }} %}
We define a proximal operator for variable $\mathbf{x}$ on function $ h(\mathbf{u})$ as follow: 

$$\textrm{prox}_h(\mathbf{x}) = \underset{\mathbf{u}}{\textrm{argmin }} \frac{1}{2}\left\Vert \mathbf{u} - \mathbf{x}\right\Vert _2^2 + h(\mathbf{u}).$$
{{ "{% endkatexmm" }} %}

More about supported functions of KaTeX can be found [here](https://katex.org/docs/supported.html)

## MathJaX
In Mathjax, there are two ways to insert math tex: `\\( \\)` for inline math and `$$  $$` for display mode.

For instance, an inline math like `\\( f(x,y) = x^2 + xy +1 \\)` will be rendered as 
\\( f(x,y) = x^2 + xy +1 \\)
and `$$ f(x,y) = \frac{x^2 + xy +1}{xy^2-1} $$ ` will give us

$$ f(x,y) = \frac{x^2 + xy +1}{xy^2-1} $$

The interesting thing about MathJaX is that there are many handy extensions.
For example:
```
$$\require{\AMScd}$$

$$\begin{CD}
A @<<< B @>>> C\\
@. @| @AAA\\
@. D @= E
\end{CD}$$
```

will allow us to use `amscd` to draw a diagram:

$$\require{\AMScd}$$
$$\begin{CD}
A @<<< B @>>> C\\
@. @| @AAA\\
@. D @= E
\end{CD}$$

More about MathJaX extensions can be found [here](http://docs.mathjax.org/en/latest/tex.html#tex-and-latex-extensions)

## TikzJaX

With TikzJaX, we can somehow draw using Tikz syntax. Although complicated drawing which require some extra tikzlibraries may not be supported at this moment, it is fancy enough to have it integrated with Jekyll.

The syntax to use TikzJaX like so:
```
<script type="text/tikz">
  \begin{tikzpicture}
    \draw (0,0) circle (0.5in);
  \end{tikzpicture}
</script>
```
which will yield:

<script type="text/tikz">
  \begin{tikzpicture}
    \draw (0,0) circle (0.5in);
  \end{tikzpicture}
</script>

or 
```
<script type="text/tikz">
\begin{tikzpicture}[scale=1.5,inner sep = 0pt]
  %[scale=0.9,every node/.style={scale=0.9}]
  % [auto, node distance=3cm]
    \draw (-0.70em,0) node[text=white!40!black,font=\Large]
    { \{ };
    \draw (0.70em,0) node[text=white!40!black,font=\Large]
    { \} };
    \draw (-0.28em,0.35em) node[text=white!10!black,font=\scriptsize]
    {$\odot$};
    \draw (0.28em,0.35em) node[text=white!10!black,font=\scriptsize]
    {$\odot$};
    \draw (0,-0.1em) node[text=black,font=\normalsize{},rotate=90]
    { \} };
    \draw (0,-0.5em) node[text=black,rotate=180,font=\tiny]
    {${\infty}$};
\end{tikzpicture}
</script>
```
give us:

<script type="text/tikz">
\begin{tikzpicture}[scale=1.5,inner sep = 0pt]
  %[scale=0.9,every node/.style={scale=0.9}]
  % [auto, node distance=3cm]
    \draw (-0.70em,0) node[text=white!40!black,font=\Large]
    { \{ };
    \draw (0.70em,0) node[text=white!40!black,font=\Large]
    { \} };
    \draw (-0.28em,0.35em) node[text=white!10!black,font=\scriptsize]
    {$\odot$};
    \draw (0.28em,0.35em) node[text=white!10!black,font=\scriptsize]
    {$\odot$};
    \draw (0,-0.1em) node[text=black,font=\normalsize{},rotate=90]
    { \} };
    \draw (0,-0.5em) node[text=black,rotate=180,font=\tiny]
    {${\infty}$};
\end{tikzpicture}
</script>


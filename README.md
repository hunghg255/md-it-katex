<p align="center">
<a href="https://www.npmjs.com/package/md-it-katex" target="_blank" rel="noopener noreferrer">
<img src="https://api.iconify.design/teenyicons:markdown-outline.svg?color=%2300bfff" alt="logo" width='100'/></a>
</p>

<p align="center">
  Add Math to your Markdown
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/md-it-katex" target="_blank" rel="noopener noreferrer"><img src="https://badge.fury.io/js/csvs-parsers.svg" alt="NPM Version" /></a>
  <a href="https://www.npmjs.com/package/md-it-katex" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/npm/dt/csvs-parsers.svg?logo=npm" alt="NPM Downloads" /></a>
  <a href="https://bundlephobia.com/result?p=md-it-katex" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/bundlephobia/minzip/md-it-katex" alt="Minizip" /></a>
  <a href="https://github.com/hunghg255/md-it-katex/graphs/contributors" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/badge/all_contributors-1-orange.svg" alt="Contributors" /></a>
  <a href="https://github.com/hunghg255/md-it-katex/blob/main/LICENSE" target="_blank" rel="noopener noreferrer"><img src="https://badgen.net/github/license/hunghg255/md-it-katex" alt="License" /></a>
</p>

[KaTeX](https://github.com/Khan/KaTeX) is a faster alternative to MathJax. This plugin makes it easy to support in your markdown.

Need convincing?

- Check out the comparative benchmark: [KaTeX vs MathJax](https://jsperf.com/katex-vs-mathjax/42)
- Try it in your browser: [md-it-katex demo](http://hunghg255.github.io/md-it-katex/)

## Usage

Install markdown-it

```
npm install markdown-it
```

Install the plugin

```
npm install md-it-katex
```

Use CJS

```javascript
var md = require('markdown-it')(),
  mk = require('md-it-katex');

md.use(mk);

// double backslash is required for javascript strings, but not html input
var result = md.render('# Math Rulez! \n  $\\sqrt{3x-1}+(1+x)^2$');
```

Use ESM

```javascript
import md from 'markdown-it',
import mk from 'md-it-katex';

md.use(mk);

// double backslash is required for javascript strings, but not html input
var result = md.render('# Math Rulez! \n  $\\sqrt{3x-1}+(1+x)^2$');
```

Include the KaTeX stylesheet in your html:

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css" />
```

If you're using the default markdown-it parser, I also recommend the [github stylesheet](https://github.com/sindresorhus/github-markdown-css):

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/github-markdown-css/2.2.1/github-markdown.css"
/>
```

`KaTeX` options can be supplied with the second argument to use.

```javascript
md.use(mk, { throwOnError: false, errorColor: ' #cc0000' });
```

## Examples

### Inline

Surround your LaTeX with a single `$` on each side for inline rendering.

```
$\sqrt{3x-1}+(1+x)^2$
```

### Block

Use two (`$$`) for block rendering. This mode uses bigger symbols and centers
the result.

```
$$\begin{array}{c}

\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
= \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

\nabla \cdot \vec{\mathbf{B}} & = 0

\end{array}$$
```

## Syntax

Math parsing in markdown is designed to agree with the conventions set by pandoc:

    Anything between two $ characters will be treated as TeX math. The opening $ must
    have a non-space character immediately to its right, while the closing $ must
    have a non-space character immediately to its left, and must not be followed
    immediately by a digit. Thus, $20,000 and $30,000 won’t parse as math. If for some
    reason you need to enclose text in literal $ characters, backslash-escape them and
    they won’t be treated as math delimiters.

## Math Syntax Support

KaTeX is based on TeX and LaTeX. Support for both is growing. Here's a list of
currently supported functions:

[Function Support in KaTeX](https://github.com/Khan/KaTeX/wiki/Function-Support-in-KaTeX)
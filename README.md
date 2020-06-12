# quotebacks-mdx

Python-Markdown extension to support the [Quotebacks](https://quotebacks.net) format.


## Installation

Copy `quotebacks_mdx.py` into your script directory.

Python-Markdown is required. Python 3 is required.


## Motivation

This allows the final webpage to display a Quotebacks embed without having to have custom
HTML in the content source files.

The Markdown format has been chosen such that it will look natural even if this extension
is not used.

(There have been small changes to the final HTML so that the blockquote and citation are
still well formatted even when quotebacks.js is not loaded. See
`docs/quoteback-example.html` for details.)


## Usage

Include a citation in a Markdown blockquote using the following format:

```markdown
> QUOTED-CONTENT
>
> -- AUTHOR, [LINKTEXT](URL)
```

The citation MUST be within the blockquote, and start with "--" and the author must
terminate with ",". The citation must be preceded by a blank line.

Use the extension with Python-Markdown:

```python
import markdown
import quotebacks_mdx

md = markdown.Markdown(extensions=[quotebacks_mdx.QuotebacksExtension()])
html = md.convert(markdown_source)

print(html)

# Include quotebacks.js at the bottom of page, if quotebacks were found
if md.quotebacks_found:
    html += quotebacks_mdx.QUOTEBACKS_SCRIPT_TAG
```


## Status

This is a proof of concept, but in use at Interconnected, [e.g. this
post.](http://interconnected.org/home/2020/06/12/gibson)

Main to-dos:

* Get feedback on the Markdown format
* Package the extension

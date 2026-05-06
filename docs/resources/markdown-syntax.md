# Using Markdown in Documentation

### What is Markdown?

> Markdown is a text-to-HTML conversion tool for web writers.

> Markdown allows you to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally valid XHTML (or HTML).

For example, this entire page was created using Markdown!

Below is a quick reference of all the Markdown syntax that is supported by Stoplight.

### Table of Contents

- [Headers](#headers)
- [Emphasis](#emphasis)
- [Lists](#lists)
- [Links](#lnks)
- [Images](#imgs)
- [Code and Syntax Highlighting](#code)
- [Tables](#tables)
- [Blockquotes](#blockquotes)
- [Code block](#code-block)
- [Horizontal Rule](#hr)
- [Line Breaks](#linebreaks)

## <a name="headers"/> Headers

```no-highlight
# H1

H1
=====

## H2

H2
------

### H3

#### H4

##### H5

###### H6
```

# H1

## H2

### H3

#### H4

##### H5

###### H6

## <a name="emphasis"/> Emphasis

```no-highlight
Emphasis, aka italics, with *asterisks* or _underscores_.

Strong emphasis, aka bold, with **asterisks** or __underscores__.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~
```

_This_ is a ~~not~~ **very** important example.

## <a name="lists"/> Lists

> In this example, leading and trailing spaces are shown with with dots: ⋅⋅⋅

```no-highlight
1. First ordered list item
2. Another item
   ..- Unordered sub-list
3. Actual numbers don't matter, just that it's a number
   ..1. Ordered sub-list
4. And another item

...You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).
```

1. First
   - Thing
2. Second
   - Item
3. Third
   1. Point one

## <a name="links"/> Links

Different ways to create links:

```no-highlight
1. To link Inline-style
[I'm an inline-style link](https://www.google.com)

2. To link Reference-style
[I'm a reference-style link][https://www.google.com "Google's Homepage"]

3. To link to API explorer from documentation pages
[Charge](/product/CommerceHub/api/post/payments-vas/v1/3ds/authenticate)

4. To link/reference to another document/markdown
[Configure Your Tenant](/product/TenantSupport/docs/getting-started/configure-tenant.md)

5. To create anchor link within the page. You can place anchor by declaring <a name = "portal"></a>. Now you can reference this link anywhere within the page by declaring link such as [Dev Portal](#portal)
```

## <a name="imgs"/> Images

Different ways to create images:

```no-highlight
- To embed Inline-style
   ![Image](https://image-link.com/image.png)
- To embed with html (you can adjust the size with this approach)
   <img src="https://image-link.com/image.png" alt="image"/>
- Defined reference
   - Reference: ![Image]
   - Reference definition (generally at bottom of the markdown page): [Image]: <https://image-link.com/image.png>

```

Here's our logo (hover to see the image description/title):

The following image is being set as `![Nyan cat]` where we define `[Nyan cat]: <https://image-link.com/nyan_cat.jpg>` or since it's hosted in our Github we can use `[Nyan cat]: <assets/images/nyan_cat.jpg>`

![Nyan cat]

## <a name="code"/> Code and Syntax Highlighting

Inline `code` has `back-ticks around` it.

> Here is the example for javascript code.

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

> Use language tags to change the syntax highlighting.

```json
{
  "JSON": "Syntax Highlighting"
}
```

## <a name="tables"/> Tables

Tables aren't part of the core Markdown spec, but they are part of GFM and _Markdown Here_ supports them. They are an easy way of adding tables to your email -- a task that would otherwise require copy-pasting from another application.

```no-highlight
Colons can be used to align columns.

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

The outer pipes (|) are optional, and you don't need to make the raw Markdown line up prettily. You can also use inline Markdown.

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3
```

| Markdown | Less      | Pretty     |
| -------- | --------- | ---------- |
| _Still_  | `renders` | **nicely** |
| 1        | 2         | 3          |

```no-highlight
| Name | Description | Example |
|------|-------------|  :----: |
| Headers | Large text refer to Header section for more detail | <h1> Hello </h1>
| Emphasis | italics, bold, or strikethrough | *italics*, **bold**, ~~strikethrough~~, **bold and _italics_**
| Lists | Refer to Lists section for more details | 1. List item 1 <br /> 2. List item 2
| Links | Hyperlinks, refer to above Link section for more details | To link to API explorer from documentation pages API page [API page](../api?type=post&path=/v1/apis)
| Images | Visual representation | ![Fiserv Logo](../../assets/images/Fiserv_Logo.jpg "Fiserv Logo")
| Code | code blocks, syntax highlighting | <pre> String main(void) <br /> { <b>this is a pre block </b> } </pre>  `rendering code snippets`
| Tables | contains rows and columns | <table><tr><td>Table</td><td>Mini Description</td></tr><tr><td>Type</td><td>String</td></tr></table>
```

## <a name="blockquotes"/> Blockquotes

```no-highlight
> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line of text that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote, just in case you didn't know.
```

> This is a very long line of text that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can _put_ **Markdown** into a blockquote, just in case you didn't know.

You can also use this format for standard colored callout boxes.

```no-highlight
<!-- theme: info/success/warning/danger -->
> Callout box text
```

<!-- theme: info -->
> This is an information callout box

<!-- theme: success -->
> This is a success callout box

<!-- theme: warning -->
> This is a warning callout box

<!-- theme: danger -->
> This is a danger callout box

## Code block

```no-highlight
The black boxes we've been putting markdown syntax in are called code blocks.
You can use them to auto-escape various coding specific characters and display code in a copy-pasteable manner.
The three ` should be all together but for this example, we'll put a space before the last one to not break our current code block.

`` `python
print('Hello world')
`` `
```

```python
print('Hello world')
```

```no-highlight
You can also indicate a string of text as code in the middle of a normal text sentence using `some coding stuff` syntax.
```

The famous `Nyan cat` was placed somewhere on this page using the `![Nyan cat]` image embed.

## <a name="hr"/> Horizontal Rule

```
Three or more...

---

Hyphens

***

Asterisks

___

Underscores
```

## <a name="linebreaks"/> Line breaks
In general, there are two approaches:

- Add two spaces at the end of a line (followed by the 'return' key)
- Add ```<br />``` at the end of the line

[//]: # "These are reference links used in markdown file"
[Nyan cat]: assets/images/nyan.jpg

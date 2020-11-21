# Writer's Mark

Easy, safe and flexible markup for user-generated content.

Writer's Mark attempts to thread the needle between the simplicity of markdown and the power of HTML/CSS, while providing security guarantees so that user-generated content can be both safe and flexible at the same time.

Live Demo : (insert link here)

## Introduction:

In short, it allows you to write like this:

```
__title__
This is the title

__subtitle__
It's pretty neat

This is a paragraph.

This is another single paragraph. It is
spread over multiple lines, but still renders as a single <p> tag.

__aside__
This paragraph has some special styling applied to it

In this paragraph **spans of words** can be styled

---
p __title__ {font-size: 2em; font-weight: bold;}
p __subtitle__ {font-size: 1.5em;}
p __aside__ {margin-left: 2em;}
s ** {font-weight: bold;}
---
```

**N.B.** Styling rules do not have to be embedded within the text itself, they can also be externally provided.

### Writing Styles

There are two kinds of style rules: **Paragraph** and **span** rules. A style is simply a collection of these rules. Each rule is a collection of CSS properties.

A paragraph rule looks like this:

```
p <token> {
  property-1: value;
  property-2: value;
  etc...
}
```

A span rule looks like either one of these. In the first flavor, `token` is used both as the open and close sequence.
```
s <token> {
  property-1: value;
  property-2: value;
  etc...
}

s <open> <close> {
  property-1: value;
  property-2: value;
  etc...
}
```

### Aplying style rules

#### Paragraph rules
If a paragraph begins with text matching a paragraph rule by itself on a line, that rule is applied to the paragraph.
```
some_style
The text of the parapgraph
```

#### Span rules

If the open sequence of a span rule is present in a paragraph, and the close sequence follows it. Everything in between will have the rule applied.

```
The *text* of the parapgraph.
```

## Safety

Writer's mark is meant to be safe by default.

* Arbitrary HTML is not supported.
* Links, images, or anything using an url is not supported.
* CSS properties are opted-in.

## Implementations

* [writers-mark-ts](https://github.com/writers-mark/writers-mark-ts) Contains basic parsing and validation features.
* [writers-mark-dom](https://github.com/writers-mark/writers-mark-dom) Atomically renders Writer's Mark directly to the dom, with a matching stylesheet.
* [writers-mark-react](https://github.com/writers-mark/writers-mark-react) Can render Writer's Mark directly as a react component with partial re-renders.
# Writer's Mark

Easy, safe and flexible markup for user-generated content.

Writer's Mark attempts to thread the needle between the simplicity of markdown and the power of HTML/CSS, while providing security guarantees so that user-generated content can be both safe and flexible at the same time.

Live Demo : https://writers-mark.github.io/demo/

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
para __title__ {font-size: 2em; font-weight: bold;}
para __subtitle__ {font-size: 1.5em;}
para __aside__ {margin-left: 2em;}
span ** {font-weight: bold;}
---
```

**N.B.** Styling rules do not have to be embedded within the text itself, they can also be externally provided.

### Why?

A text should belong to its author, not to whatever software platform it was authored on. At the same time, we acknowledge
that powerful markup languages like LaTeX or HTML/CSS are not particularly welcoming to new users.

The goal of Writer's Mark is to allow authors to write and format text in a way that they fully own, while being straightforward
enough that they can just dive in.

## Writing

### Text

Text is just a collection of paragraphs

```
This is a paragraph.

This is a longer paragraph. Its text is spread over multiple
lines, but it will behave as if it was written on a single line.



It does not matter how much space there is between paragraphs.
```

There are two kinds of style rules: **Paragraph** and **span** rules. A style is simply a collection of these rules.

### Paragraph styles
If a paragraph begins with text matching a paragraph rule **by itself on a line**, that rule is applied to the paragraph.
```
some_style
This paragraph has the some_style rule applied to it.
It will be formatted according to its properties as long as some_style is a style rule.
```

Multiple styles can be applied to a single paragraph:
```
some_style
some_other_style
This paragraph has the both the some_style and some_other_style rules applied to it.
The rules will be applied in order from top to bottom.
```

### Span rules

If the open sequence of a span rule is present in a paragraph, and the close sequence follows it. Everything in between will have the rule applied.

```
The *text* of the paragraph.
```

## Writing Styles

### Paragraph rules
A paragraph rule looks like this:

```
para <token> {
  margin: 12px;
  font-family: arial;
  etc...
}
```

### Span rules
A span rule looks like either one of these. In the first flavor, `token` is used both as the open and close sequence.

```
span <token> {
  font-weight: bold;
  etc...
}

span <open> [close] {
  font-style: italic;
  property-2: value;
  etc...
}
```

### Container rules
Style can also be applied to the background of a text using a container rule:

```
cont {
  background-color: lightGrey;
}
```

## FAQ:

#### What are the propperties that I can use?

On paper Writer's Mark support almost all [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference) rules with a few caveats.

* An App is free to allow or disallow any CSS property it chooses.
* Any value referencing external resources is disallowed e.g. `background: url("http://example.com/img.jpg");` will not work.
* You cannot use any escape sequence. If you don't know what that means, don't worry about it.
* Paragraphs are converted into `<p>` tags.
* Spans are converted into `<span>` tags.
* Containers are almost always `<div>` tags. 


#### Can I add images to text?

Not at the moment. We might allow something in the future, but it would have to be both secure and writer-friendly.

#### Can I put url links in the text?

No. This is something that we "might" revisit in a limited manner in the future.

## Safety

Writer's mark is meant to be safe by default.

* Arbitrary HTML is not supported.
* Links, images, or anything using an rxternal resource is not supported.
* CSS properties are opted-in.

## Implementations

* [writers-mark-ts](https://github.com/writers-mark/writers-mark-ts) Contains basic parsing and validation features.
* [writers-mark-dom](https://github.com/writers-mark/writers-mark-dom) Atomically renders Writer's Mark directly to the dom, with a matching stylesheet.
* [writers-mark-react](https://github.com/writers-mark/writers-mark-react) Can render Writer's Mark directly as a react component.

# Writer's Mark test suite

## Directory structure

Each directory contains up to 3 types of files.

* 0 or 1 `__options.json` which contains the context parameters to apply to the included tests.
* 0 to N `.style` files that will be applied in filesystem order to the tests within the directory. Make sure that all style files are defined before the first test file. 
* 0 to N `.wmt` files, each containing a test case

## Test case structure

Each test case file MUST have 3 sections:

```
[source]

<...insert wmt source here...>

[style]
<...insert expected css rules here...>


[body]
<...insert expected html body here...>
```

* The HTML body and style rules can be pretty-printed.
* The css rules are verified by content, not by name.
* Remember that there is always an implicit "default" rule applied to all paragraphs.

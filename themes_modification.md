# Modification

You can create a theme or modify an existing one easily and quickly.

::: info
You can check out `https://github.com/photonsh/themes/photon-light/photon-light.css` as an example.
:::

The themes are divided mainly into three sections.

## Structure

In this section we find rules that are in charge of applying general and structure styles.

The structural selectors are:

* `.psh`
* `.psh figure`
* `.psh pre`
* `.psh code`
* `.psh code::selection`
* `.psh samp`
* `.psh samp::selection`

## Plugins

The following rules that we find in a theme are those related to the plugins.

The selectors associated with each plugin can be found on their respective documentation pages.

## Tokens

These selectors are in charge of coloring the code.

They depend on the language used and its properties. For example, a JavaScript snippet would produce tokens different from those that would produce an HTML snippet.

Some selectors are:

* `.psh .comment`
* `.psh .entity`
* `.psh .keyword`
* `.psh .storage`
* `.psh .constant`
* `.psh .variable`
* `.psh .string`
* `.psh .punctuation`
* `.psh .support`
* `.psh .meta`

Other selectors also share the same level or are in a lower one.

For example, `.psh .keyword` would apply a general style. We can be more specific using the `.psh .keyword.control` or `.psh .keyword.operator` selectors.

Also, specific selectors can be used for each language. We could apply a different style to `.keyword.operator` depending on the language used. For example, using the `.psh .source.js .keyword.operator` and `.psh .source.python .keyword.operator` selectors (the `.source` class can be omitted).

The best way to modify these styles is through *trial and error*, since its behavior is intuitive.

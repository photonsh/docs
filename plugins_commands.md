# Commands

Adds the prompt symbol to each line to indicate that it is a command.

It is common to use this plugin with the `language-text` class since the commands normally do not have syntax highlighting.

## HTML attribute

`data-commands`

### Accepted Values

#### `true`

Using `true` will transform all lines.

#### `<int>[-<int>][,<int>[-<int>],...]`

As a numeric value, one or more integers separated by commas. Integer ranges separated by dashes are accepted. No spaces allowed.

Some examples of how numeric values are transformed:

* `3` -> `3`
* `3,4,6` -> `3,4,6`
* `3-7` -> `3,4,5,6,7`
* `3-7,10,12,14-17` -> `3,4,5,6,7,10,12,14,15,16,17`

## Example

Basic example.

### Input

``` {.language-html}
<pre><code class="language-text" data-commands="true"></code></pre>
```

### Output

``` {.language-text data-commands="true"}
./configure
make
make install
```

## CSS Selectors

* `.psh-commands::before`

## Tips and tricks

Click [here](https://photon.sh/blog/tips-and-tricks-commands-plugin).

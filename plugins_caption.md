# Caption

Add a caption in which you can describe the purpose of the content or what type it is.

## HTML attribute

`data-caption`

### Accepted Values

#### `<String>`

A single value representing the text to be displayed.

## Example

Example describing the purpose of the code.

### Input

``` {.language-html}
<pre><code class="language-python" data-caption="Minimal Flask Application"></code></pre>
```

### Output

``` {.language-python data-caption="Minimal Flask Application"}
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'
```

## CSS Selectors

* `.psh-caption`
* `.psh-caption-value`

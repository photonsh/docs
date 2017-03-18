# Node.js

Official Node.js library.

::: info
If you are using JavaScript on the browser, refer to the [libraries/javascript](https://photon.sh/docs/libraries/javascript) page.
:::

## Snippets

The Node.js library is responsible for processing snippets that meet the established conditions.

The snippets must be inside the HTML `<pre><code>...</code></pre>` (code) or `<pre><samp>...</samp></pre>` (output) tags.

Also, as in the rest of the libraries, the HTML `<code>` and `<samp>` tags must include the `language-NAME` class, as indicated on the [getting-started/quickstart#snippet-preparation](https://photon.sh/docs/getting-started/quickstart#snippet-preparation) page.

This library accepts any HTML structure, such as an article, and returns the same article with the processed snippets, keeping the rest intact.

::: warning
Some HTML special characters [must be escaped](https://photon.sh/docs/getting-started/api-reference#snippet) before being used in the snippet. We recommend using the [escape-html](https://www.npmjs.com/package/escape-html){target="_blank"} library.
:::

### Example

``` {.language-html}
<article>
  <header>
    <h1>...</h1>
  </header>
  <p>...</p>
  <pre><code>...</code></pre> <!-- Will transform this snippet -->
  <p>...</p>
  <pre><samp>...</samp></pre> <!-- Will transform this snippet -->
  <p>...</p>
  <footer>...</footer>
</article>
```

## Installation

It is installed using npm or Yarn.

``` {.language-text data-commands="true"}
npm install photon-node
```

## Usage

Import the library and call the `photon` function with the snippet to process as the first argument.

The function call **returns a promise** that fulfills with the result or is rejected with an error.

### Promises + require

Using the `setup` function to provide the API key.

``` {.language-javascript}
const photon = require('photon-node');

const snippet = '<code class="language-javascript">console.log(\'example\');</code>';

photon.setup({ apiKey: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' })

photon.highlight(snippet)
  .then(function (result) {
    console.log(result);
  })
  .catch(function (err) {
    console.error(err);
  });
```

### Async/await + import

The API key can also be provided through the `options` object to the `photon` function.

``` {.language-javascript}
import photon from 'photon-node'

async function generateHTML(snippet) {
  let finalSnippet = snippet

  try {
    finalSnippet = await photon.highlight(snippet, { apiKey: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' })
  } catch (err) {
    console.error(err)
  }

  return finalSnippet
}

generateHTML('<code class="language-javascript">console.log(\'example\');</code>')
//  .then(saveToDisk)
```

## API

### setup(options)

Function that accepts as single argument an object with configuration parameters. These parameters affect **all calls** to the `highlight` function.

#### options

* `apiKey`: The API key to use for all calls to the `highlight` function.

### highlight(snippet, options)

Function that accepts as the first argument a snippet or an HTML fragment/document with snippets inside it, nested at any level.

As a second argument, `highlight` accepts an object with configuration parameters. These parameters only affect **this call** to the `highlight` function.

#### options

* `apiKey`: The API key to use in this specific call.

::: warning
If you do not provide an API key to the `setup` function, you must provide it to the `highlight` function.
:::

## Resources

* [GitHub project](https://github.com/photonsh/photon-node){target="_blank"}
* [Issue tracker](https://github.com/photonsh/photon-node/issues){target="_blank"}

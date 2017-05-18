# JavaScript

Official JavaScript library.

::: info
If you are using JavaScript on the server, refer to the [libraries/nodejs](https://photon.sh/docs/libraries/nodejs) page.
:::

## Snippets

The JavaScript library is responsible for processing **all snippets** that meet the established conditions.

The snippets must be inside the HTML `<pre><code>...</code></pre>` (code) or `<pre><samp>...</samp></pre>` (output) tags.

Also, as in the rest of the libraries, the HTML `<code>` and `<samp>` tags must include the `language-NAME` class, as indicated on the [getting-started/quickstart#snippet-preparation](https://photon.sh/docs/getting-started/quickstart#snippet-preparation) page.

::: warning
Some HTML special characters [must be escaped](https://photon.sh/docs/getting-started/api-reference#snippet) before being used in the snippet. We recommend using the [escape-html](https://www.npmjs.com/package/escape-html){target="_blank"} library or another [solution](http://stackoverflow.com/a/4835406/3181234){target="_blank"}.
:::

## Installation

### Recommended mode

The library should be included between the HTML `<head>` and `</head>` tags and it must contain the `defer` and the `id` attributes.

``` {.language-html}
<script defer id="photon_lib" src="https://cdn.jsdelivr.net/npm/photon-js@0.1.3/dist/photon.min.js"></script>
```

### Alternative mode

The library can be also included just before the HTML closing `</body>` tag, where it does not need those attributes.

``` {.language-html}
<script src="https://cdn.jsdelivr.net/npm/photon-js@0.1.3/dist/photon.min.js"></script>
```

## Usage

### Recommended mode

To run the library include the following code **after** the installation tag.

``` {.language-html}
<script>
  document.querySelector('#photon_lib').addEventListener('load', function() {
    photon.setup({ apiKey: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' });
    photon.highlight();
  });
</script>
```

The API key can also be provided through the `options` object to the `highlight` function.

``` {.language-html}
<script>
  document.querySelector('#photon_lib').addEventListener('load', function() {
    photon.highlight({ apiKey: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' });
  });
</script>
```

### Alternative mode

If the library is placed at the end of the HTML `<body>` element, include the following code **after** the installation tag.

``` {.language-html}
<script>
  photon.setup({ apiKey: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' });
  photon.highlight();
</script>
```

Or simply:

``` {.language-html}
<script>
  photon.highlight({ apiKey: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' });
</script>
```

## API

### setup(options)

Function that accepts as single argument an object with configuration parameters. These parameters affect **all calls** to the `highlight` function.

#### options

* `apiKey`: The API key to use for all calls to the `highlight` function.

### highlight(options)

Function that accepts as single argument an object with configuration parameters. These parameters only affect **this call** to the `highlight` function.

#### options

* `apiKey`: The API key to use in this specific call.

::: warning
If you do not provide an API key to the `setup` function, you must provide it to the `highlight` function.
:::

## Resources

* [GitHub project](https://github.com/photonsh/photon-js){target="_blank"}
* [Issue tracker](https://github.com/photonsh/photon-js/issues){target="_blank"}

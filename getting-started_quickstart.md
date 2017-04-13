# Quickstart

## What is needed

To start using Photon you only need the following.

### API key

[Sign up](https://photon.sh/signup) to get one, It is free!

### Snippet preparation

A snippet inside the HTML `<pre><code>...</code></pre>` (code) or `<pre><samp>...</samp></pre>` (output) tags.

The HTML `<code>` and `<samp>` tags must include the `language-NAME` class with the desired language (e.g., `class="language-javascript"`). More information on the [getting-started/api-reference#snippet](https://photon.sh/docs/getting-started/api-reference#snippet) page.

::: warning
The HTML `<pre>` element is only **required** in official libraries. In case of making an API call the tag **must** be omitted.
:::

#### Example

``` {.language-html}
<code class="language-javascript">console.log('example');</code>
```

### Snippet process

Make an [API call](https://photon.sh/docs/getting-started/api-reference#http-request) or use one of the official libraries to send the snippet to our servers.

::: info
Check the specific documentation page for each library for more information.
:::

### Theme

Select a [theme](https://photon.sh/docs/themes/list) from the list and include the HTML `<link>' element in the web document where the highlighted snippet will be displayed.

## Quickstart using JavaScript library

In short, this is what is needed.

* The snippet with the `language-NAME` class.
* The HTML `<link>` element of the selected theme.
* The HTML `<script>` element that will load the JavaScript library.
* The HTML `<script>` element that will run the library as soon as it is loaded.

That is all!

``` {.language-html data-add="9-11" data-highlight="6,12-17"}
<!DOCTYPE html>
<html>
  <head>
    <title>Photon JavaScript example</title>
    <meta charset="utf-8">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/photon-themes/0.1.2/photon-light/photon-light.min.css">
    <script defer id="photon_lib" src="https://cdn.jsdelivr.net/photon-js/0.1.2/photon.min.js"></script>
    <script>
      document.querySelector('#photon_lib').addEventListener('load', function() {
        photon.highlight({ apiKey: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' });
      })
    </script>
  </head>
  <body>
    <pre>
      <code class="language-javascript">console.log('example');</code>
    </pre>
  </body>
</html>
```

# PHP

Official PHP library.

## Snippets

The PHP library is responsible for processing snippets that meet the established conditions.

The snippets must be inside the HTML `<pre><code>...</code></pre>` (code) or `<pre><samp>...</samp></pre>` (output) tags.

Also, as in the rest of the libraries, the HTML `<code>` and `<samp>` tags must include the `language-NAME` class, as indicated on the [getting-started/quickstart#snippet-preparation](https://photon.sh/docs/getting-started/quickstart#snippet-preparation) page.

This library accepts any HTML structure, such as an article, and returns the same article with the processed snippets, keeping the rest intact.

::: warning
Some HTML special characters [must be escaped](https://photon.sh/docs/getting-started/api-reference#snippet) before being used in the snippet. We recommend using the [htmlspecialchars](http://php.net/manual/en/function.htmlspecialchars.php){target="_blank"} built-in function.
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

The library is available at [Packagist](https://packagist.org/packages/photonsh/photon-php){target="_blank"}, so you can use Composer to install it.

``` {.language-text data-commands="true"}
$ composer require photonsh/photon-php
```

## Usage

photon-php makes use of the [PSR-4](http://www.php-fig.org/psr/psr-4/){target="_blank"} autoloading specification.

After requiring the `autoload.php` file in your application, import the `Photon` class and create a new instance of such class.

Then, provide the API key to the `setup` method using an array and call the `highlight` method providing the snippet to process as the first argument.

``` {.language-php}
require_once __DIR__.'/vendor/autoload.php';

use Photonsh\PhotonPhp;

$photon = new PhotonPhp\Photon();

$photon->setup(['apiKey' => 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx']);

echo $photon->highlight('<pre><code class="language-php">echo \'example\';</code></pre>');
```

The API key can also be provided through the `$options` array to the `highlight` method.

``` {.language-php}
require_once __DIR__.'/vendor/autoload.php';

use Photonsh\PhotonPhp;

$photon = new PhotonPhp\Photon();

echo $photon->highlight('<pre><code class="language-php">echo \'example\';</code></pre>', ['apiKey' => 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx']);
```

### Exceptions

Photon throws a `Photonsh\PhotonPhp\Exception\ClientException` exception when there is a problem highlighting the snippet.

``` {.language-php}
require_once __DIR__.'/vendor/autoload.php';

use Photonsh\PhotonPhp;
use Photonsh\PhotonPhp\Exception\ClientException;

$photon = new PhotonPhp\Photon();

$photon->setup(['apiKey' => 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx']);

try {
    echo $photon->highlight('<pre><code class="language-php">echo \'example\';</code></pre>');
} catch (ClientException $e) {
    // Handle Exception
}
```

## API

### setup(array $options)

Method that accepts as single argument an array with configuration parameters. These parameters affect **all calls** to the `highlight` method.

#### options

* *string* `apiKey`: The API key to use for all calls to the `highlight` method.

### highlight(string $snippet, array $options)

Method that accepts as the first argument a snippet or an HTML fragment/document with snippets inside it, nested at any level.

As a second argument, `highlight` accepts an array with configuration parameters. These parameters only affect **this call** to the `highlight` method.

#### options

* *string* `apiKey`: The API key to use in this specific call.

::: warning
If you do not provide an API key to the `setup` method, you must provide it to the `highlight` method.
:::

## Resources

* [GitHub project](https://github.com/photonsh/photon-php){target="_blank"}
* [Issue tracker](https://github.com/photonsh/photon-php/issues){target="_blank"}

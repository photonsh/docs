# Request

Displays a request method and the URL of a resource.

::: info
The method is converted to uppercase and the resource to lowercase.
:::

## HTML attribute

`data-request`

### Accepted Values

#### `<String>,<String>`

Two values, separated by commas, where the first value is the HTTP method and the second value is the URL of the resource.

Accepts any existing (`OPTIONS`,` HEAD`, `TRACE`, etc.) or nonexistent method.

## Example

Example using the `GET` method. The HTML `<samp>` element is used to display the HTTP response.

### Input

``` {.language-html}
<pre><samp class="language-json" data-request="get,https://api.github.com/gists/public">...</samp></pre>
```

### Output

´´´ {.language-json data-request="get,https://api.github.com/gists/public"}
[
  {
    "url": "https://api.github.com/gists/aa5a315d61ae9438b18d",
    "forks_url": "https://api.github.com/gists/aa5a315d61ae9438b18d/forks",
    "commits_url": "https://api.github.com/gists/aa5a315d61ae9438b18d/commits",
    "id": "aa5a315d61ae9438b18d",
    "...": "..."
  }
]
´´´

## Example

Example using the `POST` method. The HTML `<code>` element is used to display the data sent in the HTTP request.

### Input

``` {.language-html}
<pre><code class="language-json" data-request="post,https://api.github.com/gists">...</code></pre>
```

### Output

``` {.language-json data-request="post,https://api.github.com/gists"}
{
  "description": "the description for this gist",
  "public": true,
  "files": {
    "file1.txt": {
      "content": "String file contents"
    }
  }
}
```

## Example

Example using the `PUT` method. The HTML `<samp>` element is used to display the HTTP response.

The [caption](https://photon.sh/docs/plugins/caption) plugin is also used to indicate that the snippet corresponds to the HTTP response.

### Input

``` {.language-html}
<pre><samp class="language-text" data-request="put,https://api.github.com/gists/:id/star" data-caption="Response">...</samp></pre>
```

### Output

´´´ {.language-text data-request="put,https://api.github.com/gists/:id/star" data-caption="Response"}
Status: 204 No Content
´´´

## Example

Example using the `PATCH` method. The HTML `<code>` element is used to display the data sent in the HTTP request.

### Input

``` {.language-html}
<pre><code class="language-json" data-request="patch,https://api.github.com/gists/:id">...</code></pre>
```

### Output

´´´ {.language-json data-request="patch,https://api.github.com/gists/:id"}
{
  "description": "the description for this gist",
  "files": {
    "file1.txt": {
      "content": "updated file contents"
    }
  }
}
´´´

### Input

Example using the `DELETE` method. The HTML `<code>` element is used to display the data sent in the HTTP request.

Another snippet has been added using the HTML `<samp>` element and the [caption](https://photon.sh/docs/plugins/caption) plugin is also used to display the HTTP response.

### Input

``` {.language-html}
<pre><code class="language-json" data-request="delete,https://api.github.com/gists/:id">...</code></pre>
<pre><samp class="language-text" data-caption="Response">...</samp></pre>
```

### Output

´´´ {.language-json data-request="delete,https://api.github.com/gists/:id"}
{
  "id": 1124
}
´´´

``` {.language-text data-caption="Response"}
Status: 204 No Content
```

### Input

Example using the nonstandard `FOO` method.

### Input

``` {.language-html}
<pre><code class="language-text" data-request="foo,/api/endpoint">...</code></pre>
```

### Output

``` {.language-text data-request="foo,/api/endpoint"}
{
  "data": "You should not use nonstandard methods! But it also works."
}
```

## CSS Selectors

* `.psh-request`
* `.psh-request .psh-request-method`
* `.psh-request .psh-request-method-get`
* `.psh-request .psh-request-method-post`
* `.psh-request .psh-request-method-put`
* `.psh-request .psh-request-method-patch`
* `.psh-request .psh-request-method-delete`
* `.psh-request .psh-request-resource`
* `.psh-request .psh-request-method-get + .psh-request-resource`
* `.psh-request .psh-request-method-post + .psh-request-resource`
* `.psh-request .psh-request-method-put + .psh-request-resource`
* `.psh-request .psh-request-method-patch + .psh-request-resource`
* `.psh-request .psh-request-method-delete + .psh-request-resource`

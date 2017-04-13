# API reference

## Snippet

Some HTML special characters [must be escaped](https://www.w3.org/TR/html401/charset.html#h-5.3.2){target="_blank"} before being used in the snippet. The `<`, `>`, `&`, `"` and `'` characters must be replaced with their respective character entities (`&lt;`, `&gt;`, `&amp;`, `&quot;` and `&apos;`, respectively).

The snippet must be inside the HTML `<code>...</code>` (code) or `<samp>...</samp>` (output) tags.

::: warning
In the case of using an official library, the HTML `<pre>...</pre>` tags must also contain the snippet.
:::

The HTML `<code>` and `<samp>` tags must include the `language-NAME` class. The `NAME` placeholder must be replaced with a valid language code. Check the list on the [languages/list](https://photon.sh/docs/languages/list) page.

::: info
For compatibility the `lang-NAME` class is also accepted, but taking into account the [suggestion](https://html.spec.whatwg.org/multipage/semantics.html#the-code-element){target="_blank"} of the [WHATWG](https://wiki.whatwg.org/wiki/FAQ#What_is_the_WHATWG.3F){target="_blank"} group, we recommend using the` language-NAME` class.
:::

You can include as many plugins as you want.

## HTTP request

### Endpoint

The API endpoint is: `https://api.photon.sh/snippets`.

### Method

The method used must be `POST`.

### Header

Several headers should be used when sending the snippet.

Header                              | Value
-----------------------------------:|:----------------
`Authorization`<br>**`Required`**   | `Token API_KEY`
`Content-Type`<br>**`Required`**    | `text/html`
`Content-Encoding`<br>*`Optional`*  | `gzip`
`Accept-Encoding`<br>**`Required`** | `gzip`

In the `Authorization` header, `API_KEY` must be replaced with a valid API key. [Get one](https://photon.sh/signup).

### Body

The body of the HTTP request must be only the snippet. It should be sent as binary data.

::: info
The snippet can be compressed with [gzip](http://www.gzip.org/){target="_blank"} before being sent.
:::

### Example

Using [UNIX pipelines](https://en.wikipedia.org/wiki/Pipeline_(Unix)){target="_blank"} each of the steps are chained, including gzip compression and sending of data through [cURL](https://curl.haxx.se/){target="_blank"}.

``` {.language-text data-commands="true"}
echo "<code class=\"language-javascript\">console.log('photon');</code>" | gzip --stdout | curl --silent --request POST --header "Authorization: Token xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" --header "Content-Type: text/html" --header "Content-Encoding: gzip" --header "Accept-Encoding: gzip" --data-binary @- https://api.photon.sh/snippets
```

## HTTP response

### HTTP status code

#### In case of success

The HTTP status code `200 OK` is received.

#### In case of error

One of the following is received.

Error type                     | HTTP status code
------------------------------:|:----------------------------
`not_found`                    | `404 Not Found`
`authentication_error`         | `401 Unauthorized`
`invalid_api_key`              | `401 Unauthorized`
`unsupported_content_type`     | `415 Unsupported Media Type`
`unsupported_content_encoding` | `400 Bad Request`
`payload_too_large`            | `413 Payload Too Large`
`invalid_compressed_payload`   | `400 Bad Request`
`unknown_error`                | `>500`

### Header

Depending on whether the request is processed correctly or not, different headers are received.

#### In case of success

Header             | Value
------------------:|:----------------------------------------------
`Content-Type`     | `text/html`
`Content-Encoding` | `gzip`

#### In case of error

Header             | Value
------------------:|:----------------------------------------------
`Content-Type`     | `application/json`

### Body

#### In case of success

The body of the HTTP response is a string compressed with gzip.

#### In case of error

A JSON object is received with the error type and a descriptive message.

Error                               | Message
-----------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------
`not_found`                         | `This API endpoint does not exist.`
`authentication_error`              | `You did not provide an API key. You need to provide your API key in the Authorization header field, using Token auth (e.g. 'Authorization: Token API_KEY').`
`invalid_api_key`                   | `You did not provide a valid API key. You can get one at https://photon.sh/signup.`
`unsupported_content_type`          | `You did not provide a valid value for the Content-Type header field. You need to provide "text/html" as value (i.e. Content-Type: text/html).`
`unsupported_content_encoding`      | `You did not provide a valid value for the Content-Encoding header field. You need to provide "gzip" as value (i.e. Content-Encoding: gzip).`
`payload_too_large`                 | `Your payload exceeds the accepted size limit. Please do not send more than 25600 bytes. (25 kiB).`
`invalid_compressed_payload`        | `The Content-Encoding header field contains a valid value but the payload does not match the compression method provided or data is corrupt.`
`unknown_error`                     | `Unknown error.`

### Example

Following the previous example, to decompress the result only a pipe with gunzip should be added at the end of the command (i.e. ` | gunzip`).

``` {.language-text data-commands="true"}
echo "<code class=\"language-javascript\">console.log('photon');</code>" | gzip --stdout | curl --silent --request POST --header "Authorization: Token xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" --header "Content-Type: text/html" --header "Content-Encoding: gzip" --header "Accept-Encoding: gzip" --data-binary @- https://api.photon.sh/snippets | gunzip
```

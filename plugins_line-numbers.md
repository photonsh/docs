# Line Numbers

Displays line numbers.

## HTML attribute

`data-line-numbers`

### Accepted Values

#### `true`

Using `true` (recommended) will optimize the space used to display line numbers depending on the number of lines in the snippet.

#### `uniform`

In the case of the `uniform` value, a space capable of storing up to 3 digits (max. 999 lines) will be reserved for line numbers. This value is useful if you want all the snippets on the same page to have the line numbers aligned with each other.

## Example

Example using `true` to optimize the space reserved for line numbers.

The first snippet contains 9 lines and the second contains 13 lines. Because of this difference in number of digits, the `true` value causes snippets not to be aligned with each other. If this result is desired, use the `uniform` value.

### Input

``` {.language-html}
<pre><code class="language-javascript" data-line-numbers="true"></code></pre>
```

### Output

``` {.language-javascript data-line-numbers="true"}
import Koa from 'koa'

const app = new Koa()

app.use(async (ctx) => {
  ctx.body = 'Hello Koa'
})

app.listen(3000)
```

``` {.language-javascript data-line-numbers="true"}
var SocketCluster = require('socketcluster').SocketCluster;

var socketCluster = new SocketCluster({
  workers: 1,
  brokers: 1,
  port: 8000,
  appName: 'app',
  wsEngine: 'ws',
  workerController: __dirname + '/worker.js',
  brokerController: __dirname + '/broker.js',
  socketChannelLimit: 1000,
  rebootWorkerOnCrash: true
});
```

## CSS Selectors

* `.psh-line-numbers`
* `.psh-line-numbers .psh-line`
* `.psh-line-numbers .psh-line::before`
* `.psh-line-numbers.psh-line-numbers-s .psh-line::before`
* `.psh-line-numbers.psh-line-numbers-m .psh-line::before`
* `.psh-line-numbers.psh-line-numbers-l .psh-line::before`
* `.psh-line-numbers.psh-line-numbers-xl .psh-line::before`

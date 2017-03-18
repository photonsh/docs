# Remove

Highlight the specified lines in red to indicate that the lines have been deleted.

## HTML attribute

`data-remove`

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

Example showing line 1, lines 7 through 9 and line 12 with a subtraction effect.

### Input

``` {.language-html}
<pre><code class="language-rust" data-remove="1,7-9,12"></code></pre>
```

### Output

``` {.language-rust data-remove="1,7-9,12"}
extern crate iron;

use iron::prelude::*;
use iron::status;

fn main() {
  fn hello_world(_: &mut Request) -> IronResult<Response> {
    Ok(Response::with((status::Ok, "Hello World!")))
  }

  let _server = Iron::new(hello_world).http("localhost:3000").unwrap();
  println!("On 3000");
}
```

## CSS Selectors

* `.psh-remove`

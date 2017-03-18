# Filename

Displays the name of the file or resource.

## HTML attribute

`data-filename`

### Accepted Values

#### `<String>`

A single value representing the name of the file or resource to be displayed.

## Example

Example using a filename.

### Input

``` {.language-html}
<pre><code class="language-go" data-filename="/usr/src/app/hellojson.go"></code></pre>
```

### Output

``` {.language-go data-filename="/usr/src/app/hellojson.go"}
package main

import "github.com/kataras/iris"

func main(){
  iris.Get("/api/user/:id", func(ctx *iris.Context){
    userID := ctx.ParamInt("id")

    user := userRepo.GetByID(userID)

    ctx.JSON(iris.StatusOK, user)
  })

  iris.Listen("localhost:5700")
}
```

## CSS Selectors

* `.psh-filename`
* `.psh-filename > .psh-filename-value`

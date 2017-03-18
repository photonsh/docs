# Invisibles

Shows the `CHARACTER TABULATION`,` SPACE` and `LINE FEED` special characters.

`CARRIAGE RETURN` is not compatible because HTML preprocessing algorithm [gets rid of it](https://html.spec.whatwg.org/multipage/syntax.html#preprocessing-the-input-stream){target="_blank"}.

## HTML attribute

`data-invisibles`

### Accepted Values

#### `true`

Using `true` will show all special characters.

## Example

Basic example.

### Input

``` {.language-html}
<pre><code class="language-r" data-invisibles="true"></code></pre>
```

### Output

``` {.language-r data-invisibles="true"}
library(shiny)   

function(input, output) {     
  output$contents <- renderTable({
    inFile <- input$file1

    if (is.null(inFile))
    		return(NULL)

    read.csv(inFile$datapath, header=input$header, sep=input$sep, 
    		quote=input$quote)
  })
}
```

## CSS Selectors

* `.psh-invisibles-tab`
* `.psh-invisibles-tab::before`
* `.psh-invisibles-space`
* `.psh-invisibles-space::before`
* `.psh-invisibles-lf`
* `.psh-invisibles-lf::before`

## Tips and tricks

### Symbols

Selectors ending in `::before` contain the `content` property with the value of the symbol to be displayed. By default `↩` for `CHARACTER TABULATION`, `·` for `SPACE` and `⇥` for `LINE FEED`.

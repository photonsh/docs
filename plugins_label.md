# Label

Add a label to indicate the language used or a custom text.

## HTML attribute

`data-label`

### Accepted Values

#### `true`

Using `true` will make use of the automatic language formatter. For example, if the language used is `javascript`, the correct language name will appear in the label (`JavaScript`).

Some examples of automatic conversions:

* `css` -> `CSS`
* `cpp` -> `C++`
* `sml` -> `Standard ML`

#### `<String>`

Using a different value, you can add a custom label. For example: `JAVASCRIPT`, `language: js`, `Framework: Express` or any other text.

## Example

Example using `true` to invoke the automatic formatter.

### Input

``` {.language-html}
<pre><code class="language-csharp" data-label="true"></code></pre>
```

### Output

``` {.language-csharp data-label="true"}
public class SampleModule : Nancy.NancyModule
{
  public SampleModule()
  {
    Get["/"] = _ => "Hello World!";
  }
}
```

## Example

Example using a custom value.

### Input

``` {.language-html}
<pre><code class="language-csharp" data-label="C# Nancy Framework"></code></pre>
```

### Output

``` {.language-csharp data-label="C# Nancy Framework"}
public class SampleModule : Nancy.NancyModule
{
  public SampleModule()
  {
    Get["/"] = _ => "Hello World!";
  }
}
```

## CSS Selectors

* `.psh-label`
* `.psh-label-value`

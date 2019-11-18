# Parsing HTML

### How to Parse HTML aka creating the **`Doc`**-object

Skrape{it} will create a **`Doc`** -object that is representing the parsed HTML Document. 

{% tabs %}
{% tab title="Parse from Web" %}
```kotlin
skrape {
    url = "http://skrape.it"
    extract {
        htmlDocument {
            // parsed Doc is available here
        }
    }
}
```
{% endtab %}

{% tab title="Parse from File" %}
```kotlin
htmlDocument(File("path/to/file/example.html")) {
    // parsed Doc is available here
}
```
{% endtab %}

{% tab title="Parse from String" %}
```kotlin
htmlDocument("<div>skrape<b>it</b></div>") {
    // parsed Doc is available here
}
```
{% endtab %}
{% endtabs %}

### Picking Html-Elements from a Doc

Now that we have a [**`Doc`**-object](parsing-html.md#how-to-parse-html-aka-creating-the-doc-object) this is one of the parts where skrape{it} probably shines the most. It provides the possibility to pick Html-elements in a DSL-ish way. To archive this behaviour skrape{it} provides extension functions on Doc that are representing all available HTML tags following the HTML5 standart.

```kotlin
val someHtml = """
    <html>
        <head>
            <link rel="shortcut icon" href="https://some.url/icon">
            <script src="https://some.url/some-script.js"></script>
            <meta name="foo" content="bar">
        </head>
        <body>
            i'm the body
            <h1>i'm the headline</h1>
            <main>
                <p class="foo bar">i'm a paragraph</p>
                <p>i'm a second paragraph</p>
                <p>i'm a paragraph <wbr> with word break</p>
                <p>i'm the last paragraph</p>
            </main>
        </body>
    </html>
"""

htmlDocument(someHtml) {
    meta { 
        withAttribute = "name" to "foo"
        findFirst {
            attribute("content") toBe "bar"
        }
    }
    h1 {
        findFirst {
            text toBe "i'm the headline"
        }
    }
    ol {
        findFirst {
            className toContain "navigation"
        }
    }
    p {
        findAll {
            toBePresentTimes(4)
            forEach { 
                text toContain "paragraph"
            }
        }
    }
    p {
        withClass = "foo" and "bar"
        findFirst {
            text toBe "i'm a paragraph"
        }
    }
}
```

### Picking Custom HTML tags

Since the HTML5 standart it is possible create [Custom Elements](http://w3c.github.io/webcomponents/spec/custom/) that define new types of HTML elements. Such elements as well as all other elements can be selected by the use of string inkocation that will again create an css-selector and be used to pick matching elements.

```kotlin
val someHtml = """
    <body>
        <a-custom-tag>foo</a-custom-tag>
        <a-custom-tag class="some-style">bar</a-custom-tag>
    </body>
"""

htmlDocument(someHtml) {
    "a-custom-tag" {
        withClass = "some-style"
        findFirst {
            text toBe "bar"
        }
    }
}
```

### Building CSS selectors

As shown above Skrape{it} provides the possibility to pick elements by either use its corresponding dsl function or via String invokation. Both will create a **`CssSelector`**-scope that allows us to build complex css-selectors in an idiomatic fashion.

Let's imagine we want to create a selector that is matching the following complex html element:   
`<button class="foo bar" fizz="buzz" disabled>click me</button>`

We could either archive this by using a css query selector:

```kotlin
htmlDocument {
    "button.foo.bar[fizz='buzz'][disabled]" {
        findFirst { /* will pick first occurence */ }
        findAll { /* will pick all occurences */ }
    }
}
```

or we could do it even more readable and less error prone:

```kotlin
htmlDocument {
    button {
        withClass = "foo" and "bar"
        withAttribute = "fizz" to "buzz"
        withAttributeKey = "disabled"
        findFirst { /* will pick first occurence */ }
        findAll { /* will pick all occurences */ }
    }
}
```


---
description: >-
  This section describes how to scrape data from client-side rendered DOM
  elements.
---

# JS-rendered sites

Most modern webpages are dynamically adding elements or data to the DOM by the use of Javascript. Some even are single-page-applications \(SPA\) build with React.js, Vue.js, Angular, etc - that in turn means nearly the whole DOM is rendered by Javascript that has to be interpreted by a Javascript engine \(usually your Browser\).

**Skrape{it}**'s  default mode is making simple HTTP requests - and thereby it's not possible to scrape JS driven websites in default mode.

{% hint style="info" %}
**Request option `mode = Mode.DOM` for the win!**

When using **skrape{it}**'s browser mode it emulates to be a real browser, executes the pages Javascript and returns a parsed representation of a website. It supports parsing of client side rendered markup \(thereby it's possible to scrape or parse websites that uses React.js, Vue.js, Angular, jQuery and so on\). The DOM mode will use the latest Chrome engine to render the page, therefore it provides support for ES6 and modern Javascript features.

💡 Keep in mind: _**Because of the browser emulation it is not as fast as the default mode!**_
{% endhint %}

## Example

**Let's assume a pretty basic scenario. We want to make a request to a website that is rendering data via Javascript. For instance it's markup could look like this - that is adding an extra div element including some text.** 

{% code-tabs %}
{% code-tabs-item title="Example Markup that renders elements via Javascipt" %}
```markup
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>i'm the title</title>
    </head>
    <body>
        i'm the body
        <h1>i'm the headline</h1>
        <p>i'm a paragraph</p>
        <p>i'm a second paragraph</p>
    </body>
    <script>
        var dynamicallyAddedElement = document.createElement("div");
        dynamicallyAddedElement.className = "dynamic";
        var textNode = document.createTextNode("I have been dynamically added via Javascript");
        dynamicallyAddedElement.appendChild(textNode);
        document.body.appendChild(dynamicallyAddedElement);

    </script>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="How to scrape client-side rendered DOM elements" %}
```kotlin
fun main() {
    val scrapedData = skrape {
        url = "http://some.url"
        mode = Mode.DOM
        extract { 
            element("div.dynamic").text()
        }
    }
    println(scrapedData)
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Will print extracted data to the console" %}
```bash
> I have been dynamically added via Javascript
```
{% endcode-tabs-item %}
{% endcode-tabs %}




# Response

Whenever you call the `response` function of the skrape{it} DSL it will take the given request config and performs a HTTP request by the use of [the given fetcher](../fetchers/).

{% code title="Example" %}
```kotlin
skrape(AsyncFetcher) { // <-- could use any valid fetcher depending on your use-case
    request {
        // some request config
        url = "https://some.url"
        userAgent = "my fancy UA"
    }
    
    response { // 🍉 <-- response will make actual HTTP request and convert its response to a Result object 
        // the scope of 'this' inside the response lambda is Result!
        // that means you can directly call any field or function of Result here.
        
        // e.g. print the response body
        println(responseBody)
        
        // the last thing called inside the response lambda will be returned
        // e.g. the status code
        status { code }
    }
}
```
{% endcode %}

The response of a call done by a fetcher will be represented in a `Result` object.

A result comes with a bunch of basic fields as well as some handy DSL functions 

### Fields

| Name | Description | Type |
| :--- | :--- | :--- |
| responseBody | The response body as raw String representation. At this point it can be everything from HTML to XML, JSON or even plain text. | String |
| [responseStatus](status.md) | The HTTP requests response status containing the status code and message. See [Status documentation](status.md) for more information. | [Status](status.md) |
| contentType | The value of the HTTP requests Content-Type response header. | String |
| headers | Contains all the HTTP headers of the response. Additional headers with name duplicates will be ignored. | Map&lt;String, String&gt; |
| [cookies](cookies.md) | List of all given cookies. See [Cookies documentation](cookies.md) for more information. | List&lt;[Cookie](cookies.md)&gt; |
| baseUri | The `baseUri` argument is used to resolve relative URLs into absolute URLs, and should be set to the URL where the document was fetched from and will be set based on the given request URL. | String |

{% hint style="info" %}
**The html-parser artifact provides extension functions to directly parse the responseBody String to Html document \(`Doc` object\) that represents the html tree based on `DocElements` .**
{% endhint %}

### Functions




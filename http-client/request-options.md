# Request Options

### Request Options

{% hint style="info" %}
**All** of the available **options** already **have reasonable defaults** to make the use of skrape{it} as easy and intuitive as possible.
{% endhint %}

| Option | Description | Type | Default |
| :--- | :--- | :---: | :--- |
| **url** | The URL that is used to fetch and parse a web page. The protocol must be `http` or `https` | **String** | `http://localhost:8080` |
| **method** | HTTP defines a set of [**request methods**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) to indicate the desired action to be performed for a given resource. Although they can also be nouns, these request methods are sometimes referred as _HTTP verbs_. | **Method** | `GET` |
| **userAgent** | The [**User-Agent**](https://developer.mozilla.org/de/docs/Web/HTTP/Headers/User-Agent) request header contains a characteristic string that allows the network protocol peers to identify the application type, operating system, software vendor or software version of the requesting software user agent. | **String** | `Mozilla/5.0 skrape.it` |
| **headers** | \*\*\*\*[**Request headers** ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)containing more information about the resource to be fetched or about the client itself. | **Map&lt;String, String&gt;** | no additional custom headers will be sent by default |
| **cookies** | Will add Cookies to your request | **Map&lt;String, String&gt;** | will send no Cookies by default |
| **timeout** | Sets the total request timeout duration. A timeout of zero \(`0`\) is treated as an infinite timeout. | **Int** | `5000` |
| **followRedirects** | Configures the connection to \(not\) follow server redirects. | **Boolean** | `true` |
| **sslRelaxed** | Allow HTTPS connections with broken or self-signed certificates | **Boolean** | `false` |

{% code title="Full Example using all available request options" %}
```kotlin
skrape(HttpFetcher) {
    request {
        method = Method.POST // defaults to GET 
        url = "https://some.url" // you can  either pass url as String (defaults to 'http://localhost:8080')
        url { // or build url (will respect value from url as String param)
            // thereby you can pass a url and just override or add parts
            protocol = UrlBuilder.Protocol.HTTPS // defaults to given scheme from url param (HTTP if not set)
            host = "skrape.it" // defaults to given host from url param (localhost if not set)
            port = 12345  // defaults to given port from url param (8080 if not set explicitly - none port if given url param value does noit have port) - set to -1 to remove port
            path = "/foo" // defaults to given path from url param (none path if not set)
            queryParam { // can handle adding query parameters of several types (defaults to none)
                "foo" to "bar" // add query paramter foo=bar
                "aaa" to false // add query paramter aaa=false
                "bbb" to .4711 // add query paramter bbb=0.4711
                "ccc" to 42    // add query paramter ccc=42
                "ddd" to listOf("a", 1, null) // add query paramter ddd=a,1,null
                +"xxx"         // add query paramter xxx (just key, no value)
            }
        }
        timeout = 5000 // optional -> defaults to 5000ms
        followRedirects = true // optional -> defaults to true
        userAgent = "some custom user agent" // optional -> defaults to "Mozilla/5.0 skrape.it"
        cookies = mapOf("some-cookie-name" to "some-value") // optional
        headers = mapOf("some-custom-header" to "some-value") // optional
        
        authentication = basic {
            username = "admin"
            password = "password"
        }
        
        proxy = proxyBuilder {
            type = Proxy.Type.HTTP
            host = "http://some.proxy"
            port = 12345
        }
        
        sslRelaxed = true
        
        body {
            json { // will automatically set content-type header to "application/json"
                "foo" to "bar"
                "xxx" to json {
                    "a" to "b"
                    "c" to listOf(1, "d")
                }
            } // will create {"foo":"bar","xxx":{"a":"b","c":[1,"d"]}} as request body
            
            // or
            xml("<foo>bar</foo>") // will automatically set content-type header to "text/xml" 
            
            // or
            form { // will automatically set content-type header to "application/x-www-form-urlencoded"
                "foo" to "bar"
                "xxx" to 1.5
            } // will create foo=bar&xxx=1.5 as request body
        }
        // or custom body
        body {
            data = "just a plain text" // content-type header will automatically set to "text/plain"
            contentType = "your-custom/content" // can optionally override content-type
        }
    }
}
```
{% endcode %}




---
description: 'Why does skrape{it} provide its own http client implementations?'
---

# Overview

Skrape{it} offers an unified, intuitive and DSL-controlled way to make parsing of websites as comfortable as possible. 

* [x] [Http-Client DSL](../parse-html-from-web.md) without verbosity and ceremony to make requests and corresponding request options like headers, cookies etc. in a fluent style interface. 
* [x] [Pre-configure a client](../pre-configure-client.md) once to either reuse it or adjust only the things that differ at certain requests - especially handy while working with authentication flows or custom headers.
* [x] Can [handle client side rendered web pages](browserfetcher.md) \(e.g. pages created with frameworks like React.js, Angular or Vue.js or pages manipulated with jQuery or other javascript\)

```kotlin
skrape(HttpFetcher) {
    // ... request options goes here
    
    expect {
        // ... you can do some checks in here by working on the http response
        
        htmlDocument { // will parse the HTTP requests response body
            // ... parsing and do stuff with the parsed data goes here
        }
    }
    extract {
        // same behaviour as expect BUT returning a Generic, that allows you to create opbjects and pass scrped data to them.
    }
}
```

{% hint style="info" %}
The http-request is only executed after either the [**`extract`**](../../dsl/extracting-data-from-websites.md) or [**`expect`**](../../dsl/basic-test-scenario.md) function has been called. This behaviour also allows to preconfigure the http-client for multiple calls. If you use expect as well as extract it will only make 1 request.
{% endhint %}


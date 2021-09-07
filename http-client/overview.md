---
description: 'Why does skrape{it} provide its own http client implementations?'
---

# Overview

Skrape{it} offers an unified, intuitive and DSL-controlled way to make parsing of websites as comfortable as possible. 

* [x] [Http-Client DSL](request-options.md) without verbosity and ceremony to make requests and corresponding request options like headers, cookies etc. in a fluent style interface. 
* [x] [Pre-configure a client](pre-configure-client.md) once to either reuse it or adjust only the things that differ at certain requests - especially handy while working with authentication flows or custom headers.
* [x] Can [handle client side rendered web pages](fetchers/browserfetcher.md) \(e.g. pages created with frameworks like React.js, Angular or Vue.js or pages manipulated with jQuery or other javascript\)

A Http request is done as easy as in the given example. Just call the `skrape` function wherever you want in your code. It will force you to pass a [fetcher](fetchers/) and makes further[ request option](request-options.md) available in the clojure. 

```kotlin
skrape(HttpFetcher) { // <-- pass any Fetcher, e.g. HttpFetcher, BrowserFetcher, ...
    request {
        // ... request options goes here, e.g the most basic would be url
    }
    response {
        // do stuff with the response like parsing the response body ...
    }
}
```

{% hint style="info" %}
The http-request is only executed after either the `response` function has been called. This behaviour also allows to[ preconfigure the http-client](pre-configure-client.md) and reusing request settings for multiple calls.
{% endhint %}




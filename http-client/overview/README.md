---
description: 'Why does skrape{it} provide its own http client implementations?'
---

# Overview

Skrape{it} offers an unified, intuitive and DSL-controlled way to make parsing of websites as comfortable as possible. 

* [x] [Http-Client DSL](../parse-html-from-web.md) without verbosity and ceremony to make requests and corresponding request options like headers, cookies etc. in a fluent style interface. 
* [x] [Pre-configure a client](../pre-configure-client.md) once to either reuse it or adjust only the things that differ at certain requests - especially handy while working with authentication flows or custom headers.
* [x] Can [handle client side rendered web pages](browserfetcher.md) \(e.g. pages created with frameworks like React.js, Angular or Vue.js or pages manipulated with jQuery or other javascript\)

A Http request is done as easy as in the given example. Just call the `skrape` function wherever you want in your code. It will force you to pass a [fetcher](./#the-different-fetchers) and make further[ request option](../parse-html-from-web.md) available in the clojure.

```kotlin
skrape(HttpFetcher) {
    // ... request options goes here, e.g the most basic would be url
    url = "https://docs.skrape.it"
    
    expect {}
    extract {}
}
```

{% hint style="info" %}
The http-request is only executed after either the [**`extract`**](../../dsl/extracting-data-from-websites.md) or [**`expect`**](../../dsl/basic-test-scenario.md) function has been called. This behaviour also allows to[ preconfigure the http-client](../pre-configure-client.md) for multiple calls. If you use expect as well as extract it will only make 1 request.
{% endhint %}

### The Different Fetchers

Skrape{it} provides different types of Fetchers \(aka Http-Clients\) that can be passed to its DSL. All of them will execute http requests but each of them handles a different use-case. 

#### You want to scrape a simple HTML page, easy, as fast as possible, but with deactivated Javascript?

{% page-ref page="httpfetcher.md" %}

#### You want to scrape a complex website, maybe a SPA app that has been written with frameworks like React.js, Angular or Vue.js or at least rely on javascript a lot?

{% page-ref page="browserfetcher.md" %}

#### You want to scrape a simple HTML page from a coroutine?

{% page-ref page="asyncfetcher.md" %}




---
description: A Browser-ish client implementation with JS rendering support
---

# BrowserFetcher

Skrape{it} provides different fetcher implementations. All of the Fetchers behave different and you should pick them depending on your needs.

The `BrowserFetcher` is a special http client. It will send an HTTP-request \(with [given request parameters](../parse-html-from-web.md), headers etc.\) to a given url and returns a result that consists of the http response status as well as of the response headers and body. The special thing is that it will be have like a browser and will return a rendered DOM as body instead of a plain simple body string.

**It is not as fast as the other fetchers since it take some time to render a response, but the result will look simular to what you would get when surfing a page in your browser.**

Thereby it is the best pick if you want to call client-side rendered websites, e.g. Single-Page-Applications build with react.js, vue.js, angular and so on. 

{% hint style="info" %}
if you do not need skrape{it}'s full feature set you can use the BrowserFetcher standalone by adding the following dependency to your project.
{% endhint %}

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle.kts" %}
```kotlin
dependencies {
    implementation("it.skrape:skrapeit-browser-fetcher:1.1.1")
}
```
{% endcode %}
{% endtab %}

{% tab title="Maven" %}
{% code title="pom.xml" %}
```markup
<dependency>
  <groupId>it.skrape</groupId>
  <artifactId>skrapeit-browser-fetcher</artifactId>
  <version>1.1.1</version>
</dependency>
```
{% endcode %}
{% endtab %}
{% endtabs %}




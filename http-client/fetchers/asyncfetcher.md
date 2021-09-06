---
description: A none-blocking Http-Client implementation
---

# AsyncFetcher

Skrape{it} provides different fetcher implementations. All of the Fetchers behave different and you should pick them depending on your needs.

The `AsyncFetcher` is a none-blocking http client. It will send an HTTP-request \(with [given request parameters](../parse-html-from-web.md), headers etc.\) to a given url and returns a result that consists of the http response status as well as of the response headers and body in a none-blocking fashion by the use of coroutines. Thereby it can be convenient called from a suspend function.

**It is fast, robust and result will look simular to what you would get when surfing a page in your browser with deactivated Javascript.**

Thereby it is the best pick if you want to call websites in parallel or at least from a coroutine scope and if you just don't care about the excecution of a websites Javascript. 

{% hint style="info" %}
if you do not need skrape{it}'s full feature set you can use the AsynFetcher standalone by adding the following dependency to your project.
{% endhint %}

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle.kts" %}
```kotlin
dependencies {
    implementation("it.skrape:skrapeit-asyn-fetcher:1.1.1")
}
```
{% endcode %}
{% endtab %}

{% tab title="Maven" %}
{% code title="pom.xml" %}
```markup
<dependency>
  <groupId>it.skrape</groupId>
  <artifactId>skrapeit-async-fetcher</artifactId>
  <version>1.1.1</version>
</dependency>
```
{% endcode %}
{% endtab %}
{% endtabs %}


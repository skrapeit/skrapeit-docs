---
description: A "classic" Http-Client implementation
---

# HttpFetcher

Skrape{it} provides different fetcher implementations. All of the Fetchers behave different and you should pick them depending on your needs.

The `HttpFetcher` is a classic http client. It will send an HTTP-request \(with [given request parameters](../request-options.md), headers etc.\) to a given url and returns a result that consists of the http response status as well as of the response headers and body. Nothing more, nothing less.

**It is fast, robust and result will look simular to what you would get when surfing a page in your browser with deactivated Javascript.**

Thereby it is the best pick if you want to call server-side rendered websites, a static html pages or if you just don't care about the excecution of a websites Javascript. 

{% hint style="info" %}
if you do not need skrape{it}'s full feature set you can use the HttpFetcher standalone by adding the following dependency to your project.
{% endhint %}

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle.kts" %}
```kotlin
dependencies {
    implementation("it.skrape:skrapeit-http-fetcher:1.1.5")
}
```
{% endcode %}
{% endtab %}

{% tab title="Maven" %}
{% code title="pom.xml" %}
```markup
<dependency>
  <groupId>it.skrape</groupId>
  <artifactId>skrapeit-http-fetcher</artifactId>
  <version>1.1.5</version>
</dependency>
```
{% endcode %}
{% endtab %}
{% endtabs %}

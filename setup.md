# Setup

## Getting Super Powers

**Becoming a super hero is a fairly straight forward process:**

{% tabs %}
{% tab title="Maven" %}
{% code-tabs %}
{% code-tabs-item title="pom.xml" %}
```markup
<dependency>
  <groupId>it.skrape</groupId>
  <artifactId>skrapeit-core</artifactId>
  <version>0.6.0</version>
</dependency>
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}

{% tab title="Gradle" %}
{% code-tabs %}
{% code-tabs-item title="build.gradle.kts" %}
```kotlin
dependencies {
    compile("it.skrape:skrapeit-core:0.6.0")
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}
{% endtabs %}

Once you're strong enough, let's either scrape the world or make your markup a safer place!

**Skrape{it} provides several bindings for some well-known testing-frameworks and HTTP-clients:**

* \*\*\*\*[**Spring MockMvc extension**](extensions/mockmvc/)\*\*\*\*
* \*\*\*\*[**Ktor extension**](extensions/ktor/)\*\*\*\*

{% hint style="info" %}
Super-powers are granted randomly so please submit an [**issue**](https://github.com/skrapeit/skrape.it/issues) if you're not happy with yours or feels like you're missing some.   
🤝 Contributions are very welcome as well.
{% endhint %}


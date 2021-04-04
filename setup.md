# Setup

## Getting Super Powers

**Becoming a super hero is a fairly straight forward process:**

{% tabs %}
{% tab title="Maven" %}
{% code title="pom.xml" %}
```markup
<dependency>
  <groupId>it.skrape</groupId>
  <artifactId>skrapeit</artifactId>
  <version>1.0.0</version>
</dependency>
```
{% endcode %}
{% endtab %}

{% tab title="Gradle" %}
{% code title="build.gradle.kts" %}
```kotlin
dependencies {
    compile("it.skrape:skrapeit:1.0.0")
}
```
{% endcode %}
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

### **Using bleeding edge features before official release** 🚀 

We are offering snapshot releases via jitpack. Thereby you can install every commit and version you want. But be careful, these are non official releases and may be unstable as well as breaking changes can occur at any time.

{% tabs %}
{% tab title="Maven" %}
{% code title="pom.xml" %}
```markup
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>

...

<dependency>
    <groupId>com.github.skrapeit</groupId>
    <artifactId>skrape.it</artifactId>
    <version>master-SNAPSHOT</version>
</dependency>
```
{% endcode %}
{% endtab %}

{% tab title="Gradle" %}
{% code title="build.gradle.kts" %}
```kotlin
repositories {
    maven { url "https://jitpack.io" }
}
dependencies {
    implementation("com.github.skrapeit:skrape.it:master-SNAPSHOT")
}
```
{% endcode %}
{% endtab %}
{% endtabs %}


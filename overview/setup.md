# Setup

## Getting Super Powers

**Becoming a super hero is a fairly straight forward process.**

Checkout the latest releases on [maven central](https://search.maven.org/search?q=g:it.skrape) and just add the following to your build tool of choice to get the full feature set:

{% tabs %}
{% tab title="Maven" %}
{% code title="pom.xml" %}
```markup
<dependency>
  <groupId>it.skrape</groupId>
  <artifactId>skrapeit</artifactId>
  <version>1.1.5</version>
</dependency>
```
{% endcode %}
{% endtab %}

{% tab title="Gradle" %}
{% code title="build.gradle.kts" %}
```kotlin
dependencies {
    implementation("it.skrape:skrapeit:1.1.5")
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

Once you're strong enough, let's either scrape the world or make your markup a safer place!

**Skrape{it} provides several bindings for some well-known testing-frameworks and HTTP-clients:**

* \*\*\*\*[**Spring MockMvc extension**](../extensions/mockmvc/)\*\*\*\*
* \*\*\*\*[**Ktor extension**](../extensions/ktor/)\*\*\*\*

{% hint style="info" %}
Super-powers are granted randomly so please submit an [**issue**](https://github.com/skrapeit/skrape.it/issues) if you're not happy with yours or feels like you're missing some.   
🤝 Contributions are very welcome as well.
{% endhint %}

### **Using bleeding edge features before official release** 🚀 

We are offering snapshot releases by publishing every successful build of a commit that has been pushed to master branch. Thereby you can just install the latest implementation of skrape{it}.  
Be careful since these are non-official releases and may be unstable as well as breaking changes can occur at any time.

{% tabs %}
{% tab title="Maven" %}
{% code title="pom.xml" %}
```markup
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://oss.sonatype.org/content/repositories/snapshots/</url>
    </repository>
</repositories>

...

<dependency>
    <groupId>it.skrape</groupId>
    <artifactId>skrapeit</artifactId>
    <version>0-SNAPSHOT</version>
</dependency>
```
{% endcode %}
{% endtab %}

{% tab title="Gradle" %}
{% code title="build.gradle.kts" %}
```kotlin
repositories {
    maven { url = uri("https://oss.sonatype.org/content/repositories/snapshots/") }
}
dependencies {
    implementation("it.skrape:skrapeit:0-SNAPSHOT") { 
        isChanging = true 
    } // version number will stay - implementation may change ...
}

// optional
configurations.all {
    resolutionStrategy {
        cacheChangingModulesFor(0, "seconds")
    }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}


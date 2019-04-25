# Setup



{% hint style="info" %}
In order to use the Ktor-extension it's required to have the [**skrapeit-core**](../setup.md#getting-super-powers) artifact in the classpath as well as having a proper Ktor setup up and running.
{% endhint %}

{% tabs %}
{% tab title="Maven" %}
{% code-tabs %}
{% code-tabs-item title="pom.xml" %}
```markup
<dependency>
   <groupId>it.skrape</groupId>
   <artifactId>skrapeit-core</artifactId>
   <version>LATEST</version>
   <scope>test</scope>
</dependency>
<dependency>
   <groupId>it.skrape</groupId>
   <artifactId>skrapeit-ktor</artifactId>
   <version>LATEST</version>
   <scope>test</scope>
</dependency>
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}

{% tab title="Gradle" %}
{% code-tabs %}
{% code-tabs-item title="build.gradle.kts" %}
```kotlin
testCompile("it.skrape:skrapeit-core:+")
testCompile("it.skrape:skrapeit-ktor:+")
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}
{% endtabs %}


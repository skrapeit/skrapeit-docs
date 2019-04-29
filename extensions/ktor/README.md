# Ktor

### Setup

{% hint style="info" %}
In order to use the Ktor-extension it's required to have the [**skrapeit-core**](../../setup.md#getting-super-powers) artifact in the classpath as well as having a proper Ktor setup up and running.
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

### How to Use

The [**skrape{it}**](../../) **Ktor-extension** will extend Ktor's `TestApplicationResponse` with an`expectHtml{}` lambda function. The scope of the lambda will give you a parsed response body \(deserialized to a `Doc`\) and enables you to make comfortable assumptions about the content, properties and structure of the document. 

![Documentation by example](../../.gitbook/assets/example-usage%20%282%29.gif)


---
description: >-
  An Extension for Spring MockMvc tests to enable meaningful testing of
  controllers that produces HTML.
---

# MockMvc

### Setup

{% hint style="info" %}
In order to use the MockMvc-extension it's required to have the [**skrapeit-core**](../../setup.md#getting-super-powers) artifact in the classpath as well as having a proper spring-test / spring-boot-test setup.
{% endhint %}

{% tabs %}
{% tab title="Maven" %}
{% code title="pom.xml" %}
```markup
<dependency>
   <groupId>it.skrape</groupId>
   <artifactId>skrapeit-core</artifactId>
   <version>LATEST</version>
   <scope>test</scope>
</dependency>
<dependency>
   <groupId>it.skrape</groupId>
   <artifactId>skrapeit-mockmvc</artifactId>
   <version>LATEST</version>
   <scope>test</scope>
</dependency>
```
{% endcode %}
{% endtab %}

{% tab title="Gradle" %}
{% code title="build.gradle.kts" %}
```kotlin
testCompile("it.skrape:skrapeit-core:+")
testCompile("it.skrape:skrapeit-mockmvc:+")
```
{% endcode %}
{% endtab %}
{% endtabs %}

### How to Use

The [**skrape{it}**](../../) **MockMvc-extension** will extend MockMvc's `ResultActions` with an `andExpectHtml{}` lambda function. The scope of the lambda will give you a parsed response body \(deserialized to a `Doc`\) and enables you to make comfortable assumptions about the content, properties and structure of the document. 

![Documentation by example](../../.gitbook/assets/example-usage.gif)


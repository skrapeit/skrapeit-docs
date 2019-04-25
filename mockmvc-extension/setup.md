---
description: >-
  An Extension for Spring MockMvc tests to enable meaningful testing of
  controllers that produces HTML.
---

# Setup

{% hint style="info" %}
In order to use the MockMvc-extension it's required to have the [**skrapeit-core**](../setup.md#getting-super-powers) artifact in the classpath as well as having a proper spring-test / spring-boot-test setup.
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
   <artifactId>skrapeit-mockmvc</artifactId>
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
testCompile("it.skrape:skrapeit-mockmvc:+")
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}
{% endtabs %}


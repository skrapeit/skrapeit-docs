# Pre-configure client

Sometimes you may want to reuse your [HTTP Client configuration](request-options.md) to avoid code duplication or to archive better maintainability of your code base.  
Skrape{it} supports shared client configurations by default -- you just need to configure the client properties you want to reuse using the skrape{it} DSL without calling the `response` function. 

Calling the `request` function will create a `Request` object which can then be stored to a variable.

{% hint style="info" %}
The DSL is design to behave like fluent API, which means it will always return the return value of the last thing that was called inside the `skrape` lambda function.
{% endhint %}

```kotlin
val myPreConfiguredClient = skrape(HttpFetcher) {
    request {
        timeout = 10_000
        headers = mapOf("some-custom-header" to "some-value")
        followRedirects = true
    }
}

@Test
fun `can use preconfigured client straight away`() {

    myPreConfiguredClient.response {
        status { code toBe 200 }
        headers.getValue("some-custom-header") toBe "some-value"
    }
}

@Test
fun `can use preconfigured client but slightly modify`() {

    myPreConfiguredClient.apply {
        request {
            followRedirects = false
        }
    }.response {
        status { code toBe 301 }
        headers.getValue("some-custom-header") toBe "some-value"
    }
}
```


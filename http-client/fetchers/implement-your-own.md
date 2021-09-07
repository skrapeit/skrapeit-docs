# Implement your own

By providing different HTTP client implementations that already fulfill the need of [having good old Http requests](httpfetcher.md), [imitating a browser by executing Javascript](browserfetcher.md) and [doing async http calls](asyncfetcher.md) you probably have special requirements that are hard to meet using the provided client implementations but on the other hand you still want to use the full skrape{it} DSL experience.

All the Fetchers are implementing either [BlockingFetcher or a NonBlockingFetcher](https://github.com/skrapeit/skrape.it/blob/master/fetcher/base-fetcher/src/main/kotlin/it/skrape/fetcher/BaseFetcher.kt) which are interfaces provided by the skrape{it} library. Both of them wants to have an implementation of a fetch method and requestBuilder.

In the example we implement a BlockingFetcher that can be passed to the skrape{it} DSL that is using Ktors different HttpClient implementations under the hood.

{% code title="implement custom fetcher" %}
```kotlin
class KtorBlockingFetcher(val ktorClient: HttpClient) : BlockingFetcher<HttpRequestBuilder> {
    override fun fetch(request: HttpRequestBuilder): Result = runBlocking {
        with(ktorClient.request<HttpResponse>(request)) {
            Result(
                responseBody = readText(),
                responseStatus = Result.Status(status.value, status.description),
                contentType = contentType()?.toString(),
                headers = headers.toMap().mapValues { it.value.firstOrNull().orEmpty() },
                baseUri = request.url.toString(),
                cookies = listOf(setCookie()) as List<Cookie>
            )
        }
    }

    override val requestBuilder: HttpRequestBuilder
        get() = HttpRequestBuilder()
}
```
{% endcode %}

{% code title="use custom fetcher" %}
```kotlin
val KTOR_CLIENT = HttpClient(Apache)

val result = skrape(KtorBlockingFetcher(KTOR_CLIENT)) {
    request {
        url = "http://some.url"
    }

    response {
        // do your stuff here
    }
}
```
{% endcode %}


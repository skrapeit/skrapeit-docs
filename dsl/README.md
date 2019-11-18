# How to Use

> **People find DSLs valuable because a well-designed DSL can be much easier to program with than a traditional library. This improves programmer productivity, which is always valuable.**
>
> Martin Fowler

### The Skrape{it} DSL$$_1$$ is the recommended way of using the library. It offers the highest level of features and usability.

The DSL should be nearly self-explaining. Depending on your use-case here is an example with explanations on how to use skrape{it} to write automated tests that validates an endpoint or an URL that is returning HTML:

```kotlin
class CompleteSkrapeItExampleTest {
    
@Test
internal fun `dsl can skrape by url`() {
    skrape {
        url = "http://localhost:8080/example"
        
        mode = DOM // optional -> defaults to SOURCE (plain http request) - DOM will also render JS
        method = GET // optional -> defaults to GET
        timeout = 5000 // optional -> defaults to 5000ms
        followRedirects = true // optional -> defaults to true
        userAgent = "some custom user agent" // optional -> defaults to "Mozilla/5.0 skrape.it"
        cookies = mapOf("some-cookie-name" to "some-value") // optional
        headers = mapOf("some-custom-header" to "some-value") // optional
        
        extract {
            htmlDocument {
                // all offical html and html5 elements are supported by the DSL
                div {
                    withClass = "foo" and "bar" and "fizz" and "buzz"
                    withAttribute = "some-key" to "some-value"
                    // will create css-query div.foo.bar.fizz.buzz[some-key='some-value']
                    
                    findFirst { // will find the first matching occurence 
                        text toBe "div with class foo"
                    }

                    findAll { // will find the all matching occurences
                        toBePresentExactlyOnce()
                    }
                }
                // can handle custom tags as well
                "a-custom-tag" {
                    findFirst {
                        text toBe "i'm a custom html5 tag"
                    }
                }
                // can handle custom tags written in css selctor query syntax
                "div.foo.bar.fizz.buzz" {
                    findFirst {
                        text toBe "div with class foo"
                    }
                }

                // can handle custom tags and add selector specificas via DSL
                "div.foo" {

                    withClass = "bar" and "fizz" and "buzz"

                    findFirst {
                        text toBe "div with class foo"
                    }
                }
            }
        }
    }
}
}
```

To learn more about the possible request-options please have a look here:

{% page-ref page="parse-html-from-web.md" %}

To learn more about the parsing html and working with elements please have a look here:

{% page-ref page="parsing-html.md" %}

To learn more about the build-in matchers please have a look here:

{% page-ref page="matchers.md" %}



Further Testing Example:

{% page-ref page="basic-test-scenario.md" %}

Further information on what is the best way to actually scrape the content of an webpage and work with that data can be found here:

{% page-ref page="extracting-data-from-websites.md" %}

#### 

* > $$1)$$ A [**domain-specific language** \(**DSL**\)](https://en.wikipedia.org/wiki/Domain-specific_language) is a computer language specialized to a particular application domain.


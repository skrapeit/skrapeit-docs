# Testing

### Testing an Endpoint that is returning HTML

#### Let's assume a request to the URL `http://localhost:8080/example` will respond with the following markup:

```markup
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>i'm the title</title>
    </head>
    <body>
        i'm the body
        <h1>i'm the headline</h1>
        <p>i'm a paragraph</p>
        <p>i'm a second paragraph</p>
    </body>
</html>
```

#### What we want to do is to call the URL with a HTTP-Request `GET` and verify certain assumptions in a defined html-structure. Because Skrape{it} has no direct bindings to a certain test-runner or library it works seamlesly with all different Test-Runners. Just to give you a clue how a typical test that is using the Skrape{it} DSL would look like you can find multiple examples of the same test scenario here:

{% tabs %}
{% tab title="jUnit 5" %}
```kotlin
class ExampleTest {

    @Test
    internal fun `can parse and verify response of example endpoint`() {
        skrape {
            url = "http://localhost:8080/example"
            expect {
                statusCode toBe 200
                statusMessage toBe "OK"
                contentType toBe "text/html; charset=UTF-8"

                p {
                    findFirst {
                        text toBe "i'm a paragraph"
                    }
                    findAll {
                        size toBe 2
                    }
                }
            }
        }
    }
}
```
{% endtab %}

{% tab title="jUnit 5 & assertJ" %}
```kotlin
class ExampleTest {

    @Test
    internal fun `can parse and verify response of example endpoint`() {
        skrape {
            url = "http://localhost:8080/example"
            expect {
                assertThat(statusCode).isEqualTo(200)
                assertThat(statusMessage).isEqualTo("OK")
                assertThat(contentType).isEqualTo("text/html; charset=UTF-8")

                p {
                    findFirst {
                        assertThat(text()).isEqualTo("i'm a paragraph")
                    }
                    findAll {
                        assertThat(size).isEqualTo(2)
                    }
                }
            }
        }
    }
}
```
{% endtab %}

{% tab title="KotlinTest" %}
```kotlin
class ExampleTest : StringSpec({

    "can parse and verify response of example endpoint" {
        skrape {
            url = "http://localhost:8080/example"
            expect {
                statusCode shouldBe 200
                statusMessage shouldBe "OK"
                contentType shouldBe "text/html; charset=UTF-8"

                p {
                    findFirst {
                        text toBe "i'm a paragraph"
                    }
                    findAll {
                        size toBe 2
                    }
                }
            }
        }
    }
})
```
{% endtab %}

{% tab title="Spek" %}
```kotlin
object ExampleSpec: Spek({
    describe("example endpoint") {
        it("returns expected markup") {
            skrape {
                url = "http://localhost:8080/example"
                expect {
                    statusCode toBe 200
                    statusMessage toBe "OK"
                    contentType toBe "text/html; charset=UTF-8"
    
                    p {
                        findFirst {
                            text toBe "i'm a paragraph"
                        }
                        findAll {
                            size toBe 2
                        }
                    }
                }
            }
        }
    }
})
```
{% endtab %}

{% tab title="Spek & assertJ" %}
```kotlin
object ExampleSpec: Spek({
    describe("example endpoint") {
        it("returns expected markup") {
            skrape {
                url = "http://localhost:8080/example"
                expect {
                    assertThat(statusCode).isEqualTo(200)
                    assertThat(statusMessage).isEqualTo("OK")
                    assertThat(contentType).isEqualTo("text/html; charset=UTF-8")
    
                    p {
                        findFirst {
                            text toBe "i'm a paragraph"
                        }
                        findAll {
                            size toBe 2
                        }
                    }
                }
            }
        }
    }
})
```
{% endtab %}
{% endtabs %}


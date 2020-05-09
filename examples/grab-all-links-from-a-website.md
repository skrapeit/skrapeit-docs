# Grab all links from a Website

```bash
fun main() {
    val links: List<String> = skrape {
        url = "https://kotlinlang.org/docs/reference/"
        mode = Mode.SOURCE
        extract {
            htmlDocument {
                a {
                    findAll {
                        eachHrefAsAbsoluteLink()
                    }
                }
            }
        }
    }
    println(links)
}
```

{% hint style="info" %}
 Consider to change the mode from `SOURCE` to `DOM` if you are targeting a client-side rendered website.
{% endhint %}

And here we go:

{% code title="console output:" %}
```bash
[https://kotlinconf.com/registration, https://play.kotlinlang.org, https://github.com/JetBrains/kotlin-web-site/edit/master/pages/docs/reference/index.md, https://www.jetbrains.com/help/education/learner-start-guide.html?section=Kotlin%20Koans, https://www.jetbrains.com/help/idea/converting-a-java-file-to-kotlin-file.html, https://blog.jetbrains.com/kotlin/, https://discuss.kotlinlang.org/, https://surveys.jetbrains.com/s3/kotlin-slack-sign-up, https://stackoverflow.com/questions/tagged/kotlin, https://play.kotlinlang.org, https://play.kotlinlang.org/byExample, https://play.kotlinlang.org/koans, https://www.amazon.com/Kotlin-Programming-Nerd-Ranch-Guide/dp/0135161630, https://leanpub.com/kotlin-for-android-developers, https://www.atomickotlin.com/atomickotlin/, https://www.manning.com/books/kotlin-in-action, http://shop.oreilly.com/product/0636920052982.do, http://shop.oreilly.com/product/0636920052999.do, https://www.coursera.org/learn/vvedenie-v-yazyk-kotlin, https://coursera.org/learn/kotlin-for-java-developers, https://www.jetbrains.com/company/partners/kotlin/, https://kotlin.link, https://superkotlin.com/blog/, https://github.com/JetBrains/kotlin-web-site/blob/master/LICENSE, https://kotlinlang.org/foundation/kotlin-foundation.html, http://jetbrains.com]
```
{% endcode %}

## Grab all links including its text from a Website

```bash
fun main() {
    val links: Map<String, String> = skrape {
        url = "https://kotlinlang.org/docs/reference/"
        extract {
            htmlDocument {
                a {
                    withAttributeKey = "href"
                    findAll {
                        map {
                            it.text to it.attribute("abs:href")
                        }.toMap()
                    }
                }

            }
        }
    }

    links.forEach { (text, link) -> println("$text --> $link")}
}
```

And here we go:

{% code title="console output:" %}
```text
Kotlin Heroes Coding Challenge Take Part! --> https://www.jetbrains.com/promo/kotlin-heroes/
Kotlin --> https://kotlinlang.org/
1.3.61 --> https://github.com/JetBrains/kotlin/releases/tag/v1.3.61
Learn --> https://kotlinlang.org/docs/reference/
Community --> https://kotlinlang.org/community/
Play --> https://play.kotlinlang.org
Language Guide --> https://kotlinlang.org/docs/reference/
Tutorials --> https://kotlinlang.org/docs/tutorials/
Books --> https://kotlinlang.org/docs/books.html
More resources --> https://kotlinlang.org/docs/resources.html
Kotlin for Server Side --> https://kotlinlang.org/docs/reference/server-overview.html
Kotlin for Android --> https://kotlinlang.org/docs/reference/android-overview.html
Kotlin for JavaScript --> https://kotlinlang.org/docs/reference/js-overview.html
Kotlin for Native --> https://kotlinlang.org/docs/reference/native-overview.html
Kotlin for Data Science --> https://kotlinlang.org/docs/reference/data-science-overview.html
Coroutines --> https://kotlinlang.org/docs/reference/coroutines-overview.html
...
```
{% endcode %}


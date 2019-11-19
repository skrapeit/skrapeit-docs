# Grab all links from a Website

```bash
val links: List<String> = skrape {
        url = "https://kotlinlang.org/docs/reference/"
        mode = Mode.SOURCE
        extract {
            htmlDocument {
                a {
                    findAll {
                        eachHrefAsAbsoluteLink
                    }
                }
            }
        }
    }

println(links)
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




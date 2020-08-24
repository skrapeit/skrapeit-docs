---
description: >-
  If you want to extract data from websites this is the part of the
  documentation you where looking for.
---

# Scraping

💡 **Let's assume a pretty basic scenario. We want to make a request to a github profile page and extract the nickname of the profiles owner as well as getting the names of them pinned repositories.** 

### Documentation by Example

All of the interesting parts are marked with  an \(ℹ️\) and explained at the bottom of the code sample.

```kotlin
import it.skrape.core.htmlDocument
import it.skrape.selects.and
import it.skrape.selects.eachImage
import it.skrape.selects.eachText
import it.skrape.selects.html5.a
import it.skrape.selects.html5.div
import it.skrape.selects.html5.p
import it.skrape.selects.html5.span
import org.junit.jupiter.api.Test

// just some object where we will store our scraped data
data class MyExtractedData(
            var httpMessage: String = "",
            var userName: String = "",
            var repositoryNames: List<String> = emptyList(),
            var theThirdRepositoriesName: String = "",
            var firstThreeHrefs: List<String> = emptyList(),
            var overviewLink: String = "",
            var firstThreeImageSources: List<String> = emptyList(),
            var title: String = "",
            var starsCount: String = ""
    )

fun main() {
    val extracted = skrape { // 1️⃣
        url = "https://github.com/skrapeit" 
    
        extractIt<MyExtractedData> { it ->
            it.httpMessage = status { message } // 2️⃣
            htmlDocument { // 3️⃣
                relaxed = true // 4️⃣
    
                it.userName = ".h-card .p-nickname" { findFirst { text } } // 5️⃣
                val repositories = span(".repo") { findAll { this }} // 6️⃣
                println("hello world") // 7️⃣
                it.repositoryNames = repositories.filter { it.text.contains("skrape") }.eachText // 8️⃣
                it.theThirdRepositoriesName = span(".repo") { 
                    2 { text } // 9️⃣
                }
                it.firstThreeImageSources = findAll { eachImage.map { image -> image.value } }.take(3) // 1️⃣0️⃣
                it.firstThreeHrefs = findAll { eachHref }.take(3) // 1️⃣1️⃣ 
                it.overviewLink = findAll { eachLink["Overview"] ?: "not found" } // 1️⃣2️⃣ 
                it.title = titleText // 1️⃣3️⃣
    
                // *️⃣
                it.starsCount = div { // 1️⃣5️⃣ 
                    withClass = "pinned-item-list-item"
                    findFirst {
                        p { // 1️⃣6️⃣
                            findSecond {
                                a {
                                    // 1️⃣7️⃣ 
                                    withClass = "pinned-item-meta" and "muted-link" // 1️⃣8️⃣
                                    withAttribute = "href" to "/skrapeit/skrape.it/stargazers" // 1️⃣9️⃣
    
                                    findFirst {
                                        ownText
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    }
    println(extracted)
}
```

{% code title="Will print extracted data to the console" %}
```bash
> hello world
> MyExtractedData(httpMessage=OK, userName=skrapeit, repositoryNames=[skrape.it, skrapeit-ktor-extension, skrapeit-mockmvc-extension, skrapeit-docs], theThirdRepositoriesName=skrapeit-mockmvc-extension, firstThreeHrefs=[https://github.githubassets.com, https://avatars0.githubusercontent.com, https://avatars1.githubusercontent.com], overviewLink=/skrapeit, firstThreeImageSources=[https://github.githubassets.com/images/spinners/octocat-spinner-128.gif, https://avatars0.githubusercontent.com/u/46688980?s=88&u=c99dfeadc23ab06f4c428ffd4330e95f0b32d2cb&v=4, https://avatars0.githubusercontent.com/u/46688980?s=460&u=c99dfeadc23ab06f4c428ffd4330e95f0b32d2cb&v=4], title=skrapeit · GitHub, starsCount=119)

```
{% endcode %}

{% hint style="info" %}
1⃣ We are in the scope of skrape{} here. This is the place to configure your request. The code example we are only defining the url we want to make a request against but there are a lot [**more options to configure the request**](parse-html-from-web.md).
{% endhint %}

{% hint style="info" %}
2️⃣ In the extract scope we are able to get everything from the http request, such as http status code and message, http-headers, Cookies, ... , as well as the response body as plain String.
{% endhint %}

{% hint style="info" %}
3️⃣ The `htmlDocument` lambda function will take the response body and converts it into a `Doc` object that allows us to parse it in a convenient fashion.
{% endhint %}

{% hint style="info" %}
4️⃣ You can optionally activate the relaxed html parsing mode \(defaults to false\). The non relaxed mode will throw meaningful exception if an element could not be found, the relaxed one will just proceed and return emtpy lists or strings for selections that can not be found in the HTML document.
{% endhint %}

{% hint style="info" %}
5️⃣ To query a certain element you can invoke plain CSS-selector queries as string and directly use the picked element inside the lambde function to do your stuff. 🌶 
{% endhint %}

{% hint style="info" %}
6️⃣  You can pass additional css selector query to an element that will be automatically merged to a valid selector. The example is equal to `span.repo`.
{% endhint %}

{% hint style="info" %}
7️⃣ Just for clarification in case you are not familiar with kotlin-DSLs already, it's a DSL, means you can just put any other valid kotlin code inside of here. 🙂 
{% endhint %}

{% hint style="info" %}
8️⃣  The `findAll {}` is returning a List&lt;DocElement&gt;, means you can use all of Kotlins collection functions to do stuff with your selected elements
{% endhint %}

{% hint style="info" %}
9️⃣ On a defined selector, you can invoke an integer as a lambda function that will act as a shorthand to pick the nth occurrence of an element.
{% endhint %}

{% hint style="info" %}
1️⃣0️⃣ We are using one of the convenient shorthand functions \(eachImage\) to get all images \(will return a map of alt-text to src\) here. Additionally there are more shorthands to parse all links, all hrefs, all source attribute values and more.
{% endhint %}

{% hint style="info" %}
1️⃣1️⃣ Another shorthand example that is getting the values of all href attributes that are contained in the HTML document and stores the first 3 items.
{% endhint %}

{% hint style="info" %}
1️⃣2️⃣ Because of you can just use any valid Koltin code inside the DSL and the `eachLink` function will find each link as map of text to url you can get a specific href by its text by kotlins usual map access.
{% endhint %}

{% hint style="info" %}
1️⃣3️⃣ Here we are using some more handy helpers like titleText \(shorthand for `title { findFirst { text } }` \) but this time we are operating top level on the parsed HTML document. 
{% endhint %}

{% hint style="info" %}
\*️⃣ In the next few lines of code we are doing a complex and nested search for of element. The example will select `div.pinned-item-list-item p:(2)` but in a much more readable way than using a plain CSS-selector query.

1️⃣5️⃣ As you will see from here and the next marker you can nest a html element query to keep complex selections comprehensible and readable.

1️⃣6️⃣ element selection are nesting, so we will search for the second p-tag inside the **parent** `div.pinned-item-list-item` only. This is really powerful behaviour. 🙃 

1️⃣7️⃣ You can define properties of an element without having deep knowledge about CSS-selector query syntax by just setting properties without the foo to keep things simple and readable.

1️⃣8️⃣ Properties that are of type `String` can conveniently be chained with the provided `and` function. 🚀 

1️⃣9️⃣ Properties that are of type `Map<String, String>` can directly be passed as `Pair` values. 🤯 sexy...
{% endhint %}




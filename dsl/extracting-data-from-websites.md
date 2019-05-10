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
import it.skrape.extract
import it.skrape.selects.`$`
import it.skrape.selects.el
import it.skrape.skrape

data class MyScrapedData(
    val userName: String, 
    val repositoryNames: List<String>
)

fun main() {
    val githubUserData = skrape {
        url = "https://github.com/skrapeit" //ℹ️1
        
        extract {
            MyScrapedData(
                    userName = el(".h-card .p-nickname").text(), //ℹ️2
                    repositoryNames = `$`("span.repo").map { it.text() } //ℹ️3
            )
        }
    }
    println("${githubUserData.userName}'s repos are ${githubUserData.repositoryNames}")
}
```

{% code-tabs %}
{% code-tabs-item title="Will print extracted data to the console" %}
```bash
> skrapeit's repos are [skrape.it]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
1⃣ We are in the scope of skrape{} here. This is the place to configure your request. The code example we are only defining the url we want to make a request against but there are a lot [**more options to configure the request**](how-to-make-a-http-request.md).

2⃣ To select the first occurrence of an element within the html tree you can use the `el()` function in the scope of `extract{}`. It is expecting an CSS selector String and will return an object of type`Element`.  
There's a lot you can do with an `Element`, in this example we just want to get its text. You can find a full list of the methods `Element` offers over [**here**](https://jsoup.org/apidocs/org/jsoup/nodes/Element.html).

3⃣ To select ALL occurrences of an element within the html tree you can use the `$()` function in the scope of `extract{}`. It is expecting an CSS selector String and will return an `Elements` object. Elements is basically an `ArrayList<Element>.`  
You can find a full list of the methods `Elements` offers over [**here**](https://jsoup.org/apidocs/org/jsoup/select/Elements.html).
{% endhint %}


# Creating a RESTful API \(Spring-Boot\)

This is a basic example on how you could build a REST API directly return data from a scraped website as JSON:

```kotlin
import it.skrape.extract
import it.skrape.selects.`$`
import it.skrape.selects.el
import it.skrape.skrape
import org.springframework.web.bind.annotation.GetMapping
import org.springframework.web.bind.annotation.RestController

@RestController
class MyController {

    @GetMapping("/user-data")
    fun extractGithubUserData() =
        skrape {
            url = "https://github.com/skrapeit"
            extract {
                MyScrapedData(
                    userName = el(".h-card .p-nickname").text(),
                    repositoryNames = `$`("span.repo").map { it.text() }
                )
            }
        }
}

data class MyScrapedData(val userName: String, val repositoryNames: List<String>)
```

This will return the following JSON as response body when `/user-data` is getting called: 

```javascript
{
  "userName": "skrapeit",
  "repositoryNames": [
    "skrape.it"
  ]
}
```


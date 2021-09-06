# Fetchers

{% hint style="info" %}
Skrape{it} provides different types of Fetchers \(aka Http-Clients\) that can be passed to its DSL. All of them will execute http requests but each of them handles a different use-case.
{% endhint %}

Depending on your use-case you may want to choose a certain Fetcher implementation that fits your needs. Each of the different fetchers comes with different advantages / features. To pick the one that suits you best you should ask yourself following questions:  
  
**You want to scrape a simple HTML page, easy, as fast as possible, but with deactivated Javascript?**

#### You want to scrape a complex website, maybe a SPA app that has been written with frameworks like React.js, Angular or Vue.js or at least rely on javascript a lot?

{% page-ref page="browserfetcher.md" %}

#### You want to scrape multiple HTML pages in parallel from inside a coroutine?

{% page-ref page="asyncfetcher.md" %}


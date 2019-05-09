---
description: A Story of Deserializing HTML / XML.
---

# Introduction

{% hint style="info" %}
[**skrape{it}**](http://www.skrape.it) is a Kotlin-based HTML / XML testing and web scraping parser-library that can be used seamlessly in Spring-Boot, Android or other JVM projects. It places particular emphasis on ease of use, a high level of readability, attention to performance through the use of non-blocking operations and is not bound to a specific test runner.
{% endhint %}

## A Story of Deserializing HTML

Have you ever heard of the [**kotlinx.html**](https://github.com/Kotlin/kotlinx.html) DSL?  
In case you don't, it is a Kotlin multiplatform library that provides a type-safe DSL to build / serialize static HTML right from your Kotlin code.

But what if we want to do it the other way around and deserialize HTML or XML in Kotlin?

💪 Let's rescue the world \(at least in terms of html scraping 🤓\) and do it the Kotlin way.

The idea to have a Kotlin-based library to scrape or parse HTML / XML was getting clearer after seeing the awesome talk about [_**Creating Internal DSLs in Kotlin**_](https://kotlinconf.com/talks/#date=5-october&session=41599) \_**\*\*\_by Venkat Subramaniam at the KotlinConf 2018 in Amsterdam. Totally amazed by the readability and the possibilities a DSL written in Kotlin provides, the idea of** Skrape{it}\*\* was born!

The major paradigms of the library are that it's flexible, highly readable, not bound to specific test-runner and reactive / non blocking

> Hold on, hold on. I'm already knowing a library that is doing what you described, it's called [jSoup](https://jsoup.org) or I could could just use Selenium in order to behave in the manner mentioned above.

Nearly true. **Skrape{it}** is using jSoup internally to parse HTML documents. But since jSoup is written in Java it's neither null-safe nor intuitiv to use and read. Skrape{it} _\*\*_abstracts the idea of jSoup but it's easy to use by having a focus on readability by simplicity.  
Furthermore, Skrape{it} offers the possibility to verify expectations by offering a DSL that is specifically designed to do HTML-related assertions and bindings for well-known testing libraries and HTTP clients.

## Open source

### _Skrape{it}_ is an open source project distributed under the liberal [MIT license](https://raw.githubusercontent.com/skrapeit/skrape.it/master/LICENSE).  The source code is available at [GitHub](https://github.com/skrapeit/skrape.it).

<a href="https://github.com/skrapeit/skrape.it" class="github-corner" aria-label="View source on GitHub"><svg width="80" height="80" viewBox="0 0 250 250" style="fill:#e3a1d8; color:#fff; position: absolute; top: 0; border: 0; right: 0; z-index: 50000" aria-hidden="true"><path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z"></path><path d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2" fill="currentColor" style="transform-origin: 130px 106px;" class="octo-arm"></path><path d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z" fill="currentColor" class="octo-body"></path></svg></a>

# Why it exists

The motivation to parse HTML was the need to have a robust and fast solution to relieve a long-running and unstable Selenium test suite. After a code dive through these Selenium tests it turned out that many of them only checked things \(like Dom elements, displayed data, cookies, etc.\) without interacting with a web browser by clicking around etc.

The whole test suite took hours because it had to struggle with the overhead of starting browser instances over and over which really takes time. Furthermore we could not parallelize the execution in a high scale cause as you can imagine starting 100 instances of a real browser will allocate a lot of memory, even in headless mode with deactivated UI etc.

So it was clear, we need some lightweight and flexibel approach that in best case should be very easy to use and highly readable.

Skrape{it} fixed that issue by doing its job rapidly fast and reliable. In a bigger test project where this framework is in use it runs ~400 tests in less than 10 seconds thanks to parallelization and focus. 

Technically it was proven it works out well. But the user experience should be nice as well. Thankfully this could be solved by really using all the possibilities Kotlin as a programming language is giving us.

## A Story of Deserializing HTML

Have you ever heard of the [**kotlinx.html**](https://github.com/Kotlin/kotlinx.html) DSL?  
In case you don't, it is a Kotlin multiplatform library that provides a type-safe DSL to build / serialize static HTML right from your Kotlin code.

But what if we want to do it the other way around and deserialize HTML or XML in Kotlin?

💪 Let's rescue the world \(at least in terms of html scraping 🤓\) and do it the Kotlin way.

The idea to have a Kotlin-based library to scrape or parse HTML / XML was getting clearer after seeing the awesome talk about [_**Creating Internal DSLs in Kotlin**_](https://kotlinconf.com/talks/#date=5-october&session=41599) by Venkat Subramaniam at the KotlinConf 2018 in Amsterdam. Totally amazed by the readability and the possibilities a DSL written in Kotlin provides, the idea of Skrape{it} was born!

The major paradigms of the library are that it's flexible, highly readable, not bound to specific test-runner and reactive / non blocking

> Hold on, hold on. I'm already knowing a library that is doing what you described, it's called [jSoup](https://jsoup.org) or I could  just use Selenium in order to behave in the manner mentioned above.

Nearly true. **Skrape{it}** is using jSoup internally to parse HTML documents. But since jSoup is written in Java it's neither null-safe nor intuitiv to use and read. Skrape{it} abstracts the idea of jSoup but it's easy to use by having a focus on readability by simplicity and has **native support for scraping of client-side rendered webpages** which is not possible with jSoup. The whole rendering will happen inside the JVM - from which it follows that no browser installation and ramp-up is needed \(contrary to Selenium\).  
Furthermore, Skrape{it} offers the possibility to verify expectations by offering a DSL that is specifically designed to do HTML-related assertions and bindings for well-known testing libraries and HTTP clients.


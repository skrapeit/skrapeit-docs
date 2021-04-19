---
description: >-
  A Kotlin-based HTML / XML deserialization library that places particular
  emphasis on ease of use and a high level of readability by providing an
  intuitive DSL.
---

# Introduction

{% hint style="info" %}
[**skrape{it}**](http://www.skrape.it) is a Kotlin-based HTML/XML testing and web scraping library that can be used seamlessly in Spring-Boot, Ktor, Android or other Kotlin-JVM projects. The ability to **analyze and extract HTML including client-side rendered DOM trees** and all other XML-related markup specifications such as SVG, UML, RSS,... makes it unique. It places particular emphasis on **ease of use** and a **high level of readability** by providing an **intuitive DSL**. First and foremost skrape{it} aims to be a testing tool \(not tied to a particular test runner\), but it can also be used to scrape websites in a convenient fashion.
{% endhint %}

## Features

#### Parsing

* [x] Deserialization of HTML/XML from websites, local html files and html as string to data classes / POJOs.
* [x] Designed to deserialize HTML but can handle any XML-related markup specifications such as SVG, UML, RSS or XML itself.
* [x] DSL to select html elements as well as supporting CSS query-selector syntax by string invocation.

#### Http-Client

* [x] Http-Client without verbosity and ceremony to make requests and corresponding request options like headers, cookies etc in a fluent style interface.
* [x] Pre-configure client regarding auth and other request settings
* [x] Can handle client side rendered web pages. Javascript execution results can optionally be considered in the response body.

#### Idomatic

* [x] Easy to use, idiomatic and type-safe DSL to ensure a high level of readability.
* [x] Build-in matchers/assertions based on infix functions to archive a very high level of readability.
* [x] DSL is behaving like a Fluent-Api to make data extraction/scraping as comfortable as possible.

#### Compatibility

* [x] Not bind to a specific test-runner, framework or whatever.
* [x] Open to use any other assertion library of your choice.
* [x] Open to implement your own fetcher
* [x] Supports non-blocking fetching / Coroutine support
* [x] Extensions for other well-known libraries

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


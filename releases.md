---
description: >-
  Includes all the core functionality like parsing of documents, making http
  requests, providing the skrape-DSL and matchers.
---

# Releases

> latest version: [![maven central](https://img.shields.io/maven-central/v/it.skrape/skrapeit-core.svg?color=0)](https://search.maven.org/search?q=g:it.skrape%20AND%20a:skrapeit-core&skrapeit-core=gav)
>
> test-coverage: [![Codecov](https://img.shields.io/codecov/c/github/skrapeit/skrape.it.svg)](https://codecov.io/gh/skrapeit/skrape.it)

## 1.0.0-alpha4 - 14.01.20

### Bugfix

* fix `findAll`  functionality 

### Added

* convenient way to extract list of text \(`eachText`\)

## 1.0.0-alpha3 - 07.01.20

### Added

* add more convenient features to the HTTP client
  * url can either be passed as plain String or by usage of `urlBuilder`
  * supports basic-auth

## 1.0.0-alpha2 - 18.11.19

### Added

* support to build complex css-selectors for elements via DSL
* support element picking by string invoke of css query selector

## 1.0.0-alpha1 - 23.10.19

#### ⚠ This release is including breaking changes \(elements, element, $, el - functions has been kicked out\)

### Added

* support to pick css-selectors for elements via DSL

## 0.6.0 - 09.05.19

### Added

* support to render JS and get parsed DOM tree
* request option to add cookies to the request in a more convenient fashion

## 0.5.1 - 25.04.19

### Bugfix

* fix trust store issue for https connections

## 0.5.0 - 09.05.19

### Added

* support to render JS and get parsed DOM tree
* request option to add cookies to the request in a more convenient fashion

## 0.4.3 - 18.04.19

### Patch

* can parse a string representation of HTML via DSL
* add `toBeNotPresent` matcher

## 0.4.2 - 17.04.19

#### ⚠ Artifact ID has been renamed from "core" to "skrapeit-core"

### Patch

* add `toBePresent` matcher to verify if an Element exists
* refactoring to enable extensions

## 0.4.1 - 08.04.19

### Added

* Experimental feature to support client-side rendered HTML

## 0.4.0 - 01.04.19

### Added

* Dsl supports parsing from HTML as String
* refactoring of parsing from file 

## 0.3.1 - 22.02.19

### Patch

* add more custom assertions / matchers

## 0.3.0 - 21.02.19

### Added

* convenient methods to select
  * a certain response header
  * all response headers
  * response body

## 0.2.0 - 20.02.19

### Added

* can extract data via reflection -&gt; `extractIt{}`

## 0.1.1 - 17.02.19

### Bugfix

* visibility of some DSL functions
* refactoring

## 0.1.0 - 15.02.19

### Added

* possibility to extract data more handy 
* shorthand to select elements
* dsl function to parse html from file

## 0.1.0-beta - 22.01.2019

### Added

* Initial release to maven-central including:
  * configurable Fetch-mechanism \(http-request\) that provides meaningful defaults
  * add parsing functionality
  * add DSL for convenient scraping with request-options
    * DSL supports picking  by CSS-selector for `element` \(first occurrence in DOM\) and `elements` \(all occurrences in DOM\)

> ### See [**Maven Central release history**](https://search.maven.org/search?q=g:it.skrape%20AND%20a:core&core=gav)**.**


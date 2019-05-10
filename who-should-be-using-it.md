---
description: Deserialize HTML? Why should that be useful?
---

# Who should be using it



**Skrape{it}** focuses first and foremost on parsing html, but it's possible to parse any XML related markup specification, like:

* SVG [\(Scalable Vector Graphics\)](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics)
* RSS [\(Rich Site Summary\)](https://en.wikipedia.org/wiki/RSS)
* GraphML [\(Graphical Markup Language\)](https://en.wikipedia.org/wiki/GraphML)
* UML [\(Unified Modeling Language\)](https://en.wikipedia.org/wiki/Unified_Modeling_Language)
* OSM [\(OpenStreetMap\)](https://en.wikipedia.org/wiki/OpenStreetMap)
* GPX [\(GPS Exchange Format\)](https://en.wikipedia.org/wiki/GPS_Exchange_Format)
* XMPP [\(Extensible Messaging and Presence Protocol\)](https://en.wikipedia.org/wiki/XMPP)
* MathML [\(Mathematical Markup Language\)](https://en.wikipedia.org/wiki/MathML)
* ...

**some thoughts when it is helpful to use skrape{it}:**

{% hint style="success" %}
"I would like to test the endpoints of my application that produces HTML/XML in a meaningful and idiomatic way!"
{% endhint %}

{% hint style="success" %}
"I'm running a huge Selenium suite that is checking the appearance of certain elements and its values. Therefore I'm looking for a fast and reliable alternative with less overhead!"
{% endhint %}

{% hint style="success" %}
"I'm maintaining a complex application with high SEO requirements, therefore i want to have e2e tests checking the relevant meta tag information!"
{% endhint %}

{% hint style="success" %}
"I need to refactor an \(legacy or hard to mock\) application that produces HTML/XML and want to have high level tests that ensure my changes fulfill the expectations!"
{% endhint %}

{% hint style="success" %}
"I'm an Android developer and want to write proper tests for my Manifest file, XML Layout files and other XML related stuff within my project!"
{% endhint %}

{% hint style="success" %}
"I want to grab some data from a website that's not providing an API!"
{% endhint %}

These are just a few reasons that came to our mind  from time to time and if you think one these quotes have came to your mind as well you should definitely give **skrape{it}** a try. 


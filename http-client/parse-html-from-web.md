# Request Options

### Request Options

{% hint style="info" %}
**All** of the available **options** already **have reasonable defaults** to make the use of skrape{it} as easy and intuitive as possible.
{% endhint %}

| Option | Description | Type | Default |
| :--- | :--- | :---: | :--- |
| **url** | The URL that is used to fetch and parse a web page. The protocol must be `http` or `https` | **String** | `http://localhost:8080` |
| **method** | HTTP defines a set of [**request methods**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) to indicate the desired action to be performed for a given resource. Although they can also be nouns, these request methods are sometimes referred as _HTTP verbs_. | **Method** | `GET` |
| **userAgent** | The [**User-Agent**](https://developer.mozilla.org/de/docs/Web/HTTP/Headers/User-Agent) request header contains a characteristic string that allows the network protocol peers to identify the application type, operating system, software vendor or software version of the requesting software user agent. | **String** | `Mozilla/5.0 skrape.it` |
| **headers** | \*\*\*\*[**Request headers** ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)containing more information about the resource to be fetched or about the client itself. | **Map&lt;String, String&gt;** | no additional custom headers will be sent by default |
| **cookies** | Will add Cookies to your request | **Map&lt;String, String&gt;** | will send no Cookies by default |
| **timeout** | Sets the total request timeout duration. A timeout of zero \(`0`\) is treated as an infinite timeout. | **Int** | `5000` |
| **followRedirects** | Configures the connection to \(not\) follow server redirects. | **Boolean** | `true` |
| **sslRelaxed** | Allow HTTPS connections with broken or self-signed certificates | **Boolean** | `false` |




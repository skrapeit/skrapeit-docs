# Http-Client

skrape-it offers an intuitive and DSL-controlled http client to make parsing websites as comfortable as possible. A special feature is the mode parameter, which allows web pages to be client-side rendered \(e.g. pages created with frameworks like React.js, Angular or Vue.js or pages manipulated with jQuery or other javascript\).

```kotlin
skrape {
    // ... request options goes here
    
    expect {
        // ... you can do some checks in here by working on the http response
        
        htmlDocument { // will parse the HTTP requests response body
            // ... parsing and do stuff with the parsed data goes here
        }
    }
    extract {
        // same behaviour as expect BUT returning a Generic, that allows you to create opbjects and pass scrped data to them.
    }
}
```

{% hint style="info" %}
The http-request is only executed after either the [**`extract`**](extracting-data-from-websites.md) or [**`expect`**](basic-test-scenario.md) function has been called. This behaviour also allows to preconfigure the http-client for multiple calls. If you use expect as well as extract it will only make 1 request.
{% endhint %}

### Request Options

{% hint style="info" %}
**All** of the available **options** already **have reasonable defaults** which aim to make the use of skrape{it} as easy and intuitive as possible.
{% endhint %}

<table>
  <thead>
    <tr>
      <th style="text-align:left">Option</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:center">Type</th>
      <th style="text-align:left">Default</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>url</b>
      </td>
      <td style="text-align:left">The URL that is used to fetch and parse a web page. The protocol must
        be <code>http</code> or <code>https</code>
      </td>
      <td style="text-align:center"><b>String</b>
      </td>
      <td style="text-align:left"><code>http://localhost:8080</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>method</b>
      </td>
      <td style="text-align:left">HTTP defines a set of <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods"><b>request methods</b></a> to
        indicate the desired action to be performed for a given resource. Although
        they can also be nouns, these request methods are sometimes referred as <em>HTTP verbs</em>.</td>
      <td
      style="text-align:center"><b>Method</b>
        </td>
        <td style="text-align:left"><code>GET</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>userAgent</b>
      </td>
      <td style="text-align:left">The <a href="https://developer.mozilla.org/de/docs/Web/HTTP/Headers/User-Agent"><b>User-Agent</b></a> request
        header contains a characteristic string that allows the network protocol
        peers to identify the application type, operating system, software vendor
        or software version of the requesting software user agent.</td>
      <td style="text-align:center"><b>String</b>
      </td>
      <td style="text-align:left"><code>Mozilla/5.0 skrape.it</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>headers</b>
      </td>
      <td style="text-align:left">&lt;b&gt;&lt;/b&gt;<a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers"><b>Request headers </b></a>containing
        more information about the resource to be fetched or about the client itself.</td>
      <td
      style="text-align:center"><b>Map&lt;String, String&gt;</b>
        </td>
        <td style="text-align:left">no additional custom headers will be sent by default</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cookies</b>
      </td>
      <td style="text-align:left">Will add Cookies to your request</td>
      <td style="text-align:center"><b>Map&lt;String, String&gt;</b>
      </td>
      <td style="text-align:left">will send no Cookies by default</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>timeout</b>
      </td>
      <td style="text-align:left">Sets the total request timeout duration. A timeout of zero (<code>0</code>)
        is treated as an infinite timeout.</td>
      <td style="text-align:center"><b>Int</b>
      </td>
      <td style="text-align:left"><code>5000</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>followRedirects</b>
      </td>
      <td style="text-align:left">Configures the connection to (not) follow server redirects.</td>
      <td style="text-align:center"><b>Boolean</b>
      </td>
      <td style="text-align:left"><code>true</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>ignoreContentType</b>
      </td>
      <td style="text-align:left">Ignore the document&apos;s Content-Type when parsing the response. If
        set to false, an unrecognized content-type will cause an IOException to
        be thrown. (This is to prevent producing garbage by attempting to parse
        a JPEG binary image, for example.)</td>
      <td style="text-align:center"><b>Boolean</b>
      </td>
      <td style="text-align:left"><code>true</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>ignoreHttpErrors</b>
      </td>
      <td style="text-align:left">Configures the connection to not throw exceptions when a HTTP error occurs.
        (4xx - 5xx, e.g. 404 or 500). An IOException is thrown if an error is encountered.
        If set to <code>true</code> the response is populated with the error body,
        and the status message will reflect the error.</td>
      <td style="text-align:center"><b>Boolean</b>
      </td>
      <td style="text-align:left"><code>true</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>validateTLSCertificates</b>
      </td>
      <td style="text-align:left">
        <p>Disable/enable TLS certificates validation for HTTPS requests.</p>
        <p>All connections over HTTPS perform normal validation of certificates,
          and will abort requests if the provided certificate does not validate.</p>
      </td>
      <td style="text-align:center"><b>Boolean</b>
      </td>
      <td style="text-align:left"><code>true</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>maxBodySize</b>
      </td>
      <td style="text-align:left">Set the maximum bytes to read from the (uncompressed) connection into
        the body, before the connection is closed, and the input truncated.</td>
      <td
      style="text-align:center"><b>Int</b>
        </td>
        <td style="text-align:left">no maximum body size</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>mode</b>
      </td>
      <td style="text-align:left">
        <p>For server-side rendered Websites or other XML related responses you should
          always use the default mode (<em>SOURCE</em>) because it&apos;s more performant
          (good old HTTP request).</p>
        <p>If you need to parse client side rendered Websites (e.g. build with React.js,
          Vue.js, Angular or jQuery) try the DOM mode.</p>
      </td>
      <td style="text-align:center"><b>Mode</b>
      </td>
      <td style="text-align:left">SOURCE</td>
    </tr>
  </tbody>
</table>




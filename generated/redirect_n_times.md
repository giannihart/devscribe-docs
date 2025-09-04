---
title: redirect_n_times
description: This endpoint triggers a series of `n` HTTP 302 redirects, where `n`
  is an integer provided in the URL path. The final destination of the redirect chain
  is the `/get` endpoint. An optional `absolute` query parameter, when set to `true`,
  forces the use of absolute URLs for each step of the redirect; otherwise, relative
  URLs are used by default.
openapi: GET ['/redirect/<int:n>']
---
# redirect_n_times

{% callout type="tip" %}
View source on [**GitHub ↗**](https://github.com/devscribe-team/httpbin/blob/master/httpbin/core.py#L557-L583)
{% /callout %}

## Summary
This endpoint triggers a series of `n` HTTP 302 redirects, where `n` is an integer provided in the URL path. The final destination of the redirect chain is the `/get` endpoint. An optional `absolute` query parameter, when set to `true`, forces the use of absolute URLs for each step of the redirect; otherwise, relative URLs are used by default.

## API Info
{% cardGroup cols=2 %}
{% card title="HTTP Methods" icon="server" %}
`GET`
{% /card %}
{% card title="Route Path" icon="route" %}
`/redirect/<int:n>`
{% /card %}
{% /cardGroup %}

## Parameters
{% parameterField name="n" type="integer" required=true %}
The number of times to redirect. This is a path parameter.
{% /parameterField %}

{% parameterField name="absolute" type="boolean" default="false" %}
An optional query parameter that, when set to `true`, forces the use of absolute URLs for each step of the redirect.
{% /parameterField %}

## Returns
`redirect` or `_redirect`: Returns a function call to either `redirect` or `_redirect`, which generates a redirect response.

## Usage Examples
{% codeGroup %}
```python {% title="Python" showLineNumbers=true %}
import requests

response = requests.get("https://api.example.com/redirect/5")

print(f"Status Code: {response.status_code}")
print(f"URL: {response.url}")
```
```javascript {% title="JavaScript" showLineNumbers=true %}
fetch("https://api.example.com/redirect/4")
  .then(response => console.log(response.url))
  .catch(error => console.error(error));
```
```java {% title="Java" showLineNumbers=true %}
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

class Example {
    public static void main(String[] args) throws Exception {
        HttpClient client = HttpClient.newBuilder()
                .followRedirects(HttpClient.Redirect.NEVER)
                .build();

        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create("https://api.example.com/redirect/5"))
                .build();

        HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());

        System.out.println(response.statusCode());
        System.out.println(response.headers().firstValue("Location"));
    }
}
```
```php {% title="PHP" showLineNumbers=true %}
<?php

$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://api.example.com/redirect/3");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);

$response = curl_exec($ch);

curl_close($ch);

echo $response;
```
```go {% title="Go" showLineNumbers=true %}
package main

import (
	"fmt"
	"io"
	"log"
	"net/http"
)

func main() {
	resp, err := http.Get("https://api.example.com/redirect/5")
	if err != nil {
		log.Fatal(err)
	}
	defer resp.Body.Close()

	body, err := io.ReadAll(resp.Body)
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(string(body))
}
```
```bash {% title="cURL" showLineNumbers=true %}
curl -L "https://api.example.com/redirect/5?absolute=true"
```
{% /codeGroup %}
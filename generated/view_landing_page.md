---
title: view_landing_page
description: This function is mapped to the `/legacy` endpoint and handles HTTP GET
  requests. It renders the `index.html` template to serve a legacy version of the
  application's main landing page.
openapi: GET ['/legacy']
---
## Summary
This function is mapped to the `/legacy` endpoint and handles HTTP GET requests. It renders the `index.html` template to serve a legacy version of the application's main landing page.

## Parameters
{% callout type="info" %}
No parameters.
{% /callout %}

## Returns
`render_template`: Renders a template from the template folder with the given context.

## Usage Examples
{% codeGroup %}

```python {% filename="Python" showLineNumbers=true %}
import requests

url = "https://api.example.com/legacy"
response = requests.get(url)

print(f"Status Code: {response.status_code}")
print(f"Response Body: {response.text}")
```

```javascript {% filename="JavaScript" showLineNumbers=true %}
fetch("https://api.example.com/legacy")
  .then(response => {
    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }
    return response.text();
  })
  .then(html => {
    console.log("Successfully fetched landing page HTML.");
  })
  .catch(error => {
    console.error("Error fetching the legacy page:", error);
  });
```

```java {% filename="Java" showLineNumbers=true %}
import java.io.IOException;
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

public class Example {
    public static void main(String[] args) throws IOException, InterruptedException {
        HttpClient client = HttpClient.newHttpClient();
        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create("https://api.example.com/legacy"))
                .GET()
                .build();

        HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());

        System.out.println(response.statusCode());
        System.out.println(response.body());
    }
}
```

```php {% filename="PHP" showLineNumbers=true %}
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.example.com/legacy",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
]);

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}

```

```go {% filename="GO" showLineNumbers=true %}
package main

import (
	"fmt"
	"io"
	"log"
	"net/http"
)

func main() {
	resp, err := http.Get("https://api.example.com/legacy")
	if err != nil {
		log.Fatalf("error making request: %s", err)
	}
	defer resp.Body.Close()

	body, err := io.ReadAll(resp.Body)
	if err != nil {
		log.Fatalf("error reading response body: %s", err)
	}

	fmt.Println(string(body))
}

```

```bash {% filename="cURL" showLineNumbers=true %}
curl "https://api.example.com/legacy"
```
{% /codeGroup %}

{% callout type="tip" %}
View source on [**GitHub ↗**](https://github.com/giannihart/httpbin/blob/master/httpbin/core.py#L240-L243)
{% /callout %}
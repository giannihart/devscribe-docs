---
title: view_deny_page
description: This function maps to the `/deny` endpoint, which is intended to be disallowed
  by `robots.txt` rules for web crawlers. It returns a `200 OK` response with a `Content-Type`
  of `text/plain`. The response body contains a predefined ASCII art string, signaling
  that the page should not be accessed.
openapi: GET ['/deny']
---
## Summary
This function maps to the `/deny` endpoint, which is intended to be disallowed by `robots.txt` rules for web crawlers. It returns a `200 OK` response with a `Content-Type` of `text/plain`. The response body contains a predefined ASCII art string, signaling that the page should not be accessed.

## Parameters
{% callout type="info" %}
No parameters.
{% /callout %}

## Returns
`Response`: A `Response` object containing a plain-text message indicating the page is denied.

## Usage Examples
{% codeGroup %}

```python {% filename="Python" showLineNumbers=true %}
import requests

url = "https://api.example.com/deny"
response = requests.get(url)

print(f"Status Code: {response.status_code}")
print("Response Body:")
print(response.text)
```

```javascript {% filename="JavaScript" showLineNumbers=true %}

async function denyPage() {
  try {
    const response = await fetch("https://api.example.com/deny");
    if (response.ok) {
      const textData = await response.text();
      console.log(textData);
    } else {
      console.error("Request failed with status:", response.status);
    }
  } catch (error) {
    console.error("Error fetching data:", error);
  }
}

denyPage();

```

```java {% filename="Java" showLineNumbers=true %}
import java.io.IOException;
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

public class DenyPageExample {
    public static void main(String[] args) {
        HttpClient client = HttpClient.newHttpClient();
        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create("https://api.example.com/deny"))
                .GET()
                .build();

        try {
            HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
            System.out.println("Status Code: " + response.statusCode());
            System.out.println("Response Body:");
            System.out.println(response.body());
        } catch (IOException | InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

```php {% filename="PHP" showLineNumbers=true %}
<?php

$url = "https://api.example.com/deny";
$response = file_get_contents($url);

echo $response;

?>
```

```go {% filename="GO" showLineNumbers=true %}
package main

import (
	"fmt"
	"io"
	"net/http"
)

func main() {
	resp, err := http.Get("https://api.example.com/deny")
	if err != nil {
		panic(err)
	}
	defer resp.Body.Close()

	body, err := io.ReadAll(resp.Body)
	if err != nil {
		panic(err)
	}

	fmt.Println(string(body))
}

```

```bash {% filename="cURL" showLineNumbers=true %}
curl -X GET "https://api.example.com/deny"
```
{% /codeGroup %}

{% callout type="tip" %}
View source on [**GitHub ↗**](https://github.com/giannihart/httpbin/blob/master/httpbin/core.py#L281-L297)
{% /callout %}
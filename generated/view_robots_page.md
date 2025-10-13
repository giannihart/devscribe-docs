---
title: view_robots_page
description: This function serves the `robots.txt` file for our application. It responds
  to requests at the `/robots.txt` endpoint by returning a predefined set of crawler
  directives with a `text/plain` content type.
openapi: GET ['/robots.txt']
---
## Summary
This function serves the `robots.txt` file for our application. It responds to requests at the `/robots.txt` endpoint by returning a predefined set of crawler directives with a `text/plain` content type.

## Parameters
{% callout type="info" %}
No parameters.
{% /callout %}

## Returns
`Response`: A Flask `Response` object containing the `robots.txt` rules, with the `Content-Type` header set to `text/plain`.

## Usage Examples
{% codeGroup %}

```python {% filename="Python" showLineNumbers=true %}
import requests

url = "https://api.example.com/robots.txt"
response = requests.get(url)

print(f"Status Code: {response.status_code}")
print("Response Body:")
print(response.text)
```

```javascript {% filename="JavaScript" showLineNumbers=true %}
fetch("https://api.example.com/robots.txt")
  .then(response => response.text())
  .then(data => console.log(data));
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
                .uri(URI.create("https://api.example.com/robots.txt"))
                .GET()
                .build();

        HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());

        System.out.println(response.statusCode());
        System.out.println(response.body());
    }
}
```

```php {% filename="PHP" showLineNumbers=true %}
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://api.example.com/robots.txt");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

$response = curl_exec($ch);

curl_close($ch);

echo $response;
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
	resp, err := http.Get("https://api.example.com/robots.txt")
	if err != nil {
		log.Fatalf("Error fetching URL: %v", err)
	}
	defer resp.Body.Close()

	if resp.StatusCode != http.StatusOK {
		log.Fatalf("Error: received status code %d", resp.StatusCode)
	}

	body, err := io.ReadAll(resp.Body)
	if err != nil {
		log.Fatalf("Error reading response body: %v", err)
	}

	fmt.Println(string(body))
}

```

```bash {% filename="cURL" showLineNumbers=true %}
curl "https://api.example.com/robots.txt"
```
{% /codeGroup %}

{% callout type="tip" %}
View source on [**GitHub ↗**](https://github.com/giannihart/httpbin/blob/master/httpbin/core.py#L262-L278)
{% /callout %}
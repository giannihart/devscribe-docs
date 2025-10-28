---
title: view_patch
description: This endpoint handles `PATCH` requests to `/patch`. It inspects the incoming
  request and returns a JSON object containing details about the request, including
  the URL, query arguments, form data, raw data payload, origin IP, headers, any uploaded
  files, and the JSON body.
openapi: PATCH ['/patch']
---
## Summary
This endpoint handles `PATCH` requests to `/patch`. It inspects the incoming request and returns a JSON object containing details about the request, including the URL, query arguments, form data, raw data payload, origin IP, headers, any uploaded files, and the JSON body.

## Parameters
{% callout type="info" %}
No parameters.
{% /callout %}

## Returns
`jsonify`: A Flask function that serializes a Python dictionary into a JSON formatted `Response` object.

## Usage Examples
{% codeGroup %}

```python {% filename="Python" showLineNumbers=true %}
import requests

url = "https://api.example.com/patch"
payload = {"name": "Updated Name"}

response = requests.patch(url, json=payload)

print(response.json())
```

```javascript {% filename="JavaScript" showLineNumbers=true %}

fetch("https://api.example.com/patch", {
  method: "PATCH",
  headers: {
    "Content-Type": "application/json",
    "X-Custom-Header": "Your-Custom-Value"
  },
  body: JSON.stringify({
    "key": "value",
    "another_key": 123
  })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error("Error:", error));

```

```java {% filename="Java" showLineNumbers=true %}
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

class PatchRequestExample {
    public static void main(String[] args) throws Exception {
        HttpClient client = HttpClient.newHttpClient();
        String requestBody = "{\"name\": \"Updated Name\"}";

        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create("https://api.example.com/patch"))
                .method("PATCH", HttpRequest.BodyPublishers.ofString(requestBody))
                .header("Content-Type", "application/json")
                .build();

        HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());

        System.out.println(response.body());
    }
}
```

```php {% filename="PHP" showLineNumbers=true %}
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.example.com/patch",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "PATCH",
  CURLOPT_POSTFIELDS => "{\"key\":\"value\"}",
  CURLOPT_HTTPHEADER => [
    "Content-Type: application/json"
  ],
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
	"net/http"
	"strings"
)

func main() {
	client := &http.Client{}
	var data = strings.NewReader(`{"key": "value"}`)
	req, err := http.NewRequest("PATCH", "https://api.example.com/patch", data)
	if err != nil {
		fmt.Println(err)
		return
	}
	req.Header.Set("Content-Type", "application/json")
	resp, err := client.Do(req)
	if err != nil {
		fmt.Println(err)
		return
	}
	defer resp.Body.Close()
	bodyText, err := io.ReadAll(resp.Body)
	if err != nil {
		fmt.Println(err)
		return
	}
	fmt.Printf("%s\n", bodyText)
}

```

```bash {% filename="cURL" showLineNumbers=true %}
curl -X PATCH "https://api.example.com/patch" -H "Content-Type: application/json" -d "{\"key\":\"value\"}"
```
{% /codeGroup %}

{% callout type="tip" %}
View source on [**GitHub ↗**](https://github.com/giannihart/httpbin/blob/master/httpbin/core.py#L450-L465)
{% /callout %}
---
title: view_put
description: This API endpoint handles `PUT` requests to the `/put` path. It inspects
  the incoming request and returns a JSON object containing its properties. The response
  payload includes the request's URL, query arguments, form data, headers, and the
  raw request body.
openapi: PUT ['/put']
---
## Summary
This API endpoint handles `PUT` requests to the `/put` path. It inspects the incoming request and returns a JSON object containing its properties. The response payload includes the request's URL, query arguments, form data, headers, and the raw request body.

## Parameters
{% callout type="info" %}
No parameters.
{% /callout %}

## Returns
`jsonify`: Serializes a given object to a JSON formatted Response object.

## Usage Examples
{% codeGroup %}

```python {% filename="Python" showLineNumbers=true %}
import requests

url = "https://api.example.com/put"
payload = {"name": "John Doe", "occupation": "Software Engineer"}

response = requests.put(url, json=payload)

print(response.status_code)
print(response.json())
```

```javascript {% filename="JavaScript" showLineNumbers=true %}
fetch("https://api.example.com/put", {
  method: "PUT",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    "name": "John Doe",
    "email": "john.doe@example.com"
  })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error("Error:", error));
```

```java {% filename="Java" showLineNumbers=true %}

import java.io.IOException;
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

public class Main {
    public static void main(String[] args) {
        HttpClient client = HttpClient.newHttpClient();
        String requestBody = "{\"name\":\"John Doe\",\"email\":\"john.doe@example.com\"}";

        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create("https://api.example.com/put"))
                .header("Content-Type", "application/json")
                .PUT(HttpRequest.BodyPublishers.ofString(requestBody))
                .build();

        try {
            HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
            System.out.println("Status Code: " + response.statusCode());
            System.out.println("Response Body: " + response.body());
        } catch (IOException | InterruptedException e) {
            e.printStackTrace();
        }
    }
}

```

```php {% filename="PHP" showLineNumbers=true %}
<?php

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_URL => "https://api.example.com/put",
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_ENCODING => "",
    CURLOPT_MAXREDIRS => 10,
    CURLOPT_TIMEOUT => 30,
    CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
    CURLOPT_CUSTOMREQUEST => "PUT",
    CURLOPT_POSTFIELDS => "{\"name\": \"John Doe\", \"email\": \"john.doe@example.com\"}",
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
	data := strings.NewReader(`{"name":"John Doe","age":30}`)
	req, err := http.NewRequest("PUT", "https://api.example.com/put", data)
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

	body, err := io.ReadAll(resp.Body)
	if err != nil {
		fmt.Println(err)
		return
	}

	fmt.Println(string(body))
}

```

```bash {% filename="cURL" showLineNumbers=true %}
curl -X PUT "https://api.example.com/put" -H "Content-Type: application/json" -d "{\"name\": \"John Doe\", \"email\": \"john.doe@example.com\"}"
```
{% /codeGroup %}

{% callout type="tip" %}
View source on [**GitHub ↗**](https://github.com/giannihart/httpbin/blob/master/httpbin/core.py#L432-L447)
{% /callout %}
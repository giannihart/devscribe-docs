---
title: view_patch
description: This function handles `PATCH` requests to the `/patch` endpoint. It inspects
  the incoming request and returns a JSON object containing its attributes, such as
  URL arguments, headers, form data, and any attached files or JSON payload.
openapi: PATCH ['/patch']
---
## Summary
This function handles `PATCH` requests to the `/patch` endpoint. It inspects the incoming request and returns a JSON object containing its attributes, such as URL arguments, headers, form data, and any attached files or JSON payload.

## Parameters
{% parameterField name="url" type="string" %}
The URL of the request.
{% /parameterField %}

{% parameterField name="args" type="object" %}
The query string arguments from the URL.
{% /parameterField %}

{% parameterField name="form" type="object" %}
The form data submitted in the request body.
{% /parameterField %}

{% parameterField name="data" type="string" %}
The raw data from the request body.
{% /parameterField %}

{% parameterField name="origin" type="string" %}
The IP address of the client making the request.
{% /parameterField %}

{% parameterField name="headers" type="object" %}
The headers sent with the request.
{% /parameterField %}

{% parameterField name="files" type="object" %}
The files uploaded with the request.
{% /parameterField %}

{% parameterField name="json" type="object" %}
The JSON document sent in the request body.
{% /parameterField %}

## Returns
`jsonify`: A function that serializes a Python dictionary into a JSON formatted `Response` object.

## Usage Examples
{% codeGroup %}

```python {% filename="Python" showLineNumbers=true %}
import requests

url = "https://api.example.com/patch"
payload = {"key": "value"}

response = requests.patch(url, json=payload)

print(response.json())
```

```javascript {% filename="JavaScript" showLineNumbers=true %}
const data = {
  "name": "John Doe",
  "email": "john.doe@example.com"
};

fetch("https://api.example.com/patch", {
  method: "PATCH",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify(data)
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

public class PatchExample {
    public static void main(String[] args) throws IOException, InterruptedException {
        HttpClient client = HttpClient.newHttpClient();
        String requestBody = "{\"name\": \"Jane Doe\"}";

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

$data = json_encode([
    "name" => "John Doe",
    "email" => "john.doe@example.com"
]);

curl_setopt_array($curl, [
    CURLOPT_URL => "https://api.example.com/patch",
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_CUSTOMREQUEST => "PATCH",
    CURLOPT_POSTFIELDS => $data,
    CURLOPT_HTTPHEADER => [
        "Content-Type: application/json",
        "Content-Length: " . strlen($data)
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
	"bytes"
	"fmt"
	"io"
	"net/http"
)

func main() {
	url := "https://api.example.com/patch"
	jsonData := []byte(`{"key": "value"}`)

	req, err := http.NewRequest(http.MethodPatch, url, bytes.NewBuffer(jsonData))
	if err != nil {
		panic(err)
	}

	req.Header.Set("Content-Type", "application/json")

	client := &http.Client{}
	resp, err := client.Do(req)
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
curl -X PATCH "https://api.example.com/patch" -H "Content-Type: application/json" -d "{\"key\":\"value\"}"
```
{% /codeGroup %}

{% callout type="tip" %}
View source on [**GitHub ↗**](https://github.com/giannihart/httpbin/blob/master/httpbin/core.py#L450-L465)
{% /callout %}
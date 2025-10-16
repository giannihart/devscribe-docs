---
title: view_delete
description: This function handles `DELETE` requests to the `/delete` endpoint. It
  returns a JSON object containing the details of the incoming request, including
  its URL, arguments, form data, headers, and body.
openapi: DELETE ['/delete']
---
## Summary
This function handles `DELETE` requests to the `/delete` endpoint. It returns a JSON object containing the details of the incoming request, including its URL, arguments, form data, headers, and body.

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

url = "https://api.example.com/delete"
headers = {
    "accept": "application/json"
}

response = requests.delete(url, headers=headers)

print(response.json())
```

```javascript {% filename="JavaScript" showLineNumbers=true %}
fetch("https://api.example.com/delete", {
  method: "DELETE",
  headers: {
    "Content-Type": "application/json",
    "X-Custom-Header": "value"
  },
  body: JSON.stringify({
    id: "12345"
  })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error("Error:", error));
```

```java {% filename="Java" showLineNumbers=true %}
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.OutputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.nio.charset.StandardCharsets;

public class DeleteExample {
    public static void main(String[] args) {
        try {
            URL url = new URL("https://api.example.com/delete");
            HttpURLConnection connection = (HttpURLConnection) url.openConnection();
            connection.setRequestMethod("DELETE");
            connection.setRequestProperty("Content-Type", "application/json");
            connection.setRequestProperty("Accept", "application/json");
            connection.setDoOutput(true);

            String jsonInputString = "{\"id\": 123}";

            try (OutputStream os = connection.getOutputStream()) {
                byte[] input = jsonInputString.getBytes(StandardCharsets.UTF_8);
                os.write(input, 0, input.length);
            }

            int responseCode = connection.getResponseCode();
            System.out.println("Response Code: " + responseCode);

            if (responseCode == HttpURLConnection.HTTP_OK) {
                try (BufferedReader in = new BufferedReader(new InputStreamReader(connection.getInputStream()))) {
                    String inputLine;
                    StringBuilder response = new StringBuilder();
                    while ((inputLine = in.readLine()) != null) {
                        response.append(inputLine);
                    }
                    System.out.println(response.toString());
                }
            } else {
                System.out.println("DELETE request failed");
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

```php {% filename="PHP" showLineNumbers=true %}
<?php

$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "https://api.example.com/delete");
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "DELETE");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$response = curl_exec($ch);

curl_close($ch);

echo $response;

?>
```

```go {% filename="GO" showLineNumbers=true %}
package main

import (
	"fmt"
	"io/ioutil"
	"net/http"
)

func main() {
	client := &http.Client{}
	req, err := http.NewRequest("DELETE", "https://api.example.com/delete", nil)
	if err != nil {
		fmt.Println(err)
		return
	}

	resp, err := client.Do(req)
	if err != nil {
		fmt.Println(err)
		return
	}
	defer resp.Body.Close()

	body, err := ioutil.ReadAll(resp.Body)
	if err != nil {
		fmt.Println(err)
		return
	}

	fmt.Println(string(body))
}

```

```bash {% filename="cURL" showLineNumbers=true %}
curl -X DELETE "https://api.example.com/delete"
```
{% /codeGroup %}

{% callout type="tip" %}
View source on [**GitHub ↗**](https://github.com/giannihart/httpbin/blob/master/httpbin/core.py#L468-L483)
{% /callout %}
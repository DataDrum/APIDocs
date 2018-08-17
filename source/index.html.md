---
title: Data Drum API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - php
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Data Drum API!

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

Let's get started! Scroll down below to see how you can access the United States annual inflation endpoint in various ways.

# United States Annual Inflation

## Get All Values

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/us_inf_annual.cpi_SA",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/us_inf_annual.cpi_SA", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/us_inf_annual.cpi_SA"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/us_inf_annual.cpi_SA", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

> The above command returns JSON structured like this:

```json
{"status": 200,
 "error": "None",
 "headers": [],
 "data":
  [
    {"date": "1913-01-01", "us_inf_annual___cpi_SA": 0},
    {"date": "1913-02-01", "us_inf_annual___cpi_SA": 0},
    {"date": "1913-03-01", "us_inf_annual___cpi_SA": 0},
    {"date": "1913-04-01", "us_inf_annual___cpi_SA": 0}
  ]
}
```

This endpoint retrieves all values available for U.S. annual inflation.

### HTTP Request

`GET https://api.datadrum.com/json/<INDICATOR>`

## Get a Specific Value

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/us_inf_annual.cpi_SA/1967-09-01",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/us_inf_annual.cpi_SA/1967-09-01", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/us_inf_annual.cpi_SA/1967-09-01"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/us_inf_annual.cpi_SA/1967-09-01", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

> The above command returns JSON structured like this:

```json
{
  "status":200,
  "error":null,
  "headers":[],
  "data":
    [
      {"date":"1967-09-01","us_inf_annual___cpi_SA":2.9096477794793}
    ]
}
```

This endpoint retrieves a specific value.


### HTTP Request

`GET https://api.datadrum.com/json/<INDICATOR>/<DATE>`

## Get the Earliest Value

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/us_inf_annual.cpi_SA/earliest",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/us_inf_annual.cpi_SA/earliest", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/us_inf_annual.cpi_SA/earliest"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/us_inf_annual.cpi_SA/earliest", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

> The above command returns JSON structured like this:

```json
{
  "status":200,
  "error":null,
  "headers":[],
  "data":
    [
      {"date":"1913-01-01","us_inf_annual___cpi_SA":0}
    ]
}
```

This endpoint retrieves the earliest value.


### HTTP Request

`GET https://api.datadrum.com/json/<INDICATOR>/earliest`

## Get the Latest Value

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/us_inf_annual.cpi_SA/latest",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/us_inf_annual.cpi_SA/latest", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/us_inf_annual.cpi_SA/latest"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/us_inf_annual.cpi_SA/latest", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

> The above command returns JSON structured like this:

```json
{
  "status":200,
  "error":null,
  "headers":[],
  "data":
    [
      {"date":"2018-06-01","us_inf_annual___cpi_SA":2.8477600436225}
    ]
}
```

This endpoint retrieves the latest value.


### HTTP Request

`GET https://api.datadrum.com/json/<INDICATOR>/latest`

## Get the a Range of Values

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/us_inf_annual.cpi_SA/2008-08-01/2008-12-01",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/us_inf_annual.cpi_SA/2008-08-01/2008-12-01", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/us_inf_annual.cpi_SA/2008-08-01/2008-12-01"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/us_inf_annual.cpi_SA/2008-08-01/2008-12-01", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

> The above command returns JSON structured like this:

```json
{
  "status":200,
  "error":null,
  "headers":[],
  "data":
    [
      {"date":"2008-08-01","us_inf_annual___cpi_SA":5.3404815922699},
      {"date":"2008-09-01","us_inf_annual___cpi_SA":5.398065171645},
      {"date":"2008-10-01","us_inf_annual___cpi_SA":4.0508854119215},
      {"date":"2008-11-01","us_inf_annual___cpi_SA":1.8944500215115},
      {"date":"2008-12-01","us_inf_annual___cpi_SA":0.26750903554455}
    ]
}
```

This endpoint retrieves a range of values.


### HTTP Request

`GET https://api.datadrum.com/json/<INDICATOR>/<DATE>/<DATE>`
